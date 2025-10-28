Experiment 04: Analyze Email Headers and Detect Email Spoofing using MHA (Mail Header Analyzer)

Aim
To analyze email headers, identify authentication results (SPF, DKIM, DMARC), trace the Received path, and detect possible email spoofing using Mail Header Analyzer (MHA) and manual checks.

Description
Email headers contain metadata that shows the path and handling of an email from sender to recipient. By examining header fields such as Received, Return-Path, Message-ID, SPF, DKIM, and DMARC, you can detect inconsistencies that indicate spoofing or tampering. This experiment walks through accessing headers from common mail providers, parsing key fields, validating authentication, checking IP ownership, and documenting suspicious findings.

Procedure
Step 1: Access the Email Header
- Gmail: Open the email → click ⋮ (More) → **Show original**  
- Outlook (desktop): Open the email → File → Properties → look for the **Internet headers** box  
- Yahoo: Open the email → ⋮ (More) → **View raw message**

Step 2: Copy the Email Header
- Select all text shown in the message header view and copy it to a text file (e.g., `header.txt`) for analysis.

Step 3: Identify Key Header Fields
- From: Sender’s email address  
- To: Recipient’s email address  
- Date: Sent date/time  
- Subject: Subject line  
- Return-Path: Bounce address  
- Received: Chain of servers the message passed through (reverse order)  
- Message-ID: Unique identifier for the message  
- Authentication-Results / SPF / DKIM / DMARC: Authentication verdicts

Step 4: Analyze the `Received` Fields
- Read Received lines from bottom → top to reconstruct the original path.  
- Each Received line typically includes:
  - Sending server hostname/IP
  - Receiving server hostname
  - Timestamp
- Note any large time gaps, mismatched hostnames, or unexpected hops.

Step 5: Check IP Addresses and Hostnames
- For each IP found in Received lines:
  - Perform a WHOIS lookup to find owner and location.
  - Reverse-DNS (PTR) lookup to check hostname.
- Flag IPs that:
  - Do not belong to the expected mail provider, or
  - Resolve to generic or suspicious hostnames.

Step 6: Examine SPF, DKIM, and DMARC Results
- SPF: Confirm the sending IP is authorized for the sender’s domain.
  - Pass = IP is authorized.
  - Fail = suspicious — possible spoof.
- DKIM: Check signature validity to ensure content integrity.
  - Pass = signature valid, content likely untampered.
  - Fail = content may be altered or signature not present.
- DMARC: Confirms alignment between From domain and SPF/DKIM.
  - Pass = policy alignment ok.
  - Fail = potential spoofing; follow domain policy (quarantine/reject) if enforced.

Step 7: Analyze Message-ID
- Inspect the domain in Message-ID. It should match or be plausible for the sender’s domain.
- Strange domains or randomized vendors in Message-ID can be a red flag.

Step 8: Look for Anomalies
- Domain mismatches between From / Return-Path / Message-ID / Authentication-Results.
- Received hops from unrelated or geographically odd IPs.
- Timestamps that go backward or show improbable delays.
- Missing authentication headers for domains that should use them.

Step 9: Use Analysis Tools (optional)
- Paste the header into an online header analyzer or MHA to get a parsed view and automated checks (use MHA output to supplement manual analysis).
- Save MHA output as a text or image file for evidence.

Step 10: Document and Report Findings
- Create a clear report summarizing:
  - Header source (copy of header)
  - IP lookups and WHOIS findings
  - SPF/DKIM/DMARC results
  - Suspicious indicators and final assessment
- If phishing/spoofing is suspected, report to your IT/security team and the email provider.

Example Header (sample)

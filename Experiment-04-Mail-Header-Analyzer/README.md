# Ex. No. 4: Analyze Email Headers and Detect Email Spoofing using MHA (Mail Header Analyzer)

## 🧠Description
This experiment demonstrates how to analyze an email header and detect possible spoofing using the Mail Header Analyzer (MHA).

---

### Step-by-Step Guide

#### 1. Access the Email Header
**Gmail:** Open the email → click ⋮ (three dots) → **Show original**  
**Outlook:** File → Properties → look for the **Internet headers** box  
**Yahoo:** More (⋮) → **View raw message**

#### 2. Copy the Email Header
Once accessed, copy all text. This contains metadata about the email’s route.

#### 3. Identify Key Header Fields
| Field | Description |
|-------|-------------|
| From | Sender’s email address |
| To | Recipient’s email address |
| Date | Sent time |
| Subject | Email subject line |
| Return-Path | Bounce-back address |
| Received | Chain of servers that handled the email |
| Message-ID | Unique identifier for the email |
| SPF/DKIM | Authentication indicators |

#### 4. Analyze the `Received` Fields
Each `Received` line lists:
- Sending & receiving server info  
- IP addresses  
- Timestamp  

They’re in **reverse order** (latest first).

#### 5. Check IPs and Hostnames
Use [WHOIS](https://who.is/) or [MXToolbox](https://mxtoolbox.com/) to identify each IP’s owner and location.  
Watch for mismatched or shady IPs.

#### 6. Examine SPF, DKIM, and DMARC
| Check | Pass | Fail | Meaning |
|-------|------|------|---------|
| SPF | ✅ Authorized | ❌ Not authorized | IP allowed to send from domain |
| DKIM | ✅ Untampered | ❌ Altered | Email integrity verified |
| DMARC | ✅ Aligned | ❌ Spoofing risk | Domain policy verification |

#### 7. Analyze `Message-ID`
Ensure the domain in `Message-ID` matches the sender’s domain. Mismatch = red flag.

#### 8. Look for Anomalies
- Mismatched domains (`From`, `Return-Path`, etc.)  
- Suspicious IPs or hostnames  
- Odd timestamps or routing loops  

#### 9. Use Online Tools
Try:
- [MXToolbox Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- [Google Admin Toolbox](https://toolbox.googleapps.com/apps/messageheader/)

#### 10. Document & Report
Record findings and alert your IT/security team if spoofing is suspected.

---

## 🧩 Example Header Analysis

```plaintext
Received: from mail.example.com (mail.example.com [192.0.2.1])
  by mail.receiver.com with ESMTP id u29si8604336pjs.40.2023.08.10.07.00.16;
  Thu, 10 Aug 2023 07:00:16 -0700 (PDT)
Received: by mail.example.com with SMTP id a1mr1243772ywh.51;
  Thu, 10 Aug 2023 07:00:15 -0700 (PDT)
Message-ID: <CA+7eu=4pSeXgQ@mail.example.com>

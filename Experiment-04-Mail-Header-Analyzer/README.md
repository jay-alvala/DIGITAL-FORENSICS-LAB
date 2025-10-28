*EXPERIMENT -- 4*

*MHA*

*Mail Header Analyzer*

*Link:-* <https://mxtoolbox.com/EmailHeaders.aspx>

*Procedure*

*Step 1: Get the Email Header*

-   First, you need to copy the full, raw header from the email.

-   Gmail: Open the email, click the three dots (⋮), and select Show
    original.

-   Select all the text in the header and copy it.
<img width="1919" height="1019" alt="Image" src="https://github.com/user-attachments/assets/4cc06e95-bce2-4662-9067-402dc176ed15" />
*Step 2: Use a Mail Header Analyzer*

-   The easiest way to analyze the header is with an online tool.

-   Navigate to a site which analyze Email Header

-   Paste the entire header you copied into the analysis box.

-   Click the \"Analyze\" button to get a parsed, easy-to-read report.
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/f79add4c-d4cc-42f9-9887-651916019dec" />
> *Step 3: Analyze The Report*

-   This is the most critical step. In the analyzer\'s report, look for
    the SPF, DKIM, and DMARC results.

*Review the Overall Delivery Summary*

-   First, look at the high-level summary to get an immediate sense of
    the email\'s status.

-   Check DMARC Compliance: The report shows the email is DMARC
    Compliant. This is the most important overall result.

-   Check SPF Status: Both SPF Authenticated and SPF Alignment passed.
    This means the sending server was authorized.

-   Check DKIM Status: DKIM Alignment passed, but DKIM Authenticated
    failed (❌). This is a critical finding and indicates a problem with
    the email\'s digital signature.

*Investigate the SPF Record and Email Path*

-   Next, verify why the SPF check passed.

-   Examine the SPF Record: The SPF record for the domain is v=spf1
    include:mailgun.org \~all. This record explicitly authorizes servers
    from Mailgun to send emails on its behalf.

-   Trace the Relay Information: The delivery path shows the email was
    sent from m241-136.mailgun.net.

-   Conclusion: Since the email came from a Mailgun server, which is
    authorized in the SPF record, the SPF check passed.
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/0d632aae-3824-465a-9bf4-7a3525a5102d" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/86d99d0e-bbbe-4192-8d76-8724154fca8a" />

*Analyze the DKIM Failure*

*References*

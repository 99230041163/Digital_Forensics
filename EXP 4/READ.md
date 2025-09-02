# Ex.No.4   MHA (Mail Header Analyzer)
## Aim :
- The aim is to use a Mail Header Analyzer (MHA) to trace an email's origin and verify its authenticity by examining its header for signs of spoofing.
## Procedure
### Step 1: Get the Email Header
- First, you need to copy the full, raw header from the email.

- Gmail: Open the email, click the three dots (⋮), and select Show original.
<br>
<br>
<img width="1879" height="871" alt="Screenshot 2025-09-01 220218" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20220954.png" />

<br>
<br>


- Select all the text in the header and copy it.

<br>
<img width="1465" height="910" alt="Screenshot 2025-09-01 220301" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20221452.png" />

<br>
<br>

### Step 2: Use a Mail Header Analyzer (MHA)
- The easiest way to analyze the header is with an online tool.

- Navigate to a site like MXToolbox Email Header Analyzer.
 <br>
<br>

  <img width="1918" height="868" alt="Screenshot 2025-09-01 220401" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20221049.png" />

<br>
<br>

- Paste the entire header you copied into the analysis box.
<br>
<br>

Click the "Analyze" button to get a parsed, easy-to-read report.
<br>
<br>

<img width="1900" height="807" alt="Screenshot 2025-09-01 220440" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20221547.png" />

### Step 3: Analyze The Report
- This is the most critical step. In the analyzer's report, look for the SPF, DKIM, and DMARC results.
### Review the Overall Delivery Summary
- First, look at the high-level summary to get an immediate sense of the email's status.

- Check DMARC Compliance: The report shows the email is DMARC Compliant. This is the most important overall result.

- Check SPF Status: Both SPF Authenticated and SPF Alignment passed. This means the sending server was authorized.

- Check DKIM Status: DKIM Alignment passed, but DKIM Authenticated failed (❌). This is a critical finding and indicates a problem with the email's digital signature.
<br>
<br>
<img width="1893" height="888" alt="Screenshot 2025-09-01 220517" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20221642.png" />

<br>
<br>

### Investigate the SPF Record and Email Path
- Next, verify why the SPF check passed.

- Examine the SPF Record: The SPF record for the domain is v=spf1 include:mailgun.org ~all. This record explicitly authorizes servers from Mailgun to send emails on its behalf.

- Trace the Relay Information: The delivery path shows the email was sent from m241-136.mailgun.net.

- Conclusion: Since the email came from a Mailgun server, which is authorized in the SPF record, the SPF check passed.
  <br>
  <br>
  

<br>
<br>
<img width="1817" height="864" alt="Screenshot 2025-09-01 220659" src="https://github.com/sankar12x/img/blob/4ccb233dab815c5dd052003dfb9486ef059cdccd/Screenshot%202025-09-02%20112130.png" />

### Analyze the DKIM Failure

<br>
<img width="1885" height="786" alt="image" src="https://github.com/sankar12x/img/blob/709448667a3f58144adedee3d71beeb7c80b954b/Screenshot%202025-09-01%20222916.png" />

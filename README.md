
# **Email Header Analysis and DNS Investigation**

## **Overview**
This repository contains the analysis of a suspicious email header as part of **Internship Task 2**. The task involved using tools like **MXToolbox** to verify DNS records, SPF, DKIM, and DMARC configurations to determine if the email could be part of a phishing or spam campaign.

The analysis shows issues with the sender's domain authentication, which suggests that the email is potentially malicious.

---

## **Objectives**
1. Analyze the email header to trace its source.
2. Verify **SPF**, **DKIM**, and **DMARC** configurations.
3. Check DNS records for the domain used in the email.
4. Identify signs of phishing or spoofing.

---

## **Tools Used**
- [**MXToolbox**](https://mxtoolbox.com/) – For DNS, SPF, DKIM, and DMARC checks.
- Web browser for manual inspection.
- Provided email header sample.

---

## **Step-by-Step Analysis**

### **1. DNS Lookup**
- **Domain Checked:** `bl3p223mb0050.namp223.prod.outlook.com`  
- **Result:**  
  - ❌ **DNS Record Not Found**  
  - The domain did not return a valid DNS record, indicating it may not be configured correctly or could be spoofed.

**Screenshot Evidence:**  
![DNS Lookup Result](./images/dns_lookup.png)

---

### **2. Email Header Analysis**
The email header was analyzed to check for authentication mechanisms:
- ❌ **DMARC Record Not Found**
- ❌ **SPF Alignment Failed**
- ❌ **SPF Authentication Failed**
- ❌ **DKIM Alignment Failed**
- ❌ **DKIM Authentication Failed**

**Conclusion:**  
The email **failed all major authentication checks**, strongly indicating that the sender may be spoofed or malicious.

**Screenshot Evidence:**  
![Header Analysis](./images/header_analysis.png)

---

### **3. SPF and DKIM Information**
- **Domain Analyzed:** `brasil580programarecompensa.com.br`  
- **Results:**
  - ❌ **DMARC Record:** Not published
  - ❌ **DKIM Signature:** Missing
  - ❌ **SPF Lookup:** No valid name servers found

**Impact:**  
Without SPF, DKIM, or DMARC, this domain cannot prevent email spoofing or verify legitimate senders.

**Screenshot Evidence:**  
![SPF and DKIM Info](./images/spf_dkim_info.png)

---

## **Findings**
| Test                     | Result | Observation |
|--------------------------|--------|-------------|
| DNS Lookup               | ❌ Failed | Domain not properly configured |
| SPF Alignment            | ❌ Failed | Sender policy invalid |
| SPF Authentication       | ❌ Failed | Email not verified |
| DKIM Alignment           | ❌ Failed | No cryptographic signature |
| DKIM Authentication      | ❌ Failed | Email cannot be trusted |
| DMARC Policy             | ❌ Missing | No policy to prevent spoofing |

---

## **Final Conclusion**
The analyzed email shows **clear signs of phishing or spoofing**:
- No valid DNS, SPF, DKIM, or DMARC records.
- Failed alignment and authentication checks.
- Suspicious domain (`brasil580programarecompensa.com.br`) with no proper security setup.

> **Recommendation:**  
> - Do not open any links or attachments in this email.  
> - Report the email to the appropriate security team or email provider.  
> - Organizations should enforce SPF, DKIM, and DMARC policies to prevent spoofing.

---

## **Repository Structure**
```
├── README.md                # Project documentation
└── images/                  # Screenshots for reference
    ├── dns_lookup.png
    ├── header_analysis.png
    └── spf_dkim_info.png
```

---

## **How to Reproduce**
1. Open [MXToolbox](https://mxtoolbox.com/).
2. Paste the suspicious domain or email header.
3. Run tests for:
   - DNS Lookup
   - SPF Record
   - DKIM Record
   - DMARC Record
4. Compare results with this analysis.

---

## **References**
- [MXToolbox Documentation](https://mxtoolbox.com/)
- [SPF, DKIM, and DMARC Explained](https://dmarc.org/)

# Apply-OS-Hardening-Techniques


## **Section 1: Identifying the Network Protocol Involved**

The protocol involved in the incident is the **Hypertext Transfer Protocol (HTTP)**.  
Since the issue involved accessing the **web server for `yummyrecipesforme.com`**, we know that requests to web servers for web pages involve **HTTP traffic**.

Additionally:
- When **`tcpdump` was run**, the log file confirmed **HTTP protocol usage** when accessing the website.
- The **malicious file** was transported to **users’ computers using the HTTP protocol at the application layer**.

---

## **Section 2: Incident Documentation**

### **Customer Reports**
Several customers reported to the **website’s helpdesk** that:
- When visiting the website, they were **prompted to download and run a file** claiming to provide **new recipes**.
- After downloading the file, their **personal computers began operating slowly**.
- The **website owner was locked out** of their **admin account** when attempting to log in.

### **Cybersecurity Analyst Investigation**
- A **sandbox environment** was used to safely open the website **without impacting the company network**.
- A **`tcpdump` session** was started to **capture network traffic packets** while interacting with the site.
- The analyst was **prompted to download a suspicious file**, which was accepted and executed.
- The browser then **redirected the analyst to a fake website**: `greatrecipesforme.com`.

### **tcpdump Log Analysis**
- Initially, the **browser requested the IP address** for `yummyrecipesforme.com`.
- Once the connection was established over **HTTP**, the **malicious file was downloaded and executed**.
- **A sudden change in network traffic** occurred as the browser requested **a new IP address** for `greatrecipesforme.com`.
- **Traffic was rerouted** to the new IP address for **the spoofed website**.

### **Findings from Senior Cybersecurity Analysis**
- The **website’s source code** and **downloaded file** were examined.
- It was discovered that an **attacker manipulated the website’s code** to **prompt users to download a fake browser update**.
- The website owner reported **being locked out of their admin account**.
- It is suspected that the attacker **used a brute force attack** to gain administrative access and change the password.
- **Executing the malicious file** resulted in **compromised end-user computers**.

---

## **Section 3: Recommendations for Preventing Brute Force Attacks**

### **1. Prevent Reuse of Previous Passwords**
- The attacker likely **used a default password** to gain access.
- **Disallowing previous passwords** prevents the **reuse of compromised credentials**.
- This measure ensures that **default passwords cannot be exploited again**.

### **2. Require Frequent Password Updates**
- Enforce **mandatory password changes** at **regular intervals**.
- If an unauthorized person **gains access to a password**, frequent updates **limit its usefulness**.

### **3. Implement Two-Factor Authentication (2FA)**
- 2FA adds an **extra layer of authentication**, requiring:
  - **A password** (something the user knows).
  - **A one-time passcode (OTP)** sent to **email or phone** (something the user has).
- This measure **significantly reduces** the likelihood of **successful brute force attacks**.

---

By implementing **strong password policies, frequent updates, and two-factor authentication**, the organization can **strengthen security** and **prevent similar attacks in the future**.

# Testing Web Vulnerabilities 

  <img src="https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/websec.png?raw=true" alt="Description" width="35%">
<small>Image source:  
<a href="https://www.toptal.com/cybersecurity/10-most-common-web-security-vulnerabilities">https://www.toptal.com/cybersecurity/10-most-common-web-security-vulnerabilities</a></small>


## 📌 Overview
This penetration test, conducted in a simulated Kali Linux environment, assessed a web application's security using a white-hat approach to identify vulnerabilities and strengthen defenses.

## 🚨 Exploits
### SQL Injection
- SQL injection is a high-risk vulnerability that allows attackers to execute unauthorised database queries, potentially compromising the entire system. If an app interacts with a database, it may be vulnerable.
- **Steps taken to complete the exploit**
    - Using a web browser, open ‘http://192.168.0.2/dvwa’
    - Set the security level to Low.
    - Go to the SQL Injection page.
    - In the User ID field, enter: 1' OR '1'='1
    - Click Submit.
    - Look at the results - you should see information for all users, not just one.


  ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image3.png?raw=true)

- **Recommended mitigation**
    - **Use Safe APIs**: Employ APIs that separate data from commands to avoid using interpreters.
    - **Input Validation**: Validate input on the server side to ensure it meets expected formats.
    - **Escape Special Characters**: Properly escape special characters in dynamic queries to prevent injection.
    - **Limit Query Results**: Use SQL controls like LIMIT to restrict the number of records returned.


### Broken Authentication
- Websites often require users to log in with a username and password, assigning each a unique session ID. If not secured, cybercriminals can impersonate users, leading to unauthorised access​.

- **Steps taken to complete the exploit**
    - Start Burp Suite and accept defaults.
    - Configure Firefox to use Burp as a proxy (127.0.0.1:80).
    - Verify web pages are inaccessible.
    - Turn Intercept ON, login to the Mutillidae website, and forward the request.
    - Import/export the CA certificate and install it in Firefox and Chrome.
    - Capture and manipulate the Cookie header in intercepted requests.

 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image4.png?raw=true)
 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image6.png?raw=true)
 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image8.png?raw=true)


- **Recommended mitigation**
    - To prevent broken authentication, use multi-factor authentication, avoid default passwords, check for weak passwords, follow secure password rules, limit failed login attempts and use secure session management to protect user accounts.


### Cross Site Scripting
- Cross-Site Scripting (XSS) attacks occur when harmful code, often JavaScript, is sent to a user's browser through a website. It can steal data, like cookies or trick users into visiting malicious sites.

- **Steps taken to complete the exploit**
    - Log in to http://192.168.0.2/dvwa/login/php (admin/password).
    - Set security level to Low.
    - Go to XSS (Stored) page.
    - Enter name (e.g., "Hacker")
    - Enter message: <script>alert("You have been hacked!");</script>
    - Click "Sign Guestbook".
    - Viewing Guest Book triggers the alert.

 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image1.png?raw=true)
 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image7.png?raw=true)

- **Recommended mitigation**
    - Disabling HTTP TRACE on web servers prevents attackers from stealing cookies via malicious scripts. OWASP's ESAPI helps prevent XSS attacks, while WebGoat offers training on securing web apps.

 
### Insecure Direct Object References
- Insecure Direct Object References (IDOR) allow attackers to access unauthorised data by modifying references (like account IDs) in a URL. If security is weak, users can bypass normal authorisation checks and access restricted objects.

- **Steps taken to complete the exploit**
    - Open the OWASP ZAP tool in Kali Linux.
    - Enter the Metasploitable2 target URL in the "URL to attack" field.
    - Click the "Attack" button to start the scan.
    - After the attack, go to the "Alerts" menu and select "Path Traversal."
    - Identify the URL for the password file.
    - Open a web browser and enter the identified URL to access the password file.

 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image2.png?raw=true)
 ![Description](https://github.com/itstonypham/Testing-Web-Vulnerabilities/blob/images/image9.png?raw=true)

- **Recommended mitigation**
    - To prevent IDOR, always check if a user has permission before accessing objects. Use session-based authentication, avoid exposing identifiers, and replace simple IDs with complex random ones like UUIDs for extra security.


## 🔚 Conclusion
This penetration test identified critical security vulnerabilities that pose significant risks. Immediate remediation is necessary to secure sensitive data, strengthen authentication and prevent exploitation. Implementing the recommended security measures will enhance protection and compliance for the web application.


## 👤 Author
**Tony Pham** – [GitHub](https://github.com/itstonypham) | [LinkedIn](https://www.linkedin.com/in/itstonypham/)

## 🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss.  


## ⭐ Acknowledgments
Thanks to contributors and resources that helped with the project.

---

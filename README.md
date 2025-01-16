# SQL Injection Lab

⚠️ Disclaimer: This project is strictly for educational and ethical hacking purposes and done under controlled environment. Unauthorized use of these techniques is illegal.


## Overview
This lab, conducted by **Ammaruddin Mohammed**, demonstrates the exploitation of SQL injection vulnerabilities using the **Damn Vulnerable Web Application (DVWA)**. The primary objective is to identify and exploit SQL injection points, extract database information, and analyze the results in a controlled environment.

---

## Objectives
1. Understand and exploit SQL injection vulnerabilities in web applications.
2. Use **SQLmap** to enumerate databases, tables, and data.
3. Test the impact of different security levels in DVWA on SQL injection attacks.
4. Highlight the importance of secure coding practices to mitigate such vulnerabilities.

---

## Environment Setup
- **Web Application**: Damn Vulnerable Web Application (DVWA)
- **Server**: Apache2 running on a local host
- **Database Management System (DBMS)**: MySQL
- **Tool Used**: SQLmap

---

## Key Steps and Findings

### Part A: SQL Injection at Low Security
1. **Setup**:
   - Adjusted DVWA’s security settings to **Low**, making the application vulnerable to SQL injection.
   - Logged in to the DVWA interface using credentials.

2. **SQL Injection Process**:
   - Used **SQLmap** to detect and exploit SQL injection vulnerabilities in the application.
   - Enumerated the database names, revealing the following:
     - `information_schema` (default schema)
     - `dvwa` (target application database)

3. **Extracted Tables**:
   - From the `dvwa` database, retrieved the following tables:
     1. `guestbook`
     2. `users`

4. **Dumping Data**:
   - Dumped data from the `users` table and chose the user `gordonb` for further analysis.

---

### Part B: SQL Injection at Medium and High Security
1. **Medium Security**:
   - Used SQLmap to bypass medium-level protections, demonstrating how SQL injection vulnerabilities persist even with moderate defenses.
   - Decrypted MD5 hashes successfully, showcasing the ability to extract sensitive data.

2. **High Security**:
   - SQLmap struggled against the higher security level but still managed to enumerate databases and extract some information, highlighting the importance of robust input validation and security measures.

---

## Tools and Commands
1. **SQLmap**:
   - Used for detecting and exploiting SQL injection vulnerabilities.
   - Commands included flags like `--cookie` (for maintaining session), `--batch` (to automate decision-making), and `--threads` (to optimize attack speed).

2. **Key Commands**:
   - Enumerating databases:
     ```bash
     sqlmap -u "http://localhost/dvwa/vulnerable_page.php?id=1" --cookie="PHPSESSID=session_id" --dbs
     ```
   - Dumping table data:
     ```bash
     sqlmap -u "http://localhost/dvwa/vulnerable_page.php?id=1" --cookie="PHPSESSID=session_id" -D dvwa -T users --dump
     ```

---

## Insights
- **SQL Injection**: A severe vulnerability allowing attackers to access and manipulate database content.
- **Security Levels**: Demonstrated how increasing security levels in DVWA reduced the impact of attacks but required robust defenses to fully mitigate risks.
- **Tools like SQLmap**: Automated SQL injection tools simplify the exploitation process, emphasizing the need for secure coding and regular security assessments.

---

## Recommendations
1. **Secure Coding Practices**:
   - Use prepared statements and parameterized queries to prevent SQL injection.
2. **Input Validation**:
   - Implement strong input validation and sanitization techniques.
3. **Regular Security Audits**:
   - Conduct regular testing to identify and patch vulnerabilities.
4. **Educate Developers**:
   - Train developers on secure coding practices and common vulnerabilities.

---

## Disclaimer
This lab was conducted in a controlled environment using the **Damn Vulnerable Web Application (DVWA)**. The techniques demonstrated are for **educational purposes only**. Unauthorized use of these methods is illegal and unethical.

---

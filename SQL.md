# SQL Injection Basics: A Write-Up

I had the opportunity to explore SQL injection as part of my preparation for my club selection interview, and I would like to document the basics I learned. This write-up highlights key concepts related to SQL queries and how vulnerabilities can arise from improper handling of SQL queries in web applications.

## Introduction to SQL Injection

SQL Injection (SQLi) is a common web security vulnerability that allows attackers to interfere with the queries that an application makes to its database. By manipulating input fields or URL parameters, attackers can execute arbitrary SQL code to access sensitive data, modify database content, or even take control of the database server.

### How SQL Injection Works

SQL Injection occurs when an application includes untrusted data in its SQL queries. For example, if an application allows user input to be included in a query without proper validation or sanitization, an attacker can craft malicious SQL queries that change the structure or logic of the original query.

Consider the following example:
```
SELECT * FROM users WHERE username = 'user_input';
```
If the user_input is not properly sanitized, an attacker could supply a value like ' OR '1'='1, which would result in the following query:
```
SELECT * FROM users WHERE username = '' OR '1'='1';
```
This query would return all records from the users table, bypassing authentication.

Types of SQL Injection
In-band SQLi: The most common type, where the attacker uses the same communication channel to both launch the attack and gather results.

Blind SQLi: Occurs when the attacker can send queries but cannot see the results directly. This usually happens when error messages are suppressed.

Out-of-band SQLi: This type of SQL injection uses a different communication channel to retrieve the results, such as via email or DNS requests.

Preventing SQL Injection
Based on my learning, the following best practices are key to preventing SQL injection attacks:

Parameterized Queries (Prepared Statements): Using parameterized queries ensures that user input is treated as data, not executable code. This is the most effective way to mitigate SQL injection risks.

Example in Python using sqlite3:
```
cursor.execute("SELECT * FROM users WHERE username = ?", (user_input,))
```
Input Validation and Sanitization: Always validate and sanitize user input. Ensure that input matches the expected format (e.g., a username should not contain special characters or SQL keywords).

Stored Procedures: Utilizing stored procedures can add an additional layer of security by abstracting direct access to the database. However, this alone is not sufficient if user inputs are not properly sanitized within the stored procedure itself.

Least Privilege Principle: Ensure that database users have the minimum permissions necessary to perform their tasks. For example, the user account used by the web application should not have administrative privileges.

Error Handling: Avoid displaying detailed error messages to users, as they can reveal information about the database structure or application logic. Instead, log errors securely on the server side.

Conclusion :
Through my exploration of SQL injection, I gained a foundational understanding of how improperly handled SQL queries can lead to serious security vulnerabilities. Learning how to mitigate these risks through techniques like parameterized queries and input validation is critical for developing secure web applications.

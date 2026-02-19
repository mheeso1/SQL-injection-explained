# SQL-injection-explained
Todays topic: SQL Injections
Here is your blog post in clean English without emojis and without hyphen separators.

SQL Injection and Other Common Web Attacks

Introduction

Web applications are one of the primary targets in offensive security. Many real world breaches are not caused by complex zero day exploits but by simple input handling mistakes. One of the most well known vulnerabilities is SQL injection. In this article I explain how SQL injection works and briefly cover other common web attack vectors.

What is SQL Injection

SQL injection is a vulnerability that occurs when user input is directly inserted into a database query without proper sanitization or parameterization. An attacker can manipulate the original SQL query and inject malicious SQL code.

Example of a Vulnerable Query

Imagine a login system that builds a query like this:

SELECT * FROM users WHERE username = ‘input’ AND password = ‘input’

If the application directly inserts user input into the query, an attacker could enter the following as the password:

’ OR ‘1’=’1

The query would then become:

SELECT * FROM users WHERE username = ‘admin’ AND password = ‘’ OR ‘1’=‘1’

Since the condition 1 equals 1 is always true, the authentication check is bypassed and login succeeds.

Why This Works

The application fails to distinguish between data and code. Everything provided by the user becomes part of the SQL statement. This allows the attacker to alter the logic of the query.

Impact of SQL Injection

Reading sensitive data
Bypassing authentication systems
Modifying or deleting database content
Extracting entire databases

In severe cases attackers can escalate the attack to full system compromise depending on database configuration and permissions.

Types of SQL Injection

Error based SQL injection
The application returns detailed database error messages. These errors can reveal table names and database structure.

Union based SQL injection
The attacker uses UNION SELECT to combine results from other tables and extract additional data.

Blind SQL injection
The application does not show database errors. The attacker relies on true or false conditions and analyzes application behavior.

Time based SQL injection
The attacker triggers database delays to infer whether certain conditions are true.

How to Prevent SQL Injection

Use prepared statements
Use parameterized queries
Validate and sanitize input
Do not expose detailed error messages
Apply the principle of least privilege for database accounts

Other Common Web Attacks

Cross Site Scripting
Attackers inject malicious JavaScript into web pages. The goal is often to steal session cookies or perform actions on behalf of victims.

Command Injection
User input is executed as a system command on the server. This can lead to full server compromise.

Directory Traversal
Attackers manipulate file paths to access restricted files such as configuration files or password files.

Insecure Direct Object References
Applications expose internal object identifiers without proper access control checks.

Server Side Request Forgery
The application fetches remote resources based on user input. Attackers abuse this to access internal systems.

Conclusion:

SQL injection remains one of the most dangerous and common web vulnerabilities. Understanding how it works is essential for both attackers and defenders. Many web attacks rely on the same fundamental mistake: trusting user input.

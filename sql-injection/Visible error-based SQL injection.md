# Lab: Visible error-based SQL injection

**Difficulty:** Practitioner
**Category:** SQL Injection
**Link:** https://portswigger.net/web-security/sql-injection/blind/lab-sql-injection-visible-error-based

## 1. Lab Description

This lab contains a SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie. The results of the SQL query are not returned

The database contains a different table called users, with columns called username and password. To solve the lab, find a way to leak the password for the administrator user, then log in to their account

## 2. Reconnaissance / Initial Analysis

- I opened the page and researched it. I read the lab description and searched for the parameter "trackId". Then I pasted "'", and I understood that the lab has an SQL injection vulnerability

![I found parameter](../images/visible_error_based_sql_injection_recon.jpg)

## 3. Exploitation Step-by-Step

1. I decided to try sending "AND (SELECT 1)" and saw this:

![Need boolean type](../images/visible_error_based_sql_injection_need_boolean_type.jpg)

2. Then I decided to convert it to a boolean expression using 1=(SELECT 1)

![Convert Boolean Type](../images/visible_error_based_sql_injection_convert_to_boolean_type.jpg)

3. I decided to add CAST, and I got the username and password fields and the table name from the lab description. I received an error because there were too many characters

![Many characters](../images/visible_error_based_sql_injection_many_chars.jpg)

4. I fixed it by deleting the cookie (MySQL error messages are limited to 32 characters)

![Many strings](../images/visible_error_based_sql_injection_many_strings.jpg)

5. Then I fixed it using LIMIT 1

![Return username](../images/visible_error_based_sql_injection_return_username.jpg)

6. I got the password by changing the field from username to password

![Return password](../images/visible_error_based_sql_injection_return_password.jpg)

7. Then I sent these credentials to the login page and logged in

![Completed this lab](../images/visible_error_based_sql_injection_final.jpg)
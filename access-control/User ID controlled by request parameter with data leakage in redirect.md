# Lab: User ID controlled by request parameter with data leakage in redirect

**Difficulty:** APPRENTICE<br>
**Category:** Broken Access Control<br>
**Link:** https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect

## 1. Lab Description

This lab contains an access control vulnerability where sensitive information is leaked in the body of a redirect response

To solve the lab, obtain the API key for the user carlos and submit it as the solution

You can log in to your own account using the following credentials: wiener:peter

## 2. Reconnaissance / Initial Analysis

- I opened the page and analyzed it. After reading the lab description, I logged in to my account. Then, I noticed my API key in the page
- Next, I tried open another pages on this web site because I needed get more information
- Then, I noticed "id" parameter in URL

<!-- ![My account page](../images/user_id_controlled_by_request_parameter_with_data_leakage_in_redirect1.png) -->

## 3. Exploitation Step-by-Step

1. Finally, I changed "id" parameter in URL

![My account page](../images/user_id_controlled_by_request_parameter_with_data_leakage_in_redirect1.png)

2. I saw carlos's API key and success solved the lab

![I solved the lab](../images/user_id_controlled_by_request_parameter_with_data_leakage_in_redirect2.png)

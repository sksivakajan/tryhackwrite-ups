Reflected XSS in HTML Context - Challenge Write-Up

Introduction

Welcome to the Reflected XSS in HTML Context challenge! In this room, you will be exploring a classic Reflected Cross-Site Scripting (XSS) vulnerability. Your task is to identify and exploit this vulnerability in the web application and capture the hidden flag. XSS attacks can allow attackers to inject client-side scripts into web pages viewed by other users, potentially leading to severe consequences.

In this lab, no special encoding has been applied to the HTML context, making it vulnerable to script injection.

Challenge Setup

You are presented with a basic web application that includes a search feature. This search page does not properly sanitize the user’s input, which leads to a reflected XSS vulnerability. Your goal is to find this vulnerability, inject a malicious script, and retrieve the hidden flag.

Objective

Find the Reflected XSS vulnerability in the search feature of the web application.
Trigger an alert box using a simple JavaScript injection.
Reveal the hidden flag by exploiting the vulnerability.
Step-by-Step Solution

1. Inspect the Web Application
Open the web application’s homepage and navigate to the search functionality (usually found on a page like search.php).
On this page, there is an input field that allows users to search for terms.
Try entering a simple search term and observe the output to see how the input is reflected in the HTML response.

2. Inject a Basic XSS Payload
The key to solving this challenge is to exploit the search field, which directly reflects user input into the HTML output without proper sanitization.
Start by injecting a basic XSS payload:
                   <script>alert('XSS')</script>
Enter this payload into the search field and submit the form.
If successful, you will see a pop-up alert box displaying the message 'XSS'.

3. Capture the Flag
Now that you’ve confirmed the presence of an XSS vulnerability, the next step is to retrieve the hidden flag.
Typically, the flag is stored in the application’s session or cookie. To access this information, use another XSS payload:
      <script>alert(document.cookie)</script>
Inject this payload into the search field and submit it.
The alert box will now display the contents of the document.cookie, which will include the flag.
The flag will look something like this: FLAG{***_******}.

4. Example Output
After successfully injecting the XSS payload, you will see an alert box similar to the following:
    FLAG{***_******}
   
5.Remediation

In real-world applications, preventing XSS vulnerabilities is crucial. Here are some best practices to avoid such vulnerabilities:

Input Validation: Always validate and sanitize user input. Never trust user inputs directly, and ensure special characters like <, >, &, etc., are properly encoded.
Output Encoding: Encode user inputs when reflecting them in the HTML context. This prevents the execution of malicious scripts.
Content Security Policy (CSP): Implement CSP headers to restrict the execution of inline JavaScript, reducing the potential for XSS attacks.
Use Secure Frameworks: Leverage frameworks or libraries that automatically handle input/output sanitization, like React or Angular.

6.Conclusion
This challenge highlights the risk of Reflected XSS vulnerabilities in web applications. By following proper input validation, output encoding practices, and adopting modern security headers like CSP, developers can mitigate the risk of such vulnerabilities. Congratulations on completing the challenge!

7.References

 OWASP XSS Prevention Cheat Sheet

 Mozilla Developer Network (MDN) - Cross-Site Scripting (XSS)





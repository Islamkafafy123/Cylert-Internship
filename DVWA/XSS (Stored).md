# low
- the provided form
- two input fields, "Name" and "Message". Upon clicking the "Sign Guestbook" button, the two fields get echoed below the form
- proof-of-concept XSS test
-  form restricts "Name" input to 10 characters and "Message" input to 50 characters.
-  task for the stored XSS DVWA vulnerability is to make a redirect to an external page
-  add an <img> element that, on error, opens a page
-  ```
   <img src="https://nonexisting.url" onerror=window.open("https://www.owasp.org","xss",'height=500,width=500');>
   ```
-  text field has a max size of 50 characters, we have to extend it, otherwise our payload won’t fit the field
-  and we got the redirect
# Medium
- our former attack vector, the "Message" field, has been locked down pretty well, with multiple functions for input sanitization.
-  However, the "Name" field didn't get the same treatment
- only being subjected to a simple, case-sensitive removal of <script>.
- like last time, that the improperly-sanitized "Name" field truncates all input to a maximum of 10 characters
- that's only on the client-side form. If we can intercept the HTTP request in Burp Suite and insert our modified exploit in the "Name" field there
- we got the redirect

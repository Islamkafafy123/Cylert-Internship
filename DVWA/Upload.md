# Low
- a simple file upload form
- immediately try to upload s reverse shell
-  form tells you exactly where the newly-uploaded shell is!
-  hackable/uploads/php-reverse-shell.php
-  we run netcat
-  and go to http://192.168.206.128/dvwa/hackable/uploads/php-reverse-shell.php
-  we got a shell
# Medium
- medium DVWA file upload level, there are two filters added: for the file name and file size.
- the allowed type is image/jpeg
- start Burp Suite with a proxy and try to upload the same file we used for the low security level. But before forwarding it make sure you stopped it in Burp Suite.
- there is a Content-Type header that has a value application/x-php
- edit this value (Content-Type: image/jpeg) and forward the request with our PHP script.
- now go to the same path and open netcat and we got a shell
- 

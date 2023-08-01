# 1) Injection
- all about injecting SQL, NoSQL, OS, and LDAP into the application. It can be as SQL queries through the input interface of the application. Successful SQL injection can lead to sensitive data from the database being exposed.
- occurs when data is inserted into a program from an untrusted source because of the lack of input validation and data sanitization, which can directly expose input into the query
- Injection Mitigation :
  - use of Prepared Statements with Parameterized queries
  - use of Stored Procedures
  - Implement input validation and sanitization
  - escaping all user-supplied input

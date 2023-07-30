# Low
- might be trickier to check if an input field leads to the blind SQL injection. It does differ from the classical SQL injection by the fact that it does not show directly the results of injection
- By executing the query and checking if there are any errors on the page is one of the ways to test for blind SQL
- Another way, that will be used in our DVWA blind SQL injection example, is trying to inject sleep operation into the database
- By comparing normal behavior to the application behavior after sleep() injection
- add the mentioned sleep function: ' or sleep(5)#
- and we break the app by letting it sleep for 5 sec
# Medium
- we see source code and there is mysql function that strip :'
- we try same payload without it and it works : 1or sleep(5)#


# Assignment 5

## Knock Knock...
We inspected the `/var/log/auth.log` file and looked for the successful logins.
We used this command to filter out the usernames with the number of logins: `cat /var/log/auth.log | grep opened | awk {'print $11'} | sort | uniq -c`

We got the following results:
![alt](img/ass5_1.png)

## Never send a human to do a machine's job
We knew that we are intersted in authentication log, which we can find in `/var/log/auth.log`. Also we knew that we are looking for authentication failures. We put this together and composed this command:

`cat /var/log/auth.log | grep 'authentication failure`

From which we received this output:

![alt](img/ass5_2.png)

We can observe, that there were 3 failed attempts, but one of them was from user 'link', whom is not a Matrix character. So we tried number 2 and it was a right answer.
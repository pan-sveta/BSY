# Assignment 5

## Never send a human to do a machine's job
We knew that we are intersted in authentication log, which we can find in `/var/log/auth.log`. Also we knew that we are looking for authentication failures. We put this together and composed this command:

`cat /var/log/auth.log | grep 'authentication failure`

From which we received this output:

![alt](img/ass5_2.png)

We can observe, that there were 3 failed attempts, but one of them was from user 'link', whom is not a Matrix character. So we tried number 2 and it was a right answer.
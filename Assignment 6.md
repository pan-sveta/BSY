# Assignment 6
## Criminal Mastermind
We started by exploring the assigned IP and tried to connect with SSH. Naturally, we did not have the password, and with Nmap, it does not seem to be a vulnerable SSH version, so we had to brute-force our access.

In the hint, there was a lead that "Moriarty's favourite movies are superhero blockbusters" we assumed this was a hint to create a related wordlist. We used [this](https://github.com/sindresorhus/superheroes/blob/main/superheroes.json) JSON file to prepare a wordlist with all the heroes.

With the help of the Nmap script, we have started our attack.

`nmap -sS -sV -p 22 172.16.1.59 -v -n --script ssh-brute --script-args userdb=mor.txt,passdb=fancy.txt,brute.firstonly=true,timeout=5h`

We got lucky since the password was `Aquaman`. We quickly started working on our persistence. For this, we decided to use ssh. We copied the public SSH key from our machine and executed the following commands.

`mkdir -p ~/.ssh`

`touch ~/.ssh/authorized_keys`

`{our_public_key} >> ~/.ssh/authorized_keys`

After logging out, we discovered that we indeed have persistence. We began to look for the flag.

We quickly discovered a file named `final_problem.txt` in our home directory. But the connection was just a part of the flag. We saved this part and started looking in the fs for other parts. After a while, our ssh connection was interrupted, which was weird. We tried to log in after a time, and we were still able to log in. We checked the file in the home directory again, and BINGO! It has changed. We figured out that we had to wait for the whole flag.

After two more connection interruptions, we concatenated the flag, and it worked.

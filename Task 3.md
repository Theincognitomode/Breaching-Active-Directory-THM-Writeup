# Task 3 NTLM Authenticated Services

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/a4f74bd3-632d-4c54-b443-ca64a02036cf)

This diagram is more then sufficient to understand the working of a NTLM Authentication system, the main advantage of this system is that  the user is not authenticated directly on the application itself, 
but the NTLM acts as a middle man between the client and the AD which prevents the application from storing AD credentials, which should only be stored on a Domain Controller.

# Brute-force Login Attacks

In order to perform this task we will be using the python script that is given in the task files, we can also use the hydra!!


If you are instreated in using hydra the command of hydra will look something like this:


    hydra -L users.txt -P Changeme123 http://ntlmauth.za.tryhackme.com/ http-post-form "/login.php:username=^USER^&password=^PASS^:F=incorrect"


Or another method is to use the python script which is recommended..


Donwload the task file you will get the python file as well as the username.txt file in it then simply run the command:

    python ntlm_passwordspray.py -u usernames.txt -f za.tryhackme.com -p Changeme123 -a http://ntlmauth.za.tryhackme.com/

The output will be like this 
![Screenshot 2023-11-03 234433](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/0b4dec7c-c114-4df3-838a-4ad345677c63)


Now lets answer the questions:


**Q. 
What is the name of the challenge-response authentication mechanism that uses NTLM?**

    NetNTLM

**Q. What is the username of the third valid credential pair found by the password spraying script?**

    gordon.stevens

**Q. 
How many valid credentials pairs were found by the password spraying script?**

    4

**Q. 
What is the message displayed by the web application when authenticating with a valid credential pair?**

    Hello World

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/5e058505-6e7e-4f5e-99e0-eaeef07ed95b)



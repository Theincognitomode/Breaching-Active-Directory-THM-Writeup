# Authentication Relays

Continuing with attacks that can be staged from our rogue device, we will now look at attacks against broader network authentication protocols. In Windows networks, there are a significant amount of services talking to each other, allowing users to make use of the services provided by the network.

These services have to use built-in authentication methods to verify the identity of incoming connections. In Task 2, we explored NTLM Authentication used on a web application. In this task, we will dive a bit deeper to look at how this authentication looks from the network's perspective. However, for this task, we will focus on NetNTLM authentication used by SMB.

# Intercepting NetNTLM Challenge

For this we will first set the responder !

    set responder -I breachad

After doing so we will now start the responder and will wait for 10 mins to see the hash of the password  

    responder -I breachad


After 10 mins the output screen will look something like this:

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/f4b58f4e-946b-4edd-a0e2-dc674b8bb6b9)


Then save the hash, use `john` or `hashcat` to break the hash 

Now lets answer the questions :

**Q. What is the name of the tool we can use to poison and capture authentication requests on the network?**

    Responder


**Q. What is the username associated with the challenge that was captured?**

    svcfilecopy

**Q. What is the value of the cracked password associated with the challenge that was captured?**

    FPassword1!


Lets move forward with task 6.

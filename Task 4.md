# Task 4 LDAP Bind Credentials


LDAP (Lightweight Directory Access Protocol) :

LADP authentication is similar to NTLM authentication, the main difference between them is that in LADP authentication the application directly verifies the user's credentials.

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/17a724cb-0058-4b83-ad6a-2aa630c84487)

# LDAP Pass-back Attacks

However, one other very interesting attack can be performed against LDAP authentication mechanisms, called an LDAP Pass-back attack. This is a common attack against network devices, 
such as printers, when you have gained initial access to the internal network, such as plugging in a rogue device in a boardroom.

 In an LDAP Pass-back attack, we can modify this IP to our IP and then test the LDAP configuration, which will force the device to attempt LDAP authentication to our rogue device. We can intercept this authentication attempt to recover the LDAP credentials.


 Lets Perform a LDAP Pass-back


 We are given a printer network : http://printer.za.tryhackme.com/settings.aspx  where the administration website does not even require credentials.

 ![inspect](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/67997abc-09d9-4bed-9447-7d40050a7357)

 By using the inspect option we can verify that the printer website was at least secure enough to not just send the LDAP password back to the browser.


 So we have the username, but not the password. However, when we press test settings, we can see that an authentication request is made to the domain controller to test the LDAP credentials. Let's try to exploit this to get the printer to connect to us instead, which would disclose the credentials. To do this, let's use a simple Netcat listener to test if we can get the printer to connect to us. 


Before doing so make sure to change the **server's ip address** with that of the current one for ex in my case its 10.200.20.101, cause if we dont change the server you will see an error i.e LDAP Connection was unsuccessful


In order to get a reverse shell use the command 

    nc -lnvp 389

Now we have to send the `Test settings` 2-5 times in order to get a reverse shell.


If the authentication method is too secure, the credentials will not be transmitted in cleartext. With some authentication methods, the credentials will not be transmitted over the network at all! So we can't just use normal Netcat to harvest the credentials. We will need to create a rogue LDAP server and configure it insecurely to ensure the credentials are sent in plaintext.


# Hosting a Rogue LDAP Server

If u are using attack box its already there if you are using virtual machine install it using this command 

    sudo apt-get update && sudo apt-get -y install slapd ldap-utils && sudo systemctl enable slapd

Go through the task for the installation process and make sure to follow each steps carefully..


After going through this now lets answer the questions:


**Q. What type of attack can be performed against LDAP Authentication systems not commonly found against Windows Authentication systems?**

    LDAP Pass-back Attacks


**Q. What two authentication mechanisms do we allow on our rogue LDAP server to downgrade the authentication and make it clear text?**

    plain, login

**Q. What is the password associated with the svcLDAP account?**

    tryhackmeldappass1@


Now lets move forward with task 5.

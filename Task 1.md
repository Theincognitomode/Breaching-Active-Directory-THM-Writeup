 # Introduction to AD Breaches

 Active Directory (AD) is used by approximately 90% of the Global Fortune 1000 companies. If an organisation's estate uses Microsoft Windows, you are almost guaranteed to find AD. Microsoft AD is the dominant suite used to manage Windows domain networks. However, since AD is used for Identity and Access Management of the entire estate, it holds the keys to the kingdom, making it a very likely target for attackers.



 # How to connect using OpenVPN


 1. Download the Openvpn file from the access option under your profile pic

 
 ![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/643dfdf0-1110-4177-998d-ce688ceb573d)

 2. Now click on networks and choose the Breachingad file and download it..

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/5359782d-fdd8-4248-9234-8fb8e46d4a74)


3. Now after donwloading run the file using the command `sudo openvpn <filename>`
After running the command you will get a IP but you are not done yet the next few steps are very important do them carefully..

- If you are using a Virtual machine then go to the `wisher menu` and search for `Advanced Network Configuration` open it

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/1603ba02-0438-42d7-acb3-fd8cf12ce93f)

You will see a menu like this now click on `Wired Connection` in that navigate to the option `IPv4 settings` and add the `TMDC IP address` in it 

![Screenshot 2023-11-03 225859](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/d3e0aac5-90c3-475a-b2e6-2b456f386c5e)'


![dns settings](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/eff50b07-ff18-4cb5-b547-ebcf4a9b01a9)

After doing this save the settings and then run the command to verify your connection :


    nslookup thmdc.za.tryhackme.com


If you are connected the output will look like this :

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/83410ac5-44c8-4e87-a5e8-86b20c8f3fc0)

After doing all this you are good to move to the **Task 2** now 


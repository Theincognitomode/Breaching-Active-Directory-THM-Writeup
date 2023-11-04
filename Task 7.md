# Task 7  - Configuration Files


The last enumeration avenue we will explore in this network is configuration files. Suppose you were lucky enough to cause a breach that gave you access to a host on the organisation's network. In that case, configuration files are an excellent avenue to explore in an attempt to recover AD credentials. Depending on the host that was breached, various configuration files may be of value for enumeration: 

- Web application config files
- Service configuration files
- Registry keys
- Centrally deployed applications


**Configuration File Credentials**

1. cd to MCafree DB

       cd C:\ProgramData\McAfee\Agent\DB

2. Copy the contents in out machine using the `scp`

        scp thm@THMJMP1.za.tryhackme.com:C:/ProgramData/McAfee/Agent/DB/ma.db .

3. Read the db using any tool that you like to use in my casse will move with the task ..

       sqlitebrowser ma.db

Make sure to select the option **AGENT_REPOSITORIES**

![image](https://github.com/Theincognitomode/Breaching-Active-Directory-THM-Writeup/assets/73027020/d1755bee-ccb9-486d-a297-a807ead01a83)

Now we are only instrested in the second entry of this table..

Now download the task file and unzip in, in the zip folder there is python file which is cable of base64 encoded and encrypted password, the script will provide the decrypted password

    python2 mcafee_sitelist_pwd_decrypt.py <Auth value>

Lets answer the questions :

**Q. What type of files often contain stored credentials on hosts?**

    Configuration File 

**Q. What is the name of the McAfee database that stores configuration including credentials used to connect to the orchestrator?**

    ma.db

**Q. What table in this database stores the credentials of the orchestrator?**

    AGENT_REPOSITORIES

**Q. What is the username of the AD account associated with the McAfee service?**

    svcAV

**Q. What is the password of the AD account associated with the McAfee service?**

    MyStrongPassword!

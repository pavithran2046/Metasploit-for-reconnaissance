# EX-5.Metasploit-for-reconnaissance
## Date:7/10/24
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode
2) Investigate on the various categories of tools as follows
3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/892396e2-54aa-422a-98c1-99074ab301c8)


Invoke msfconsole:

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/ae3f59e3-9953-4a72-ad50-89229e92de07)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/db1a0bdd-bbe1-435c-8313-9217ec87f781)


Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/1d215848-9a2c-40ba-ae28-36dfe7d8cc50)


USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24


## OUTPUT:

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/34a5d5e4-287c-41e4-8eee-68c8cce8828b)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/d2b49d50-dbb7-4339-a963-017f80a8d30f)


Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/5cf833ec-58f8-4877-b512-39c68b71fa2c)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/375031c3-0897-4056-8033-d9d82f6a0545)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/df5536aa-ec48-441d-9bbc-9b6bee919e36)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/d3b2c581-a224-421f-8bc1-d2bb4262d3ae)


Use the set rhosts command to set the parameter and run the module, as follows:

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/60f381e4-c1e4-4029-8632-f80aabc22367)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/d9c01906-64f8-4505-870e-c541e614bff2)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![image](https://github.com/Darkwebnew/Metasploit-for-reconnaissance/assets/143114486/7c4bc53c-c226-4872-ba71-03772dc4cf9d)

## RESULT:

The Metasploit framework for reconnaissance is  examined successfully

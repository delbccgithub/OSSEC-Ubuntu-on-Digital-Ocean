
# OSSEC-Ubuntu on Digital Ocean Droplet (Lastest Update: Nov 2021)



### OSSEC installation tutorial.


<img src="https://www.ossec.net/wp-content/uploads/2019/01/ossec.png" width=50% height=50%> 


*Have a question or need information? Please refer to the **[FAQ](#faq)** section at the bottom of the page.*

</br>

<ins>Synopsis:</ins>

This tutorial will briefly go over the installation of OSSEC within a Digital Ocean droplet.
Additionally, we will also install the OSSEC agent (via Windows) to report to this server. And as a last step we’ll also install a web user interface to look for alerts.

</br>

<ins>Instructions:</ins>

[1. Installing OSSEC on Ubuntu Server using DigitalOcean.](#1-lets-begin-the-installation-of-ossec-ubuntu-using-digitalocean)

[2. Setting up an OSSEC agent using Windows.](#2-next-setting-up-an-agent-and-connecting-to-the-server)

[3. Installing the Web User Interface.](#3-installing-the-web-user-interface)

[4. Demo (Video)](#demo-instructional-video)

[5. FAQ.](#faq)

[6. Reference.](#possible-errors)


[7. Reference.](#reference)

[8. Credit.](#this-project-was-created-while-attending-a-course-at-bronx-community-college)

</br>


## 1. Let's begin the Installation of OSSEC Ubuntu using DigitalOcean:

<img src="https://images.squarespace-cdn.com/content/v1/5980deaee6f2e1738e18738c/1550165343634-2QDHAJHNQ82KZZ8KY91C/start-here-gif.gif" width=50% height=50%>

Update system sources

``` $ sudo apt update ``` 

<br/>
<br/>

Upgrade packages

``` $ sudo apt upgrade -y ``` 

<br/>
<br/>

Install the packages to build OSSEC from sources.

``` $ sudo apt install build-essential gcc make unzip sendmail inotify-tools expect libevent-dev libpcre2-dev libz-dev libssl-dev -y ``` 


<br/>
<br/>


Begin to download OSSEC.

 ``` $ sudo wget -P /opt https://github.com/ossec/ossec-hids/archive/3.6.0.tar.gz ``` 


<br/>
<br/>


Extract them from the tar. Use the following command:

 ``` $ sudo tar -zxf /opt/3.6.0.tar.gz --directory /opt ``` 

<br/>
<br/>


Once downloaded start the installation.

 ``` $ sudo sh /opt/ossec-hids-3.6.0/install.sh ``` 

<br/>
<br/>


The first questions is what language would you like to install OSSEC in on your system.

 ``` $ sudo sh /opt/ossec-hids-3.6.0/install.sh ``` 

<br/>
<br/>



(en/br/cn/de/el/es/fr/hu/it/jp/nl/pl/ru/sr/tr?) [en]:

I’ll choose the default. (Select differently if you want another language.)

Than  ``` PRESS ENTER. ``` 

<br/>
<br/>



Next install the OSSEC script.

OSSEC HIDS v3.6.0 Installation Script - http://www.ossec.net


You are about to start the installation process of the OSSEC HIDS.

You must have a C compiler pre-installed in your system.


- System: Linux ossecman 4.15.0-88-generic

- User: root

- Host: ossecman

 ``` -- Press ENTER to continue or Ctrl-C to abort. -- ``` 


<br/>
<br/>



Answer the following questions:

1- What kind of installation do you want (server, agent, local, hybrid or help)?

Type  ``` server ``` . 

<br/>
<br/>


You'll see.

- Server installation chosen.


Choose where to install OSSEC.

2- Setting up the installation environment.


- Choose where to install the OSSEC HIDS [/var/ossec]:

 ``` Use the default by pressing enter ``` 

<br/>
<br/>



Proceed to configure OSSEC.

3- Configuring the OSSEC HIDS.


3.1- Do you want e-mail notification? (y/n) [y]:

Type  ``` Yes ``` 

<br/>
<br/>



- What's your e-mail address?

 ``` Type the **your email** or use **root@localhost** ``` 

<br/>
<br/>



3.1- Do you want e-mail notification? (y/n) [y]:

<br/>

Type  ``` Y ``` 

<br/>
<br/>

- What's your e-mail address? root@localhost or your email address.


- We found your SMTP server as: 127.0.0.1 or IP Address of server 


- Do you want to use it? (y/n) [y]:

<br/>

Type  ``` Y ``` 

<br/>
<br/>

Note: This option alerts will be root’s mail account. And they will read similar to this following format.



3.2- Do you want to run the integrity check daemon? (y/n) [y]:

<br/>

Type  ``` Y ``` 


<br/>
<br/>


Time to ask if a rootkit check daemon is of your interest. Why not? 


<br/>

Type  ``` Y ``` 


<br/>
<br/>


3.3- Do you want to run the rootkit detection engine? (y/n) [y]:

<br/>

 ``` Y ``` 


<br/>
<br/>


3.4- Active response allows you to execute a specific

command based on the events received. For example,

you can block an IP address or disable access for

a specific user.

More information at:

http://www.ossec.net/en/manual.html#active-response

- Do you want to enable active response? (y/n) [y]:

If you want strongest security than choose:


<br/>

Type  ``` Y ``` 

<br/>
<br/>


Now we’ll be aksed an interesting question.

- By default, we can enable the host-deny and the

firewall-drop responses. The first one will add

a host to the /etc/hosts.deny and the second one

will block the host on iptables (if linux) or on

ipfilter (if Solaris, FreeBSD or NetBSD).

- They can be used to stop SSHD brute force scans,

portscans and some other forms of attacks. You can

also add them to block on snort events, for example.

- Do you want to enable the firewall-drop response? (y/n) [y]: 

<br/>

Choose  ``` Y ``` 


<br/>
<br/>



If you choose yes you’ll see something like this.


- firewall-drop enabled (local) for levels >= 6

- (_note_an_ip_address_should_appear_here)


Go to next question.


Now, this question will be asked.

Do you want to add more IPs to the white list? (y/n)? [n]:

 ``` Press Enter ``` 

<br/>
<br/>


Next, is enabling system log remotely.


3.5- Do you want to enable remote syslog (port 514 udp)? (y/n) [y]:

 ``` Press Enter ``` 

<br/>
<br/>



Now after all the questions you should see something similar to this message.


3.6- Setting the configuration to analyze the following logs:

-- /var/log/auth.log

-- /var/log/syslog

-- /var/log/dpkg.log


 ``` --- Press ENTER to continue --- ``` 

<br/>
<br/>



The last message from the build will read very similar to this.

- System is Debian (Ubuntu or derivative).

- Init script modified to start OSSEC HIDS during boot.

- Configuration finished properly.

- To start OSSEC HIDS:

/var/ossec/bin/ossec-control start

- To stop OSSEC HIDS:

/var/ossec/bin/ossec-control stop

- The configuration can be viewed or modified at /var/ossec/etc/ossec.conf

Thanks for using the OSSEC HIDS.

If you have any question, suggestion or if you find any bug,

contact us at https://github.com/ossec/ossec-hids or using

our public maillist at

https://groups.google.com/forum/#!forum/ossec-list

More information can be found at http://www.ossec.net

<br/>
<br/>


 ``` --- Press ENTER to finish (maybe more information below). --- ``` 

Click enter and continue.

<img src="https://c.tenor.com/0AVbKGY_MxMAAAAM/check-mark-verified.gif" width=20% height=20%>  

## You server should now be installed and operational.


<br/>
<br/>


<img src="https://i.dlpng.com/static/png/6994062_preview.png" width=50% height=50%>  

# 2. Next, setting up an agent and connecting to the server.

Run the 'manage_agents' to add or remove them:

/var/ossec/bin/manage_agents

More information at:

http://www.ossec.net/en/manual.html#ma



Once OSSEC has been finally installed we need to make systemd aware of it so can can monitor processes related to it with sytem-based tools.

 ``` $ sudo systemctl enable ossec ``` 

Run the manage agent command.

 ``` sudo /var/ossec/bin/manage_agents ``` 


To create a new agent we will select option (A)dd an agent.

 ``` A ``` 
 
Name your new agent:

 ``` Please Enter the agent name you want here.```

Enter your Windows computer ip address: (You can use myip.com and copy the host address.)

 ``` Please Enter your Windows IP here.```

Confirm by entering 

 ``` Y ``` 
 
 Now go to 
 
```  https://www.ossec.net/download-ossec/ ``` 

And download the following file.

 ``` "Agent Windows"	(ossec-agent-win32-3.6.0.exe) ``` 

Right click and Run as the download file Adminstrator.

Now return to the command prompt window used to connect to the OSSEC server and extract the key. 

Use (E)xtract key for agent.

 ``` E ``` 
 
Than highlight and copy the key shown the command problem 
 
  ``` The key will be under "Agent key information for ' ' is: "  ``` 
  
Paste the long code in the the authentication key section of the (OSSEC) Agent Windows.

 ``` Confirm key by pressing OK  ``` 
  
Lastly, make sure the OSSEC Server IP matches the same IP from your digital ocean droplet.

 ``` Confirm that IP address you entered for Server IP is correct "  ``` 
 
 Inside OSSEC Agent Manager
 
 ``` In top left click "Manage" and than navigate and click "Start OSSEC" ``` 
 
 **The OSSEC Agent Manager should successfully be connected and operational.**


<img src="https://c.tenor.com/0AVbKGY_MxMAAAAM/check-mark-verified.gif" width=20% height=20%>  


# 3. Installing the Web User Interface.

Before we start anything we need to install a few more base applications.

``` sudo apt install -y php php-cli php-common libapache2-mod-php apache2-utils sendmail inotify-tools apache2 build-essential gcc make wget tar zlib1g-dev libpcre2-dev libpcre3-dev unzip libz-dev libssl-dev libpcre2-dev libevent-dev build-essential ```

Than enable Apache and launch it

``` sudo systemctl enable apache2 ```

``` sudo systemctl start apache2 ```

```sudo a2enmod rewrite ```

```sudo systemctl restart apache2 ```



To begin use PUTTY.exe connect to your server using it's IP address and port 22.

``` In PUTTY paste your IP address for digital ocean server ``` 

Press connect and login using root and the password you used to to create the droplet.
 
 
 ``` username login: root ``` 
 
 Once logged in change directory to tmp using the following command 
 
 ``` cd /tmp/ ``` 
 
 Clone the ossec.wui with this command

 ``` sudo git clone https://github.com/ossec/ossec-wui.git ``` 
 
 
 Move directory using thefollowing command.
 
 ``` sudo mv /tmp/ossec-wui /var/www/html ``` 
 
 
 Next change the directory using the command.
 
 ``` cd /var/www/html/ossec-wui ``` 
 
 
 Start the Web User Interface (WUI) setup by running
 
 
  ``` sudo ./setup.sh  ```
 
 
 Create credentials.
 
  ``` Enter the username and confirm the password you want ``` 
  
 
 For Enter your web server user name (e.g, apache, www. nobody, www-data...)
 
 ``` www-data ``` 

Finalize permissions

 ``` sudo chown -R www-data:www-data /var/www/html/ossec-wui/ ``` 

``` sudo chmod -R 755 /var/www/html/ossec-wui/ ``` 

Restart Apache and startup the Web User Interface.

 ``` sudo systemctl restart apache2 ``` 
 
 Finally you can now navigate to the address using
 
  http://```CHANGE THIS PART TO YOUR DIGITAL OCEAN IP ADDRESS```/ossec-wui/
  
 
 **You should see a webpage for OSSEC WebUI sucessfully**


<img src="https://c.tenor.com/0AVbKGY_MxMAAAAM/check-mark-verified.gif" width=20% height=20%>  

WORK IN PROGRESS
CONTINUE
CONTINUE
CONTINUE
CONTINUE
CONTINUE
CONTINUE
CONTINUE

<br/>
<br/>


<img src="https://media4.giphy.com/media/l0Ex9wjSaCkrCuKC4/giphy.gif" width=50% height=50%>

## Congratulations! You've sucessfully installed an OSSEC Server, Agent and Web UI.

<br/>
<br/>

# DEMO (Instructional Video)

Play video below:
[![Alt text](https://i9.ytimg.com/vi_webp/M57CplR6he4/mqdefault.webp?sqp=CISi_owG&rs=AOn4CLCP90pE6PxrseKwq89WYGv8qUJhlw)](https://www.youtube.com/watch?v=M57CplR6he4)

</br>
</br>

# FAQ

**What is OSSEC and how does it work?**

OSSEC is open-sourced software, that has Host-based Intrusion Detection System or HIDS. The HID system features log analysis, windows registry monitoring, regulated integrity checks, time-based alerts, active response and rootkit detection. Altogether, this application is useful if you want observe all things taking place on your server and have it logged and reported to you.


**What does the program do?**

OSSEC encorporates itself onto your server and serves as a detection system against intruders or unauthorized/suspicious access.


**What problem does the application solve?**

OSSEC aims to solve issues of intrusion on systems that will otherwise go unnoticed if you have no system logging or lack the capacity to protect your server from any unwanted access.

**Use cases**
Give 3 use case for the software.

<ins>Examples:</ins>

1 – If a user tries to use a rootkit on your server, which is a program designed to gain privileged access and hide that its running.

2 –  When an indvidual tries to access your server without authorization such as a user who types the password incorrect while trying to login with ssh or PUTTY using root@ user.

3 – If someone uses an incorrect user access key with is used by the OSSEC Windows Agent and retrieable or created through the ssh root access. The incorrect access key will immediately be shown in the system log and the system would alert the host.

## Final Review

**Is this software any good?** 

I believe this software is good because it helps detect any unseen or overlooked activity that takes place on your server.

**What are its pros and cons.**

<ins>Pros:</ins>
The software allows you to change settings to your liking and adjust them immediately.
You receive updates about any issues or flags taking place on the server.
The OSSEC software used with Ubuntu 20.04 is completely free and open-source.

<ins>Cons:</ins>
The WEB-GUI is outdated and is difficult to setup.
The Agent installation is tedious and requires the deletion of parent folders.
Sometimes install the OSSEC server requires deletion of folders or files and than reinstalling using command prompts manually.


**Can you see yourself using this tool in the future.**

Yes, I definitely see myself using this tool in the future especially because it is an open-source software. For example, if I were to host a game server and I wanted to make sure unauthorized access or changes weren't made I could be notified by them via E-mail.

**What did you learn from using this software?**

I learned how something as simple as system log can be intergrated into a software to feature a detection system. The intrusion detection feature creates notification via E-mail or through server web address. These can be used during an attack on your server and because the service is open source you can easily install it without and fees and test out many features offered by OSSEC.

# Possible Error(s)

![ERROR installing ubuntu](https://user-images.githubusercontent.com/90642714/143454893-3ff8447b-bdd1-41ec-92be-7f35c35e3fac.jpg)

**Please note:** There is a possible error encountered when installing OSSEC automatically using the following command prompt on Ubuntu. 

``` Recommended Solution: Install the OSSEC server manually and proceed use the Github instructions list above. ``` **[Instructions here.](#ossec-installation-tutorial)** 

# Platforms & Software used.

<img src="https://digital.ai/sites/default/files/pictures/styles/maxwidth_300/public/pt_logos/ossec.png?itok=koaDq_K2" width=15% height=15%> https://www.ossec.net/download-ossec/


<img src="https://meterpreter.org/wp-content/uploads/2018/10/ubuntu.png" width=15% height=15%> https://releases.ubuntu.com/20.04/



<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/DigitalOcean_logo.svg/768px-DigitalOcean_logo.svg.png" width=15% height=15%> https://www.digitalocean.com/


<img src="https://upload.wikimedia.org/wikipedia/commons/b/b6/PuTTY_icon_128px.png" width=15% height=15%> https://www.putty.org/


<br/>

### Reference: 

https://www.adminbyaccident.com/security/how-to-install-ossec-server-on-ubuntu/ by Albert Valbuena

<br/>

### This Project was created while attending a course at Bronx Community College.

Special Thanks to Professor Edwin-Reed-Sanchez.

GitHub Written by: Delawn Khudan and Shaina Mirabal

<img src="https://www.cuny.edu/wp-content/uploads/sites/4/page-assets/home-preview/cuny-tuesday/CUNYGive-BCC-ani.gif" width=50% height=50%>


**[Back to top.](#ossec-installation-tutorial)** 

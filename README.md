
# OSSEC-Ubuntu on Digital Ocean Droplet (WORK IN PROGRESS)
OSSEC installation tutorial.<br/>

<img src="https://www.ossec.net/wp-content/uploads/2019/01/ossec.png" width=50% height=50%> 

We will now install OSSEC, make a basic configuration including sending emails with alerts, will briefly explain important files so we can later tune OSSEC to our needs, we’ll also install a Windows agent to report to this server install, and as a last step we’ll also install a web user interface to look for alerts.<br />

Let’s go with this how to install OSSEC on Ubuntu. 

<img src="https://images.squarespace-cdn.com/content/v1/5980deaee6f2e1738e18738c/1550165343634-2QDHAJHNQ82KZZ8KY91C/start-here-gif.gif" width=50% height=50%>

As always we do update system sources first.

**$ sudo apt update** 

<br/>
<br/>

If packages can be upgraded do it now.

**$ sudo apt upgrade -y** 

<br/>
<br/>

First we will install the necessary packages to build OSSEC from sources.

**$ sudo apt install build-essential gcc make unzip sendmail inotify-tools expect libevent-dev libpcre2-dev libz-dev libssl-dev -y**


<br/>
<br/>


Once these dependencies have been fulfilled it is time to download OSSEC and build it in our system.

**$ sudo wget -P /opt https://github.com/ossec/ossec-hids/archive/3.6.0.tar.gz**


<br/>
<br/>


The above command will download the OSSEC sources into the /opt directory. Before building those we need to extract them from the tarball. We’ll use the next command:

**$ sudo tar -zxf /opt/3.6.0.tar.gz --directory /opt**

<br/>
<br/>


Once downloaded and uncompressed we can start the installation process. Very conveniently there is an script already incorporated on the program for this task. We launch this installer.

**$ sudo sh /opt/ossec-hids-3.6.0/install.sh**

<br/>
<br/>


This will trigger the script which will first ask a few questions and then it will build and install OSSEC in our system.

First step we will be aksed what language to use:

**$ sudo sh /opt/ossec-hids-3.6.0/install.sh**

<br/>
<br/>



(en/br/cn/de/el/es/fr/hu/it/jp/nl/pl/ru/sr/tr?) [en]:

I’ll choose the default. Pick up yours. 

Than **PRESS ENTER.**

<br/>
<br/>



Next we will install the OSSEC script.

OSSEC HIDS v3.6.0 Installation Script - http://www.ossec.net


You are about to start the installation process of the OSSEC HIDS.

You must have a C compiler pre-installed in your system.


- System: Linux ossecman 4.15.0-88-generic

- User: root

- Host: ossecman

**-- Press ENTER to continue or Ctrl-C to abort. --**


<br/>
<br/>



Next the questions start.

1- What kind of installation do you want (server, agent, local, hybrid or help)?

Type **server**. 

<br/>
<br/>


You see message like this.

- Server installation chosen.


Next, choosing where to install OSSEC.

2- Setting up the installation environment.


- Choose where to install the OSSEC HIDS [/var/ossec]:

**Use the default by pressing enter**

<br/>
<br/>



Next configure OSSEC.

3- Configuring the OSSEC HIDS.


3.1- Do you want e-mail notification? (y/n) [y]:

Type **yes**

<br/>
<br/>



- What's your e-mail address?

Type the **your email** or use **root@localhost**

<br/>
<br/>



3.1- Do you want e-mail notification? (y/n) [y]:

<br/>

**Y**

<br/>
<br/>

- What's your e-mail address? root@localhost or your email address.


- We found your SMTP server as: 127.0.0.1 or IP Address of server 


- Do you want to use it? (y/n) [y]:

<br/>

**Y**

<br/>
<br/>

Note: This option alerts will be root’s mail account. And they will read similar to this following format.



3.2- Do you want to run the integrity check daemon? (y/n) [y]:

<br/>

say **Y**


<br/>
<br/>


Time to ask if a rootkit check daemon is of your interest. Why not? 


<br/>

say **Y**


<br/>
<br/>


3.3- Do you want to run the rootkit detection engine? (y/n) [y]:

<br/>

**Y**


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

**Y**

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

choose **Y**


<br/>
<br/>



If you choose yes you’ll see something like this.


- firewall-drop enabled (local) for levels >= 6

-ip_address_here


Go to next question.


Now, this question will be asked.

Do you want to add more IPs to the white list? (y/n)? [n]:

**Press Enter**

<br/>
<br/>


Next, is enabling system log remotely.


3.5- Do you want to enable remote syslog (port 514 udp)? (y/n) [y]:

**Press Enter**

<br/>
<br/>



Now after all the questions you should see something similar to this message.


3.6- Setting the configuration to analyze the following logs:

-- /var/log/auth.log

-- /var/log/syslog

-- /var/log/dpkg.log


**--- Press ENTER to continue ---**

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


**--- Press ENTER to finish (maybe more information below). ---**

Click enter and continue.


<img src="https://media4.giphy.com/media/l0Ex9wjSaCkrCuKC4/giphy.gif" width=50% height=50%>

Next, to to connect agent and server, you need to add each agent to the server.

Run the 'manage_agents' to add or remove them:

/var/ossec/bin/manage_agents

More information at:

http://www.ossec.net/en/manual.html#ma



Once OSSEC has been finally installed we need to make systemd aware of it so can can monitor processes related to it with sytem-based tools.

**$ sudo systemctl enable ossec** 

<br/>
<br/>



Once systemd is aware of this, we can launch OSSEC.

**$ sudo systemctl start ossec**

<br/>
<br/>



We can now check which processes are active.

**$ sudo systemctl status ossec**

<br/>
<br/>



The above command will display:

albert@ossecman:~$ sudo systemctl status ossec

● ossec.service - LSB: Start and stop OSSEC HIDS

Loaded: loaded (/etc/init.d/ossec; generated)

Active: active (running) since Wed 2020-03-04 11:58:07 UTC; 2s ago

Docs: man:systemd-sysv-generator(8)

Process: 25127 ExecStart=/etc/init.d/ossec start (code=exited, status=0/SUCCESS)

Tasks: 7 (limit: 1108)

CGroup: /system.slice/ossec.service

├─25158 /var/ossec/bin/ossec-maild

├─25159 /var/ossec/bin/ossec-maild

├─25166 /var/ossec/bin/ossec-execd

├─25170 /var/ossec/bin/ossec-analysisd

├─25175 /var/ossec/bin/ossec-logcollector

├─25187 /var/ossec/bin/ossec-syscheckd

└─25191 /var/ossec/bin/ossec-monitord

Mar 04 11:58:04 ossecman ossec[25127]: Starting OSSEC HIDS v3.6.0...

Mar 04 11:58:04 ossecman ossec[25127]: Started ossec-maild...

Mar 04 11:58:04 ossecman ossec[25127]: Started ossec-execd...

Mar 04 11:58:04 ossecman ossec[25127]: Started ossec-analysisd...

Mar 04 11:58:04 ossecman ossec[25127]: Started ossec-logcollector...

Mar 04 11:58:04 ossecman ossec[25127]: Started ossec-remoted...

Mar 04 11:58:05 ossecman ossec[25127]: Started ossec-syscheckd...

Mar 04 11:58:05 ossecman ossec[25127]: Started ossec-monitord...

Mar 04 11:58:07 ossecman ossec[25127]: Completed.

Mar 04 11:58:07 ossecman systemd[1]: Started LSB: Start and stop OSSEC HIDS.

root@ossecman:~$


Alternatively the combination of ‘ps’ and ‘grep’ commands will do similarly.

**$ ps -ef | grep ossec**

<br/>
<br/>


As a result we’ll see something similar to this:

albert@ossecman:~$ ps -ef | grep ossec

ossecm 25158 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-maild

ossecm 25159 25158 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-maild

root 25166 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-execd

ossec 25170 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-analysisd

root 25175 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-logcollector

root 25187 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-syscheckd

ossec 25191 1 0 11:58 ? 00:00:00 /var/ossec/bin/ossec-monitord

ossecm 25205 25158 0 11:58 ? 00:00:00 [ossec-maild] <defunct>

albert 25210 1087 0 11:58 pts/0 00:00:00 grep --color=auto ossec

albert@ossecman:~$

Most tutorials end here, with the install finished, and although many incorporate how to set a graphical user interface on a web service too. This bit is at the end of this guide, but before that, we should have a look at some important configuration files so we have a basic understanding of this tool.

File permissions on the install directory /var/ossec are set to 550.

root@ossecman:/var/ossec# ll /var | grep ossec

dr-xr-x--- 13 root ossec 4096 Mar 4 11:56 ossec/

root@ossecman:/var/ossec#

Inside we will encounter the following directory structure.

root@ossecman:/var/ossec# ll

total 52

dr-xr-x--- 13 root ossec 4096 Mar 4 11:56 ./

drwxr-xr-x 14 root root 4096 Mar 4 11:56 ../

drwx------ 2 root ossec 4096 Mar 4 11:56 .ssh/

dr-xr-x--- 3 root ossec 4096 Mar 4 11:56 active-response/

dr-xr-x--- 2 root ossec 4096 Mar 4 11:56 agentless/

dr-xr-x--- 2 root root 4096 Mar 4 11:56 bin/

dr-xr-x--- 3 root ossec 4096 Mar 4 11:56 etc/

drwxr-x--- 5 ossec ossec 4096 Mar 4 11:56 logs/

dr-xr-x--- 11 root ossec 4096 Mar 4 11:56 queue/

dr-xr-x--- 2 root ossec 4096 Mar 4 11:56 rules/

drwxr-x--- 5 ossec ossec 4096 Mar 4 11:58 stats/

dr-xr-x--T 2 root ossec 4096 Mar 4 11:56 tmp/

dr-xr-x--- 3 root ossec 4096 Mar 4 11:58 var/

root@ossecman:/var/ossec#

As the convention states configuration files are found into the ‘etc’ directory. Inside we’ll find this structure.

root@ossecman:/var/ossec/etc# ll

total 192

dr-xr-x--- 3 root ossec 4096 Mar 4 11:56 ./

dr-xr-x--- 13 root ossec 4096 Mar 4 11:56 ../

-rw-r----- 1 root ossec 0 Mar 4 11:56 client.keys

-rw-r----- 1 root ossec 152472 Mar 4 11:56 decoder.xml

-rw-r----- 1 root ossec 3306 Mar 4 11:56 internal_options.conf

-rw-r----- 1 root ossec 320 Mar 4 11:56 local_internal_options.conf

-r--r----- 1 root ossec 127 Mar 4 11:56 localtime

-rw-r----- 1 root root 90 Mar 4 11:56 ossec-init.conf

-rw-r----- 1 root ossec 7703 Mar 4 11:56 ossec.conf

-r--r----- 1 root ossec 715 Mar 4 11:56 resolv.conf

drwxrwx--- 2 root ossec 4096 Mar 4 11:58 shared/

root@ossecman:/var/ossec/etc#

One important file here is the ‘ossec.conf’ one. It is divided into 9 sections as far as I can read. Let’s briefly talk about them.

Section 1.- There is a first block where some global settings are applied such as if email notifications are enabled, what address has to be used and what smtp server has to be connected to.

<ossec_config>

<global>

<email_notification>yes</email_notification>

<email_to>root@localhost</email_to>

<smtp_server>127.0.0.1</smtp_server>

<email_from>ossecm@ossecman</email_from>

</global>

These aren’t the only ‘global’ entries on the file. Others can be read embedded in other ‘sections’ of the ossec.conf file such as the one underneath the ‘rootkit check’ section. It reads like this:

<global>

<allow_list>127.0.0.1</allow_list>

<allow_list>::1</allow_list>

<allow_list>localhost.localdomain</allow_list>

<allow_list>127.0.0.53</allow_list>

</global>

If you recall this above corresponds to the white listing when enabling the ‘active-response’ feature. Tune these entries to modify the white-list behaviour at your will.

Section 2.- Another section is the long ‘rules’ one. This is a long list of entries to rules which are located in the /var/ossec/rules directory. Checking one of the rules files we can read one dedicated for WordPress, although that file contains a few of these.

<rule id="9505" level="7">

<if_sid>9500</if_sid>

<pcre2>Warning: Comment flood attempt</pcre2>

<description>Wordpress Comment Flood Attempt.</description>

</rule>

As we can see an alert about a type of attack known as ‘comment flood attempt’ will be triggered by such event and it will qualify as a level 7 severity type. For more details read this entry to have a basic understanding on the rules and this from Wikiepdia for the syslog alert convention.

By default OSSEC will use all the rules stated in the ossec.conf file unless we disable them. If you need them all go ahead and leave them as they are. Some nefarious activity on your network can trigger them, and you may not have a WordPress install whatsoever, but this could indicate something wrong is going on. It could be a the host level, at the network level or just a false positive. But this is an indicator at the end of the day.

If you choose to deactivate some of the rules, you can do it by appending this ‘<!–’ at the beginning of the line, and include this other bit ‘–>’ at the end.

Example of an activated rule:

<include>openbsd_rules.xml</include>

Example of a deactivated rule:

<!-- <include>openbsd_rules.xml</include> -->

Section 3.- Another interesting section, and this you may desire to change the default settings, is the ‘syscheck’ one. OSSEC will perform a system check every 79200 seconds, or 22 hours. The original bit for this reads like so:

<!-- Frequency that syscheck is executed - default to every 22 hours -->

<frequency>79200</frequency>

In this section there are also statements for what directories to check but also which ones to ignore, both on UNIX and UNIX-like systems and Windows. If there are some other directories you wish to be ignored at them into the list. Defaults for UNIX and UNIX-like reads like this:

<!-- Files/directories to ignore -->

<ignore>/etc/mtab</ignore>

<ignore>/etc/mnttab</ignore>

<ignore>/etc/hosts.deny</ignore>

<ignore>/etc/mail/statistics</ignore>

<ignore>/etc/random-seed</ignore>

<ignore>/etc/adjtime</ignore>

<ignore>/etc/httpd/logs</ignore>

<ignore>/etc/utmpx</ignore>

<ignore>/etc/wtmpx</ignore>

<ignore>/etc/cups/certs</ignore>

<ignore>/etc/dumpdates</ignore>

<ignore>/etc/svc/volatile</ignore>

Section 4.- Next section is the rootkit one. It reads like so:

<rootcheck>

<rootkit_files>/var/ossec/etc/shared/rootkit_files.txt</rootkit_files>

<rootkit_trojans>/var/ossec/etc/shared/rootkit_trojans.txt</rootkit_trojans>

<system_audit>/var/ossec/etc/shared/system_audit_rcl.txt</system_audit>

<system_audit>/var/ossec/etc/shared/cis_debian_linux_rcl.txt</system_audit>

<system_audit>/var/ossec/etc/shared/cis_rhel_linux_rcl.txt</system_audit>

<system_audit>/var/ossec/etc/shared/cis_rhel5_linux_rcl.txt</system_audit>

</rootcheck>

If the rootkitcheck has been enabled at install time OSSEC will monitor the filesystem looking for already known files which are typically used on attacks and implanted on systems. Think of this as those were signatures in an antivirus software. If the software sees them present it will act accordingly. Further details can be read on the documentation.

By default checks will be performed every two hours. And if we need to monitor Windows boxes for example the default doesn’t include the specific files for those, only generic ones. Include them on the section depicted above. They are included in the /var/ossec/etc/shared/ directory.

Section 5.- Another section in the ossec.conf file is the one dedicated to the syslog facility so logs can be forwarded.

<remote>

<connection>syslog</connection>

</remote>

<remote>

<connection>secure</connection>

</remote>

Section 6.- Here we find the alerts level configured.

<alerts>

<log_alert_level>1</log_alert_level>

<email_alert_level>7</email_alert_level>

</alerts>

Section 7.- Actions can be found here. As we recall, at install time, we have been asked if we wanted any actions would be triggered by some default alerts configured on OSSEC. These are a few of those actions.

<command>

<name>host-deny</name>

<executable>host-deny.sh</executable>

<expect>srcip</expect>

<timeout_allowed>yes</timeout_allowed>

</command>

<command>

<name>firewall-drop</name>

<executable>firewall-drop.sh</executable>

<expect>srcip</expect>

<timeout_allowed>yes</timeout_allowed>

</command>

<command>

<name>disable-account</name>

<executable>disable-account.sh</executable>

<expect>user</expect>

<timeout_allowed>yes</timeout_allowed>

</command>

<command>

<name>restart-ossec</name>

<executable>restart-ossec.sh</executable>

<expect></expect>

</command>

<command>

<name>route-null</name>

<executable>route-null.sh</executable>

<expect>srcip</expect>

<timeout_allowed>yes</timeout_allowed>

</command>

The list of available scripts those command entries trigger can be found at the following directory:

/var/ossec/active-response/bin

Removing those command entries, and restarting OSSEC afterwards, will make it stop using them. Add and remove those you need. And remember this at install time. Do I really want inmediate actions to be triggered on certain events? To answer this question carefully read the documentation and do some testing.

Section 8.- In here we find the configuration bits for the ‘active-response’ feature.

<!-- Active Response Config -->

<active-response>

<!-- This response is going to execute the host-deny

- command for every event that fires a rule with

- level (severity) >= 6.

- The IP is going to be blocked for 600 seconds.

-->

<command>host-deny</command>

<location>local</location>

<level>6</level>

<timeout>600</timeout>

</active-response>

<active-response>

<!-- Firewall Drop response. Block the IP for

- 600 seconds on the firewall (iptables,

- ipfilter, etc).

-->

<command>firewall-drop</command>

<location>local</location>

<level>6</level>

<timeout>600</timeout>

</active-response>

We can obviosly tune the blocking time for a certain offensive IP but the severity level this is triggered by. As you can see this configuration points to ‘local’. But be aware of this with agents if you start experiencing blocks after OSSEC is installed on your infrastructure. For further detail do not forget to read this section of the documentation.

Section 9.- Here we will find the local files this OSSEC installation is monitoring.

<!-- Files to monitor (localfiles) -->

<localfile>

<log_format>syslog</log_format>

<location>/var/log/auth.log</location>

</localfile>

<localfile>

<log_format>syslog</log_format>

<location>/var/log/syslog</location>

</localfile>

<localfile>

<log_format>syslog</log_format>

<location>/var/log/dpkg.log</location>

</localfile>

<localfile>

<log_format>command</log_format>

<command>df -P</command>

</localfile>

<localfile>

<log_format>full_command</log_format>

<command>netstat -tan |grep LISTEN |egrep -v '(127.0.0.1| ::1)' | sort</command>

</localfile>

<localfile>

<log_format>full_command</log_format>

<command>last -n 5</command>

</localfile>

</ossec_config>

You may want to for example disable the auth.log monitoring if you are bothered to see you and your team being warned about your own logins to this system. But leave it on if this should be running and no one getting in unless for maintenance tasks, every month for example.

Another bit you may want to disable is the packages monitoring. At every system update you’ll be warned about changes on the system. A nefarious actor may want to install you a few bits of this and that so their malicious python code will work on your systems. Not nice.

Furthermore we can extend OSSEC functionality with an integrated web user interface called OSSEC-WUI. Be aware this is not under development nor maintenance from anyone, bugs may appear and other issues such as security vulnerabilities may be encountered. You can perfectly skip this part of the tutorial completely and OSSEC will work for you just fine.

Packages for the OSSEC-WUI interface include:

apache2 apache2-utils libapache2-mod-php7.2 php7.2 php7.2-cli php7.2-common

So make an install of those with the following command:

$ sudo apt install apache2-utils libapache2-mod-php7.2 php7.2 php7.2-cli php7.2-common -y

We will now need to install git so we can clone the OSSEC-WUI repo and install it.

$ sudo apt install git

With git installed we clond the repo.

$ sudo git clone https://github.com/ossec/ossec-wui.git /opt/ossec-wui-install

We now launch the installation script.

$ sudo sh /opt/ossec-wui-install/setup.sh

A series of very simple questions will be asked, such as username and password. Once we finish installing and configuring OSSEC-WUI, when visiting the server’s ip with the browser will be asked for those. We will also be asked about the Apache username, in this case we have to type ‘www-data’ which is Ubuntu’s one.

Once we have installed OSSEC-WUI we need to configure it.

First we create an Apache HTTP virtual host file

$ sudo touch /etc/apache2/sites-enabled/ossec-wui.conf

We will include this configuration. Tune it to your needs.

<VirtualHost *:80>

DocumentRoot /opt/ossec-wui-install/

ServerName 127.0.0.1

ServerAlias localhost

ServerAdmin root@localhost

<Directory /opt/ossec-wui-install/>

Options +FollowSymlinks

AllowOverride All

Require all granted

</Directory>

ErrorLog /var/log/apache2/moodle-error.log

CustomLog /var/log/apache2/moodle-access.log combined

</VirtualHost>

Remove now the original default configuration on the default virtualhost entry, otherwise you won’t see anything when firing up Apache HTTP and visiting the server’s IP with the browser.

$ sudo rm /etc/apache2/sites-enabled/000-default.conf

Enable the Apache HTTP’s rewrite module, so URL’s can be correctly transformed by OSSEC-WUI.

$ sudo a2enmod rewrite

Now change /var/ossec directory permissions so OSSEC-WUI can read from it. Otherwise you’ll be left without seeing anything.

$ sudo chmod 554 /var/ossec

Restart Apache HTTP.

$ sudo systemctl restart apache2

Now use your browser to check OSSEC-WUI.

URL: http://yourserverip/index.php

This is what you should see:



To improve security on this stack of Apache HTTP and PHP, something you’ll need, you can follow security recommendations on this article about hardening Apache HTTP. It’s based on FreeBSD but all the premises and concepts apply.

This how to install OSSEC on Ubuntu guide has two drawbacks. The unmaintained OSSEC-WUI is one of those but you can avoid its use with alternatives such as an ELK stack and integrate it, or just rely on email. The second issue is around maintenance. See, this install has been made on sources so any new update on the software will not land automatically with ‘apt update’ and ‘apt upgrade’. A new build is necessary since we haven’t installed any repository nor used an already compiled binary. Therefore this implies time to build and possibly build fails which in turn require more time and effort to check what is missing/wrong. The solution?

Installing an already compiled binary and setting a repository entry, from the creators, in our sources list, is one simple solution to the maintenance problems.

If you are already here it is because not only you are interested but you may understand how scripts work. If so, you can use some of the scripts for OSSEC installs I wrote. Those can be found here. Use them at your own discretion and if anything breaks I am not liable nor responsible by any mean for it. Be wise.

This is all for this how to install OSSEC on Ubuntu. For further details on how the tool works just visit the official documentation pages. At a later article we’ll configure an agent on a Windows box and will speak about configuring agents connected to servers like this one we’ve just set up.

PS: Where have you seen someone saying their guide has drawbacks? Aren’t they all perfect? This one isn’t and you can tell you saw this unperfection comment here first, on adminbyaccident.com. Because accidents happen.

<img src="https://www.cuny.edu/wp-content/uploads/sites/4/page-assets/home-preview/cuny-tuesday/CUNYGive-BCC-ani.gif" width=50% height=50%>

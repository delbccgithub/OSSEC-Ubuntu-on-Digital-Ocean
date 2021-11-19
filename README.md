
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

Type **Yes**

<br/>
<br/>



- What's your e-mail address?

Type the **your email** or use **root@localhost**

<br/>
<br/>



3.1- Do you want e-mail notification? (y/n) [y]:

<br/>

Type **Y**

<br/>
<br/>

- What's your e-mail address? root@localhost or your email address.


- We found your SMTP server as: 127.0.0.1 or IP Address of server 


- Do you want to use it? (y/n) [y]:

<br/>

Type **Y**

<br/>
<br/>

Note: This option alerts will be root’s mail account. And they will read similar to this following format.



3.2- Do you want to run the integrity check daemon? (y/n) [y]:

<br/>

Type **Y**


<br/>
<br/>


Time to ask if a rootkit check daemon is of your interest. Why not? 


<br/>

Type **Y**


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

Type **Y**

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

Choose **Y**


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

<img src="https://c.tenor.com/0AVbKGY_MxMAAAAM/check-mark-verified.gif" width=20% height=20%>  

## You server should now be installed and operational.


<br/>
<br/>


<img src="https://i.dlpng.com/static/png/6994062_preview.png" width=50% height=50%>  

# Next, to connect agent and server, you need to add an agent.

Run the 'manage_agents' to add or remove them:

/var/ossec/bin/manage_agents

More information at:

http://www.ossec.net/en/manual.html#ma



Once OSSEC has been finally installed we need to make systemd aware of it so can can monitor processes related to it with sytem-based tools.

**$ sudo systemctl enable ossec** 

<br/>
<br/>


<img src="https://media4.giphy.com/media/l0Ex9wjSaCkrCuKC4/giphy.gif" width=50% height=50%>

## Congratulations! You've sucessfully installed an OSSEC Server, Agent and Web UI.

<img src="https://www.cuny.edu/wp-content/uploads/sites/4/page-assets/home-preview/cuny-tuesday/CUNYGive-BCC-ani.gif" width=50% height=50%>

<img src="https://meterpreter.org/wp-content/uploads/2018/10/ubuntu.png" width=10% height=10%>

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/DigitalOcean_logo.svg/768px-DigitalOcean_logo.svg.png" width=10% height=10%>




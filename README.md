# Nagios

1. What is Nagios Core ?
------------------------
Nagios core is an open source enterprise monitoring tool. which will monitor various types of systems and networking devices.

2. Nagios Server can be installed only on Linux Servers but we can monitor all

3. Features:
   a. monitoring host resources ( like CPU Load, Disk Usage, Memory Usage and etc. )
   b. available 5843 Plugins in 458 categories
   c. Ability to define network hierarchy
   d. Send Email/SMS Notifications when host or service problem occur
   e. parellalized checks
4. Why We need Nagios ?
   a. Detects all types of network or server Issues
   b. Helps you to find the root cause of problem which allows you to get the permanent solution to the problem
   c. active monitoring of your entire infrastructure and business processes
   d. allows you to monitors and troubleshoot server performance issues.
   e. Helps you oto plan for Infrastructure upgrades before outdated systems cretae failures
   f. you can maintain the security and availability of the service
   g. automatically fix problems in panic situations

5. Comaprision Between Nagios Core and Nagios XI ![image](https://github.com/anilgunde/Nagios/assets/87513730/0102ebb8-ae9a-4477-8d1a-7ff1e4383e77)

6. Nagios Architecture

![image](https://github.com/anilgunde/Nagios/assets/87513730/cb195de9-37de-434e-9e01-83892f208e0f)

8. Terminology
    Plugins: which is external Programs that can consist of either a script or compiled executable.
    Host: Is a Server or any network device which you kwant monitor
    Service: Is any metric (Ex. CPU, Memory Usage)
    Users: who has the access to Web Interface
    Contacts: Individual administrator or end -user (email or Phone Number)
    Contact Groups: Grouping Contacts
    Acknoledgement: Tempororily Suppress alert notifications
    Downtime: planned activity (Ex: Updating Software)
    Latency: Difference between scheduled to run and when it does actually run
    State: SOFT or HARD to avoid false positive aletrs.
   Agent: Usually daemons or servicees that must be places on the client to listen for connection coming from the nagios Server.
    Host Groups: Grouping the Hosts (Ex: US_Hosta, Oracle_Servers, Windows Servers)
    Service Groups: Grouping Multiple Services
   
9. Active Vs Passive Checks

    ![image](https://github.com/anilgunde/Nagios/assets/87513730/a01fe1df-68ef-4c51-8c65-9f023e95019d)

10. SOFT and HARD States

    ![image](https://github.com/anilgunde/Nagios/assets/87513730/f3af262d-0246-4ff9-809e-4e57c5a13bc0)
    
    ![image](https://github.com/anilgunde/Nagios/assets/87513730/e8ce03e0-02eb-4e87-8ea2-01986494d458)
    
    ![image](https://github.com/anilgunde/Nagios/assets/87513730/0c815f90-d4f6-4212-848d-893014ce2e15)
    

12. Setup Nagios Lab
    a. Disable selinux
    b. disable firewall
    c. update the server

        $ sudo apt update && sudo apt upgrade -y

        $ sudo apt install -y wget build-essential apache2 php openssl perl make php-gd libgd-dev libapache2-mod-php libperl-dev libssl-dev daemon autoconf libc6-dev libmcrypt-dev libssl-dev libnet-snmp-perl gettext unzip

        $ cd /tmp
        $ wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.6.tar.gz
        $ sudo useradd nagios
        $ sudo groupadd nagcmd
        $ sudo usermod -a -G nagcmd nagios
        $ tar -xzf nagios-4.4.6.tar.gz
        $ cd nagios-4.4.6
        $ sudo ./configure --with-httpd-conf=/etc/apache2/sites-enabled
        $ sudo make all
        $ sudo make install
        $ sudo make install-init
        $ sudo make install-commandmode
        $ sudo make install-config
        $ sudo /usr/bin/install -c -m 644 sample-config/httpd.conf /etc/apache2/sites-enabled/nagios.conf
        $ sudo a2enmod rewrite
        $ sudo a2enmod cgi
        $ sudo systemctl restart apache2
        $ cd /tmp
        $ wget https://nagios-plugins.org/download/nagios-plugins-2.3.3.tar.gz
        $ tar -xzf nagios-plugins-2.3.3.tar.gz
        $ cd nagios-plugins-2.3.3
        $ sudo ./configure --with-nagios-user=nagios --with-nagios-group=nagios --with-openssl
        $ sudo make
        $ sudo make install
        $ sudo /usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg

        $ sudo systemctl enable --now nagios.service
        $ sudo systemctl restart apache2.service

    create password

        $ sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin

    login using userid and admin @ <publicIp?/nagios

    




   

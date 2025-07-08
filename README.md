# Firewall

Mr. Avenal was very pleased with your work conducting the network traffic analysis for the Reynholm subsidiary. After further review and the alarming activity which occurred over FTP and Telnet, the attempted exploit of the web server, and the suspect SSH traffic, Mr. Avenal, with the recommendation of Mr. Trenneman and Mr. Moss of Reynholm's IT division, would like to implement a new firewall policy that will restrict access to these services in the form of a shell script which can be used to deploy these policies at both organizations.

 

Tasks
To test your rules, you will need three source computers. You can set this up in a few ways, but two of your options are:

Use/create three VMs: An Ubuntu server and two Desktop Linux installation. These will be referred to as Ubuntu and Mint, but you can use two of either.
Video Here
Update: No need to mess with the Virtual Network Editor. The VMs can remain on NAT as long as they are all on the same subnet.
Use/create two VMs (Ubuntu server and another Linux), and use your host Windows/Mac as your third computer.
Video Here
 

 

c) Install the appropriate services on the Server including:

 

ssh server
sudo aptitude install openssh-server
telnet
sudo aptitude install telnetd
ftp
sudo aptitude install vsftpd
web
sudo aptitude install apache2
 

If you do not have the Aptitude package manager, replace "aptitude" with "apt-get". Example: 'sudo aptitude install openssh-server' becomes' sudo apt-get install openssh-server '

 

d) Test that you can connect to each of the services.

 

Screenshot
Once finished with the assignment (rules are in place), I want you to run "sudo iptables --list" and take a screenshot of that terminal window. You may have to expand the window for it to include all of the rules. This is a graded deliverable and without it, you will not receive full credit for the rules.

 
Security Policy/Rules To Create
You are to create and apply a firewall rule set on your Ubuntu server and each rule should be commented.

 

Make sure to use variables for the IP addresses in your firewall. It's good practice and if I have to test one or more of your rules, I can replace the address in the variable.

 

Regardless of operating systems you choose to use, make sure you label your variables as Server, Ubuntu, and Mint appropriately as below. If those three variables are not used, you will lose some points.

 

For any packets you REJECT or DENY, those should be logged.  That means you'll need to modify the rule so that if the rule matches a DENY or REJECT a packet, that alert is written out to a log file.

 

For anything that says DENY below, I want a rule written which explicitly denies this action even if it would be covered by the default policy.

For example, #6 allows Ubuntu and Mint would be denied by default. Make sure you write a deny rule.

 

Your firewall should implement the following policies. The policies below are not in the order which they should be applied; put these rules in a reasonable order.

   1) Allow all loopback connections.

   2) Deny any connections from any IPs other than those on your local network

     Note: I realize the default INPUT policy effectively has this outcome, but I want a written rule for #2

   3) The firewall should be STATEFUL

   4) Allow echo-requests ONLY from computers on your network.

   5) Allow echo-replies ONLY to computers on your network.

   6) Allow ftp for the Ubuntu box ONLY (DENY Mint).

   7) DENY all telnet connections from Mint and Ubuntu.

     Note: I realize the default INPUT policy effectively has this outcome, but I want a written rule for #7 as well

   8) Allow ssh to the server for Mint box ONLY (DENY Ubuntu box).

   9) Allow web access (Apache) for the Mint box ONLY (DENY Ubuntu box).

 10) Default incoming policy should be DENY.

 11) Default outgoing policy should be ALLOW.

 12) Default forward policy should be DENY.

 13) Firewall should flush previously run rules.

 

Note that for deny rules, you will have to decide to use either REJECT or DROP and I want a comment justifying why you chose to use REJECT or DROP

 

Test your Rules
Setup your logging, then attempt to test the following:

Accessing the FTP service from Ubuntu and Mint
Accessing the telnet service from Ubuntu and Mint
Accessing the ssh service from Ubuntu and Mint
Accessing the Apache test page (web) from Ubuntu and Mint
 

Based on your firewall rules, some of your connections should be allowed and others denied. If logging is setup correctly, the denied packets will show up as being denied.

 

 

Setting Up Logging:
These rules have been used for logging, but that doesn’t mean you would use these exact rules; tailor your rules so they fit the assignment. In this instance, you would want to log any of the rules above that have a DENY in the description.

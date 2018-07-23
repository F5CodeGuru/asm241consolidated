Lab 1: Bot Protection
------------------------------

This lab will simulate botnet activity against the Webgoat virtual server and show how to protect yourself from these types of threats.

Connect to the lab environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. From the jumpbox, launch Chrome, click the BIG-IP bookmark and login to TMUI. admin/f5DEMOs4u


Configure a DOS Profile
~~~~~~~~~~~~~~~~~~~~~~~

#. From the F5 UI go to Security > Dos Protection > DoS Profiles and click Create

#. Name the profile BotsLab and click Finished

#. Click on the BotsLab profile and select the Application Security tab at top.

#. Click where it says Disabled and select the checkbox to Enable Application Security

#. Disable TPS-Based Detection on the left column by setting Blocking to Off.

#. Enable Bot Signatures on the left column by clicking Disabled and check the Enabled box.

#. Click Update to save the profile changes.


Create a Bot Logging Profile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Go to Security > Logging Profiles and click Create

#. Name the profile BotsLogger and check Bot Defense

#. Check all the boxes and leave remote publisher to None 

#. Click Update to save the profile


Assign DoS and Logging Profile to Virtual Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Go to Local Traffic > Virtual Servers > click on the 10.1.10.145 VIP

#. At the top, click on the Security Tab > Policies 

#. For DoS Protection Profile, select BotsLab

#. For Log Profile, select BotsLogger

#. Click Update to save changes


Simulate Bot Activity and Review Logs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. On the client workstation, open a terminal app

#. Run the following apache bench command:  ab -c 10 -n 10 -r http://10.1.10.145/

#. Review the Security Logs at Security > Event Logs > Bot Security > Requests
  a.Did requests succeed or fail?
  b.Why or why not?

#. Run the attack using a custom user-agent:
  a.Ab -c 10 -n 10 -r -H “User-Agent: Agilitybot” http://10.1.10.145/
  b.Review the request logs to determine if the attack was mitigated
  c.Why did the attack succeed?

#. Add a custom bot signature to your BotsLab profile
  a.Go to Security > Options > DoS Protection > Bot Signatures List and click Create
  b.Name the signature Agilitybot and populate the following, then click Create
    Category: DoS Tool
    Rule:  User-agent > contains > Agilitybot
    Risk: Medium

#. Rerun the attack from step 4 and review the request logs.
  a.Was the attack mitigated?

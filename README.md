A STEP-BY-STEP TUTORIAL:
<h1>SETUP DOKKU ON AMAZON AWS LIGHTSAIL</h1>


![](./images/title-graphic1.jpeg) 


TODOS:  This article is still a work-in-progress...
- add Let's Encrypt using dokku-letsencrypt HTTPS
- add SWAP file on server with less than 1GIG RAM
- add domains to Dokku manually


<br>
##TABLE OF CONTENTS:
  * [**PREREQUISITES:** What you need before you start](#prerequisites)
  * [**STEP #1:** Create a new AWS Ubuntu server instance](#step-1)
  * [**STEP #2:** Connect to your new server and apply updates](#step-2)
  * [**STEP #3:** xxxxxxxxxxxxxxxxxx](#step-3)
  * [**STEP #4:** xxxxxxxxxxxxxxxxxx](#step-4)
  * [**STEP #5:** xxxxxxxxxxxxxxxxxx](#step-5)
  * [**STEP #6:** xxxxxxxxxxxxxxxxxx](#step-6)
  * [**STEP #7:** xxxxxxxxxxxxxxxxxx](#step-7)
  * [**STEP #8:** xxxxxxxxxxxxxxxxxx](#step-8)
  * [**STEP #9:** xxxxxxxxxxxxxxxxxx](#step-9)
  * [**STEP #10:** xxxxxxxxxxxxxxxxxx](#step-10)
  * [**STEP #11:** xxxxxxxxxxxxxxxxxx](#step-11)

<br>
<br>
##PREREQUISITES:
- You will need your own registered domain name (i.e. mydomain.com) and will need administrative access to modify the DNS settings for it on your registrar's website.

- You will need to sign-up for an AWS account and be able to  login to LightSail (www.amazonlightsail.com).

<br>
<br>
##STEP #1
<h3>Create a new AWS Ubuntu server instance</h3>



- Login to your LightSail account. Click the CREATE INSTANCE button. Under 'Pick your instance image', click the BASE OS button. Then, choose UBUNTU.

- Scroll down and you will see: "You are using the default SSH key pair for connecting to your instance." If you wish, you can create a new SSH key here, but it is not necessary. We will use the DEFAULT SSH KEY. 

- Scroll down and CHOOSE YOUR INSTANCE PLAN. Click on the $5/month instance plan to begin with. You can always up-size to a larger instance later as needed. 

- Scroll down and NAME YOUR INSTANCE. You can keep the default name, or give it any name you wish. I will name mine: Dokku1.

- Finally, hit the CREATE button.

In a few minutes, your new server instance will be ready.



<br>
<br>
##STEP #2
<h3>Connect to your new server and apply updates</h3>

Use the browser-based terminal window to connect to your server instance and update it.

- Find your new server instance. You will see three vertical dots. Click them and select CONNECT from the list. A terminal emulator window should pop-up with a command prompt.

- At the command prompt($), type: sudo apt update  (hit enter).

- Next, type: sudo apt upgrade  (hit enter).

- You will be asked: Do you want to continue? [Y/n]. Type y (hit enter). This will install a bunch of updates for your Ubuntu Linux server. This could take about 5 minutes or so. Be patient.

- Finally, type: sudo reboot  (hit enter). This will reboot the server and disconnect you from the terminal window. You can now close the terminal window. 

Your Ubuntu Linux server is now updated with the latest OS updates.

<br>
<br>
##STEP #3
<h3>CREATE AND ASSIGN A STATIC IP </h3>
First, setup a static IP address for your new server. By default, your new server instance will get a new IP address everytime it restarts. We don't want this. We want our IP address to stay the same forever.

- Click the CREATE OTHER RESOURCES button/menu and choose STATIC IP.

- Go to ATTACH TO AN INSTANCE. Select the instance you just created from the SELECT AN INSTANCE menu. Mine is: Dokku1. Yours will be whatever you named your instance. 

- (optional) Under NAME YOUR STATIC IP, you can enter in a custom name. I used the default name.

- Click the CREATE button.


<br>
<br>
##STEP #4
<h3>ADD A NEW DNS ZONE</h3>
Next, we want to create a new DNS ZONE for our domain name.

- Click the CREATE OTHER RESOURCES button/menu again, choose DNS ZONE.

- Create DNS Zone. Enter your domain name in the box under ENTER THE DOMAIN NAME YOU HAVE REGISTERED. You do not need the "WWW." before your domain name. For example: mydomainname.com.

- Scroll down and click the CREATE DNS ZONE button.

<br>
<br>
##STEP #5
<h3>CONFIGURE THE DNS ZONE</h3>
You should now be on the DETAILS page of your new DNS ZONE.
Let's add some DNS Records to our new DNS ZONE.

- Click on the link-button:  **+ ADD RECORD **

<h5>First entry:</h5>
    TYPE: A
    SUB-DOMAIN: YOURDOMAIN.COM (NO WWW. OR DOT BEFORE NAME)
    DESTINATION IP: (CHOOSE YOUR SERVER INSTANCE FROM THE MENU)
	
- Click on the link-button:  **+ ADD RECORD** 

<h5>Second entry:</h5>
    TYPE: A
    SUB-DOMAIN: WWW.YOURDOMAIN.COM (NO WWW OR DOT BEFORE NAME)
    DESTINATION IP: (CHOOSE YOUR SERVER INSTANCE FROM THE MENU)

- Click on the link-button:  **+ ADD RECORD **

<h5>Third entry:</h5>
    TYPE: A
    SUB-DOMAIN: NAME-OF-YOUR-DOKKU-APP.YOURDOMAIN.COM (NO WWW. OR DOT BEFORE NAME)
    DESTINATION IP: (CHOOSE YOUR SERVER INSTANCE FROM THE MENU)
<br>


- Click SAVE to lock in your new settings.



<br>
<br>
##STEP #6
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>


<br>
<br>
##STEP #7
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>


<br>
<br>
##STEP #8
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>


<br>
<br>
##STEP #9
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>


<br>
<br>
##STEP #10
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>


<br>
<br>
##STEP #11
<h3>xxxxxxxxxxxxxxxxxxxxxxx</h3>



--------------------------------------------------------------------
PART #4 - CONFIGURE THE DNS ZONE

You should now be on the DETAILS page of your new DNS ZONE.
Let's add some DNS Records to our new DNS ZONE.
--------------------------------------------------------------------

xx. Click on the link-button: [ + ADD RECORD ]

First entry:
	TYPE: 				A
	SUB-DOMAIN:			YOURDOMAIN.COM (NO WWW. OR DOT BEFORE NAME)
	DESTINATION IP:		(CHOOSE YOUR SERVER INSTANCE FROM THE MENU)

Second entry:
	TYPE: 				A
	SUB-DOMAIN:			WWW.YOURDOMAIN.COM
	DESTINATION IP:		(CHOOSE YOUR SERVER INSTANCE FROM THE MENU)

Third entry:
	TYPE: 				A
	SUB-DOMAIN:			NAME-OF-YOUR-DOKKU-APP.YOURDOMAIN.COM
	DESTINATION IP:		(CHOOSE YOUR SERVER INSTANCE FROM THE MENU)

xx. Click SAVE to lock in your new settings.



NOTE: You will need to create a seperate A-RECORD for each sub-domain that you wish to use with YOURDOMAIN.COM. For example, if you want to create a new Dokku app called 'SUPERDOOPER', you will need to create the following DNS entry:
	TYPE: 				A
	SUB-DOMAIN:			SUPERDOOPER.YOURDOMAIN.COM (NO WWW.)
	DESTINATION IP:		(CHOOSE YOUR SERVER INSTANCE FROM THE MENU)

xx. Click SAVE to lock in your new settings.



--------------------------------------------------------------------
PART #xxxxx - ALLOW HTTPS THROUGH THE AWS FIREWALL

In order for web visitors to be able to visit your sites over HTTPS,
we need to open a port in the AWS firewall. It's easy, here's how...
--------------------------------------------------------------------

xx. Click on the AMAZON LIGHTSAIL logo in the upper-right-hand corner. This will take you back to the main screen.

xx. Find your new server instance. You will see three vertical dots. Click them and select MANAGE from the list.

xx. Click the NETWORKING link. Scroll down to the FIREWALL settings. You should see the following settings:

	APPLICATION		PROTOCOL	PORT RANGE
	-------------	----------	------------
	SSH				TCP			22
	HTTP			TCP			80

xx. Click the button/link: [ + ADD ANOTHER ].

xx. Under APPLICATION, select "HTTPS" from the menu. PROTOCOL and PORT RANGE fields are set automatically.

xx. Click SAVE to lock in your new settings.




--------------------------------------------------------------------
PART #xxxxx - POINT YOUR DOMAIN NAME TO AWS

Now that we have created a static IP address and a DNS ZONE, we can configure the domain on your registrar's website to point to AWS.
--------------------------------------------------------------------

xx. In a new brower window, you will need to login to your registrar's website. The registrar is the company that you used when you registered the domain name. My domain name was registered on GoDaddy.com, but your registrar should have similar settings.

xx. Once logged in, you will want to find the domain name that you want to point to AWS. Select it and look for settings similar to: MANAGE or MANAGE DNS SETTTINGS.

xx. Look for NAMESERVERS or USE CUSTOM NAMESERVERS. We need to enter in some addresses that will point this domain's DNS to AWS. We will get theses addresses from the AWS/LightSail website.

xx. Go back to the AWS/LightSail website. Click on the logo in the upper-right-hand corner so that you are on the main page. Sroll down to the DNS ZONE you created with your domain name. Click on the three vertical dots and choose MANAGE.

xx. Scroll down to the bottom of the page until you see NAMESERVERS. These are the namesevers that you will need to enter into your registrar's CUSTOM NAMESERVERS entry box. Enter all four of them. Be sure to hit SAVE.

Now, your domain name is pointed to AWS! Time to setup DOKKU!





 

--------------------------------------------------------------------
PART #xxxxx - INSTALL DOKKU
--------------------------------------------------------------------
xx. Click on the AMAZON LIGHTSAIL logo in the upper-right-hand corner. This will take you back to the main screen.



Use default SSH key. Download key to your local machine and store it in: ~/.ssh/


2. On LightSail, click on your new instance name. This will take you to MANAGE settings. 



2. Assign the new instance a Static IP.
3. Go to MANAGE
3. Connect to new instance using SSH. ($ ssh -i ~/.ssh/AWS/LightsailDefaultPrivateKey.pem ubuntu@emveeoh.com).
4. Run UPDATE and UPGRADE on Ubuntu to make the installation current. ($ sudo apt update && sudo apt upgrade).
5. Install DOKKU with curl script found at: http://dokku.viewdocs.io/dokku



--------------------------------------------------------------------
PART #xxxxx - CREATE THE RSA PRIVATE/PUBLIC KEY PAIR FOR SSH CONNECTION TO DOKKU
--------------------------------------------------------------------
Step-by-step directions:
https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2

6. On your local machine, run this terminal command: $ ssh-keygen -t rsa
7. Enter file in which to save the key (/home/mvo/.ssh/id_rsa). Give it a name. Example: dokku1-key
8. Pass phrase is optional. You will have to type this each time you connect. Leave it blank if you want faster login.
9. Two files were created for you. Both have the same name, but one will have the extension .pub. Grab these files and put them in: ~/.ssh/

>> You now have the public/private key you need to SSH into your Dokku server.



--------------------------------------------------------------------
 PART #xxxxx - CONFIGURE DOKKU / ADD PUBLIC KEY:
--------------------------------------------------------------------
6. Get IP Address for new LightSail instance. Open this URL in browser. Should be a static IP.
7. You should see: Dokku Setup and it should already have the PUBLIC KEY text pasted into the Public Key box. Erase any text that might appear before the text "ssh-rsa". This is not part of the key. 
8. In the HOSTNAME box, enter in a domain name that you have registered.
9. Check the box "Use virtualhost naming for apps".
10. Click "Finish Setup". 

>> Your Dokku instance is now ready to receive site/app uploads.








**alexa_skill_bridge_lambda**

The **Checklist** for your guys in the past and the future for the record.
(If you don't pass thru below checklist any of bit, you cannot get the own Alexa skill link.)



# **[Summary]**
- Exposed 443 HA port(MUST).
- Any SSL cert.
- Get the external HA Address.
- Alexa config in HA confiuration.xml
- Lambda at right region for locale
- Set the address into everywhere correctly like BASE_URL, Alexa console, etc.
- Non-blocked network path to HA reside in your room.
- Wait discovery and use.



# **[pre-requisition]**
1. Check HA address that your own domain or dynamic DNS(DDNS) or even IP
2. Prepare sure SSL certification that the free Let'sencrypt or free self-signed or commercial SSL cert if you would like.
3. Set the SSL cert on your server for HTTPS. And make sure SSL properly applied.

4. Set Alexa configuration in configuration.xml. Start simple and fill up later after link. Make problem simple for linkage.

5. Create AWS account
6. Choose the AWS Lambda region that N.Virginia or Oregon or EU that related to your Alexa language locale. AWS Alexa service will automatically find your Lambda region geologically by judging your Alexa locale.
 > I prefer make three identically same lambda in each Regions that Virginia, Oregon, EU if you need it.
7. Just copy & paste the source code into the Lambda(s) from Matt2005 at https://gist.github.com/matt2005/744b5ef548cc13d88d0569eea65f5e5b (thanks)

8. Create AWS Alexa Developer Account
9. Create AWS Alexa Skill for your own HA linkage as the materials
10. Put the endpoint address into the Alexa skill setting(as only default if you only have one, or set multiply each by check the checkbox.)

11. Setup the Lambdas's trigger as Alexa

12. READ carefully ALL the MATERIALS regards above to complete the section for 'Lambda' and 'Skill' both.(above are only simple summary)

13. Stop/cut and logout the home asisstant's(by nabucase.net) cloud annual payment service from the HA settings if you have.



# **[To get account link(important part)]**
1. Check the AWS Lambda region that N.Virginia or Oregon or EU that related to your Alexa locale
2. Make sure your home assistant's exposed port is 443 not 8123 which Alexa OAuth standard requirement.
 > so need to change your nginx's exernal open port into 443. Giveaway the 443 to HA if another your own service holding it.
3. Make sure your network firewall that possible to reach to Home assistant by LTE or from any outside not your home Wi-Fi self.
 by test POST https://your_ha-domain_name/api/alexa/smart_home from lambda source code that any of response working. If you can see 40x on web browser, you will be fine.
 > Make sure below paths are accessible without any blocker(do not care about server errors if you can reach it.)
  - GET https://your_ha-domain_name/auth/authorize (OAuth standard api interface)
  - GET https://your_ha-domain_name/auth/providers (OAuth standard api interface)
  - GET https://your_ha-domain_name/manifest.json (OAuth standard api interface)
  - POST https://your_ha-domain_name/auth/login_flow (OAuth standard api interface)
  - POST https://your_ha-domain_name/api/alexa/smart_home (Alexa standard interface)
  which means that allow every URL paths in your firewall and NginX for HA.

4. Make sure your NginX really bypassing to your HA the outside traffic.
 > Especially, https://your_ha-domain_name/api/alexa/smart_home paht possible to bypass all traffic.

5. Get your final external address, and set into all BASE_URL of environment variables & every in AWS Alexa console, AWS Lambeda, NginX, etc that port 443 without ':xxxx' part for your HA address.

6. If your SSL cert is free one, make sure your skill as in 'DEV' mode on the Alexa console where listed. If you have commercial no matter what dev or production mode.

7. Go to Alexa app or web > go to skill list > find your skill in DEV or peroper tab > click the skill you made > 'Enable' > Now login into HA(doesn't matter MFA or not) > TADA! you can see beautiful green 'successfully linked' message.
(if you cannot, it might firewall or any network path issue that blocked to reach to HA. So go back and recheck again.)



# **[Wait discovery(which Automatic drive)]**
1. AFTER, account link as above, the Alexa app gose to discovery mode.
IF you already have discovered devices list in the Alexa app by another Alexa link service,
the app will tell you 'NO NEW device discovered' that nothing wrong since there are NO MORE NEW devices to discover.
or
if you are very new to link-up with Alexa, after discovery while, you can see all the devices on your Alexa app.

Walla!. All your from now.



# **[Addition]**
1. Do not spend your money for same services. Since this is exactly same service you have now.




# **[Q & A]**
- Is there will be extra charges/bill from AWS Lambda or Alexa Console?
 > Mostly zero. Since the Lambda(a bridge between Alexa system and HA) only used when you are in log-in via Alexa skill
 > and discovery and some only few.
 > By the discovered infomation(which rarely occur), Alexa communicate with HA directly in your local home network.
 > In common sense, monthly 5000 calls of small Lambda only make about 0.02 USD per month. That cheap enough. 
 > it only make sevral hundres of calls. Do not worry unless your system hacked by bad guys.
- Is there any addtional technical modification while do all above?
 > No and Yes.
 > For Alexa console and AWS Lambda code, no extra effort needed. Just copy & paste all the things and do as the materials exaclty guide you. Do no addtional thing unless you are exaxtly understand what you are doing additionally.
 > For your local home network(like nginx and firewalls, etc), yes. you need to do adjust your own network configuration. But you can find everythings from web. Just do google.


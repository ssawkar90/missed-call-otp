# What is mOTP: #

mOTP is an Open ~~Source~~ API Alternative to sms based One Time Password. It is a hosted, secured, scalable solution for customer phone verification. The literal meaning of mOTP is Missed Call Based One Time Passwords

# Why mOTP: #

mOTP disrupts the way one time passwords are delivered for Two Factor Authentications ( 2FA ). mOTPs are pushed via Missed Calls in place of an SMS and thus eliminates any and every Cost, Delay & Dnd Hurdles.


# An Idea #


An Idea is to disrupt the way in which Two Factor Authentication is performed.

**Background:**
Two  factor authentication is an extension to the pin based / password based  login process, which adds up an extra layer of security, towards  validating end user's identity.

**As Is:**
With the traditional  approach, One time passwords ( hereafter, referred to as OTPs ) are sent  via either an SMS or an Automated call to the end user. End user then  enters back, the OTP information received, which validates his identity  and then is given an authorization to access the system.

**To Be:**
An  idea is to disrupt the way, in which OTP information is communicated to  the user. Instead of using an SMS or an automated outbound call, the  OTP content would be delivered to end user, via just a Missed call.

**The Implementation:**
The implementation of mOTP would workout in following fashion.

1. End user enters his phone number to initiate 2nd factor authentication
2. OTP is delivered to end user via missed call
3. End user enters the information present in a missed call
4. On matching the information in OTP and information entered by user, Access is granted.

To justify its feasibility, I have created a simple API under project, code named ( mOTP - missed call OTP )
mOTP Community Website - An Open ~~Source~~ API for Phone Verification




# Problem Area: #


With the traditional approach, One time password ( hereafter, referred  to as OTP ) information was delivered via an SMS Or an automated  outbound call, so the system had mentioned below issues or the overheads  associated with the implementation.

**1. The Cost:**
1.1 The over all cost of implementation was high, as the cost was directly associated with
  1. 1.1 SMS : Sending Domestic / International SMS, depending on end user's geography.
  1. 1.2 Calls : Triggering Domestic / International Calls, depending on end user's geography.

1.2 The cost of implementation was also exponential to the Volume of SMS / Calls triggered by the system.
1.3 The cost of implementation was also related the service maintenance fees and such depending parameters.


**2. The Risk:**
With  the implementation of SMS, there was an acute risk of messages getting  blocked / dropped due to network issues or DND constraints.

To  control the costs incurred in above methods, a new technique was brought  into picture ( quite a while ago ), which emphasized on asking users to  give a missed call to the number displayed over target website. Well,  this definitely helps in cutting down the significant cost...But, Is it  really secured and safe ?
- Several caller id spoofinjg mechanisms  available over internet are sufficient to bypass the most critical step  involved as a 2nd factor to authenticate. Hence I thought of re-defining  use of a missed call in a 2nd factor authentication.

Contrast to above approach, mOTP approach has significant advantages, as listed below,

**1. Minimal or No Cost:**
-  As the OTP information is conveyed via mere missed call, so it directly  eliminated the cost detailed in points 1.1, 1.2 of the SMS / Call based  implementation.
- The system would cost very marginal fees for the service maintenance.

**2. Secured:**
-  As the mOTP is directly delivered to end user's device, thus it is more  secured and safe enough from any intermediate tampering attempts.

**3. Faster & Reliable:**
-  mOTP is delivered via missed call. Any operator across globe, gives  Priority to Calls over SMS and other VAS ( value added services ). Hence  mOTP has more probability to get delivered Faster & Successfully  over an SMS implementation.
- More over it has a higher probability  of getting delivered to almost every end user, as it complies with the  DND Scrubber rules.




# Market Impact: #


The Idea of delivering One time passwords ( hereafter, referred to as  OTPs ) would disrupt the way in which OTPs are delivered to the end  user, across vast variety of Verticals ( May it be Banking, Finance,  ITES, Travel, Healthcare Or Pharmacy ) as detailed below,

The  highest traction would be witnessed across eCommerce segment ( web and  mobile app world ) which uses OTPs as a primary way to authenticate  user's phone number / identity ( at Signup, while performing online  transaction etc )

Banks, Travel services and ITES can replace RSA  based physical token implementation ( which costs USD 45 per token  device + additional service cost ) with mOTP service and there by  significantly cutting down the costs incurred against the process of  user identity validation.

Health and Pharma companies can replace  the secure Id implementation with missed call OTPs for granting access  to their laboratory sections.

So would, it Disrupt the way in which Authentication is performed.
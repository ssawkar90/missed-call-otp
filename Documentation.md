# Introduction #

Get started with mOTP API to quickly implement user authentication
push and validate user's identity with mOTP API


# Details #

1.  Generate an mOTP API Access Key - GET Request
( You would receive an email with APIKey ( Public Key ) & Private key assigned for your domain. )

Syntax:
```
https://api.mOTP.in/v1/Add/<Domain>/<EmailAddress>
```

Sample Call:
```
https://api.mOTP.in/v1/Add/motp.in/admin@motp.in
```

Sample Response: JSON
```
{
"Status":"Success",
"Result":"API Key Generated for Domain - motp.in"
}
```

---

2.  Push An OTP to user's phone device - GET Request
( A user should receive a One time password on his phone. )

Syntax:
```
https://api.mOTP.in/v1/<APIKey>/<Phone_With_ISD>
```

Sample Call:
```
https://api.mOTP.in/v1/0223-8872-32883/+919733443344
```

Sample Response: JSON
```
{
"Status":"Success",
"Result":"sid526403fb836c13.05018010"
}
```


---

3. Validate OTP Entered by user on a web form - POST Request
( For verification, a POST request needs to be made to the below URL, passing private key in 'private' parameter )

Syntax:
```
https://api.mOTP.in/v1/OTP/<APIKey>/<SessionId>
```

Sample Call:
```
curl -XPOST https://api.motp.in/v1/OTP/0223-8872-32883/sid52634a850086d6.31056793 \
-d "private=0009-5263457d-fe87-6adf53fb"
```

Sample Response: JSON
```
{
"Status":"Success",
"Result":"08058"
}
```
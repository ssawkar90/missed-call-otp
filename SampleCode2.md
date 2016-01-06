# Introduction #

The code is contributed by tny.im developer.
Live demo: https://tny.im/otplogin.php

# Details #

**To send a one-time password to a phone:**


```

$replye = file_get_contents("http://api.motp.in/v1/YOUR_API_KEY_HERE/" . "USER_PHONE_NUMBER_HERE");
$reply = json_decode(trim($replye), true);
if($reply["Status"] == "Success") {
    // OTP sent, session ID is on $reply["Result"]
    // you need the session ID to get the correct code
} 

```



**To retrieve the correct password for the session ID that is returned on the previous step (so you can compare with what the user entered):
PHP Code:**



```

// get login otp that was sent to user
$ch = curl_init();
curl_setopt($ch,CURLOPT_URL,"http://api.motp.in/v1/OTP/YOUR_API_KEY_HERE/" . $reply["Result"]);
curl_setopt($ch,CURLOPT_POST,1);
curl_setopt($ch,CURLOPT_RETURNTRANSFER,1);
curl_setopt($ch,CURLOPT_POSTFIELDS,"private=YOUR_PRIVATE_KEY_HERE");
$replye = curl_exec($ch);
$reply = json_decode(trim($replye), true);
if($reply["Status"] == "Success") {
    // correct code is on $reply["Result"]
    // you can now compare it with what the user entered
    // obviously, you must let the user enter the received code before 

```

You can push the code to the user and get a session ID first, then have the user input the code and only then retrieve the correct one from the API, or you can do like me and do it all in one run, storing the correct code in a session variable and only comparing it later when the user provides it.
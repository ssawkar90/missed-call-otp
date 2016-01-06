# Introduction #

This is the customized example of Twilio two factor sample code.
The code is customized and made really simple with mOTP API.

Live Demo:
http://ws.motp.in/~rahcomp/twilio-custom/

Download Source Code:
http://ws.motp.in/~rahcomp/twilio-custom/dl/two-factor-authentication.zip

# Two-Factor Authentication #

Two-Factor Authentication is a more secure way of logging in to a website. In addition to entering a password online, a user has to enter a random verification code generated at login time. This combination of passwords makes it easier to safeguard your applications.

Historically companies that want to implement two-factor authentication distribute little devices to all of their employees that generate passcodes on demand. But these are expensive and get lost easily. With mOTP API you can set up your two-factor authentication system to run on a devices all of your employees already carry with them - their cellphone.

## Usage ##

There are three steps involved in building a two-factor authentication system.

  * We want to collect the username, phone number.

  * Next, we want to generate and send that password via a second (non-email/web) channel that an attacker is unlikely to have.

  * Finally, compare our originally generated password against the submitted password.


**1: Following code displays a simple login page, asking user to provide username and the phone number with international dialing code**

**index.php
```
<?php

session_start();

?>
<html>
    <head>
        <title>Two Factor Authentication Demo - with mOTP ( Missed Call OTP )</title>
        <style>
            .center {
                margin-left: auto;
                margin-right: auto;
                margin-top: 25px;
            }

            #submit { float: right; }

            form { border-style: solid; padding: 10px; width: 300px; }

            input[type="button"], input[type="text"], input[type="password"]
                { float: right; }

            div { text-align: center; width: 500px; }
        </style>
    </head>
    <body>
        <div class="center">
            <p>This is just a demo that demonstrates how mOTP ( Missed call OTP ) could be
                integrated to build a simple two-factor authentication system
                for better security and fraud prevention.</p>

            <p>No matter what username you put into the initial box, the system
                will generate a one-time use password similar to an RSA token.
                Once this password is used, the user's session is set and the
                password is destroyed. In this particular case, we're not
                storing anything long term.</p>

            <span id="message">
                <?php
                $message = urldecode($_GET['message']);
                echo "<font color=\"blue\">".preg_replace("/[^A-Za-z0-9 ,']/", "", $message)."</font>";
                $action = (isset($_SESSION['password'])) ? 'login' : 'token';
                ?>
            </span>

        <form id="reset-form" action="process.php" method="POST" class="center">
            <input type="hidden" name="action" value="<?php echo $action; ?>" />
            <p>Username: <input type="text" name="username" id="username" value="<?php echo $_SESSION['username']; ?>" /></p>

            <?php if (isset($_SESSION['password'])) { ?>
                <p>Password: <input type="password" name="password" id="password" /></p>
            <?php } else { ?>
                <p>Phone Number: <input type="text" name="phone_number" id="phone_number" value="like +919739593959" /></p>
                Preferred method:<br />
                mOTP: <input type="radio" name="method" value="mOTP" checked="checked" />
            <?php } ?>

            <p><input type="submit" name="submit" id="submit" value="login!" /></p>
            <p>&nbsp;</p>
        </form>

        <p>Original code submitted by - Twilio <br/>( https://www.twilio.com/docs/howto/two-factor-authentication ) </p>
      </div>
    </body>
</html>`
```**

**2: User fills in his details and submits login, this submit process calls Process.php page which determines the required action and calls the appropriate function within functions.php**

**Process.php
```
<?php

include 'functions.php';

/*
 * First we retrieve each of the relevant variables and remove any
 *   non-alphanumeric characters filter them to protect against things such
 *   as SQL Injection.
 */
$username = isset($_POST['username']) ? $_POST['username'] : '';
$username = preg_replace("/[^A-Za-z0-9]/", "", $username);
$password = isset($_POST['password']) ? $_POST['password'] : '';
$password = preg_replace("/[^A-Za-z0-9]/", "", $password);
$phoneNum = isset($_POST['phone_number']) ? $_POST['phone_number'] : '';
$phoneNum = preg_replace("/[^0-9]/", "", $phoneNum);
$method   = isset($_POST['method']) ? $_POST['method'] : '';

$action   = isset($_POST['action']) ? $_POST['action'] : '';
switch ($action) {
    case 'token':
        $message = user_generate_token($username, $phoneNum, $method);
        break;
    case 'login':
        $message = user_login($username, $password);
        break;
    default:
        echo 'do nothing';
}
header("Location: index.php?message=" . urlencode($message));
```**


**3: Function user\_generate\_token generates OTP ( stores it in session variable ) and pushes it to user's phone number using mOTP API code.**

on sending mOTP to user, user is prompted to enter received mOTP code.

functions.php also has a function 'user\_login' which checks the mOTP entered by user matches with mOTP stored in the session variable and thus performs the authentication process.


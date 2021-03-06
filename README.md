GAuth : Google Authenticator Code Generator/Validation
=========================

[![Total Downloads](https://img.shields.io/packagist/dt/enygma/gauth.svg?style=flat-square)](https://packagist.org/packages/enygma/gauth)

The `GAuth` library is designed to generate and validate codes compatible with the
Google Authenticator tools.

### Installation via Composer:

Include in your `composer.json` file:

```
{
    "require": {
        "enygma/gauth": "dev-master"
    }
}
```

#### Getting Started

To get started using the Google Authenticator with your application, you'll need to make an 
initialization key (using `generateCode`) and save that to your app's settings. This is the 
code you'll share with your users when they're trying to set up their client for your system.

Then, when they log in you have them enter in the latest code listed for your application for
thier account. 
 
**NOTE:** This tool offers a "window of opportunity" for the codes of 2 seconds forward and
backward of the current timestamp, just in case things are a bit off. You can change this with
the `setRange` method:

```php
<?php
$g = new \GAuth\Auth();

// set it to 3 seconds
$g->setRange(3);
?>
```

#### To generate a new code:

```php
<?php

require_once 'vendor/autoload.php';

// Useful for creating a new Initialization key if needed
$g = new \GAuth\Auth();
$code = $g->generateCode();
var_dump($code);

?>
```

#### To validate a code

```php
<?php

$code = 'code-inputted-from-user';

$g = new \GAuth\Auth('your-initialization-code');
$verify = $g->validateCode($code);

if ($verify == true) {
    echo 'User code verified!';
} else {
    echo 'User code invalid!';
}
?>
```

#### More info:

- [Google TOTP Two-factor Authentication for PHP](http://www.idontplaydarts.com/2011/07/google-totp-two-factor-authentication-for-php/)
- [Links to client for smartphones](http://support.google.com/accounts/bin/answer.py?hl=en&answer=1066447)

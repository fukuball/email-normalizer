# Email Normalizer
This library that will normalize email addresses for cases when different email addresses all point towards a single email account.
This is useful for cases such as when you want to limit a single user using a single email account to signup using different email addresses.

For example, Gmail will ignore dots and anything after a plus sign in an email address so `user.name+anything@gmail.com` is the same as `username@gmail.com`.

By default we have normalization rules in place for Gmail, Outlook, Yahoo and Fastmail emails including all their country specific and alternate domains.

Examples of rules that are implemented:

Plus Tags: `username+tag@gmail.com` normalizes as `username@gmail.com`

Hyphen Tags: `username-tag@yahoo.com` normalizes as `username@yahoo.com`

Dots: `first.last@gmail.com` normalizes as `firstlast@gmail.com`

Subdomain Addressing: `whatever@username.fastmail.com` normalizes as `username@fastmail.com`

Aliases: `username@googlemail.com` normalizes as `username@gmail.com`

### Install Using Composer
```shell script
composer require gabrola/email-normalizer
```

### Usage
```php
<?php
use Gabrola\EmailNormalizer\EmailNormalizer;
use Gabrola\EmailNormalizer\EmailRules;

$emailNormalizer = new EmailNormalizer(new EmailRules());
$normalizedEmail = $emailNormalizer->normalize('username+whatever@gmail.com');

echo $normalizedEmail; //Returns username@gmail.com
```
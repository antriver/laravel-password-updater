# laravel-password-updater

Handles password verification and re-hashing passwords that may be hashed by outdated methods. 

## Setup
```
composer require tmd/laravel-password-updater
```

## Usage
(Overly simplified example.)
```php
<?php

use Tmd\LaravelPasswordUpdater\PasswordHasher;

public function login(PasswordHasher $passwordHasher)
{
    /** @var User $user */
    $user = User::where('username', $credentials['username'])->first();

    if (!$user) {
        return ['username' => ['There is no account with that username.']];
    }

    if (!$passwordHasher->verify($credentials['password'], $user, 'password')) {
        return ['password' => ['That password is not correct.']];
    }

    // Password is correct.
}
```

# SPINEN's Laravel Mail Assertions

NOTE: This is based off a video titled ["Testing Email With Custom Assertions"](https://laracasts.com/series/phpunit-testing-in-laravel/episodes/12) that [Jeffrey Way](https://github.com/JeffreyWay) did on [Laracasts.com](https://laracasts.com).  If you do not have an account on that site, then you should.  It is an amazing resource.  We have just take that example & made it in an easy to install package.  Thanks Jeffrey!

[![Latest Stable Version](https://poser.pugx.org/spinen/laravel-mail-assertions/v/stable)](https://packagist.org/packages/spinen/laravel-mail-assertions)
[![Total Downloads](https://poser.pugx.org/spinen/laravel-mail-assertions/downloads)](https://packagist.org/packages/spinen/laravel-mail-assertions)
[![Latest Unstable Version](https://poser.pugx.org/spinen/laravel-mail-assertions/v/unstable)](https://packagist.org/packages/spinen/laravel-mail-assertions)
[![Dependency Status](https://www.versioneye.com/php/spinen:laravel-mail-assertions/0.1.1/badge.svg)](https://www.versioneye.com/php/spinen:laravel-mail-assertions/0.1.1)
[![License](https://poser.pugx.org/spinen/laravel-mail-assertions/license)](https://packagist.org/packages/spinen/laravel-mail-assertions)

PHPUnit mail assertions for testing email in Laravel.

## Build Status

| Branch | Status | Coverage | Code Quality |
| ------ | :----: | :------: | :----------: |
| Develop | [![Build Status](https://travis-ci.org/spinen/laravel-mail-assertions.svg?branch=develop)](https://travis-ci.org/spinen/laravel-mail-assertions) | [![Coverage Status](https://coveralls.io/repos/spinen/laravel-mail-assertions/badge.svg?branch=develop&service=github)](https://coveralls.io/github/spinen/laravel-mail-assertions?branch=develop) | [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/spinen/laravel-mail-assertions/badges/quality-score.png?b=develop)](https://scrutinizer-ci.com/g/spinen/laravel-mail-assertions/?branch=develop) |
| Master | [![Build Status](https://travis-ci.org/spinen/laravel-mail-assertions.svg?branch=master)](https://travis-ci.org/spinen/laravel-mail-assertions) | [![Coverage Status](https://coveralls.io/repos/spinen/laravel-mail-assertions/badge.svg?branch=master&service=github)](https://coveralls.io/github/spinen/laravel-mail-assertions?branch=master) | [![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/spinen/laravel-mail-assertions/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/spinen/laravel-mail-assertions/?branch=master) |

## Install

Install the package:

```bash
    $ composer require spinen/laravel-mail-assertions
```

## Using

You mixin the assertions with the ```Spinen\MailAssertions\MailTracking``` trait.  You get the following assertions...

* seeEmailBcc
* seeEmailCc
* seeEmailContains
* seeEmailEquals
* seeEmailFrom
* seeEmailReplyTo
* seeEmailSubject
* seeEmailTo
* seeEmailWasNotSent
* seeEmailWasSent
* seeEmailsSent

NOTE: If there was more than 1 email sent, then the assertions look at the last email.

## Example

```php
<?php
use Illuminate\Foundation\Testing\WithoutMiddleware;
use Illuminate\Foundation\Testing\DatabaseMigrations;
use Illuminate\Foundation\Testing\DatabaseTransactions;
use Spinen\MailAssertions\MailTracking;

class ExampleTest extends TestCase
{
    use MailTracking;
    
    /**
     * A basic functional test example.
     *
     * @return void
     */
    public function testBasicExample()
    {
        $this->visit('/route-that-sends-an-email')
             ->seeEmailWasSent()
             ->seeEmailSubject('Hello World')
             ->seeEmailTo('foo@bar.com')
             ->seeEmailEquals('Click here to buy this jewelry.')
             ->seeEmailContains('Click here');
    }
}
```

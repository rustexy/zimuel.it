# Enrico Zimuel web site

[![Build Status](https://secure.travis-ci.org/ezimuel/zimuel.it.svg?branch=master)](https://secure.travis-ci.org/ezimuel/zimuel.it)

This repository contains the source code of [Enrico Zimuel](http://www.zimuel.it)
web site.

The web site is built using the following technologies:

- PHP 7
- [zend-expressive](https://zendframework.github.io/zend-expressive/)
- [Plates](http://platesphp.com/) as template engine for PHP
- [Bootstrap](http://getbootstrap.com/) for HTML, CSS and JS
- [SparkPost](https://www.sparkpost.com/) for delivery service email
- [Invisible reCAPTCHA](https://www.google.com/recaptcha) for contact validation

The blog post section is managed using static HTML files, collecting the data
for pagination using a simple cache file in PHP.

## Installation

You need to use [composer](https://getcomposer.org/) to install all the library
dependencies:

```bash
composer install
```

If you don't have the composer command installed in your system, you can install
following [these steps](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx).

## Configuration

In order to run the web site you need to have an API key from [SparkPost](https://www.sparkpost.com/)
and a secret value from [Invisible reCAPTCHA](https://www.google.com/recaptcha).

These values need to be stored in `/config/autoload/sparkpost.local.php` and
`/config/autoload/recaptcha.local.php`. You can generate these files starting
from the `*.local.php.dist` versions and copy in `*.local.php`.

## Blog

The blog posts are stored in the `/data/posts` folder. If you modify, add or
delete a blog post you need to remove the `/data/cache/posts.php` file. This
file will be autogenerated on the first load of a blog related page.

## Run

For testing purpose, you can run the website using the internal web server
of PHP, running the following command:

```bash
php -S 0.0.0.0:8000 -t public public/index.php
```

If you want to deploy the website in a production environment you need to
use `public` as web directory.

You can optimize the composer autoload in a production environment and omit the
dev requirement using the following command:

```bash
composer install --no-dev --optimize-autoloader
```

## Copyright

Copyright (c) 2001-2017, [Enrico Zimuel](http://www.zimuel.it).

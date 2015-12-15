common-dev
==========

[![Latest Stable Version](https://poser.pugx.org/leanphp/common-dev/version)](https://packagist.org/packages/leanphp/common-dev)
[![Latest Unstable Version](https://poser.pugx.org/leanphp/common-dev/v/unstable)](https://packagist.org/packages/leanphp/common-dev)
[![MIT License](https://poser.pugx.org/leanphp/common-dev/license)](https://packagist.org/packages/leanphp/common-dev)

[leanPHP/common-dev][0] is a set of modern PHP **5.6+** development tools and
libraries, which help you write PHP packages and libraries that comply with
[PHP-FIG][1] standards and adhere to best PHP practices defined in [PHP - The
Right Way][2] guidelines.

These tools help you write **well-tested** functional & **OOP** code ([TDD][3],
[BDD][4], [SOLID][5]). It will allows you to **distribute** your code via
[Packagist][6] by using [composer][7].

See [Packages](#Packages) for a list of packages that this meta-package
provides. [Usage](#Usage) section covers information regarding various tools
and libraries. Additionally, we provide [example configuration
files](#Configuration) for various tools that this package provides (`config/`
directory).

## Install

Install this package as a development requirement in your project. It's always
best to let composer pick up the latest supported version, which will be based
on your PHP version:

    $ composer require-dev leanphp/common-dev

### PHP 5.5

    $ composer require-dev leanphp/common-dev ~5.5

### PHP 5.4

    $ composer require-dev leanphp/common-dev ~5.4

### PHP 5.3

    $ composer require-dev leanphp/common-dev ~5.3

## Packages

This package will trigger installation of various PHP [libraries](#Libraries) and [development tools](#Development Tools).

### Libraries

This is a list of PHP Libraries that this package installs:

- [symfony/var-dumper](#var-dumper) **v3** - Advanced Variable Dumper by
  Symfony project (`dump()` instead of `var_dump()`).
- [mockery][210] **v0.9** - a simple yet flexible PHP mock object framework for
  use in unit testing.
- [prophecy][220] - highly opinionated mocking framework for PHP.
- [alice][240] - Expressive Fixtures generator based on [faker][250].
- [faker][250] - PHP Library to generate fake data for you.
- [vfsStream][300] - Virtual file system to mock the real file system in unit
  tests.
- [PHPUnit](#PHPUnit) **v5** - The PHP Unit Testing framework.
- [PHPSpec](#PHPSpec) **v2** - SpecBDD / BDD Testing framework for PHP with extensions:
    - [phpspec-code-coverage][805] - Code Coverage for [PHPSpec][800].
    - [phpspec-typehintedmethods][810] - Generate Typehinted methods
    - [phpspec-exemplify-extension][820] - Add exemplify command to generate
      example in [PHPSpec][800] specs.
- [behat][900] **v3** - ScenarioBDD / BDD Testing framework for PHP, with
  extensions:
    - [behat/mink-extension][950] - [mink][400] extension for [behat][900].
    - [behat/mink-goutte-driver][960] - [Goutte][450] driver for [mink][400].
    - [behat/mink-browserkit-driver][970] - Symfony BrowserKit driver for
      [mink][400].
    - [rmiller/behat-spec][980] - [behat][900] and [PHPSpec][800] integration.
- [mink][400] - Browser Emulator / Abstraction framework for PHP.


### Development Tools

This is a list of PHP Development Tools that this package installs:

- [ApiGen](#ApiGen) **v4** - PHP Source Code API generator.
- [PHPMD](#PHPMD) **v2** - PHP Mess Detector. Optimize your code, reduce
  complexity, cleanup unused parameters, methods, variables & more.
- [PHP_CodeSniffer](#PHP CodeSniffer) **v2** - PHP Code Sniffer ensures that
  your code remains clean and consistent. It is a set of scripts to detect and
  automatically correct violations of a defined coding standard.
- [phpcs-symfony2-standard][140] - Symfony2 Coding Standard configuration for
  [PHP_CodeSniffer][130].
- [phpcpd](#phpcpd) - Copy/Paste Detector (CPD) for PHP code.
- [phploc](#phploc)- a tool that quickly measures the size of your PHP project.

## Usage

**Note!** When executing command we will use `bin/command` as an example. This
requires `bin-dir` parameter set in `composer.json` of your project:

```js
    "config": {
        "bin-dir": "bin"
    },
```

If `bin-dir` is not set, use `./vendor/bin` prefix when running command line tools.

### ApiGen

[ApiGen][100] is a PHP Source Code API generator, which generated class
reference files in HTML format for your source code. The generated reference
files are useful for developer to familiarize with API of your PHP classes.

It is best to use example [apigen.yaml](config/apigen.yaml) configuration file.
Copy it to the root of your project:

    $ cp vendor/leanphp/common-dev/config/apigen.yml apigen.yml

If your source code is NOT stored in `src/` directory, adjust the `source` parameter in `apigen.yml`.

Generate the API:

    $ bin/apigen generate

The HTML files will be generated in `build/docs` directory, which is configured via `destination` parameter in `apigen.yml`.

### PHPMD

[PHPMD][120] (PHP Mess Detector) is a code optimizer, which scans your code for
complexity, unused parameters, methods. It helps developers optimize their PHP
code. It can also point out more problematic areas of your code, that need
refactoring or are too complex. It's a great tool in any PHP developers
toolbox.

PHP Mess Detector is highly configurable and you can define different [rulese][121].
It is best to use example [phpmd.xml](config/phpmd.xml) configuration file,
which has all of them enabled and customize from there.

Copy it to the root of your project:

    $ cp vendor/leanphp/common-dev/config/phpmd.xml phpmd.xml

PHPMD is run via console:

    $ bin/phpmd <SOURCE_DIR> <FORMAT> <RULESET_FILENAME>

You can generate a text formatted report for your source code in `src/`
directory, but using `phpmd.xml` ruleset:

    $ bin/phpmd src/ text phpmd.xml

**Note!** Consult [PHPMD Documentation on Rules][121] when customizing
`phpmd.xml` for your project!

### PHP CodeSniffer

[PHP_CodeSniffer][130](#PHP CodeSniffer) ensures that your code remains clean
and consistent. It is a set of scripts to detect and automatically correct
violations of a defined coding standard. It is extremely useful to keep the
code consistent, especially when there are multiple developers working on one
project. It is also helpful when working alone as it will make you write more
consistent code.

It is best to use example [phpcs.xml](config/phpcs.xml) configuration file as it has a Symfony based coding standard defined, which will give you a good start.

Copy the example config to the root of your project:

    $ cp vendor/leanphp/common-dev/config/phpcs.xml phpcs.xml

If your source code is NOT stored in `src/` directory, adjust the `<file>` tag
in `phpcs.xml`. Additionally, make sure that any test or build directories are
excluded (via `<exclude-pattern>` tag).

To get a list of coding standard violations, Run PHP CodeSniffer tool:

    $ bin/phpcs

PHP CodeSniffer also includes a tool which allows you to fix many of these
violations automatically:

    $ bin/phpcbf

### phpcpd

[phpcpd][150] is a Copy/Paste Detector (CPD) for PHP code. It allows you to
scan your PHP files and detect duplicate code (likely a Copy/Paste). This is
a code that likely needs refactoring. It's a great tool to improve the quality
of your code.

To scan `src/` directory and detect problematic areas in your code:

    $ bin/phpcpd src/

### phploc

[phploc][160] is a tool that quickly measures the size of your PHP project. It
scans the structure of your PHP Source Code and returns various statistics
about it (such as number of Classes, Methods, Variables etc.).

In order to scan source code directory `src/`:

    $ bin/phploc src/

### var-dumper

[symfony/var-dumper][110] is an Advanced Variable Dumper by  Symfony project.
It provides developer with `dump()` function which is a better alternative to
`var_dump()` or `print_r()`. It provides well formatted output, which adapt
depending on context (console, browser) and packs nice additional features.

This package add **global function** `dump()`, which can be called from
anywhere in your code:

```php
    <?php
    require 'vendor/autoload.php';

    $date = new \DateTime()
    dump($date)
```

**Note!** Try executing the example snippet above in the console AND then
browser to see the differences.

### PHPUnit

[PHPUnit][200] is The PHP Unit Testing framework. It's an industry proven and
standard unit testing framework for PHP. If you prefer to do simple TDD instead
of BDD - [behat][900] (StoryBDD) or [PHPSpec][800] (SpecBDD), then this is your
test tool of choice.

In order to setup PHPUnit for your project, you can use example
[phpunit.xml](config/phpunit.xml) configuration file.

Copy it to the root of your project:

    $ cp vendor/leanphp/common-dev/config/phpunit.xml phpunit.xml

If your tests are NOT stored in `tests/` directory, adjust the `<testsuites>`
tag in `phpunit.xml`. The file provides additional comments and settings that
can be useful when setting up PHPUnit for your project PHP package.

Run PHPUnit tests:

    $ bin/phpunit

PHPUnit will generate various reports (defaults to `build/` directory), which
can be used by various tools when analyzing your code and tests (i.e. test code
coverage generation).

For more information check [PHPUnit Documentation][201].

### PHPSpec

[PHPSpec][800] is a SpecBDD ([BDD][4]) Testing framework for PHP. It is
specification oriented testing framework. It allows you to define your tests,
which then are used to generate PHP Classes, based on the defined
specification. PHPSpec is also great for unit testing.

In order to setup PHPSpec for your project, you can use example
[phpspec.yml](config/phpspec.yml) configuration file.

Copy it to the root of your project:

    $ cp vendor/leanphp/common-dev/config/phpspec.yml phpspec.yml

The configuration file will enable all the PHPSpec extensions that come
installed with this package.

**Note!** Due to PSR-4 you have to set the default PSR-4 namespace in
`phpspec.yml` which is set to `LeanPHP\Common` in the example `phpspec.yml`.
**Make sure to change it to your package's namespace!**.

Write your first spec file `spec/ClassSpec.php`:

```php
<?php

namespace spec\LeanPHP\Common;

use PhpSpec\ObjectBehavior;

class ClassSpec extends ObjectBehavior
{
    function it_can_say_hello()
    {
        $this->say('hello')->shouldReturn('hello');
    }
}
```

Run PHPSpec to generate the class, based on the defined specification:

    $ bin/phpspec run

PHPSpec will fail the test, but will ask you to generate the classes for you.

For more information check [PHPSpec Documentation page][801].

## Configuration

You can find example configuration files for the tools and libraries in
`config/` directory. Included example config files:

- [apigen.yaml](config/apigen.yaml) - [ApiGen](#ApiGen) example config.
- [phpcs.xml](config/phpcs.xml) - [PHP_CodeSniffer](#PHP CodeSniffer) Coding
  Standard config.
- [phpmd.xml](config/phpmd.xml) - [PHPMD](#PHPMD) example config.
- [phpunit.xml](config/phpunit.xml) - [PHPUnit][200] example config.
- [phpspec.yml](config/phpspec.yml) - [phpspec][800] example config.
- [behat.yml](config/behat.yml) - [behat][900] example config.

These configuration files must either be placed in the root of your repository
or you have to point configuration file manually when using a specific tool.
Most of the time making a copy of the file in the project's root and
customizing it should be sufficient.

## Change Log

Please see [CHANGELOG.md](CHANGELOG.md) for information of what was changed.

## Author

Copyright (c) 2012-2015 ek9 <dev@ek9.co> (https://ek9.co)

## License

Licensed under [MIT License](LICENSE).

[0]: https://packagist.org/packages/leanphp/common-dev
[1]: http://www.php-fig.org
[2]: http://www.phptherightway.com
[3]: https://en.wikipedia.org/wiki/Test-driven_development
[4]: https://en.wikipedia.org/wiki/Behavior-driven_development
[5]: https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)
[6]: https://packagist.org
[7]: https://getcomposer.org

[100]: http://apigen.org
[110]: https://github.com/symfony/var-dumper
[120]: https://phpmd.org
[121]: https://phpmd.org/rules/index.html
[130]: https://pear.php.net/package/PHP_CodeSniffer
[140]: https://github.com/leaphub/phpcs-symfony2-standard
[150]: https://github.com/sebastianbergmann/phpcpd
[160]: https://github.com/sebastianbergmann/phploc
[200]: https://phpunit.de
[201]: https://phpunit.de/documentation.html
[210]: https://github.com/padraic/mockery
[220]: https://github.com/phpspec/prophecy
[240]: https://github.com/nelmio/alice
[250]: https://github.com/fzaninotto/Faker
[300]: https://github.com/mikey179/vfsStream
[400]: http://mink.behat.org
[450]: https://github.com/FriendsOfPHP/Goutte
[800]: http://www.phpspec.net
[801]: http://www.phpspec.net/en/stable/manual/introduction.html
[805]: https://github.com/henrikbjorn/PhpSpecCodeCoverageExtension
[810]: http://github.com/ciaranmcnulty/phpspec-typehintedmethods
[820]: https://github.com/richardmiller/ExemplifyExtension
[900]: http://behat.org
[950]: http://extensions.behat.org/mink
[960]: https://github.com/minkphp/MinkGoutteDriver
[970]: https://github.com/minkphp/MinkBrowserKitDriver
[980]: https://github.com/richardmiller/BehatSpec

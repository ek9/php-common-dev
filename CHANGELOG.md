# CHANGELOG

This is a CHANGELOG file for [ek9/common-dev][0] package.

## 3.3.x-dev / FUTURE

### Changed

- Update vfsStream from `~1.1` to `~1.2`

## 3.1.1 / 2013-12-29
- Updated PHP from `^5.3` to `~5.3,^5.3.3` as lower than `5.3.3` is NOT
  supported.


## 3.2.0 / 2014-01-02

### Changed

- vipsoft/code-coverage-extension from `~2.5` to `~2.5.0,^2.5.0.3`
## 3.1.1 / 2013-12-29
- Updated PHP from `^5.3` to `~5.3,^5.3.3` as lower than `5.3.3` is NOT
  supported.

## 3.1.0 / 2013-12-20

### Changed

- Updated faker from `~1.2` to `~1.3`

### Added


## 3.0.0 / 2013-12-03

### Changed

- Update php_codesniffer from `~1.4,^1.4.2` to `~1.5`
- Updated package information.

### Added

- PHP `^5.3`
- vipsoft/code-coverage-extension `~2.5` (for behat)

## 2.1.0 / 2013-11-10

### Changed

- Update phpcpd from `~1.4,^1.4.1` to `~2.0`

## 2.0.0 / 2013-09-09

### Changed

- Update alice from `~1.4` to `~1.5,^1.5.2`
- Update behat from `~2.4` to `~2.5`
- Update behat/mink-extenstion from `~1.1` to `~1.2`
- Update phpunit from `~3.7` to `~3.7,^3.7.19`
- Update phploc from `~1.7,^1.7.3` to `~2.0`

## 1.5.0 / 2013-06-18

### Changed

- Update faker from `~1.1` to `~1.2`

## 1.4.0 / 2013-05-27

### Changed

- Update mink from `~1.4` to `~1.5`
- Update mink-extension from `~1.0` to `~1.1`

## 1.3.0 / 2013-04-21

### Changed

- alice from `~1.3` to `~1.4`

## 1.2.0 / 2013-04-20

### Added

- phpcpd `~1.4,^1.4.1`

## 1.1.0 / 2013-02-23

### Changed

- Update alice from `~1.1` to `~1.3`

## 1.0.0 / 2012-12-30

### Changed

- Update alice from `~1.0` to `~1.1`

## 0.4.0 / 2012-11-25

### Added

- PHP_CodeSniffer `~1.4,^1.4.2`
- phploc `~1.7,^1.7.3`
- alice `~1.0`

## 0.3.0 / 2012-11-04

### Added

- faker `~1.1`
- phpmd ~1.4

## 0.2.0 / 2012-10-28

### Fixed

- Install would fail on `0.1.x-dev` after mockery was moved before phpspec in
  `composer.json`.
- Unable to install package on PHP 5.2 (see [Removed](#Removed))
- No longer using `version` in `composer.json` and will rely on VCS (git) tags.

### Added

- behat `~2.4`
- mink `~1.4`
- behat/mink-extension `~1.0`
- behat/mink-goutte-driver `~1.0`
- behat/mink-browserkit-driver `~1.0`

### Removed

- PHP `^5.3` requirement as there is no need to specify it in a dev package
  explicitly.

## 0.1.1 / 2012-10-26

### Added

- mockery `~0.7`
- phpspec `~1.4`

### Changed

- Added more information in README.md regarding package information.
- Updated Package description and keywords.

## 0.1.0 / 2012-10-21

### Added

- PHP `^5.3`
- PHPUnit `~3.7`
- vfsStream `~1.1`

[0]: https://packagist.org/packages/ek9/common-dev

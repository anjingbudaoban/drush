Drush's test suite is based on [PHPUnit](http://www.phpunit.de). In order to maintain
high quality, our tests are run on every push by [Travis](https://travis-ci.org/drush-ops/drush)

Usage
--------
1. Review the configuration settings in tests/phpunit.xml.dist. If customization is needed, copy to phpunit.xml and edit away.
1. Run unit tests: `unish.sh` or `cd tests && ..\vendor\phpunit`

Advanced usage
---------
- Run only tests matching a regex: `unish.sh --filter=testVersionString`
- Skip slow tests (usually those with network usage): `unish.sh --exclude-group slow`
- XML results: `unish.sh --filter=testVersionString --log-junit results.xml`
- Use an alternate version of Drupal: `UNISH_DRUPAL_MAJOR_VERSION=8 unish.sh ...`

Reuse by Drush Commandfiles
-----------
Drush commandfiles are encouraged to ship with PHPUnit test cases that
extend UnitUnishTestCase and CommandUnishTestCase. In order to run
the tests, you have to point to the [bootstrap.inc](tests/bootstrap.inc) file
such as `phpunit --bootstrap=/path/to/drush/tests/bootstrap.inc`.
The devel project does exactly this -
http://drupalcode.org/project/devel.git/blob/refs/heads/8.x-1.x:/drush/develDrushTest.php

Cache
-----------
In order to speed up test runs, Unish (the Drush testing class) caches built Drupal sites
and restores them as requested by tests. Once in while, you might need to clear this cache
by deleting the <tmp>/drush-cache directory.

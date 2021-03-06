# PHPUnit migration tool

Migrate project to the newest version of PHPUnit.

**[Work In Progress] Use it on the own risk :)**

## How to use the tool?

Clone the project:
```console
$ git clone https://github.com/webimpress/phpunit-migration.git
```

Go into the directory and install dependencies:
```console
$ cd phpunit-migration
$ composer install
```

To update your project to the newest version of PHPUnit go to your project directory and run:
```console
$ ../path/to/phpunit-migration/bin/phpunit-migration migrate
```

## What the tool is changing?

1. compose dependencies to the latest PHPUnit versions,
2. `\PHPUnit_Framework_TestCase` to namespaced `\PHPUnit\Framework\TestCase`,
3. `setExpectedException` to `expectException*`,
4. `getMock` to `getMockBuilder` with other required function calls,
5. `setUp` and `tearDown` to `protected` and correct case (`setup` => `setUp` etc.),
6.  FQCN in `@cover` tag (i.e. `@covers MyClass` to `@covers \MyClass`).
7. `$this->assert` to `self::assert`,

## What the tool is NOT doing?

1. changing `PHPUnit_Framework_Error_*` classes
2. probably other things I don't remember now ;-)

> ### Note
>
> Please remember it is developer tool and it should be used
> only as a helper to migrate your tests to newer version
> of PHPUnit.
> Always after migration run all your test to verify if applied
> changes are right and your tests are still working!

# Rose 

Rose is a fake data filling to any target(Redis, MySQL)

## Install

```php
composer require netroby/rose
```

## Use

Create file named runRose.php

```php
<?php

$rose = new \Com\Netroby\Rose();
$rose->setGenerator(new \Com\Netroby\Rose\Generator\MySQL([
    [
        'database_name' => 'test',
        'data' => [
            'table_a' => [
                'loop' => 100, //Insert 100 row
                'define' => [
                    'id' => \Com\Netroby\Rose\Utils::Increment(1),
                    'name' => array_rand(['david', 'smith', 'jose']),
                    'age' => rand(12, 65),
                    'create_time' => \Com\Netroby\Rose\Utils:DateIncrement('Ymd', 'now') //First arg controll the date format, second fill a base timestamp
                ]
            ],
            'table_b' => [
                'loop' => 50, //Insert 100 row
                'define' => [
                    'id' => \Com\Netroby\Rose\Utils::Increment(1),
                    'book_title' => array_rand(['david', 'smith', 'jose']),
                    'isbn_number' => rand(12, 65),
                    'create_time' => \Com\Netroby\Rose\Utils:DateIncrement('Ymd', 'now') //First arg controll the date format, second fill a base timestamp
                ]
            ],
        ]
    ]
]))->writeTo(new \Com\Netroby\Rose\Writter\MySQL([
    'host' => '127.0.0.1',
    'port' => '3306',
    'user' => 'root',
    'password' => 'sdafadsf'
]));

```

Then you can run with ```php runRose.php```

You will see 
# gnxb.db.php
PHP MySQL Database Manipulation Library (0.3.0-alpha)

"Based on PHP PDO Class"

To make using of MySQL with PHP more easier instead of straight writing MySQL Query Code include with **Auto-Prepared Statement** feature. I have provided essential functions which can manipulate data in any table.

## Requirement
- PHP 5.4 or better
- Apache with PHP and MySQL
- MySQL with PDO enable

I have initialized project with the [guide line](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04) and it works properly.

## Getting Started
I used `namespace` to prevent duplicating class name in same project. So I give you a solution to use my `gnxb.db.php` project, please see some code below.

```php
<?php

include "/path/to/gnxb.db.php";

// DB Definition goes here
class db extends \gnxb\db {}
db::connect("mysql:host=127.0.0.1;dbname=example", "root", "password");
```

I haven't tested on others DB yet and not available to [composer](https://getcomposer.org/).

## Manipulating Data
Next is how to manipulate data in table.

### SELECT
```php
<?php

// Select all data
db::prepare("SELECT * FROM user");
$data = db::fetch();
// return with 2-dimension array

// Select data with WHERE clause
db::prepare("SELECT username 'name' FROM user WHERE id=:id");
$data = db::fetch(["id" => 1]);
// always return with 2-dimension array
```

### UPDATE
```php
<?php

db::update("user", ["password" => "1234"], ["id" => 1]);
// Return Boolean
```

### INSERT
```php
<?php

db::insert("user", ["username" => "john", "password" => "1234"]);
// Return Boolean
```

### DELETE
```php
<?php

db::delete("user", ["id" => 1]);
// Return Boolean
```

### Last Inserted ID
```php
<?php

db::insert_id();
// Return String Number
```

### Manual Query
```php
<?php

db::prepare("YOUR MYSQL QUERY");
db::execute();
// Return Boolean
```


## What's next
- [ ] Others essential function
- [ ] Makes **Manual Query** to return others data types
- [ ] Schema Manipulation
- [ ] PHP Version Compatibility
- [ ] Web Server Compatibility


## Authors
Apiwith Potisuk [(po.apiwith@gmail.com)](po.apiwith@gmail.com)

GNXB, 2016 All Right Reserved.

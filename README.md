# Swagger-php
Generate interactive [OpenAPI](https://www.openapis.org) documentation for your RESTful API using [doctrine annotations](http://doctrine-common.readthedocs.org/en/latest/reference/annotations.html).

## Features

 - Compatible with the OpenAPI 3.0 specification.
 - Exceptional error reporting (with hints, context)
 - Extracts information from code & existing phpdoc annotations.
 - Command-line interface available.
 
## Installation (with [Composer](https://getcomposer.org))
```sh
composer require zircote/swagger-php
```
For cli usage from anywhere install swagger-php globally and make sure to place the `~/.composer/vendor/bin` directory in your PATH so the `swagger` executable can be located by your system.

```sh
composer global require zircote/swagger-php
```

## Usage

Add annotations to your php files.
```php
/**
 * @OAS\Info(title="My First API", version="0.1")
 */

/**
 * @OAS\Get(
 *     path="/api/resource.json",
 *     @OAS\Response(response="200", description="An example resource")
 * )
 */
```
See the [Getting started guide](docs/Getting-started.md) and [Examples directory](Examples/) for more examples.

### Usage from php

Generate always-up-to-date documentation.

```php
<?php
require("vendor/autoload.php");
$openapi = \Swagger\scan('/path/to/project');
header('Content-Type: application/json');
echo $openapi;
```
### Usage from the Command Line Interface

Generate the swagger documentation to a static json file.

```sh
./vendor/bin/swagger --help
```
### Usage from the Deserializer

Generate the OpenApi annotation object from a json string, which makes it easier to manipulate objects programmatically.

```php
<?php

use Swagger\Serializer;

$serializer = new Serializer();
$openapi = $serializer->deserialize($jsonString, 'Swagger\Annotations\OpenApi');
echo $openapi;
```

## More on OpenAPI

  * https://www.openapis.org
  * https://github.com/swagger-api/swagger-spec/
  * http://bfanger.github.io/swagger-explained/
  * [Related projects](docs/Related-projects.md)
  * https://www.marcoraddatz.com/en/2015/07/21/integrate-swagger-into-laravel/

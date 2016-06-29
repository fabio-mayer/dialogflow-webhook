Api.ai PHP sdk
==============

This is an unofficial php sdk for [Api.ai][1] and it's still in progress...

```
Api.ai: Build brand-unique, natural language interactions for bots, applications and devices.
```

## Install:

Via composer:

```
$ composer require iboldurev/api-ai-php
```

## Usage:

Using the low level `Client`:

```php
require_once __DIR__.'/vendor/autoload.php';

use ApiAi\Client;

try {
    $client = new Client('access_token');

    $query = $client->get('query', [
        'query' => 'Hello',
    ]);

    $response = json_decode((string) $query->getBody(), true);
} catch (\Exception $error) {
    echo $error->getMessage();
}
```

## Usage:   

Using the low level `Query`:

```php
require_once __DIR__.'/vendor/autoload.php';

use ApiAi\Client;
use ApiAi\Model\Query;
use ApiAi\Method\QueryApi;

try {
    $client = new Client('access_token');
    $queryApi = new QueryApi($client);

    $meaning = $queryApi->extractMeaning('Hello', [
        'sessionId' => '1234567890',
        'lang' => 'en',
    ]);
    $response = new Query($meaning);
} catch (\Exception $error) {
    echo $error->getMessage();
}
```

Some examples are describe in the [iboldurev/api-ai-php-example][2] repository.

[1]: https://api.ai
[2]: https://github.com/iboldurev/api-ai-php-example

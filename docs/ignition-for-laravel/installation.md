---
title: Installation
---

To install Ignition in your Laravel application, install it as a dependency via composer:

```txt
composer require facade/ignition
```

In Laravel 5.5, 5.6, 5.7 and older versions of 5.8 you will also need to modify your `app/Exceptions/Handler.php` file to load Ignition instead of the default Whoops page.

Add this method to your `Handler.php` file:

```php
protected function whoopsHandler()
{
    try {
        return app(\Whoops\Handler\HandlerInterface::class);
    } catch (\Illuminate\Contracts\Container\BindingResolutionException $e) {
        return (new \Illuminate\Foundation\Exceptions\WhoopsHandler)->forDebug();
    }
}
```

The configuration files can be published with:

```txt
php artisan vendor:publish --provider="Facade\Ignition\IgnitionServiceProvider" --tag="config"
```

This will publish two files: `config/ignition.php` and `config/flare.php`.

## Sending errors to Flare

If you want to send errors to Flare, you must specify a valid API key in the `key` variable of the config file or as your `FLARE_KEY` environment variable. You can get an API key when [creating a new project](/docs/general/projects).

The package uses Laravel's logging system to send errors. You must configure your log stack to use the `flare` channel.

Here's an example where the `flare` channel has been added.

```php
// in config/logging.php

return [
       'default' => env('LOG_CHANNEL', 'stack'),

       'channels' => [
           'stack' => [
               'driver' => 'stack',
               'channels' => ['daily', 'flare'],
               'ignore_exceptions' => false,
           ],
        ],
];
```

To test out if the package is configured correctly to send error you can use the test command:

```php
php artisan flare:test
```

If there's something wrong with your configuration, the message should guide you towards the solution.

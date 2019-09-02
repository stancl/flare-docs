---
title: Adding custom context
---

When you send an error to Flare, we already collect a lot of Laravel and user specific information for you and send it along with the exceptions that happened in your application.
But you can also add custom context to your application. This can be very useful if you want to provide key-value related information that furthermore helps you to debug a possible exception.

For example, your application could be in a multi-tenant environment and in addition to reporting the user, you also want to provide a key that quickly lets you identify which tenant was active when the exception occurs.

Flare allows you to set custom context items using the `Facade\FlareClient\Flare` class like this:

```php
use Facade\Ignition\Facades\Flare;

Flare::context('Tenant', 'My-Tenant-Identifier');
```

This could for example be set automatically in a Laravel service provider or an event. So the next time an exception happens, this value will be sent along to Flare and you can find it on the "Context" tab.

## Grouping multiple context items

Sometimes you may want to group your context items by a key that you provide to have an easier visual differentiation when you look at your custom context items.

The Flare client allows you to also provide your own custom context groups like this:

```php
use Facade\Ignition\Facades\Flare;

Flare::group('Custom information', [
    'key' => 'value',
    'another key' => 'another value',
]);
```

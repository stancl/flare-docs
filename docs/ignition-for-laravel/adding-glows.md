---
title: Adding glows
---

In addition to [custom context items](/docs/ignition-for-laravel/adding-custom-context), you can also add "Glows" to your application.
Glows allow you to add little pieces of information, that can later be found in a chronological order in the "Debug" tab of your application.

You can think of glows as breadcrumbs that can help you track down which parts of your code an exception went through.

To add a glow to your application, you can use the `Facade\FlareClient\Flare` class like this:

```php
use Facade\Ignition\Facades\Flare;
use Facade\FlareClient\Enums\MessageLevels;

Flare::glow('This is a message from glow!', MessageLevels::DEBUG, func_get_args());
```

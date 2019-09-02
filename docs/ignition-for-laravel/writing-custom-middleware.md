---
title: Writing custom middleware
---

Before Flare receives the data that was collected from your local exception, we give you the ability to call custom middleware methods.
These methods retrieve the report that should be sent to Flare and allow you to add custom information to that report.

Just like with the Flare client itself, you can [add custom context information](/docs/ignition-for-laravel/adding-custom-context) to your report as well. This allows you to structure your code so that you have all context related changes in one place.
 
You can register a custom middleware by using the `registerMiddleware` method on the `Facade\FlareClient\Flare` class, like this:

```php
use Facade\FlareClient\Report;
use Facade\Ignition\Facades\Flare;

Flare::registerMiddleware(function (Report $report, $next) {
    // Add custom information to the report
    $report->context('key', 'value');

    return $next($report);
});
```

A middleware can either be a callable, as seen above, or a custom class that implements a `handle` method. This class can make use of dependency injection in its constructor:

Here is an example:

```php
use Facade\Ignition\Facades\Flare;

Flare::registerMiddleware(FlareMiddleware::class);
``` 

And the middleware class might look like this:

```php
use Facade\FlareClient\Report;

class FlareMiddleware
{
    public function handle(Report $report, $next)
    {
        // Modify your report instance here.
        
        return $next($report);
    }
}
```
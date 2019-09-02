---
title: Adding solutions to your exceptions
---

Ignition ships with a lot of useful solutions out of the box. But you can also take advantage of Ignition's solutions yourself and add custom exceptions to your codebase.

## Adding text-based solutions

To add a solution text to your exception, let the exception implement the `Facade\IgnitionContracts\ProvidesSolution` interface.

> If you want to add solutions to an open source package, you can require the `facade/ignition-contracts` composer package. This will only provide you with the required interfaces, without actually requiring Ignition itself.

This interface requires you to implement one method, which is going to return the `Solution` that users will see when the exception gets thrown.

The `getSolution` method expects you to return a class that implements the `Solution` interface. This solution will then be shown to the user.

Here is a basic example of the exception class:

```php
use Facade\IgnitionContracts\ProvidesSolution;

class CustomException implements ProvidesSolution
{
    public function getSolution(): Solution
    {
        return new CustomSolution();
    }
}
```

And the corresponding solution class looks like this:

```php
use Facade\IgnitionContracts\Solution;

class CustomSolution implements Solution
{
    public function getSolutionTitle(): string
    {
        return 'The solution title goes here';
    }

    public function getSolutionDescription(): string
    {
        return 'This is a longer description of the solution that you want to show.';
    }

    public function getDocumentationLinks(): array
    {
        return [
            'Laravel documentation' => 'https://laravel.com/docs/master/some-page',
        ];
    }
}
```

## Adding runnable solutions

In addition to text-based solutions, you can also create solutions that provide a button in the Ignition UI. When pressing that button, you can perform additional actions, such as calling Artisan commands.

To make one of your solutions runnable, let it implement the `RunnableSolution` interface. This interface requires you to implement four additional methods.

Let's take a look at an example solution:

```php
use Facade\IgnitionContracts\Solution;
use Facade\IgnitionContracts\RunnableSolution;

class CustomSolution implements Solution, RunnableSolution
{
    // ...

    public function getSolutionActionDescription(): string
    {
        return 'This is a description that will be shown above the run button';
    }

    public function getRunButtonText(): string
    {
        return 'Run Button Title';
    }

    public function run(array $parameters = [])
    {
        // Perform your runnable solution code.
    }

    public function getRunParameters(): array
    {
        // Provide additional parameters that will get passed to your 'run' method.
        return [
            'parameter' => 'value',
        ];
    }
}
```

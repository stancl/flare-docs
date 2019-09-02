---
title: Using solution providers
---

Instead of adding solutions to exceptions directly, you can also create a solution provider.
While exceptions that return a solution, provide the solution directly to Ignition, a solution provider allows you to figure out if an exception can be solved.

For example, you could create a custom "Stack Overflow solution provider", that will look up if a solution can be found for a given throwable.

Solution providers can be added by third party packages or within your own application.
  
A solution provider is any class that implements the `\Facade\IgnitionContracts\HasSolutionsForThrowable` interface.

This is how the interface looks like: 

```php
interface HasSolutionsForThrowable
{
    public function canSolve(Throwable $throwable): bool;

    /** \Facade\IgnitionContracts\Solution[] */
    public function getSolutions(Throwable $throwable): array;
}
```
 
When an error occurs in your app, the class will receive the `Throwable` in the `canSolve` method. In that method you can decide if your solution provider is applicable to the `Throwable` passed. If you return `true`, `getSolutions` will get called. 
 
Here is an example from [the Ignition package](/docs/flare-for-laravel/introduction) codebase:
 
```php
use Throwable;
use RuntimeException;
use Facade\IgnitionContracts\Solution;
use Facade\Ignition\Solutions\GenerateAppKeySolution;
use Facade\IgnitionContracts\HasSolutionsForThrowable;

class MissingAppKeySolutionProvider implements HasSolutionsForThrowable
{
    public function canSolve(Throwable $throwable): bool
    {
        if (! $throwable instanceof RuntimeException) {
            return false;
        }

        return $throwable->getMessage() === 'No application encryption key has been specified.';
    }

    public function getSolutions(Throwable $throwable): array
    {
        return [
            new GenerateAppKeySolution()
        ];
    }
}
```

Next, you must register your solution provider. This can typically be done in a service provider.

```php
namespace App\Providers;

use App\Solutions\GenerateAppKeySolution;
use Facade\IgnitionContracts\SolutionProviderRepository;
use Illuminate\Support\ServiceProvider;

class YourServiceProvider extends ServiceProvider
{
    /**
     * Register services.
     *
     * @return void
     */
    public function register(SolutionProviderRepository $solutionProviderRepository)
    {
        $solutionProviderRepository->registerSolutionProvider(GenerateAppKeySolution::class);

        // alternatively you can register multiple solution providers at once
        $solutionProviderRepository->registerSolutionProviders([
            MySolution::class,
            AnotherSolution::class,
        ]);
    }
}
```

The `getSolutions` method of your solution provider should return an array of `Facade\IgnitionContracts\Solution` implementations. Here's a possible implementation of `GenerateAppKeySolution`.

```php
namespace App\Solutions;

use Illuminate\Support\Facades\Artisan;
use Facade\IgnitionContracts\RunnableSolution;

class GenerateAppKeySolution implements RunnableSolution
{
    public function getSolutionTitle(): string
    {
        return 'Missing App Key';
    }

    public function getDocumentationLinks(): array
    {
        return [
            'Laravel' => 'https://laravel.com/docs/master/installation#configuration',
        ];
    }

    public function getSolutionActionDescription(): string
    {
        return 'Generate your application encryption key using `php artisan key:generate`.';
    }

    public function getRunButtonText(): string
    {
        return 'Generate App Key';
    }

    public function getSolutionDescription(): string
    {
        return '';
    }

    public function run(array $parameters = [])
    {
        Artisan::call('key:generate');
    }

    public function getRunParameters(): array
    {
        return [];
    }

}
```

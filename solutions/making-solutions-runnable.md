---
title: Making solutions runnable
---

Ignition can also help and run custom solutions to try and automatically fix an error. 
Here's how a runnable solution looks like.

![Screenshot of error with runnable solution](/images/docs/error-with-runnable-solution.png)

To mark your solution as "runnable", let it implement the `Facade\IgnitionContracts\RunnableSolution` interface. Here is how that interface looks like:

```php
namespace Facade\IgnitionContracts;

interface RunnableSolution extends Solution
{
    public function getSolutionActionDescription(): string;

    public function getRunButtonText(): string;

    public function run(array $parameters = []);

    public function getRunParameters(): array;
}
```

To return that solution in one of your exceptions, let your exception implement the `Facade\IgnitionContracts\ProvidesSolution` interface.

```php
class MyException extends Exception implements ProvidesSolutions
{
    public function getSolutions(): array
    {
        return [new MyRunnableSolution()];    
    }
}
```

And  this is an example of a runnable solution class. 

```php
namespace App\Solutions;

use Facade\IgnitionContracts\RunnableSolution;

class MyRunnableSolution implements RunnableSolution
{
    public function getSolutionTitle(): string
        {
            return 'My solution title';
        }
    
        public function getSolutionDescription(): string
        {
            return 'My solution description';
        }
    
        public function getDocumentationLinks(): array
        {
            return [
                'My docs' => 'https://flareapp.io/docs',
            ];
        }
    
        public function getSolutionActionDescription(): string
        {
            return 'We can try to solve this exception by running a little code';
        }
    
        public function getRunButtonText(): string
        {
            return 'Press me to run the solution';
        }
    
        public function run(array $parameters = [])
        {
            // code that tries to fix the problem
        }
    
        /*
         *  The array you return here will be passed to the `run` function.
         *
         *  Make sure everything you return here is serializable.
         *
         */
        public function getRunParameters(): array
        {   
            return [];
        }
}
```

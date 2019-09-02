---
title: Adding solutions
---

In addition to simply displaying your exception, Ignition can also display a text-based solution along with your exception message.

![Screenshot of error with non runnable solution](/images/docs/error-with-non-runnable-solution.png)

To add a solution text to your exception, let the exception implement the `Facade\IgnitionContracts\ProvidesSolution` interface.

> If you want to add solutions to an open source package, you can require the `facade/ignition-contracts` composer package. This will only provide you with the required interfaces, without actually requiring Ignition itself.

This is what that interface looks like:

```
namespace Facade\IgnitionContracts;

interface ProvidesSolutions
{
    public function getSolution(): Solution;
}
```

The `getSolution` method expects you to return an implementation of the `Solution` interface. You can either create a custom class that implements that interface or make use of the built-in `BaseSolution` class to easily return a textual solution.

Here's an example of an implementation in a custom exception class:

```php
namespace App\Http\App;

use Exception;
use Facade\IgnitionContracts\Solution;
use Facade\IgnitionContracts\BaseSolution;
use Facade\IgnitionContracts\ProvidesSolution;

class MyException extends Exception implements ProvidesSolution
{
    /** @return \Facade\IgnitionContracts\Solution[] */
    public function getSolution(): Solution
    {
        return BaseSolution::create('My solution title')
            ->setSolutionDescription('My solution description')
            ->setDocumentationLinks([
                'My docs' => 'https://flareapp.io/docs',
            ]);
    }
}
```

This is how the exception would be displayed if you were to throw it.

![Screenshot of exception with solution in Ignition](/images/docs/custom-exception-ignition.png)

If you're sending your exception to Flare, the solution will be sent along as well. Here's how the exception above would look like in Flare.

![Screenshot of exception with solution in Flare](/images/docs/custom-exception-flare.png)

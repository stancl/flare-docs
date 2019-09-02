---
title: Adding custom tabs
---

## Anatomy of a custom tab

A custom tab in Ignition has two main components:

1. A custom `Tab` class that tells Ignition which assets it needs to load.
2. A Vue component that gets rendered in your custom tab.

Here is how a basic Tab class could look like:

```php
use Facade\Ignition\Tabs\Tab;

class CustomTab extends Tab
{
    public function registerAssets()
    {
        $this->script('my-custom-tab', __DIR__.'/../dist/js/tab.js');
    }
}
```

The `CustomTab` class is responsible for telling Ignition, where the assets for its Vue component can be found.

Let's take a look at that JavaScript file next:

```javascript
Ignition.registerTab(Vue => {
    Vue.component('custom-tab', require('./components/tabs/CustomTab').default);
});
```

Inside the Javascript file, you can use the `Ignition.registerTab` method to add a callable that will be executed when custom tabs should get injected. In there you will receive the `Vue` instance where you can add your custom tab component.

And the `CustomTab` component looks like this:

```javascript
<template>
    <div class="tab-content">
        <div class="layout-col">
            <h2>Custom Tab</h2>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['meta'],
    }
</script>
```

Within this component you have complete freedom to do whatever you want to do.

## Registering your custom tab

To register your own custom tab with Ignition, you will have to use the `tab` method on the `Facade\Ignition\Ignition` class. This would typically be done in the `boot` method of one of your service providers.

```php
public function boot()
{
    Ignition::tab(new CustomTab);
}
```

## Using the skeleton

To make the development of custom tabs easier, we created a custom [Ignition skeleton](https://github.com/facade/ignition-skeleton) repository which you can use as your starting point for your next Ignition package.

To use it, just clone the repository and follow the instructions in the README file that we provide.

The skeleton project comes with Laravel mix installed to compile all your assets into a single file and it allows you to register custom routes to use within your tab.

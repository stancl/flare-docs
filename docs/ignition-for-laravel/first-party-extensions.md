---
title: First party extensions
---

We've created a couple of packages that add functionality to Ignition. If you want to build your own custom Ignition extension, feel free to take these as a source of inspiration.
Head over to the [custom tab documentation](/docs/ignition-for-laravel/adding-custom-tabs) to learn how you can create your own custom tab. 

## Ignition Tinker Tab

This package allows you to use [Artisan tinker](https://laravel.com/docs/master/artisan#tinker) right on the error page. The package is a wrapper around [spatie/laravel-web-tinker](https://github.com/spatie/laravel-web-tinker).

![Screenshot of tinker tab in Ignition](/images/docs/tinker-tab.png)

You can install the package using this command.

```txt
composer require facade/ignition-tinker-tab --dev
```

[GitHub](https://github.com/facade/ignition-tinker-tab)

## Ignition Code Editor

This package replaces the existing "Stack Trace" tab and adds an online code editor as the code snippet view. You can edit all application frames and by pressing CMD-S/CTRL-S immediately save the changes you made.

![Screenshot of editor tab in](/images/docs/ignition-editor.png)

You can install the package using this command.

```txt
composer require facade/ignition-code-editor --dev
```

[GitHub](https://github.com/facade/ignition-code-editor)

## Ignition Self Diagnosis

This package adds a new tab to Ignition, that shows you common self-diagnosis checks and their results

![Screenshot of self diagnosis tab](/images/docs/ignition-self-diagnosis.png)

You can install the package using this command.

```txt
composer require facade/ignition-self-diagnosis --dev
```

[GitHub](https://github.com/facade/ignition-self-diagnosis)

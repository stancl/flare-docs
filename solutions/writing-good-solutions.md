---
title: Writing good solutions
---

When writing custom solutions, make sure that the text that your solution provides is helpful to the user reading it.

For all solutions that are built into Ignition, we make use of a solution "style guide".
You may want to use them in your solutions too.

## Solution title

The solution title should be a full sentence with the "problem" that this solution is trying to fix upfront. It should not contain any punctuation and no caps on all words.

### Example:

<i class="fas fa-times-circle text-red-400"></i> App Key Missing

<i class="fas fa-check-circle text-green-500"></i> Your app key is missing

## Solution description

Avoid questions in your solution descriptions. If you are in doubt that your solutions are going to fix the problem 100% of the time, use verbs like "seems", "might", "could", etc.
Optionally state the problem in full sentences and give clear instructions on what the user can do to solve the problem.

You can use markdown inside your solution description to highlight inline-code snippets to point to files or classes.

### Example:

<i class="fas fa-times-circle text-red-400"></i> Is your application key missing? Try adding it to your environment variables.

<i class="fas fa-check-circle text-green-500"></i> Generate your application encryption key using `php artisan key:generate`.

## Runnable solutions

If there is a chance to let you automatically fix the problem for the user, provide a runnable solution. This way, developers can quickly try and fix the problem with the press of a button.

Make sure also to provide the information on how to manually perform the fix, in case something goes wrong.

The button of a runnable solution should point out what happens when the button gets clicked.

### Example:

<i class="fas fa-times-circle text-red-400"></i> Fix the problem

<i class="fas fa-check-circle text-green-500"></i> Run missing migrations

## Solution links

In addition to a solution title and description, you can also point the user to various links where the user can read more about how the issue can be fixed or avoided. When linking to external resources, try to be as specific as possible, where the link will take the user.

### Example:

<i class="fas fa-times-circle text-red-400"></i> Laracasts

<i class="fas fa-check-circle text-green-500"></i> Watch "Laravel 5 Fundamentals - Migrations" on Laracasts

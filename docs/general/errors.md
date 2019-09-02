---
title: Working with errors
---

Whenever an error gets reported by your application, we show it on the projects page. If you want to know more about the error, click on it to see [more details about the last occurrence](/docs/general/error-occurrences).

![Screenshot of project screen showing list of errors](/images/docs/error-list.png)

## Filtering errors

On the list of error of a project, you can search for errors. By default, we only show unresolved and unsnoozed errors. To search on error message, exception name, or url just start typing.

![Screenshot of searching errors on project screen](/images/docs/search-errors.png)

To search on a class only prefix your query with `class:`

![Screenshot of searching errors on class on project screen](/images/docs/search-errors-on-class.png)

You can use these prefixes to search on a specific attribute of an error. Additionally you can use `is:*` filters to query by error status.

-   `class`
-   `message`
-   `file`
-   `first_seen_at`
-   `last_seen_at`
-   `resolved_at`

-   `is:resolved`
-   `is:unresolved`
-   `is:snoozed`
-   `is:unsnoozed`
-   `is:recent`

## Resolving errors

You can resolve an error to inform anybody working on a project that the problem has been fixed.

![Screenshot of resolved error](/images/docs/resolved-error.png)

## Snoozing errors

If you don't want to get notified about new occurrences coming in you can snooze the error.

![Screenshot of snoozing options](/images/docs/snoozing-options.png)

## Deleting errors

Should any of the occurrences of your error contain sensitive data, you can delete the error by clicking "Delete" on the top left corner.

![Screenshot of error deletion confirmation](/images/docs/deleting-error.png)

After confirming the deletion, we will delete the error and all of its occurrences from our systems. This action cannot be reversed.

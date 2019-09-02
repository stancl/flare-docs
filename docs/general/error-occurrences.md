---
title: Working with error occurrences
---

After you've clicked on an error in a project, you'll see more details of  the latest occurrence.

![Screenshot of an error occurrence](/images/docs/error-occurence.png)

## Seeing all occurrences

To see all error occurrences, click "All"

![Screenshot of a list of error occurrences](/images/docs/all-occurrences.png)

## Searching occurrences

Using the search bar above the occurrences, you can hunt down specific occurrences. To search on error message, exception name, or URL start typing.

![Screenshot of a list of searching occurrences](/images/docs/searching-occurrences.png)

You can use these prefixes to search on a specific attribute of an occurrence:

- `exception_class`
- `exception_message`
- `file`
- `first_seen_at`
- `last_seen_at`
- `resolved_at`

## Grouping occurrences

You can use `group:` prefix to group the occurrences. Here's an example of grouping on URL

![Screenshot of a list of grouping occurrences](/images/docs/grouping-occurrences.png)

You can use these groupings:

- `group:seen_at_url`
- `group:exception_message`
- `group:exception_class`

You can also group on anything present in the context of occurrence. Here's how you can group on user id: `group:context.user.id`
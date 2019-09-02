---
title: Controlling collected data
---

When you have set up Flare to track your exceptions, you have full control over what data should get collected and sent to Flare.

There are various options that control what information is sent to Flare. These options are inside the `reporting` key in your `flare` configuration file.

## Anonymizing IPs

By default, Flare does not collect and send information about the IP address of your application users. If you want to collect this information, you can set the `anonymize_ips` option to `false`.

## Git information

By default, Flare collects the current commit hash, the commit message as well as the repository URL so that you can easily link an exception with the commit hash that was checked out on your deployed application. If you wish to disable this information, set the `collect_git_information` key to `false`.

## SQL Queries

Flare automatically collects all of your executed queries that happened before the exception occurred. This does not include any bindings within your queries. If you do not want to collect SQL query information at all, set the `report_queries` key to `false`.

In addition to queries, Flare can also collect the values of the query bindings for you. This can be very useful to see the actual values of the data within your queries. To disable this, set the `report_query_bindings` key to `false`.

## View data

When Flare detects an exception that occurs in one of your Blade views, Flare can collect and send the view data along with the exception.
To disable this, set the `report_view_data` key to `false`.

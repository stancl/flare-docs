---
title: Configuring notifications
---

Flare has powerful options to notify you when something goes wrong in your app. We provide notifications via email, Slack, SMS (through Nexmo) and webhooks.

## Notification events

For each of these channels, you can choose which notifications should be sent through them. These are the events we can notify you of:

-   when an error occurs for the very first time
-   when an error occurs for the 1th, 10th, 100th, 1000th, 2000th, ... time
-   every time an error occurs
-   when an error that was marked as resolved, occurs again

We can also notify you of certain activity on your error occurrences:

-   when an error is marked as [resolved](/docs/general/errors#resolving-errors)
-   when an error is marked as unresolved
-   when an error is [snoozed](/docs/general/errors#snoozing-errors)
-   when an error is unsnoozed

![Screenshot of notification settings dialog](/images/docs/notification-settings-dialog.png)

## Configuring notifications

You can configure the notifications on three levels: account, team, and project. This simple, though powerful, system gives you fine-grained control over who should be notified when any over events described above occur.

## On the account level

You can configure the notifications on the account level in on the ["My notifications"](/account/notifications) screen in the account settings.

![Screenshot of my notifications screen](/images/docs/my-notifications.png)

Only you can configure these options. You should use these options to send a notification to destinations only accessible by you. If you want to configure a channel that is used by your entire team (a group email, a shared channel on Slack, ...) it's better to use a [notifications on the team level](#on-the-team-level).

After you've created your account, we've automatically prepopulated the email channel with some sensible defaults.

## On the team level

For each team, you can configure the notifications on the team level in the "Team notifications" screen setting of your team. Only the owner and admin of the team can view and edit these settings.

![Screenshot of team notifications screen](/images/docs/team-notifications.png)

## On the project level

You can also configure notification at the project level. You can configure these options on the "Notifications" screen of the project settings. For each project, you may decide if you account-level notifications settings should be used. Owners and admins of the team a the project belongs to can decide whether the team level notifications settings should be used. If you don't want to use the default account or team notifications settings turn off the "Use my default switch".

![Screenshot of project notifications screen with "use my defaults" hightlighted](/images/docs/use-my-defaults-notifications.png)

You can also configure additional notification settings for a project. Just turn on the "Custom for <project name>" switch for any of the notification channels.

![Screenshot of custom project notifications](/images/docs/custom-project-notifications.png)

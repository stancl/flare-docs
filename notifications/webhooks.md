---
title: Webhooks
---

Flare can notify your application of events using webhooks. Each hook is cryptographically signed, so the request cannot be tampered with. If you receive a webhook, you can validate it to make sure it comes from us.

## Configuring webhooks

You can configure webhooks on the [account](/docs/configuring-notifications#on-the-account-level), [team](/docs/configuring-notifications#on-the-team-level) and [project](/docs/configuring-notifications#on-the-project-level) level. 

![Screenshot of webhook settings](/images/docs/webhook-settings.png)

## Accepting webhooks in your application

Every configured event will be sent as `POST` request to the webhook URL you configured. All data related to the event that just took place will be inside the `POST` payload.

### Verify the signature

All the webhooks we send will be signed. One of the components of the signature is the secret specified at the webhooks notifications screen. 

Our signing method is simple but efficient. For every webhook we call, we pass an additional header called  `Signature` that contains the hash of the payload. This is how we calculate the hash:

```php
$contentsOfSignatureHeader = hash_hmac('sha256', $payload, $secret);
```

The `$payload` is the body of the POST request, which will be a JSON representation of the event. The `$secret is the one you can find the notifications settings. The `hash_hmac()` function is a [PHP function](https://www.php.net/hash_hmac) that generates a keyed hash value using the HMAC method.

To verify if the webhook request has not been tampered with and was initiated by Flare you should calculate the hash at your end and check if your calculated hash is equal to the contents of the `Signature` header of the incoming webhook request.

### Webhook retries

If we receive an `HTTP/200` from your webhook URL within 3 seconds, we consider the webhook successful. If your application returns anything else, including 301 or 302 redirects, we mark the webhook as failed and will resend the same payload again.

We will try to send the webhook up to 3 times. After the first attempt, we'll wait at least 10 seconds before making the 2nd attempt. If the second attempt should fail, we'll wait at least 100 seconds before making the third and final attempt.

### Testing a webhook

After you've set up the webhook notification and prepared your app to receive them, you can send a test notification by clicking "Send test notification".

## Receiving webhooks in a Laravel app

If you want to receive a Laravel app to receive webhooks, you can take a head start by using [the laravel-webhook-server package](https://github.com/spatie/laravel-webhook-client). This package contains functionality to [validate signatures](https://github.com/spatie/laravel-webhook-client#verifying-the-signature-of-incoming-webhooks), storing and processing incoming webhook requests.

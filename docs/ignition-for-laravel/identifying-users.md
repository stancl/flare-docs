---
title: Identifying users
---

When reporting an error to Flare, we'll automatically send along the properties of the authenticated user. Behind the scenes, we'll call `toArray` on your `User` model. This will exclude all attributes that are marked as hidden in your model, so we're not sending along the password.

If you need more control over which user data you want to send to Flare, you can customize this by adding a `toFlare` method to your `User` model. If we detect that your model has a `toFlare` model we'll use the retuend array as the user information instead of `toArray`.

```php
class User extends Model {
    //

   public function toFlare(): array {
      // Only `id` will be sent to Flare.
      return [
         'id' => $this->id
      ];
   }
}
```

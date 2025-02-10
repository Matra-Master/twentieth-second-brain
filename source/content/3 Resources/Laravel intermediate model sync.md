---
created: 20220720-1653
tags:
  - Resources/laravel
---

# Laravel intermediate model sync
Laravel describes syncing an intermediate table with an array of IDs like so: 

    $user->roles()->sync([1, 2, 3]);

But the documentation wont say to you where the hell are the IDs from... Are they apples, candies?? I supposed they where a default auto incrementing and unique 'id' value, like the one in a record from a normal table. And therefore i added that column to a couple intermediate tables.
It turns out that that array is an array of ids from the second table in the relationship, a thing that makes **PERFECT SENSE** but the documentation doesn't tell you that.

This is a better example IMO

    $role_ids = [1, 2, 3];
    $user->roles()->sync($role_ids);

---
# References
[Laravel syncing asociations](https://laravel.com/docs/8.x/eloquent-relationships#syncing-associations)

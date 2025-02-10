---
created: 20221130-1736
tags:
  - Resources/mysql
---

# A series of operations on a DB that occur either all or none

If it's critical that a series of operations occur without beign cut in the middle by a power failure or something like that, you use a transaction.
I't ensures that all things in it where done correctly or it reverts and can try again.
Transactions can assure idempotency.

A Laravel Example

    use Illuminate\Support\Facades\DB;

    DB::transaction(function () {
        DB::update('update users set votes = 1');

        DB::delete('delete from posts');
    });


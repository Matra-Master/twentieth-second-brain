---
created: 20220804-1403
tags:
  - Resources/laravel
---

Tags: #Laravel

# Laravel Routing
Routes are elocuent, you can inject the names of models in the route definitions like `{user}` so that when you put an url that has the id of a user, Laravel will capture the model of that id and pass it as a parameter into the route's function. 

You can even return related models by adding parameters.
```
use App\Models\Post;
use App\Models\User;

Route::get('/users/{user}/posts/{post:slug}',
	function (User $user, Post $post)
		{
		    return $post;
		});
```

Order Payment relation to change a comment
``` Example
Route::put('/{order}/payments/{payment}',
	function (Request $request, Order $order, Payment $payment) {
		$payment->update(['comments' => $request['comment']]);
	}
);
```

---
Related Ideas: [[Laravel]]

# References
[Custom keys & Scoping](https://laravel.com/docs/8.x/routing#implicit-model-binding-scoping)

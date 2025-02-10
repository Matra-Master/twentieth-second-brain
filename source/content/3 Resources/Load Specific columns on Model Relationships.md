---
created: 20220705-1344
tags:
  - Resources/laravel
---

# Load Specific columns on Model Relationships
The important part is the usage of with and chosing not just the relationed model but also the columns you specifically want. Magic ✨

	$books = Book::with('author:id,name,book_id')->get();

### An example from Hierros Sanchez
	$order['services_iva'] = Order::where('id', $order->id)
      ->with('services:order_service.quantity')->get();

This will return the object with the pivot just because the Order Model has the withPivot set on it's relationship with Services. But either way it returns quantity as if it were a field on the Services object OwO

```
"services": [
	{
		"quantity": 4,
		"pivot": {
			"order_id": 2,
			"service_id": 2,
			"quantity": 4,
			"observations": ""
	}
]
```


---
# References
[Laravel Documentation](https://laravel.com/docs/8.x/eloquent-relationships#eager-loading-specific-columns)

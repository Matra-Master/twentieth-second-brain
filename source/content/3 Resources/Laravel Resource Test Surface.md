---
created: 20230621-1018
tags:
  - Resources/laravel
  - Resources/testing
---

How can I write tests reliably for a Laravel resource?
What is a Laravel Resource? Are all resources equal?

A resource for me is composed of main structures and some optional ones. Like so:

#### Model
* Has *Factory*
* *Fillable* fields
* What kind of *relations* will it have with other models?
* Has accessor *Attributes*?
* Has particular *methods*?

#### Controller
* Traits
* CRUD
  * Store
  * Index
  * Show
  * Update
  * Destroy

#### Routes
* Middlewares?
* CRUD
  * Store
  * Index
  * Show
  * Update
  * Destroy

#### DB Table 
They are kind of soft tested when you run migrations
* Migration 
* Columns
* Relationships
* Pivots?

#### Optionals:
  * Singular Resource
  * Collection Resource
  * Form request validations
  * Factory
  * Seeder

---

## Sources
[Eloquent Response Resources](https://laravel.com/docs/10.x/eloquent-resources#main-content)

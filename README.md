# Laravel Sanctum Auth Package

Laravel package for Laravel Sanctum user authentication feature

For information & usage about Laravel Sanctum, please refer to [Laravel Sanctum documentation](https://laravel.com/docs/7.x/sanctum).

## Get Started

Include the Sanctum Auth package by calling this composer command in project root:

> `composer require setiawanhu/sanctum-auth`

## Usage

We may publish the Sanctum Auth migration files using `vendor:publish` artisan command:

> `php artisan vendor:publish --provider="Hu\Auth\SanctumAuthServiceProvider"` 

This command will copy the user role's migration file to /database/migrations folder and will publishing the `laravel/sanctum` configuration and migration files.

Then, run Sanctum Auth artisan command by running:

> `php artisan sanctum-auth:controller [{type} --force]`

This command will generate the auth routing out of the box.

Note:

1. The `type` argument is optional with default value are `token`. The controller will be generated based on given argument value. Available types are `token` and `spa`. 

2. The `--force` option is optional. We may use it for ignoring existing controller.

Then, make `User` model to extend `AuthModel` class:

> `class User extends AuthModel`

## Using Roles

if the `User` has roles, we may use the `HasRole` trait to the `User` model:

> `use HasRole;`

Then, we add a new field to the users table:

> `$table->unsignedBigInteger('role_id')` 

Then, run the database migration command:

> `php artisan migrate` 

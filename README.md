# laravel-antispam

## How to use:
1) `composer require cleantalk/laravel-antispam`
2) Register the `cleantalk_antispam` middleware into your  Kernel.php
3) Add `CLEANTALK_ENABLED` and `CLEANTALK_API_KEY` to your .env or publish the config file
4) Include JS into your root blade template (into head block) `@include('cleantalk::cleantalk')`
5) Add the middleware to your routes which requires the anti-spam protection (usually form hanled route)

## Details:
1) Open the terminal in the root of your laravel application and run command to require anti-spam module: `composer require cleantalk/laravel-antispam`
2) Edit `config/app.php` file, add new service provider to the `providers` array: `cleantalk\antispam\CleantalkServiceProvider::class` ![Adding service provider](https://raw.githubusercontent.com/CleanTalk/laravel-antispam/master/documentation/screenshots/1.png)
3) Edit `app/Http/Kernel.php` file, add new middleware to the `$routeMiddleware` array: `'cleantalk_antispam' => \cleantalk\antispam\CleantalkValidate::class` ![Adding middleware](https://raw.githubusercontent.com/CleanTalk/laravel-antispam/master/documentation/screenshots/2.png)
4) Open the terminal in the root of your laravel application and run command to generate config file and javascript asset: `php artisan vendor:publish`
5) Edit newly added configuration file `config/cleantalk.php`, type your access key and change `enabled` key to `true` ![Changing configuration](https://raw.githubusercontent.com/CleanTalk/laravel-antispam/master/documentation/screenshots/3.png)
6) Include cleantalk blade template to your root blade template into <head> block: `@include('cleantalk::cleantalk')` ![Adding blade template](https://raw.githubusercontent.com/CleanTalk/laravel-antispam/master/documentation/screenshots/4.png)
7) So finally add the middleware to the required routes: `->middleware('cleantalk_antispam')` ![Using middleware](https://raw.githubusercontent.com/CleanTalk/laravel-antispam/master/documentation/screenshots/5.png)

Now you can test the protection on the route contains `cleantalk_antispam` middleware, just use s@cleantalk.org test email for email field.

## Requirements:

* CleanTalk account https://cleantalk.org/register?product=anti-spam

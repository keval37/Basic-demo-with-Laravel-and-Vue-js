

## About Laravel
Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:


## About Vue
Vue.js is a progressive, incrementally-adoptable JavaScript framework for building UI on the web.


## Vue js
Why use Laravel with Vue
Streamline the Development Process
This structure allows for one to be a full stack developer within a single project

## Single-Page Application Development
Both Vue js and Laravel support single page applications.This allows the application assets get loaded once, all that your application does as the user engages with it is request data which typically requires low bandwidth to fulfill.

## Building Optimal Complex Front-end Pages
With Vuejs a developer does not need to use jquery to manipulate blade templates.Vue allows for easier managment of DOM using a virtual Dom.

## Easy to Learn and Use
Both Laravel and Vue have a robust documentation that is easy to learn and integrate.

First ensure that Laravel is installed.
Here is link to install Laravel if you haven't installed yet.
[Laravel 8 Installation](https://laravel.com/docs/8.x/installation)

## Laravel + VueJS Demo

### Create a laravel project
``` composer create-project laravel/laravel lara-vue ```

### Scaffolding Vue js
Install laravel/ui package
``` composer require laravel/ui ```

##  Install the frontend scaffolding using the ui Artisan command
### Basic scaffolding
``` php artisan ui vue ```

### Generate login / registration scaffolding.
``` php artisan ui vue  --auth ```

Before compiling your CSS, install your project's frontend dependencies using the Node package manager (NPM):
```npm install```

Once the dependencies have been installed using `npm install`, you can compile your SASS files to plain CSS using Laravel Mix. The `npm run dev` command will process the instructions in your webpack.mix.js file. Typically, your compiled CSS will be placed in the `public/css` directory:
```npm run dev```

## Configure Blade
Add below code in welcome.blade.php

```
<!doctype html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- CSRF Token -->
    <meta name="csrf-token" content="{{ csrf_token() }}">
    <title>Laravel + Vue</title>
    <!-- Scripts -->
    <script src="{{ asset('js/app.js') }}" defer></script>
    <!-- Styles -->
    <link href="{{ asset('css/app.css') }}" rel="stylesheet">
</head>
<body>
    <div id="app">
        <main class="py-3">
            <h3>Laravel + Vue</h3>
            <router-view></router-view>
        </main>
    </div>
</body>
</html>
```

## Add Vue components
Add new vue.js file in resources/js/components called app.vue and add the following code.
```
<template>
    <div>
        {{message}}
    </div>
</template>
<script>
export default {
    data() {
        return {
            message: 'Hello World'
        }
    }
};
</script>
```
## Setup & InstallVue router
```
npm install vue-router --save
```

#### Create a routes folder and add a home.js file.Add the following code.
```
const home = () =>import ( '../components/app.vue')

export default [
    {
        path: '/home',
        component: home,
        name: 'home',
    },
]
```
Head over to the resources/js folder and create a file called routes.js and add the following code.
```
import Vue from 'vue'
import VueRouter from 'vue-router'
import home from './routes/home';

Vue.use(VueRouter);
export default new VueRouter({
    mode: 'history',
    scrollBehavior: (to, from, savedPosition) => ({ y: 0 }), 
    routes: [
        ...home,
    ],
});
```

## Add routes to app.js
Replace the code in your resources/js/app.js with the code below.
```
require('./bootstrap');
require('../sass/app.scss')
import Vue from 'vue'

window.Vue = require('vue');

// router
import router from './routes.js';
window.router = router;
window.Fire = new Vue();

const app = new Vue({
    el: '#app',
    router,
}).$mount('#app');
```

## Setup Laravel routes
Update Laravel routes in web.php
```
Route::get('/{any?}', [
    function () {
        return view('welcome');
    }
])->where('any', '.*');
```
## Compile components
```
npm run dev
```

## Run the application
```
php artisan serve
```

Yay! the demo is complete. :)

## Vue Router

Inside `welcome.blade.php`

```
<!doctype html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <meta name="csrf-token" content="{{ csrf_token() }}">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.min.css">
    <link href="https://fonts.googleapis.com/css?family=Marmelad&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="/css/spacing.css">
    <style>
    body {
        font-family: 'Marmelad', sans-serif;
    }

    </style>
    <title>Laravel Token Authorization</title>
</head>

<body>
    <div id="app">
        <router-view></router-view>
    </div>
    <script src="{{ url('js/app.js') }}"></script>
</body>

</html>

```

Inside `web.php`


```
Route::get('/{any}', function () {
    return view('welcome');
})->where('any', '.*');
```

Create `router.js` file inside `js` folder

```
import Vue from 'vue'
import Router from 'vue-router'
import Home from './components/container.vue'

Vue.use(Router)

export default new Router({
    mode: 'history',
    routes: [{
            path: '/',
            name: 'home',
            component: Home
        },
        {
            path: '/container',
            name: 'container',
            // route level code-splitting
            // this generates a separate chunk (about.[hash].js) for this route
            // which is lazy-loaded when the route is visited.
            component: () => import( /* webpackChunkName: "about" */ './components/other.vue')
        },
    ]
})

```

Inside `app.js`


```
require('./bootstrap');

window.Vue = require('vue');
import Router from './router.js'

const app = new Vue({
    router: Router
}).$mount('#app')

```

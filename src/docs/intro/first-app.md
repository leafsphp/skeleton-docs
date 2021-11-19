# Your first app ✨

Before you go on, Skeleton is powered by [Leaf](https://leafphp.dev/), so we'll recommend getting familiar with the core [Leaf package](https://leafphp.dev/) first. Not to worry, it takes just about 5-10 minutes to completely learn the basics if you've used any PHP framework before.

## Introduction 📖

This is a little "tutorial" put together to introduce you to Skeleton, and help you learn all needed concepts. We'll be building a simple blog to demonstrate how Skeleton works. We’ll be using models, request, views, controllers and a whole lot of other tools provided for us.😎

::: warning Note that
If you are not familiar with PHP, we recommend that you check out the [W3Schools PHP Tutorial](https://www.w3schools.com/php/default.asp) before continuing.
:::

## Our First App

In the [previous section](/docs/#Installation), we looked at installation, Skeleton's directory structure and running your project, it's assumed you've already read this section. After following the installation instructions, your Skeleton structure should be initialized for you. You can run the intro app with

```bash
php -S localhost:5500
```

or with leaf cli

```sh
leaf serve
```

When we take a look at our `index.php` file, we see that Leaf Core is initialised and a bunch of files including our routes are imported.

As such, `index.php` serves as our project root. Every request/page load passes through `index.php` first and this is done because of the [.htaccess](/leaf/v/2.4.3/intro/htaccess) file.

### Routing

::: warning Note that
Routing is based on the leaf 3 and uses the leaf router module. If you haven't already read the docs, we recommend that you read on [routing with leaf PHP](https://leafphp.dev/docs/routing)
:::

Routes are stored in the `routes` directory. In there, you can create routes specific to an operation like `_users.php` or `_transactions.php` which hold routes specific to that operation. After this, you can link these files by requiring them in `routes/index.php`. This is totally optional as you can list all your routes in the `routes/index.php` file.

Example routes have been created to give you a fair idea on how to handle routing in Skeleton.

Now, let’s get started.

```php
<?php

app()->get('/', function() {
  // Do something here
});

// or
app()->get('/', function() {
  // Do something here
});

# Leaf router
use Leaf\Router;

Router::get("/", function() {
  // Do something here
});
```

This is what a basic Leaf route looks like.

In some cases, you may want to use controllers to handle various routes, so, let's do just that.

### Using Controllers

The first thing we need to do to use a controller is obviously to create the controller. Our controllers are kept in the `controllers` directory by default. Let's create a `PagesController.php` file in our `controllers` directory.

```php
<?php

namespace Controllers;

class PagesController extends Controller {
  public function index()
  {
    echo "Hello";
  }
}
```

Back in our routes file, we can use this controller like so:

```php
app()->get('/', '\Controllers\PagesController@index');

# leaf router class
use Leaf\Router;

Router::get("/", "\Controllers\PagesController@index");
```

Although this is perfectly fine, it's quite annoying to type `\Controllers` for every route, so we can set a namespace for all our routes.

```php
app()->setNamespace("\Controllers");

app()->get("/", "PagesController@index");

# leaf router class
use Leaf\Router;

Router::get("/", "PagesController@index");
```

In this case, this particular controller @ method index, is supposed to output a view. There are a bunch of ways to output views in Leaf MVC. You can simply output a bunch of markup with `markup`.

```php
response()->markup("<h2>Hello</h2>");
```

Of course, this isn't that practical😆

The next method is to output a static HTML/PHP page. Of course, this method is more practical.

```php
response()->page("./index.html");
```

The final method is to use a templating engine. This is the most common method people use when it comes to displaying views. Skeleton comes with [bareui](https://leafphp.dev/modules/views/bareui/) by default which you can utilize by simply calling `view`. Let's use that in our controller.

```php
<?php

namespace Controllers;

class PagesController extends Controller {
  public function index()
  {
    echo view("home");
  }
}
```

Now, we need to define `pages/home.view.php` in our `pages` directory so we don't get an error when we load this route.

`pages/home.view.php`

```php
<!DOCTYPE html>
<html>

<head>
    <title>Welcome to Leaf 3!</title>
    <meta charset="utf-8" />
    <meta content="width=device-width,initial-scale=1.0,minimum-scale=1.0" name="viewport" />
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=DM+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700;display=swap">
    <link rel="stylesheet" href="pages/styles.css">
</head>

<body class="flex center-all h-screen">
    <div class="container">
        <div class="mt-3">
            <div class="flex center-start">
                <img src="https://www.leafphp.dev/logo-circle.png" alt="">
                <h4 style="font-size: 22px;">Welcome to Leaf <span class="green">3</span></h4>
            </div>
            <div class="flex card mt-3">
                Hello
            </div>
        </div>
    </div>
</body>

</html>
```

### Request

Response/Views send data out of our application, on the flip side, Request handles the data that comes into our application. You can find Leaf Request docs [here](https://leafphp.dev/modules/http/request.html).

Let's look at a basic example. Inside our controller:

```php
public function search() {
  $keywords = request()->get("keywords");

  // ... handle search operation
  response()->json($results);
}
```

The whole request object is available on the `request` method. The `request` method can also be used to get items from the request.

```php
// get username
$username = request("username");

// get username
$username = request()->get("username");
```

Leaf also allows you to use request methods statically which means you can also do this:

```php
use Leaf\Http\Request;

public function search() {
  $keywords = Request::get("keywords");

  // ... handle search operation
  echo view("search", ["results" => $results]);
}
```

### Models

Our models represent our data layer, usually from a database. Our models are kept in the `models` directory. Controllers get required information from models which is then passed into the response. We won't be doing much work in the model itself, since all the ground work has already been done by Leaf Core.

::: tip Note that
To use your database, you have to head to `.env` and configure your database: set the databse name, username, password...
:::

We will create a Post model to get data from a `posts` table in the database.

::: warning Note that
Read the leaf MVC core [models documentation](https://leafphp.dev/modules/mvc-core/#models) for more info.
:::

`models/Post.php`

```php
<?php
namespace Models;

class Post extends Model {
  //
}
```

### Using our model

As mentioned before, we don't really do much in the model. The magic happens in our controller. Let's create a new controller.

`controllers/PostsController`:

```php
<?php
namespace Controllers;

class PostsController extends Controller {
  /**
   * Display a listing of the resource.
   */
  public function index() {
    //
  }

  /**
   * Show the form for creating a new resource.
   */
  public function create() {
    //
  }

  /**
   * Store a newly created resource in storage.
   */
  public function store() {
    //
  }

  /**
   * Display the specified resource.
   */
  public function show($id) {
    //
  }

  /**
   * Show the form for editing the specified resource.
   */
  public function edit($id) {
    //
  }

  /**
   * Update the specified resource in storage.
   */
  public function update($id) {
    //
  }

  /**
   * Remove the specified resource from storage.
   */
  public function destroy($id) {
    //
  }
}
```

A resource controller is filled with resource methods which quickly help us perform CRUD functions.

So let's say we have a database named `blog` with a table named `posts` which has some data in it, to retrieve all the data in the `posts` table, we'll head to our controller. The first thing we'll have to do is link the resource controller to our routes. Leaf provides a simple way to do this:

```php
app()->resource("/posts", "PostsController");
```

With this, leaf will create all the required routes for your resource controller. Check out the [routing docs](https://leafphp.dev/docs/routing/#resource-routes) for a break down on resource routes. Next, we need to bring in our `Post` model so we can use our database.

```php
<?php
namespace Controllers;

// our model
use Models\Post;

class PostsController extends Controller {
  public function __construct() {
    .....
```

Now let's head over to our index method and enter this:

```php
public function index() {
  echo view("posts", ["posts" => Post::all()]);
}
```

`Post::all()` is a method which will query our database and retrieve all our `posts` for us, we're using `view()` to render all our posts in a view.

So when we navigate to `/posts` in our browser, we see all our posts in JSON format.

For a blog app, we'd usually want to see our latest posts first, so we can order the posts by the time they were created. In our controller,

```php
public function index() {
  echo view("posts", ["posts" => Post::orderBy('id', 'desc')->get()]);
}
```

This will get the latest posts first.

Next, we'll want to show a particular post when we navigate to `/post/{id}` eg: when we go to `/posts/2` in our browser, we would want to see the post 2...so, in our controller's show method, we simply have to get that particular post and pass it into the response. We can get the current post with `Post::find($id);`

```php
public function show($id) {
  render("post", ["posts" => Post::find($id)]);
}
```

Here are a bunch of other cool stuff you can do wiith the model in our controller,

```php
// find a post by title
Post::where('title', 'Post Two')->get();

// create a new post
$post = new Post;
$post->title = request("title");
$post->body = request("body");
$post->save();

// delete a post
$post = Post::find($id);
$post->delete();
```

# Skeleton
<!-- markdownlint-disable no-inline-html -->

Leaf Skeleton is a lightweight and minimal MVC boilerplate for leaf PHP framework that provides a more scalable and powerful setup for creating web apps and APIs quickly and efficiently. Skeleton is simply a boilerplate and so avoids all the rules involved in building with full-featured frameworks like leaf API and leaf MVC.

Skeleton 3.0 comes in with a bunch of fresh functionality, and also features added in [v3](https://leafphp.dev) of the core Leaf package. You can view all these [changes here](/docs/new/).

## Why Skeleton?

### ð Shallow learning curve

Whether you are new to PHP or have prior experience with the language, Skeleton helps you fit right in. All you need to get started with Leaf MVC is basic PHP knowledge and a little familiarity with MVC concepts and leaf itself.

### ðŠķ Lightweight

Skeleton is not a framework, it is simply leaf with a few pre-installed modules and a bunch of folders ð. This means that it is fast and almost as light as simply building with leaf core.

### ðŠð― Powerful

Skeleton packs a ton of powerful tools which speed up your development process by folds. You have simple tools and modules like [authentication](https://www.leafphp.dev/modules/auth/), [MVC tools with MVC core](https://www.leafphp.dev/modules/mvc-core/) and a [ton of other modules](https://www.leafphp.dev/modules/).

## Installation

You can quickly create a Skeleton project with [composer](https://getcomposer.org).

```sh
composer create-project leafs/skeleton <project-name> v3.x-dev
```

or with the leaf cli:

```sh
leaf create <project-name> --skeleton --v3
```

## Directory Structure

This will create a new Skeleton project named `<project-name>`. Inside the new directory, you should have a structure like this.

::: tip Note
The directory structure has had a refresh. We normalized the folder cases to lowercase. Note that this only applies to the default Skeleton folders. Custom folders will have to follow the class structure as done in earlier versions.
:::

```bash
C:.
âââ config
â   âââ app.php
â   âââ auth.php
â   âââ cors.php
â   âââ database.php
â   âââ paths.php
â   âââ view.php
âââ controllers
â   âââ Controller.php
â   âââ TestsController.php
âââ models
â   âââ Model.php
â   âââ Test.php
âââ pages
â   âââ body.view.php
â   âââ components
â   âââ index.html
â   âââ styles.css
â   âââ test.view.php
âââ routes
â   âââ _app.php
â   âââ index.php
âââ storage
â   âââ app
â   âââ framework
â   âââ logs
âââ vendor
âââ index.php
```

- **config**: This holds all your configuration files.
- **controllers**: This directory holds all your controllers
- **models**: This holds all your models
- **pages**: This holds all your views
- **routes**: This holds all your routes
- **storage**: Storage for your files, images, text, databases...
- **vendor**: This holds all your dependencies and installed files.

::: tip Directory Structure
Skeleton is 100% customizable. You can rearrange the directories to match your preference. Simply reconfigure the directories in `config/paths.php`
:::

In the project root, you can open up your console tool and type in

```bash
php leaf serve
```

This will start the php web server and load your project at `http://localhost:5500` by default.

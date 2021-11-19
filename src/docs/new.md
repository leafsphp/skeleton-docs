# What's new?

::: tip
This section is for those who have experience with Skeleton 2. If you are new here, you can move to the next section.
:::

## Normalized folder names

Skeleton now has normalized names for directories. Directories now use lowercase instead of the earlier pascal case.

```bash
C:.
├── config
│   ├── app.php
│   ├── auth.php
│   ├── cors.php
│   ├── database.php
│   ├── paths.php
│   └── view.php
├── controllers
│   ├── Controller.php
│   └── TestsController.php
├── models
│   ├── Model.php
│   └── Test.php
├── pages
│   ├── body.view.php
│   ├── components
│   ├── index.html
│   ├── styles.css
│   └── test.view.php
├── routes
│   ├── _app.php
│   └── index.php
├── storage
│   ├── app
│   ├── framework
│   └── logs
├── vendor
└── index.php
```

## Better configuration

Skeleton now includes configurations in the `config` folder which allows you to easily configure Leaf's features: things like cors, views, authentication and aloe's directories. Editing the configuration allows you to customize the behaviour of Leaf's features.

## Global Methods

Skeleton no longer comes with "self-defined" global methods. Leaf 3 now comes with functional mode which replaces the whole idea of defining functions for Skeleton. Leaf MVC core which is used in Leaf MVC, Leaf API and Skeleton comes in with new global functions which extend Leaf 3's functional mode.

## Leaf 3

A little obvious here, but Skeleton 3 runs on Leaf 3. This makes it even lighter, faster and easier to work with. This also means that you have access to tons of features through modules and you won't need to worry about updating the whole framework to receive updates. You only need to upgrade a particular module.

## Modules

Some leaf 3 modules come integrated directly with Leaf MVC along with some config options.

## MVC Core

MVC core is a leaf 3 module which contains all the functionality for transforming leaf into a full MVC framework. It comes with features like controllers, models, views, factories and many more MVC specific features. It has been optimised for leaf mvc, leaf API and Skeleton to provide the best developer experience.

## BareUI

The default templating engine in Skeleton is now BareUI which is a barebones, super lightweight templating engine with zero compilation which makes it super fast.

We really recommend that you [read the MVC core documentation](https://www.leafphp.dev/modules/mvc-core/)

---
aside: none
---

# Path Config

Skeleton comes in with a whole lot of available customizations. One major customization is the paths config. This allows you to manually re-arrange Skeleton's directory structure to something you prefer. This means you can rearrange the whole of Skeleton and have all your files still map correctly.

```php
<?php

return [
	'controllersPath' => 'controllers',

	'modelsPath' => 'models',

	'migrationsPath' => 'migrations',

	'seedsPath' => 'seeds',

	'factoriesPath' => 'factories',

	'helpersPath' => 'helpers',

	'viewsPath' => 'pages',

	'configPath' => 'config',

	'storagePath' => 'storage',

	'commandsPath' => 'console',

	'routesPath' => 'routes',

	'libPath' => 'lib',

	'publicPath' => '.',
];
```

These defined paths become available through global shortcut functions like `viewsPath()`

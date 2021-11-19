---
aside: none
---

# Path Config

Skeleton comes in with a whole lot of available customizations. One major customization is the paths config. This allows you to manually re-arrange Skeleton's directory structure to something you prefer. This means you can rearrange the whole of Skeleton and have all your files still map correctly.

```php
<?php

return [
  "controllers_path" => "controllers",

  "models_path" => "models",

  // skeleton doesn't come with migrations
  "migrations_path" => "migrations",

  // skeleton doesn't come with seeds
  "seeds_path" => "database/Seeds",

  // skeleton doesn't come with factories
  "factories_path" => "database/Factories",

  "helpers_path" => "helpers",

  "views_path" => "pages",

  "config_path" => "config",

  "storage_path" => "storage",

  // skeleton doesn't come with commands
  "commands_path" => "console",

  "routes_path" => "routes",

  // doesn't come with defaults
  "lib_path" => "Lib",

  // doesn't come with defaults
  "public_path" => "public",
];
```

These defined paths become available through global shortcut functions like `views_path()`

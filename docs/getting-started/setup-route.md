# Setup Route

Route is defined by `Route` class.

Here is a default route file of `FooBar` application:

```
<?php

namespace FooBar;

use Dietcube\RouteInterface;
use Pimple\Container;

class Route implements RouteInterface
{
    /**
     * {@inheritDoc}
     */
    public function definition(Container $container)
    {
        return [
            ['GET', '/', 'Top::index'],
        ];
    }
}
```

`definition()` method returns an array of route information.

The element of route information array is following format:

```
[HTTP_METHOD, PATH, HANDLER]
```

## HTTP_METHOD

`HTTP_METHOD` should be a string of HTTP Method name or an array contains HTTP Method name.

For example:

- `'GET'`: matches GET request.
- `'POST'`: matches POST request.
- `['GET', 'POST']`: matches both of GET and POST request.


## PATH

`PATH` is the path of user accessed url. And can define a route parameter.

For example:

- `/`: just matches `/`.
- `/user/{name}`: matches `/user/sotarok` and so far.
- `/user/{id:[0-9]+}`: matches `/user/12345` and so far.

## HANDLER

`HANDLER` should be folloring format:

```
CONTROLLER_NAME::ACTION_METHOD_NAME
```

For example:

- `Top::index` means `FooBar\Controller\TopController::index()`.
- `Api\User::show` means `FooBar\Controller\Api\UserController::show()`.

## Add a new route information

To create new route information, modify the array returned by `definitiion()` method.

For example:

```
    public function definition(Container $container)
    {
        return [
            ['GET', '/', 'Top::index'],
            ['GET', '/user/{name}', 'User::show'],
        ];
    }
```

added `UserController::show($user)` method as a controller for a `/user/xxxxx` path.


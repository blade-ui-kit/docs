# Contribution Guide

Thank you for taking an interest in contributing to Blade UI Kit! We welcome pull requests as well as thoughtful issues to improve it even further. We wrote this contribution guide to help you on your journey so please review it carefully before submitting your issue or pull request. Thanks!

## Requesting Components

We very much welcome requests for new components. But before doing so please make sure to search [the issue tracker](https://github.com/blade-ui-kit/blade-ui-kit/issues) to see if your component was requested before. A similar issue request might be open already so make sure to upvote it so it gets more attention. We'll generally focus more on components that are higher upvoted. 

When requesting a component make sure to thoroughly explain what you expect the component to do. Providing an example syntax of its usage helps a lot in understanding how it should be designed. As soon as you're ready, head over to the repo and [open an issue to request a component](https://github.com/blade-ui-kit/blade-ui-kit/issues/new/choose).

Your component, however might be rejected. This could be because we feel that it doesn't really belongs in the library or that we don't want to maintain it ourselves. In order to keep the library maintable we need to be critical to the amount of components we accept.

## Building Components

If you want to build a component yourself, please make sure that you [request it first](#requesting-components) before building it. Otherwise you run the risk of it being rejected even though you've put in all the work already.

When building components there's some things you need to know. First of all, every component needs a view and a class. These need to be placed in the exact same directory structures. For example, the `input` component's class is placed in `resources/views/components/forms/inputs/input.blade.php` and its class is placed in `src/Components/Forms/Inputs/Input.php`. You also need to enable the component through the config file through the `components` config option. The components here are arranged alphabetically by their class name(space).

Components are also fully standalone. This means you cannot reference other components in their views etc. This is to prevent conflicts with other libraries, prefixing being broken or people not being able to overwrite components anymore.

### Assets

When you're building a component which makes use of a library that needs some CDN CSS and/or JavaScript assets you can reference the library in the `blade-ui-kit.php` config's `assets` option. Afterwards, you can load the CDN assets through the component's reserved `$assets` property:

```php
use BladeUIKit\Components\BladeComponent;

class MyComponent extends BladeComponent
{
    protected static $assets = ['my-library'];

    ...
}
```

## Writing Tests

When building components or contributing to the library we also encourage to write tests. Please [reference the existing test suite](https://github.com/blade-ui-kit/blade-ui-kit/tree/main/tests/Components) and create equivalent tests for new components or new component functionality.

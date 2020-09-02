# Installation

## Requirements

- PHP 7.3 or higher
- Laravel 7.0 or higher

## Getting Started

Before installing a new package it's always a good idea to clear your config cache:

```bash
php artisan config:clear
```

Then install the package by running:

```bash
composer require blade-ui-kit/blade-ui-kit
```

### Directives

One of the biggest advantages of Blade UI Kit is that almost all of its components come ready out-of-the-box. To achieve this, Blade UI Kit makes use of CDNs from any 3rd party library that a component might need. To make sure these CDNs are included in your HTML, you can make use of the `@bukStyles` and `@bukScripts` directives.

Place the `@bukStyles` directive right before your closing `</head>` tag and **after** scripts from libraries like Livewire. Place the `@bukScripts` directive right before your closing `</body>` tag and **after** scripts from libraries like Livewire.

### Production

Even though these directives allow you to get up and running with the components quickly, **we recommend that you compile the 3rd party libraries that each component needs through an asset pipeline** (like [Laravel Mix](https://github.com/JeffreyWay/laravel-mix)). By default, when your `app.debug` config option is disabled, the directives are also disabled for performance reasons. 

If you always want these directives to be executed, even when `app.debug` is disabled, you can force them to load the CDN links by passing a `true` boolean:

```html
@bukStyles(true)
@bukScripts(true)
```

Libraries are only loaded for components that are enabled through the `components` config option. You can learn more about [disabling specific components](#components) below.

## Configuration

Most of the configuration is done through the `blade-ui-kit.php` config file. *Even though by default this isn't needed*, if you'd like to adjust anything to this config file, you can publish it with the following command:

```bash
php artisan vendor:publish --tag=blade-ui-kit-config
```

When doing this, make sure to keep the config file up to date with any changes when [upgrading the library](/docs/{{version}}/upgrade-guide).

### Components

Even though all components come enabled out-of-the-box, you may want to load only the components you need in your app for performance reasons. To do so, first [publish the config file](/docs/{{version}}/installation#configuration), then remove the components you don't need from the `components` settings.

You can also choose to use different names for components. Simply adjust the name for a component and reference it with a new name. For example, let's rename the `easy-mde` component to `markdown-editor`:

```php
<?php

return [
    'components' => [
        ...
        'markdown-editor' => Components\Editors\EasyMDE::class,
        ...
    ],
];
```

Now, you can reference it in your Blade views as:

```html
<x-markdown-editor name="about" />
```

### Prefixing

Components from this library might conflict with other ones from different libraries, or components from your own app. To prevent this, you can opt to add a prefix to the Blade UI Kit components. You can do this by setting the `prefix` option in the config file:

```php
<?php

return [
    ...
    'prefix' => 'buk',
    ...
];
```

Now all components can be referenced as usual, but with the prefix before their name:

```html
<x-buk-easy-mde name="about" />
```

For obvious reasons, the docs don't use any prefix in their code examples. So keep this in mind when setting a prefix and copy/pasting code snippets.

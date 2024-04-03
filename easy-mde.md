# Easy MDE

The `easy-mde` component allows you to easily include a Markdown editor in your form. Behind the scenes it makes use of [the Easy MDE library](https://github.com/Ionaru/easy-markdown-editor). The input is passed through to a form as a normal textarea input.

## Installation

While the `easy-mde` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`
- [Easy MDE](https://github.com/Ionaru/easy-markdown-editor) `^2.0`

## Basic Usage

In its most basic usage, you use it as a self closing component and pass it a name:

```html
<x-easy-mde name="about"/>
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<textarea name="about" id="about"></textarea>
```

From there, the Easy MDE editor will be rendered. Of course, you can also specifically set a default value:

```html
<x-easy-mde name="about">My about text</x-easy-mde>
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<textarea name="about" id="about">My about text</textarea>
```

### Old Values

The `easy-mde` component also supports old values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `easy-mde` component will remember the old value:

```html
<textarea name="about" id="about">
# Blade UI Kit

Blade components are **awesome**.
</textarea>
```

## Passing Options

You can also pass options to Easy MDE with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we set the minimum height:

```html
<x-easy-mde name="about" :options="['minHeight' => '500px']" />
```

For a full reference of all options, please consult [the Easy MDE documentation](https://github.com/Ionaru/easy-markdown-editor#options-list).

> Please note that only scalar values are supported. You cannot use any JavaScript language specific options like callbacks.

## Setting Defaults

If you'd like to set some sensible defaults for all your `easy-mde` component usages you can do so by overwriting the component class and `options` method:

```php
<?php

namespace App\View\Components;

class EasyMDE extends \BladeUIKit\Components\Editors\EasyMDE
{
    public function options(): array
    {
        return array_merge([
            'minHeight' => '500px',
            'status' => false, // Disable the status bar.
        ], parent::options());
    }
}
```

It's important in the above snippet that you call `parent::options()` so any options passed directly to the component are still applied as well. 

After overwriting the component we'll need to register it in our `blade-ui-kit.php` config file. Make sure to replace the default one with your own class:

```php
<?php

return [
    'components' => [
        ...
        'easy-mde' => App\View\Components\EasyMDE::class,
        ...
    ],
];
```

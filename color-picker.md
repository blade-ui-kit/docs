# Color Picker

The `color-picker` component provides an easy way to integrate a color picker into your forms. It makes use of the [Pickr](https://github.com/Simonwep/pickr) library behind the scenes.

## Installation

While the `color-picker` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`
- [Pickr](https://github.com/Simonwep/pickr) `^1.0`

## Basic Usage

The most basic usage of the component is to set a `name` attribute:

```html
<x-color-picker name="color" />
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<div title="">
    <div id="color"></div>
    <input id="color-input" name="color" type="hidden" />
</div>
```

The `<div id="color"></div>` is used by Pickr to render the color picker. What's also nice is that when a color has been chosen, the `title` attribute on the parent `div` will be filled in with the color code so it's visible when the user hovers over it.

### Old Values

The `color-picker` component also supports old values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `color-picker` component will remember the old value:

```html
<div title="#FF0000">
    <div id="color"></div>
    <input id="color-input" name="color" type="hidden" value="#FF0000" />
</div>
```

## Passing Options

You can also pass options to Pickr with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we allow opacity to be set:

```html
<x-color-picker name="color" :options="['opacity' => true]" />
```

For a full reference of all options, please consult [the Pickr documentation](https://github.com/Simonwep/pickr#options).

> Please note that only scalar values are supported. You cannot use any JavaScript language specific options like callbacks.

## Setting Defaults

If you'd like to set some sensible defaults for all your `color-picker` component usages you can do so by overwriting the component class and `options` method:

```php
<?php

namespace App\View\Components;

class ColorPicker extends \BladeUIKit\Components\Forms\Inputs\ColorPicker
{
    public function options(): array
    {
        return array_merge([
            'opacity' => true,
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
        'color-picker' => App\View\Components\ColorPicker::class,
        ...
    ],
];
```

### Customizing Swatches

You can also easily set a default set of colors for the color picker by overwriting the `swatches` method:

```php
<?php

namespace App\View\Components;

class ColorPicker extends \BladeUIKit\Components\Forms\Inputs\ColorPicker
{
    protected function swatches(): array
    {
        return [
            '000000',
            'A0AEC0',
            'F56565',
            'ED8936',
            'ECC94B',
            '48BB78',
            '38B2AC',
            '4299E1',
            '667EEA',
            '9F7AEA',
            'ED64A6',
            'FFFFFF',
        ];
    }
}
```

By default it makes use of the `500` color variants from [Tailwind CSS](https://tailwindcss.com/docs/customizing-colors/#default-color-palette).

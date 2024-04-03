# Flatpickr

The `flat-pickr` component offers an integration with [the Flatpickr Date/Time library](https://flatpickr.js.org/). By using it, you can simply add a datetime picker to your form with one component.

## Installation

While the `flat-pickr` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://alpinejs.dev/essentials/installation) `^3.0`
- [Flatpickr](https://flatpickr.js.org/getting-started) `^4`

## Basic Usage

In its most basic usage, you use it as a self closing component and pass it a name:

```html
<x-flat-pickr name="birthday" />
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<input
    name="birthday"
    type="text"
    id="birthday"
    placeholder="Y-m-d H:i"
/>
```

As you can see, the component sets a couple of nice defaults for your component. The `placeholder` is also the date format used to render the date in the input field after choosing one.

### Old Values

The `flat-pickr` component also supports old values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `flat-pickr` component will remember the old value:

```html
<input
    name="birthday"
    type="text"
    id="birthday"
    value="20/05/2021"
    placeholder="Y-m-d H:i"
/>
```

## Customizing The Format

You can choose a different format for the input field by setting the `format` attribute: 

```html
<x-flat-pickr name="birthday" format="YYYY-MM-DD" />
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<input 
    name="birthday" 
    type="text" 
    id="birthday" 
    placeholder="YYYY-MM-DD" 
/>
```

For a full reference of all formatting options, please consult [the Flatpickr documention](https://flatpickr.js.org/formatting/).

## Passing Options

You can also pass options to Pikaday with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we set the position of calender above input instead of the default value auto:

```html
<x-flat-pickr name="birthday" :options="['position' => 'above']" />
```

For a full reference of all options, please consult [the Flatpickr documentation](https://flatpickr.js.org/options/).

> Please note that only scalar values are supported. You cannot use any JavaScript language specific options like callbacks.

## Setting Defaults

If you'd like to set some sensible defaults for all your `flat-pickr` component usages you can do so by overwriting the component class and `options` method:

```php
<?php

namespace App\View\Components;

class FlatPickr extends \BladeUIKit\Components\Forms\Inputs\FlatPickr
{
    public function options(): array
    {
        return array_merge([
            'mode' => 'multiple', // make user can select multiple dates
            'time_24hr' => true,
        ], parent::options());
    }
}
```

It's important in the above snippet that you call `parent::options()`, so that any options passed directly to the component are still applied as well. 

After overwriting the component we'll need to register it in our `blade-ui-kit.php` config file. Make sure to replace the default one with your own class:

```php
<?php

return [
    'components' => [
        ...
        'flat-pickr' => \App\View\Components\FlatPickr::class,
        ...
    ],
];
```

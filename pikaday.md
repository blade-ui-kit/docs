# Pikaday

The `pikaday` component offers an integration with [the Pikaday datepicker library](https://pikaday.com). By using it, you can simply add a datepicker to your form with one component. By leveraging [Moment.js](https://momentjs.com) you can specify different datetime formats.

## Installation

While the `pikaday` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`
- [Pikaday](https://github.com/Pikaday/Pikaday#installation) `^1.0`
- [Moment.js](https://momentjs.com) `^2.26`

## Basic Usage

In its most basic usage, you use it as a self closing component and pass it a name:

```html
<x-pikaday name="birthday" />
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<input
    name="birthday"
    type="text"
    id="birthday"
    placeholder="DD/MM/YYYY"
/>
```

As you can see, the component sets a couple of nice defaults for your component. The `placeholder` is also the date format used by Moment.js to render the date in the input field after choosing one.

### Old Values

The `pikaday` component also supports old values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `pikaday` component will remember the old value:

```html
<input
    name="birthday"
    type="text"
    id="birthday"
    value="20/05/1989"
    placeholder="DD/MM/YYYY"
/>
```

## Customizing The Format

You can choose a different format for the input field by setting the `format` attribute: 

```html
<x-pikaday name="birthday" format="YYYY-MM-DD" />
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

For a full reference of all formatting options, please consult [the Moment.js documentation](https://momentjs.com/docs/#/displaying/format).

## Passing Options

You can also pass options to Pikaday with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we set the first day of the week as Monday instead of the default Sunday value:

```html
<x-pikaday name="birthday" :options="['firstDay' => 1]" />
```

For a full reference of all options, please consult [the Pikaday documentation](https://github.com/Pikaday/Pikaday#configuration).

> Please note that only scalar values are supported. You cannot use any JavaScript language specific options like callbacks.

## Setting Defaults

If you'd like to set some sensible defaults for all your `pikaday` component usages you can do so by overwriting the component class and `options` method:

```php
<?php

namespace App\View\Components;

class Pikaday extends \BladeUIKit\Components\Forms\Inputs\Pikaday
{
    public function options(): array
    {
        return array_merge([
            'disableWeekends' => true,
            'firstDay' => 1, // Set default start to Monday.
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
        'pikaday' => \App\View\Components\Pikaday::class,
        ...
    ],
];
```

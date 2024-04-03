# Mapbox

The `mapbox` component provides an easy way to render a [Mapbox](https://mapbox.com) map in your app. You can choose a different Mapbox theme, pass in options and even markers.

## Installation

While the `mapbox` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`
- [Mapbox](https://docs.mapbox.com/mapbox-gl-js/api/) `^1.8`

To set up the API access token for Mapbox you will need to add a config option to your `config/services.php` file:

```php
'mapbox' => [
    'public_token' => env('MAPBOX_PUBLIC_TOKEN'),
],
```

Get your Mapbox access key from the [dashboard](https://account.mapbox.com) after creating an app with them. Then set it in your .env file:

```
MAPBOX_PUBLIC_TOKEN=<your access key>
```

## Basic Usage

In its most basic usage, you use it as a self closing component:

```html
<x-mapbox />
```

This will output the following HTML *(inline JS has been omitted)*:

```html
<div id="map"></div>
```

Which will render the map on the above `div` element.

### Multiple Maps

When rendering multiple maps on a single page it's important to set different ID's for them:

```html
<x-mapbox id="primary-map" />
<x-mapbox id="secondary-map" />
```

Doing so will make sure the JavaScript library can render them properly.

## Using Markers

You can place markers on maps by passing them a set of coordinates as a PHP array to the `markers` attribute:

```html
<x-mapbox :markers="[[13.4105300, 52.5243700]]"/>
``` 

Doing so will place the markers at exactly these coordinates. You can place as many markers as you like.

> At the moment placing markers is pretty limited. [We're hoping to improve this feature](https://github.com/blade-ui-kit/blade-ui-kit/issues/5) over time.

## Passing Options

You can also pass options to Mapbox with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we set the zoom of the map:

```html
<x-mapbox :options="['zoom' => 8]" />
```

For a full reference of all options, please consult [the Mapbox documentation](https://docs.mapbox.com/mapbox-gl-js/api/map/#map-parameters).

> Please note that only scalar values are supported. You cannot use any JavaScript language specific options like callbacks.

## Setting Defaults

If you'd like to set some sensible defaults for all your `mapbox` component usages you can do so by overwriting the component class and `options` method:

```php
<?php

namespace App\View\Components;

class Mapbox extends \BladeUIKit\Components\Maps\Mapbox
{
    public function options(): array
    {
        return array_merge([
            'zoom' => 8,
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
        'mapbox' => App\View\Components\Mapbox::class,
        ...
    ],
];
```

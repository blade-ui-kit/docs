# Carbon

The `carbon` component in Blade UI Kit is a small and nice convenience component to work with `DateTimeInterface` objects in your Blade views. You can easily format them, auto-apply hover states, make them human readable or display them in the browser timezone of the user.

## Installation

While the `carbon` component works out-of-the-box when you've [set the directives](/docs/{version}/installation#directives), we recommend that you install and compile its JavaScript libraries when you deploy to production:

- [Moment.js](https://momentjs.com) `^2.26`
- [Moment Timezone](https://momentjs.com/timezone/) `^0.5.31`

## Basic Usage

In its most basic form you can use the component to format a `DateTimeInterface` instance in the default `Y-m-d H:i:s` format of the component:

```html
<x-carbon :date="$date" />
```

This will output the following HTML:

```html
<span title="2 hours from now">
    2020-05-13 21:00:00
</span>
```

As you can see a `span` element gets added with a title. This way if a user hovers over the date they get a nice human readable format.

## Formatting

Of course, you may also use a specific format:

```html
<x-carbon :date="$date" format="d/m/Y H:i" />
```

This will output the following HTML:

```html
<span title="2 hours from now">
    13/05/2020 21:00
</span>
```

## Human Readable

The component also features a `human` boolean attribute that you can set to inverse the behavior of the title:

```html
<x-carbon :date="$date" human />
```

This will output the following HTML:

```html
<span title="2020-05-13 21:00:00">
    2 hours from now
</span>
```

## Local Timezone

And when you apply the `local` attribute it'll format the instance into the local timezone of the user's browser:

```html
<x-carbon :date="$date" local />
```

This will output the following HTML:

```html
<span title="2 hours from now">
    2020-05-13 23:00:00 (CEST)
</span>
```

This uses Alpine to determine in which timezone the user is browsing. 

> Please note that you cannot combine `human` and `local` at the same time.

### Formatting Local

Formatting for with the `local` boolean attribute works a little different. You can still use the `format` attribute but instead of using [PHP's date formatting](https://www.php.net/manual/en/datetime.format.php) you'll need to use [Moment.js' date formatting options](https://momentjs.com/docs/#/displaying/format/).

```html
<x-carbon :date="$date" local format="DD/MM/YYYY HH:mm (z)" />
```

This will output the following HTML:

```html
<span title="2 hours from now">
    13/05/2020 23:00 (CEST)
</span>
```

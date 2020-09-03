# HTML

The `html` component is a convenience component for a often done code snippet in your web app: the `<html>` element with the `<head>` & `<body>` elements. Set your page title, scripts and styles with easy without having to remember what the syntax was again.

## Installation

The `html` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the component exists in setting its slotted content:

```html
<x-html class="font-sans">
    <h1>Hello World</h1>
</x-html>
```

This will output the following HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <meta name="csrf-token" content="...">

    <title>Blade UI Kit</title>
</head>
<body class="font-sans">
    <h1>Hello World</h1>
</body>
</html>
```

As you can see you can get rid of all the redundant boilerplate. The component behaves simarly to the stub from the auth scaffolding from Laravel. The `lang` attribute on the `html` element is determined by the app's locale. The CSRF token is set so libraries like [Laravel Echo](https://github.com/laravel/echo) can make use of it. And the page title is set based on the `app.name` config setting. All attributes that are set on the component are piped through onto the `<body>` element.

## Page Title

You can of set a custom title if you like:

```html
<x-html title="My App">
    <h1>Hello World</h1>
</x-html>
```

This will output the following HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <meta name="csrf-token" content="...">

    <title>My App</title>
</head>
<body>
    <h1>Hello World</h1>
</body>
</html>
```

Something I like to do myself often is make use of a delimiter between the page title and app name. Because Blade components allow you to use PHP when prefixing attributes with the `:` syntax we can easily do this:

```
<x-html :title="isset($title) ? $title . ' - ' . config('app.name') : ''">
    <h1>Hello World</h1>
</x-html>
```

If `$title` would have the value of `My Page` then this will generate a title like:

```html
<title>My Page - Blade UI Kit</title>
```

## Customizing The Head

You can also customize the content of the `<head>` element by using its slot:

```html
<x-html>
    <x-slot name="head">
        <link rel="icon" href="favicon.ico" />
    </x-slot>

    <h1>Hello World</h1>
</x-html>
```

This will output the following HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <meta name="csrf-token" content="...">

    <title>Blade UI Kit</title>

    <link rel="icon" href="favicon.ico" />
</head>
<body>
    <h1>Hello World</h1>
</body> 
</html>
```

This is convenient for setting scripts and styles as well as any other customization you'd like to do.

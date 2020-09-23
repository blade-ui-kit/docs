# Password

The `password` component offers an easy way to set up a password input field for your forms. By simply setting its `name` attribute it also automatically defines your `id`.

## Installation

The `password` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the component is as a self-closing component:

```html
<x-password />
```

This will output the following HTML:

```html
<input name="password" type="password" id="password" />
```

By default a `password` type will be set for the input field as well as an `id` that allows it to be easily referenced by a `label` element.

Of course, you can also specifically set a `name` attribute:

```html
<x-password name="my_password" class="p-4" />
```

This will output the following HTML:

```html
<input name="my_password" type="password" id="my_password" class="p-4" />
```

Of course, unlike the other input fields in Blade UI Kit, old values for password fields are never re-set after validation.

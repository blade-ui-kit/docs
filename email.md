# Email

The `email` component offers an easy way to set up an email input field for your forms. By simply setting its `name` attribute it also automatically defines your `id` and makes sure old values are respected.

## Installation

The `email` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{version}/installation) and you're good to go.

## Basic Usage

The most basic usage of the component exists in referencing it:

```html
<x-email />
```

This will output the following HTML:

```html
<input name="email" type="email" id="email" />
```

By default an `email` type will be set for the input field as well as an `id` that allows it to be easily referenced by a `label` element.

Of course, you can also specifically set a `name` attribute:

```html
<x-email name="email_address" class="p-4" />
```

This will output the following HTML:

```html
<input name="email_address" type="email" id="email_address" class="p-4" />
```

### Old Values

The `email` component also supports old values that were set. For example, you might want to apply some validation in the backend and make sure the user doesn't loses their input data when you show them the form anew with the validation errors. When re-rendering the form, the `email` component will remember the old value:

```html
<input name="email" type="email" id="email" value="john@example.com" />
```

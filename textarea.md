# Textarea

The `textarea` component offers an easy way to set up a textarea field for your forms. By simply setting its `name` attribute it also automatically defines your `id` and makes sure old values are respected.

## Installation

The `textarea` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the component is to set a `name` attribute:

```html
<x-textarea name="about"/>
```

This will output the following HTML:

```html
<textarea name="about" id="about" rows="3"></textarea>
```

By default a `rows` attribute will be set for the textarea field as well as an `id` that allows it to be easily referenced by a `label` element. Of course, you can overwrite all of these values as well as set a default value:

Of course, you can also specifically set a `rows` attribute, overwrite the `id` attribute and specifically set a default value:

```html
<x-textarea name="about">My about text</x-textarea>
```

This will output the following HTML:

```html
<textarea name="about" id="about" rows="3">About me text</textarea>
```

### Old Values

The `textarea` component also supports old values that were set.For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `textarea` component will remember the old value:

```html
<textarea name="about" id="about" rows="3">About me text</textarea>
```

# Trix

The `trix` component allows you to easily include a rich text editor in your form. Behind the scenes it makes use of [the Trix library](https://trix-editor.org) from [Basecamp](https://basecamp.com). The input is passed through to a form as a normal textarea input.

## Installation

While the `trix` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Trix](https://github.com/basecamp/trix) `^1.2`

## Basic Usage

In its most basic usage, you use it as a self closing component and pass it a name:

```html
<x-trix name="about" />
```

This will output the following HTML:

```html
<div>
    <input name="about" id="about" value="" type="hidden">
    <trix-editor input="about" class="trix-content"></trix-editor>
</div>
```

Which will render the Trix editor. Of course, you can also specifically set a default value:

```html
<x-trix name="about">My about text</x-trix>
```

This will output the following HTML:

```html
<div>
    <input name="about" id="about" value="My about text" type="hidden">
    <trix-editor input="about" class="trix-content"></trix-editor>
</div>
```

### Old Values

The `trix` component also supports old values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `trix` component will remember the old value:

```html
<div>
    <input name="about" id="about" value="About me text" type="hidden">
    <trix-editor input="about" class="trix-content"></trix-editor>
</div>
```

## Styling

You can use the `trix-content` class to style the content. To change this class use the `trix-class` attribute:

```html
<x-trix name="about" trix-class="trix-styles" />
```

This will output the following HTML:

```html
<div>
    <input name="about" id="about" value="" type="hidden">
    <trix-editor input="about" class="trix-styles"></trix-editor>
</div>
```

## Custom Attributes

Any custom attributes will be placed on the encapsulating `div` element:

```html
<x-trix name="about" class="border border-gray-500" />
```

This will output the following HTML:

```html
<div class="border border-gray-500">
    <input name="about" id="about" value="" type="hidden">
    <trix-editor input="about" class="trix-content"></trix-editor>
</div>
```

The reason for this is that the Trix editor places its own classes, etc., on the editor itself so any attributes you place on it will get stripped out.

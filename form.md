# Form

## Introduction

The `form` component helps you with removing the bulk work when setting up forms in Laravel. By default, it sets the HTTP method and CSRF directives and allows for an easier to use syntax than the default HTML form tag.

## Installation

The `form` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the `form` component exists in encapsulating some form elements and setting an `action` attribute:

```html
<x-form action="http://example.com">
    Form fields...
</x-form>
```

This will output the following HTML:

```html
<form method="POST" action="http://example.com">
    <input type="hidden" name="_token" value="...">
    <input type="hidden" name="_method" value="POST">

    Form fields...
</form>
```

By default a `POST` HTTP method will be set. Of course, you can customize this:

```html
<x-form method="PUT" action="http://example.com">
    Form fields...
</x-form>
```

This will output the following HTML:

```html
<form method="POST" action="http://example.com">
    <input type="hidden" name="_token" value="...">
    <input type="hidden" name="_method" value="PUT">

    Form fields...
</form>
```

As you can see only the `_method` input was updated since by default, HTML form tags only support `POST` requests. Laravel uses the `_method` key to determine which exact route is called.

## File Uploads

To enable file uploads in a form you can make use of the `has-files` attribute:

```html
<x-form action="http://example.com" has-files>
    Form fields...
</x-form>
```

This will output the following HTML:

```html
<form method="POST" action="http://example.com" enctype="multipart/form-data">
    <input type="hidden" name="_token" value="...">
    <input type="hidden" name="_method" value="POST">

    Form fields...
</form>
```

Now `file` input fields will be able to be submitted with the form.

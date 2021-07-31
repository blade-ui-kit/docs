# Checkbox

The `checkbox` component offers an easy way to set up a checkbox input field. By simply setting its `name` attribute it also automatically defines your `id` and makes sure old values are respected.

## Installation

The `checkbox` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the component is to set the `name` attribute:

```html
<x-checkbox name="remember_me"/>
```

This will output the following HTML:

```html
<input name="remember_me" type="checkbox" id="remember_me" />
```

### Old Values

The `checkbox` component also supports checked values that were set. For example, you might want to apply some validation in the backend, but also make sure the user doesn't lose their input data when you re-render the form with any validation errors. When re-rendering the form, the `checkbox` component will remember the checked value:

```html
<input name="remember_me" type="checkbox" id="remember_me" value="1" checked />
```

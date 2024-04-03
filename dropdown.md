# Dropdown

The `dropdown` component integrates with [Alpine.js](https://github.com/alpinejs/alpine) to provide you with a seamless way to integrate a dropdown menu in your app.

## Installation

While the `dropdown` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`

## Basic Usage

In its most basic usage, you use it by defining some links and a trigger button:

```html
<x-dropdown class="text-gray-500">
    <x-slot name="trigger">
        <button>Dries</button>
    </x-slot>

    <a href="#">Profile</a>
    <a href="#">Settings</a>
    <a href="#">Logout</a>
</x-dropdown>
```

This will output the following HTML:

```html
<div x-data="{ open: false }" @click.away="open = false" class="text-gray-500">
    <div @click="open = ! open">
        <button>Dries</button>
    </div>

    <div x-show="open">
        <a href="#">Profile</a>
        <a href="#">Settings</a>
        <a href="#">Logout</a>
    </div>
</div>
```

As you can see, the Alpine.js toggles are applied the surrounding `div` elements. This saves you from having to re-apply these attributes all the time. 

One nice use case for this is [the navbars from Tailwind UI](https://tailwindui.com/components/application-ui/navigation/navbars).

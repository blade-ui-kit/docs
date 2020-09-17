# Banner

The `banner` component integrates with [Alpine.js](https://github.com/alpinejs/alpine) to provide you with a seamless way to integrate a banner in your app.

## Installation

While the `banner` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^2.3`

## Basic Usage

In its most basic usage, the `banner` component requires defining a message and a trigger button:

```html
<x-banner class="flex">
    <p>Welcome to my website!</p>

    <slot name="trigger">
        <button type="button">Dismiss</button>
    </slot>
</x-banner>
```

This will output the following HTML:

```html
<div x-data="{ dismiss: false }" x-show="dismiss === false && sessionStorage.getItem('blade-ui-kit-banner-dismiss') !== '1'" class="flex">
    <p>Welcome to my website!</p>

    <div @click="dismiss = true; sessionStorage.setItem('blade-ui-kit-banner-dismiss', '1')" aria-label="Dismiss">
        <button type="button">Dismiss</button>
    </div>
</div>
```

As you can see, the Alpine.js dismiss button gets wrapped between `div` elements. This saves you from having to re-apply these attributes all the time. 
Plus, we use the [window.SessionStorage JS API](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage) to not show the banner in new page loads during the same session.

## Advanced Usage

### Session Storage Name
You can choose which key's name to use with SessionStorage to avoid duplication. Here's an example:
```html
<x-banner class="flex" session-storage-name="my-dismissible-banner">
    <p>Welcome to my website!</p>

    <slot name="trigger">
        <button type="button">Dismiss</button>
    </slot>
</x-banner>
```

This will output the following HTML:

```html
<div x-data="{ dismiss: false }" x-show="dismiss === false && sessionStorage.getItem('my-dismissible-banner') !== '1'" class="flex">
    <p>Welcome to my website!</p>

    <div @click="dismiss = true; sessionStorage.setItem('my-dismissible-banner', '1')" aria-label="Dismiss">
        <button type="button">Dismiss</button>
    </div>
</div>
```

### Trigger class
You can specify a class for the trigger slot. Here's an example:
```html
<x-banner class="flex" trigger-class="w-12">
    <p>Welcome to my website!</p>

    <slot name="trigger">
        <button type="button">Dismiss</button>
    </slot>
</x-banner>
```

This will output the following HTML:

```html
<div x-data="{ dismiss: false }" x-show="dismiss === false && sessionStorage.getItem('blade-ui-kit-banner-dismiss') !== '1'" class="flex">
    <p>Welcome to my website!</p>

    <div class="w-12" @click="dismiss = true; sessionStorage.setItem('blade-ui-kit-banner-dismiss', '1')" aria-label="Dismiss">
        <button type="button">Dismiss</button>
    </div>
</div>
```

An interesting use case for this component are [Tailwind UI banners](https://tailwindui.com/components/marketing/elements/banners).

# Cron

The `cron` component is a nice little convenience component that provides a way to make cron expressions human readable. It makes use of the [CRON Translator](https://github.com/lorisleiva/cron-translator) behind the hood.

## Installation

The `cron` component requires you to install the [CRON Translator](https://github.com/lorisleiva/cron-translator) library:

```bash
composer require lorisleiva/cron-translator:^0.1
```

## Basic Usage

The usage of the `cron` component is pretty simple. Just pass a cron expression to the self-closing component:

```html
<x-cron schedule="@weekly"/>
```

This will output the following HTML:

```html
<span title="Every Sunday at 12:00am">
    @weekly
</span>
```

What this does is allows your users to see the human readable value when they hover over the expression.

## Human Readable

The component also features a `human` boolean attribute that you can set to inverse the behavior of the title:

```html
<x-cron schedule="@weekly" human />
```

This will output the following HTML:

```html
<span title="@weekly">
    Every Sunday at 12:00am
</span>
```

As you can see, we display the human readable value and show the cron expression when you hover over it.

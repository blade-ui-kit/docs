# Countdown

The `countdown` component provides you with an easy way to display a countdown timer on your site. It makes use of JavaScript and [Alpine.js](https://github.com/alpinejs/alpine) to do the countdown. You can provide any `DateTimeInterface` object to start the countdown.

## Installation

While the `countdown` component works out-of-the-box when you've [set the directives](/docs/{{version}}/installation#directives), we recommend that you install and compile its JavaScript libraries before you deploy to production:

- [Alpine.js](https://github.com/alpinejs/alpine) `^3.0`

## Basic Usage

In its most basic usage, you use it as a self closing component and pass it a `DateTimeInterface` instance through its `expires` attribute:

```html
<x-countdown :expires="$date"/>
```

This will output the following *(inline JS has been omitted)*:

```html
00 : 00 : 00 : 00
```

## Composing The Content

You can define how the component is rendered by using its slot. Say you don't want the `:` syntax but display text labels:

```html
<x-countdown :expires="$date">
    <span x-text="timer.days">{{ $component->days() }}</span> days
    <span x-text="timer.hours">{{ $component->hours() }}</span> hours
    <span x-text="timer.minutes">{{ $component->minutes() }}</span> minutes
    <span x-text="timer.seconds">{{ $component->seconds() }}</span> seconds
</x-countdown>
```

This will output the following *(inline JS has been omitted)*:

```html
00 days 00 hours 00 minutes 00 seconds
```

As you can see we're making use of the component's methods to output the initial state of the countdown. We then make use of Alpine's `x-text` attribute to apply the calculated state depending on the current point in time. 

Using the component's slot allows you to go pretty wild with customizing the look and feel. Take a look at [its usage in Blade UI Kit's example app](https://github.com/blade-ui-kit/blade-ui-kit-example/blob/main/resources/views/home.blade.php#L8-L33).

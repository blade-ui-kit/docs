# Money

The `money` component is a conveniant way to handle presenting monetary values in your application. You can consider it a thin, Blade-specific wrapper around [Laravel's `Number::currency` helper](https://laravel.com/docs/11.x/helpers#method-number-currency).

## Installation

The `money` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic usage

In order to render a monetary value, just wrap the raw value in the `money` component:

```
<x-money>150</x-money>
```

This will output the following HTML:

```
<span>$150.00</span>
```

## Currency

You can customize the currency that is used to render the value via the `currency` property.

```
<x-money currency="EUR">149.99</x-money>
```

This will output the following HTML:

```
<span>€149.99</span>
```

## Locale

By default, the `money` component renders the monetary value using the locale you've specified in your `app.locale` configuration option. If you wish to render the value in a different locale, you can use the `locale` property.

```
<x-money locale="nl">150</x-money>
```

This will output the following HTML:

```
<span>US$ 150,00</span>
```

## Combining properties

Of course, the `currency` and `locale` properties can be used in conjunction:

```
<x-money currency="SEK" locale="sv">150</x-money>
```

This will output the following HTML:

```
<span>150,00 kr</span>
```

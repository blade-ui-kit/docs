# Avatar

The `avatar` component provides an easy way to show an avatar of a user. It makes use of [unavatar](https://unavatar.now.sh) behind the scenes to retrieve an image from different social providers. 

## Installation

The `avatar` component comes ready out-of-the-box with Blade UI Kit. Simply [install the package](/docs/{{version}}/installation) and you're good to go.

## Basic Usage

The most basic usage of the `avatar` component is as a self-closing component. Search for an identifier like a username, email or domain:

```html
<x-avatar search="johndoe" />
```

This will output the following HTML:

```html
<img src="https://unavatar.now.sh/johndoe" />
```

This will trigger unavatar to search an image across different providers for the given search request. It will *always* render an image. 

## Choosing Providers

You can choose a specific provider by using the `provider` attribute:

```html
<x-avatar search="john@example.com" provider="gravatar" />
```

This will output the following HTML:

```html
<img src="https://unavatar.now.sh/gravatar/john@example.com" />
```

And this will force unavatar to search only Gravatar images.

## Fallbacks

If you'd like to provide a fallback image when no matche is found for a given search result, you can use the `fallback` attribute:

```html
<x-avatar search="johndoe" fallback="https://example.com/image.png" />
```

This will output the following HTML:

```html
<img src="https://unavatar.now.sh/johndoe?fallback=https%3A%2F%2Fexample.com%2Fimage.png" />
```

## User Uploaded Images

The `avatar` component also allows you to pass a user-uploaded image through the `src` attribute that will take precedence over the search query:

```html
<x-avatar search="johndoe" src="https://example.com/image.png" />
```

This will output the following HTML:

```html
<img src="https://example.com/image.png" />
```

If no user uploaded image is passed, the search query is executed:

```html
<x-avatar search="johndoe" :src="$image = ''" />
```

This will output the following HTML:

```html
<img src="https://unavatar.now.sh/johndoe" />
```

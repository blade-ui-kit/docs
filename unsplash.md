# Unsplash

The `unsplash` component allows you to render images from [Unsplash](https://unsplash.com). You can render specific photos or search for random ones based on a search query.

## Installation

The `unsplash` component requires you to set up a Unsplash access key. Add the new config option in your `services.php` config file:

```bash
return [
    ...
    'unsplash' => [
        'access_key' => env('UNSPLASH_ACCESS_KEY')
    ],
];
```

Get your Unsplash access key from the [developer dashboard](https://unsplash.com/developers) after creating an app with them. Then set it in your `.env` file:

```
UNSPLASH_ACCESS_KEY=<your access key>
```

## Basic Usage

The most basic usage of the `unsplash` component is to reference a photo by its ID through a `photo` attribute: 

```html
<x-unsplash photo="t9Td0zfDTwI" />
```

This will output the following HTML:

```html
<img src="https://images.unsplash.com/photo/..." />
```

As you can see the identifier has been converted to an Unsplash URL, which is retrieved via API by this component.

## Caching

You might think making API requests to Unsplash is pretty expensive every time the UI is reloaded (and it definitely is). That's why the request will stay cached for a default of one hour. Obviously you'll need to [enable a cache driver](https://laravel.com/docs/cache) for this.

To manipulate the TTL (time to live) for this cache, you can pass a `ttl` attribute to the component:

```html
<x-unsplash photo="t9Td0zfDTwI" ttl="86400" />
```

In this example the image would be image cached for an entire day (86400 seconds).

## Randomize

You can randomize photos by providing a search query instead of referencing a specific photo:

```html
<x-unsplash query="forest" />
```

This will retrieve a random forest picture. Obviously in combination with [default caching](#caching) this will be cached for an hour. To make change this we can lower the `ttl`:

```html
<x-unsplash query="forest" ttl="300" />
```

And now our image will be randomized every five minutes.

## Username

You can limit randomized photos to only photos from a specific Unsplash user by passing their username:

```html
<x-unsplash username="johndoe" />
```

This can be combined with a search query:

```html
<x-unsplash query="wedding" username="johndoe" />
```

## Featured

You can limit randomized photos to only featured Unsplash photos by passing the `featured` attribute:

```html
<x-unsplash featured />
```

This can be combined with a search query:

```html
<x-unsplash query="sunset" featured />
```

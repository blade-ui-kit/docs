# Introduction

Blade UI Kit is a set of renderless components to utilise in your Laravel Blade views. In all essence, it's a collection of useful utilities, connecting the dots between different parts of [the TALL stack](https://tallstack.dev). 

It was made for [Blade](https://laravel.com/docs/blade), Laravel's powerful templating engine. Every Blade UI Kit component is a Blade component with a view and a class. Each component can be [extended, modified and overwritten](/docs/{{version}}/customization).

The components are renderless, meaning they ship without any styling applied to them. This puts you in full control of how their look and feel. 

To give you a practical introduction example, let's look at the way how Blade UI Kit's [`alert` component](/docs/{{version}}/alert) replaces [Laravel's default alert snippet from its UI scaffolding](https://github.com/laravel/ui/blob/fb1404f04ece6eee128e3fb750d3a1e064238b33/src/Auth/bootstrap-stubs/home.stub#L11-L15):

```html
@if (session('status'))
    <div class="alert alert-success" role="alert">
        {{ session('status') }}
    </div>
@endif
```

This is turned into this:

```html
<x-alert class="alert alert-success"/>
```

As you can see, all the implementation details about the behavior of the component are hidden away. Making it up to you do decided how to style it.

All of Blade UI Kit's components were designed with this in mind. Letting you worry less about implementation details and allowing you to focus on what truly matters: *building your app*. All the while providing a great developer experience.

## Composition

Blade UI Kit was designed with composition in mind. Meaning that we encourage to wrap Blade UI Kit's components within your own Blade view components when setting defaults like styling. Let's dive into a practical example built in Laravel 8. 

Take our [form `input` component](/docs/{{version}}/input) for example. You probably want to apply some default styling to it so it can be re-used throughout your app. Let's style it by making use of [Tailwind CSS](https://tailwindcss.com). We're gonna create an anonymous Blade component called `input` which resides in a `resources/views/components/forms` directory:

```html
<x-input {{ $attributes->merge(['class' => 'p-4 text-gray-700']) }} />
```

As you can see we're referencing Blade UI Kit's component inside your own `forms.input` component. By doing so we retain all the power of the Blade UI Kit component while making sure the component has the look and feel which is right for your app.

Of course, sometimes when wrapping components in similar named components, naming collisions may occur. Luckily we provide a way to [prefix our components](/docs/{{version}}/installation#prefixing) to prevent that from happening.

### Piping Attributes

It is important to know that the above example was written in Laravel 8. Laravel 8 allows for the ability to pipe attributes onto another component. Meaning that if you applied something like an `id` attribute onto the place where the component's used in a view, it will get piped through onto the Blade UI Kit component by using the `{{ $attributes }}` syntax. 

This isn't available in Laravel 7 unfortunately as this was a breaking change back then so it was decided to introduce it only in Laravel 8. **If you're using Laravel 7 you'll have to manually pipe through all attributes** that you want to pass on:

```html
<x-input
    :id="$id ?? null"
    :class="($class ?? '') . ' p-4 bg-white text-gray-700'"
/>
```

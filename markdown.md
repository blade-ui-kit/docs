# Markdown

The `markdown` component does exactly what you expect it to do. It'll generate any markdown you pass into HTML. Furthermore, it can handle Github Flavored Markdown and generate anchor tags for titles. 

> FYI: every page in these docs is generated with this component.

## Installation

The `markdown` component requires you to install the [CommonMark](https://github.com/thephpleague/commonmark) library:

```bash
composer require league/commonmark:^1.4
```

## Basic Usage

In its most basic usage, you use it to render some Markdown:

```html
<x-markdown>
# Hello World

Blade UI components are **awesome**.
</x-markdown>
```

Or pass in the above Markdown as a string variable:

```html
<x-markdown>{!! $markdown !!}</x-markdown>
```

This will output the following HTML:

```html
<div>
    <h1>Hello World</h1>

    <p>Blade UI components are <strong>awesome</strong>.</p>
</div>
```

## Github Flavored Markdown

Github Flavored Markdown can be enabled by passing the `github` boolean attribute:

```html
<x-markdown flavor="github">
Blade UI components are ~~cool~~, **awesome**.
</x-markdown>
```

This will output the following HTML:

```html
<div>
    <p>Blade UI components are <del>cool</del>, <strong>awesome</strong>.</p>
</div>
```

## Passing Options

You can also pass options to Commonmark with the `options` attribute. This requires you to pass a PHP array with scalar values. Below is an example where we disable underscores:

```html
<x-markdown
    name="about"
    :options="['use_underscore' => false]"
>{!! $markdown !!}</x-markdown>
```

For a full reference of all options, please consult [the Commonmark documentation](https://commonmark.thephpleague.com/1.5/configuration/).

## Anchors

One neat feature of the `markdown` component is that you can generate anchor links for your title tags. Take the following code snippet for example:

```html
<x-markdown anchors>
# Hello World

Blade UI components are *awesome*.

## Foo Title

Some content.

### Baz Title

Other content.
</x-markdown>
```

This will output the following HTML:

```html
<div>
    <h1>Hello World</h1>

    <p>Blade UI components are <em>awesome</em>.</p>

    <p><a class="anchor" name="foo-title"></a></p>
    <h2>Foo Title </h2>

    <p>Some content.</p>

    <p><a class="anchor" name="baz-title"></a></p>
    <h3>Baz Title</h3>

    <p>Other content.</p>
</div>
```

As you can see all `h` elements from levels 2 until 6 will get anchor tags. We don't generate one for the first level since there's usually only one h1 on a page's content.

This feature can be used together with [the `toc` component](/docs/{{version}}/toc) which generates the "on this page" navigation on for these docs.

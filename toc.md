# Table of Contents

The `toc` component can generate a table of contents based on Markdown input. The "on this page" navigation for these docs are generated with this component based on the headers from the current page.

## Installation

The `toc` component requires you to install the [CommonMark](https://github.com/thephpleague/commonmark) library:

```bash
composer require league/commonmark:^1.4
```

## Basic Usage

In its most basic usage, you use it to render an unordered list:

```html
<x-toc>
# Hello World

Blade UI components are **awesome**.

## Sub Title level 2

Some content.

### Sub Sub Title level 3

#### Sub Sub Title level 4

Some content.

## Other Sub Title level 2

Some content.
</x-toc>
```

Or pass in the above Markdown as a string variable:

```html
<x-toc>{!! $markdown !!}</x-toc>
```

This will output the following HTML:

```html
<ul>
    <li>
        <a href="#sub-title-level-2">
            Sub Title level 2
        </a>
    
        <ul>
            <li>
                <a href="#sub-sub-title-level-3">
                    Sub Sub Title level 3
                </a>
            </li>
        </ul>
    </li>
    <li>
        <a href="#other-sub-title-level-2">
            Other Sub Title level 2
        </a>
    </li>
</ul>
```

As you can see we generate a table of contents for level 2 & 3 headers. This component can be combined with [the `anchors` feature from the `markdown` component](/docs/{{version}}/markdown#anchors).

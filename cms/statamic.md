# Statamic

[https://statamic.com/](https://statamic.com/)

## What is Statamic?
`Statamic` is a modern, flexible `Content Management System (CMS)` built on the `Laravel` `PHP` framework. Unlike `WordPress` and traditional other CMS platforms, `Statamic` can run as a flat-file `CMS` using `Markdown` and `YAML` files. The CMS can be extended to use traditional databases, like `MySQL` or `PostgreSQL`, or function as a static site generator and headless CMS, if required.

`Statamic` is flat-file by default meaning data, such as content, users, and settings, are stored directly in plain `Markdown` or `YAML` files. This removes the overhead of having a database, improves speed and enables `Git` version control.

As it stands, `Statamic 6` currently requires `PHP 8.3` or newer for a fresh installation.

## Installation
The recommended way to install `Statamic` on `macOS` or `Windows` is to use `Laravel Herd`. This installs `PHP`, `Composer` and a local web server automatically without the need for complex configuration.

## Control Panel
The control panel is a `Vue-powered` dashboard for content teams with live preview and over 40 built-in fieldtypes.

## Templates
In `Statamic` templating is handled by `Antlers`, a built-in `Laravel` optimised template engine specifically designed for `CMS` data. This is the native default within `Statamic`, although the CMS can be setup to be headless using front-end components built in `Vue` or `React`.

The frontend design is separated into three logical layers: `Layouts`, `Templates`, and `Partials`.

## Components
The components within a `Statamic` project will be found in the project folder here: `resources/views/partials`. There are two main ways to build a component:

- `Antlers Partial` - a reusable frontend component, such as a button, card, hero, or navigation.
- `Replicator Set` - a component that content editors can add, edit, and reorder through the Statamic Control Panel.

A component usually has the file extension of: `.antlers.html`.

### Create a Component
Begin by creating a new component file inside of `resources/views/components`:

```
resources/
└── views/
    ├── components/
    │   ├── _hero.antlers.html
    │   ├── _button.antlers.html
    │   ├── _card.antlers.html
    │   └── _testimonial.antlers.html
    ├── layouts/
    │   └── layout.antlers.html
    ├── partials/
    │   ├── _header.antlers.html
    │   └── _footer.antlers.html
    └── page.antlers.html
```

Inside of the component file, `example_component.antlers.html`, write the component. Here is an example `_hero.antlers.html` component:

```html
<section class="bg-gray-100 py-20">
    <div class="container mx-auto">
        <h1 class="text-4xl font-bold">
            {{ heading }}
        </h1>

        <p class="mt-4 text-lg">
            {{ description }}
        </p>

        {{ if button_url && button_text }}
            <a href="{{ button_url }}"
               class="inline-block mt-6 bg-blue-600 text-white px-6 py-3 rounded">
                {{ button_text }}
            </a>
        {{ /if }}
    </div>
</section>
```

This checks both button fields before rendering.

Open a page template to render the component, such as: `resources/views/page.antlers.html`, and add:

```html
{{ partial:components/hero
    heading="Welcome to our website"
    description="We build amazing digital experiences."
    button_text="Get Started"
    button_url="/contact"
}}
```

`Statamic` automatically loads the partial and passes the values into it. This component is not editable in the `Statamic Control Panel`. To allow the component content to be added from within the `Statamic Control Panel`, just like how a `CMS` works, we can use a `YAML Blueprint`. In our component, this will be named: `hero.yaml` and the file should be placed here: `resources/fieldsets/hero.yaml`. This file should contain the fields for the content:

```yaml

title: Hero

fields:
  -
    handle: heading
    field:
      type: text
      display: Heading
      validate:
        - required

  -
    handle: description
    field:
      type: textarea
      display: Description

  -
    handle: button_text
    field:
      type: text
      display: Button Text

  -
    handle: button_url
    field:
      type: link
      display: Button URL
```

Then import it into your page's existing `Blueprint`, for example: `resources/blueprints/collections/pages/page.yaml`

```yaml
-
  import: hero
```

This makes the four fields available when editing pages that use that Blueprint.

## Tailwind CSS
`Tailwind CSS` is the preferred, industry-standard styling framework used by `Statamic`. The backend control panel itself is styled entirely with `Tailwind CSS` and built using `Vue`. Almost all of the official `Statamic Starter Kits` come with `Tailwind` pre-configured out of the box.

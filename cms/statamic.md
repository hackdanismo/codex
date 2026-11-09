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
The components within a `Statamic` project will be found in the project folder here: `resources/views/partials`.

## Tailwind CSS
`Tailwind CSS` is the preferred, industry-standard styling framework used by `Statamic`. The backend control panel itself is styled entirely with `Tailwind CSS` and built using `Vue`. Almost all of the official `Statamic Starter Kits` come with `Tailwind` pre-configured out of the box.

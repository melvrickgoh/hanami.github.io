---
title: "Lotus - Guides - Command Line: Generators"
---

# Command Line

## Generators

Lotus has convenient code generators to speed up our development process.

### Applications

With the Container architecture, we can have multiple Lotus applications running under `apps/`.
The default application is called `Web` and lives under `apps/web`.

We can generate new applications for different compontents that we want to add to our project.

```shell
% bundle exec lotus generate app admin
```

It generates `Admin` application under `apps/web`.

### Actions

We can generate an action, the corresponding view, template, route and test code with one command.

```shell
% bundle exec lotus generate action web books#show
```

The first argument `web`, is the name of the target application in Container arch.
**It must be omitted if used with Application arch:**


```shell
% bundle exec lotus generate action books#show
```

The argument `books#show` is the name of the controller and the action, respectively.

#### Route

The generated route, is named after the controller name.

```ruby
# apps/web/config/routes.rb
get '/books', to: 'books#show'
```

If we want to customize it, without editing our routes file, we can specify a `--url` argument.

```shell
% bundle exec lotus generate action web books#show --url=/books/:id
```

This will generate the following route:

```ruby
# apps/web/config/routes.rb
get '/books/:id', to: 'books#show'
```

### Migrations

We can generate a migration.

```shell
% bundle exec lotus generate migration create_books
```

It generates an empty migration with the UTC timestamp and the name we have specified: `db/migrations/20150621181347_create_books.rb`.
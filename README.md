# Easy Events - CS50W Capstone Project

## Introduction

Easy Events is a simple event organization platform that allows event organizers to set up events and participants to join those.

The organizers create and manage their events through an SPA written in Typescript using [Sveltekit](https://kit.svelte.dev/) and [Carbon Design System](https://carbondesignsystem.com/developing/frameworks/svelte/) as it's UI framework.

The participants use a simple Django based interface designed with [Tailwind CSS](https://tailwindcss.com/) using [Django Tailwind](https://github.com/timonweb/django-tailwind).

## Usage

The easiest way to run this project is to use Docker compose. Fill out a `.env` file with the following required variables (example values are for a simple local deployment):

```
API_HOST=http://localhost:8000
SPA_HOST=http://localhost:3000
DB_PASS=password1
DB_USER=user
```

and then run Docker compose:

```bash
docker compose up -d
```

On the first start, it is necessary to run the migrations:

```bash
docker compose exec api python manage.py migrate --noinput
```

You will also need a superuser to manage event organizers:

```bash
docker compose exec api python manage.py createsuperuser
```

After you have created a superuser, a `event_organizer` group must be created (users in this group are the only ones that can create events in the SPA)

Currently, users need to be added manually to the `event_organizer` group. This is to prevent random users from creating events. In the future, the app may be extended with a more automated approach.


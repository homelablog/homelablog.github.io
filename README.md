# Homelab Log

[Live site](https://homelablog.github.io)

## Running locally

Use Docker to avoid dealing with Ruby versions or native gems:

```bash
docker compose up site
```

Then open <http://localhost:4000>. Changes to content or layouts trigger a rebuild; the browser refreshes via LiveReload.

To stop: `Ctrl+C`.

## About

Notes about building and running an autonomous smart home. Built with Jekyll, custom design, hosted on GitHub Pages.

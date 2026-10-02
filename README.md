# TrekAhead — public site

The web pages for **TrekAhead**, an app for planning hut-to-hut walks in the
Alps and Pyrenees. Served by GitHub Pages at
<https://msoederhuizen.github.io/trekahead/>.

This repository holds the site and nothing else. The app's source is private.

| File | What it is |
|---|---|
| `index.html` | What the app does, and where its data comes from |
| `privacy.html` | The privacy policy. Apple requires this to be reachable before an app may be published. |
| `reset.html` | Where a password-reset email lands. Reads the recovery token from the URL fragment and sets the new password. |
| `confirmed.html` | Where an email-confirmation link lands. |
| `config.json` | Settings the installed app reads at launch — the routing server address, the support email, and an optional notice. |

## Why `config.json` matters

The app fetches it on every launch, so editing it here changes the behaviour of
**every installed copy**, including versions already on people's phones, without
an App Store release. It is the only lever that reaches a shipped build.

Which also means: if this repository is renamed, made private, or allowed to
stop serving, that lever is gone and the app keeps whatever it last read.

## The key in `reset.html`

`reset.html` contains a Supabase project URL and its **publishable** key. That
is public by design — the same key ships inside the app bundle, and it is an
identifier rather than a secret. Every rule that matters is enforced by
row-level security on the server. The secret key is not here and must never be.

## Hut data

Hut locations and details come from [OpenStreetMap](https://www.openstreetmap.org/copyright),
under the Open Database Licence.

# extension-linernotes

A Magritte extension which shows credits and background for the song, album and artist that's
playing, from MusicBrainz, Wikipedia and Last.fm

[![Test](https://github.com/magritte-project/extension-linernotes/actions/workflows/test.yml/badge.svg)](https://github.com/magritte-project/extension-linernotes/actions/workflows/test.yml)

## Installation

### For Developers

The Magritte project uses [`asdf`](https://asdf-vm.com/) to manage tooling. Follow the Getting
Started directions to install `asdf` on your machine. Once you've installed `asdf`, you can
bootstrap your development environment:

```sh
$ ./bootstrap
```

Bootstrapping the development environment creates a `.env` file. Edit the entries the `.env` file to
be suitable for your local working environment.

Once your development environment is bootstrapped and you've filled in `.env`, you can start the
extension server:

```sh
$ pnpm dev
```

After the extension server has started, you can import the extension into your local Magritte
instance:

- Sign in to an administrator account
- Click the **User** menu in the top right corner
- Select **Settings**
- Select **Manage Extensions** in the **Admin** section
- Click the **+ Import Extension** button
- Enter your the extension’s development server URL, `http://localhost:9295/`

After an extension has been imported, any user can install it from Settings → Extensions in the user
menu.

## Configuration

The Liner Notes extension reads its configuration from the environment, or from a `.env` file in the
current directory if one is present. These values are bundled into the extension at build time.

| Key                 | Type   | Required | Description                        |
| ------------------- | ------ | -------- | ---------------------------------- |
| VITE_LASTFM_API_KEY | string | No       | API key from a Last.fm API account |

API accounts can be created at <https://www.last.fm/api/account/create>. Without a key, Liner Notes
still shows what MusicBrainz and Wikipedia know, but leaves out Last.fm's bios, tags and listener
counts.

Because `VITE_` values are bundled into the extension, the API key is readable by anyone who can
load it.

## Deployment

This extension can be built for deployment by running `pnpm build`. This will produce a static site
under `dist/` which can be served by any web server.

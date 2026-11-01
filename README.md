# jeff007ali.github.io

The public download site for JeffLabs apps: https://jeff007ali.github.io

The apps' code lives in private repos. Only this page and the built files are public.

## How it works

- `main` holds the page (`index.html`, `icons/`, `images/`). Edit it here.
- `downloads` holds the newest file of each app plus `versions.json`. The apps' build workflows write
  it, always as a single commit, so old builds don't pile up in history. Don't edit it by hand.
- `.github/workflows/deploy.yml` combines the two and deploys to Pages. It runs on every push to
  `main`, and when an app's workflow sends a `downloads-updated` dispatch after publishing.

Files are served at `https://jeff007ali.github.io/downloads/<file>`, for example
`downloads/swing-and-shoot.apk`.

## One-time setup

1. Create the public repo `jeff007ali/jeff007ali.github.io` on GitHub, empty, and push this folder to
   its `main` branch.
2. *Settings → Pages → Build and deployment → Source*: **GitHub Actions**.
3. For each app repo: a fine-grained token with access to only this repo and *Contents: Read and
   write*, saved in the app repo as the `SITE_TOKEN` Actions secret.

## Adding an app

1. In the app's build workflow, copy the "Publish ... to the download site" step from
   `swing-and-shoot/.github/workflows/android-release.yml`, with its own `APP_ID` and file name.
2. Add a card for it in `index.html` (copy the existing `<article>`); `data-app` must match its
   `APP_ID`.

## Limits

GitHub Pages: 100 MB per file, about 1 GB per site, about 100 GB of traffic a month.

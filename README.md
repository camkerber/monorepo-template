# monorepo-template

This repo serves as a template for a frontend monorepo structure specifically for Vite + React applications deployed through GitHub Pages.

## GitHub Pages support

Included in this repo are a few pieces to support deploying through GitHub Pages. If you don't wish to use GitHub Pages, everything below can be safely removed.

### `deploy.yml`

Builds and deploys the app. It is required to create a branch based off your main branch named `gh-pages` in order for this to work correctly.

### `404.html` and `index.html`

These files contain scripts to support SPAs like React and their routing functionality to prevent 404s when navigating to your deployed site.

### `base` property in `vite.config.ts`

This prevents your deployed app from throwing a 404 when it tries to load your app's JavaScript bundle from the `assets` folder.

### Custom domains

If you wish to deploy to a custom domain, you will need to make the following changes (if you don't want the `repo-name` base path):

1. Change the `pathSegmentsToKeep` in the script in the `404.html` file to `0`
2. Remove the `base` property in `vite.config.ts`
3. Remove the top level `path` property in `AppRouter.tsx`
4. Create a `CNAME` file in the .github/workflows directory with you custom domain name (ex: `www.my-domain.com`)
5. Once the workflow completes after a new merge in main, you will need to go to **Settings > Pages** in GitHub and enter your domain in the **Custom domain** input. This will trigger a deploy to your actual custom domain rather than the `github.io` domain. GitHub is a little shy and needs a gentle nudge.

## website

This is the root of the app which will be built and deployed. This does not need to include the `App.tsx` or `AppRouter.tsx` files, it is just my personal preference.

## packages

These are your workspace packages which contain their own `package.json`, `tsconfig.json`, and `.eslintrc.cjs`. These packages can all be imported into any other package.

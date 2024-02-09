# Marmalade Headless Wordpress

## Requirements

- [php](https://www.php.net/manual/en/install.php) - Needed locally for linting

- [composer](https://getcomposer.org/download/) - Needed locally for linting

- [Local](https://localwp.com/) - For local wordpress development

## Initial Local Setup

See [INITIAL.md](./INITIAL.md)

## Development

Open Local and navigate to the Marmalade site under "Local sites".
Ensure the site is running.
If it is running, there with be a red "Stop site" in the upper right corner of the app.
If it is not running, click the green "Start site in the upper right corner.

Once the site is running, click on either the green "WP Admin" or "Open site" buttons.
They both do the same thing; they will open the Wordpress admin console in the browser.

Authenticate and enter the console.
Use the "GraphiQL IDE" to test queries.

### Git Flow

Create a new branch off of `develop`.

- Branches for new features should be named like `feature/cool_new_feature`.
- Branches for bug fixing should be named like `bugfix/pesky_bug`.
- Branches for oOther changes, like documentation, tooling, etc should be named with your initials, like `jmcr/docs`.

Make PRs to the `develop` branch.
Merging to `develop` will deploy the changes to staging.

Once merged to `develop` and develop is validated, a PR may be made from `develop` to `main`.

Merging to `main` will deploy the changes to prod.

### Linting

To lint the project, from within the wp-content folder, run

```sh
phpcs ./themes
```

To fix some linting issues automatically, right click on the open php file and select "Format Document".

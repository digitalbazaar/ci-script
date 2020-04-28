# ci-script

Script to help setup a repo with continuous integration support.

- Uses GitHub Actions.
- Actions configs for different setups.

## Usage

You may put the `setup-ci` script in your `PATH` or run it directly.

Run the following to setup CI support:

    setup-ci MODE

Where MODE is one of:

- `bedrock`
- `bedrock-web`
- `isomorphic`
- `lint`

## Lint

If you are using lint support:

    npm i -D eslint eslint-config-digitalbazaar
    # optional: eslint-plugin-jsdoc
    # optional: eslint-plugin-vue

Setup `.eslintrc.js`. See [eslint-config-digitalbazaar][] or other projects for
examples.

Add a `lint` script target in `package.json` something like:

    "lint": "eslint ."

If you are also linting `.vue` files, then use something like:

    "lint": "eslint \"**/*.{js,vue}\""

## Coverage

If you are using coverage support:

    npm i -D nyc

Add a `coverage-ci` script target in `package.json` something like:

    "coverage-ci": "cross-env NODE_ENV=test nyc --reporter=lcovonly npm run test-node",

Note the `lcovonly` reporter. The default setup will use `./coverage/lcov.info`.

Ensure `package.json` or nyc config is setup something like:

    "nyc": {
      "exclude": [
        "tests"
      ]
    }

[eslint-config-digitalbazaar]: https://github.com/digitalbazaar/eslint-config-digitalbazaar/

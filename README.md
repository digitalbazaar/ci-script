# ci-script

Script to help setup a repo with continuous integration support.

- Uses GitHub Actions.
- Actions configs for different setups.

## Usage

From your source dir, run:

    ../ci-script/setup-ci MODE

Where MODE is one of:

- bedrock
- bedrock-web
- isomorphic
- lint

## Lint

If you are using lint support:

    npm i -D eslint
    npm i -D eslint-config-digitalbazaar
    # optional: eslint-plugin-jsdoc
    # optional: eslint-plugin-vue
    # setup a .eslintrc.js

Add a `"script"` target something like:

    "lint": "eslint ."

## Coverage

If you are using coverage support:

    npm i -D nyc

Add a `"script"` target something like:

    "coverage-ci": "cross-env NODE_ENV=test nyc --reporter=lcovonly npm run test-node",

Note the `lcovonly` reporter. The default setup will use `./coverage/lcov.info`.

Ensure package.json or nyc config is setup something like:

    "nyc": {
      "exclude": [
        "tests"
      ],
      "reporter": [
        "html",
        "text-summary"
      ]
    }

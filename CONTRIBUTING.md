### Develop

Get started by running the app in development mode:

```bash
$ git clone https://github.com/stencila/desktop.git
$ cd desktop
$ npm install
$ npm start
```

### Release workflow

1. Try out the release before npm publishing using local npm installs.

    Have all projects (stencila, stencila-node, stencila-desktop) side by side.

    ```bash
    $ cd stencila
    $ npm install
    $ node make
    ```

    ```bash
    $ cd stencila-node
    $ npm install ../stencila
    ```

    ```bash
    $ cd stencila-desktop
    $ npm install ../stencila-node
    $ npm start
    ```

2. Do some testing and if it looks good we can publish the individual packages:

    Bump Stencila version in `package.json` and npm publish.

    ```bash
    $ cd stencila
    $ npm publish
    ```

    Update the Stencila dependency and bump version of stencila-node in `package.json` and npm publish.

    ```bash
    $ cd stencila-node
    $ npm publish
    ```

    Update the stencila-node dependency and bump version of stencila-desktop in `package.json`.

    Now make a release bundle for each platform (OSX, Linux, Windows)

    ```bash
    $ cd stencila-desktop
    $ rm -rf node_modules
    $ npm install
    $ npm run release
    ```

    Create a release on Github (using a new release tag) and upload the app packages for all platforms.


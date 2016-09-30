# npm Best Practices

## #0 Know your npm

### npm versions

To get the version of the npm cli you are actively using, you can do the following:

```sh
$ npm --version
2.13.2
```

npm can return a lot more than just its own version - it can return the version of the current package, the Node.js version you are using and OpenSSL or V8 versions:

```sh
$ npm version
{ bleak: '1.0.4',
  npm: '2.15.0',
  ares: '1.10.1-DEV',
  http_parser: '2.5.2',
  icu: '56.1',
  modules: '46',
  node: '4.4.2',
  openssl: '1.0.2g',
  uv: '1.8.0',
  v8: '4.5.103.35',
  zlib: '1.2.8' }
```

### npm help

As most cli toolkits, npm has a great built-in help functionality as well. Description and synopsis are always available. These are essentially [man-pages](https://www.kernel.org/doc/man-pages/).

```sh
$ npm help test
NAME
       npm-test - Test a package

SYNOPSIS
           npm test [-- <args>]

           aliases: t, tst

DESCRIPTION
       This runs a package's "test" script, if one was provided.

       To run tests as a condition of installation, set the npat config to true.
```

## #1 Start new projects with `npm init`

When starting a new project `npm init` can help you a lot by interactively creating a `package.json` file. This will prompt questions for example on the project's name or description. However, there is a quicker solution!

```sh
$ npm init --yes
```

If you use `npm init --yes`, it won't prompt for anything, just create a `package.json` with your defaults. To set these defaults, you can use the following commands:

```sh
npm config set init.author.name YOUR_NAME
npm config set init.author.email YOUR_EMAIL
```

## #2 Finding [npm packages](https://npms.io/)

## #3 Investigate npm packages

If you'd like to open the homepage of the module from the cli you can do:

```sh
$ npm home request
```

To check open issues or the publicly available roadmap (if there’s any), you can try this:

```sh
$ npm bugs request
```

Alternatively, if you'd just like to check a module's git repository, type this:

```sh
$ npm repo request
```

## #4 Saving dependencies

If you'd like to take that one step forward and automatically add it to your `package.json` file, you can do:

```sh
$ npm install request --save
```

npm will save your dependencies with the `^` prefix by default. It means that during the next `npm install` the latest module without a major version bump will be installed. To change this behaviour, you can:

```sh
$ npm config set save-prefix='~'
```

In case you'd like to save the exact version, you can try:

```sh
$ npm config set save-exact true
```

## #5 Lock down dependencies

Even if you save modules with exact version numbers as shown in the previous section, you should be aware that most npm module authors don't. It’s totally fine, they do it to get patches and features automatically.

The situation can easily become problematic for production deployments: __It’s possible to have different versions locally then on production__, if in the meantime someone just released a new version. The problem will arise, when this new version has some bug which will affect your production system.

To solve this issue, you may want to use `npm shrinkwrap`. It will generate an `npm-shrinkwrap.json` that contains not just the exact versions of the modules installed on your machine, but also the version of its dependencies, and so on. Once you have this file in place, `npm install` will use it to reproduce the same dependency tree.

## #6 Check for outdated dependencies

To check for outdated dependencies, npm comes with a built-in tool method the `npm outdated` command. You have to run in the project's directory which you'd like to check.

```sh
$ npm outdated
conventional-changelog    0.5.3   0.5.3   1.1.0  @risingstack/docker-node
eslint-config-standard    4.4.0   4.4.0   6.0.1  @risingstack/docker-node
eslint-plugin-standard    1.3.1   1.3.1   2.0.0  @risingstack/docker-node
rimraf                    2.5.1   2.5.1   2.5.4  @risingstack/docker-node
```

## #7 No `devDepenendencies` in production

To install production dependencies only, run this:

```sh
$ npm install --production
```

Alternatively, you can set the NODE_ENV environment variable to production:

```sh
$ NODE_ENV=production npm install
```

## #8 Secure your projects and tokens

In case of using npm with a logged in user, your npm token will be placed in the `.npmrc` file. As a lot of developers store dotfiles on GitHub, sometimes these tokens get published by accident. Currently, there are thousands of results when searching for the `.npmrc` file on GitHub, with a huge percentage containing tokens. __If you have dotfiles in your repositories, double check that your credentials are not pushed!__

Another source of possible security issues are the files which are published to npm by accident. By default npm respects the `.gitignore` file, and files matching those rules won't be published. However, if you add an `.npmignore` file, it will override the content of `.gitignore` - so they won't be merged.

## #9 Developing packages

When developing packages locally, you usually want to try them out with one of your projects before publish to npm. This is where `npm link` comes to the rescue.

What `npm link` does is that it creates a symlink in the global folder that links to the package where the `npm link` was executed.

You can run `npm link package-name` from another location, to create a symbolic link from the globally installed `package-name` to the `/node_modules` directory of the current folder.

Let's see it in action!

```sh
# create a symlink to the global folder
/projects/request $ npm link

# link request to the current node_modules
/projects/my-server $ npm link request

# after running this project, the require('request')
# will include the module from projects/request
```

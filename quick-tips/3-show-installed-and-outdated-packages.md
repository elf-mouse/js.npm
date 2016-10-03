## #3 Show Installed and Outdated Packages

### Installed Packages

You can leverage NPM’s functionality and list the installed packages for your project. The following command will print a list of installed packages and their dependencies:

```sh
npm ls
# or
npm list
```

If you’re just interested in the list of installed packages which you directly depend on, use the `--depth` option and pass `--depth=0`.

```sh
$ npm ls --depth=0
futurestudio-homepage@1.0.0 /Users/marcuspoehls/Dev/FutureStudio/homepage
├── bcrypt-as-promised@1.0.1
…
└── when@3.7.3
```

There is also an NPM command to print additional package information while listing the installed modules:

```sh
npm ll
# or
npm la
```

Both commands `npm ll` and `npm la` will print the same information which looks like this:

```sh
$ npm ll
futurestudio-homepage@2.0.1
│ /Users/marcuspoehls/Dev/FutureStudio/homepage
│ Future Studio homepage based on hapi, handlebars and Twitter bootstrap
│ https://futurestud.io/giturlto/homepage.git
│ https://futurestud.io
├── bcrypt-as-promised@1.0.1
│   A promisified bcrypt
│   git+ssh://git@github.com/iceddev/bcrypt-as-promised.git
│   https://github.com/iceddev/bcrypt-as-promised
…
└── when@3.7.3
    A lightweight Promises/A+ and when() implementation, plus other async goodies.
    git+https://github.com/cujojs/when.git
    http://cujojs.com
```

__Useful Options__

- `--json`: of type `boolean`, default value is `false` and possible values are `true|false`
- `--long`: of type `boolean`, default value is `false` and possible values are `true|false`
- `--depth`: of type `int` and possible value is `any positive number`

__Note__: There are also options to show only the production dependencies (`--prod=true`) or only the development dependencies (`--dev=true`). To be honest, we never restrict the list of installed packages to a given environment, since we’re interested in the list of all packages. You can find further information about the `--dev` and `--prod` options on [NPM’s documentation page for](https://docs.npmjs.com/cli/ls) `ls`.

### Outdated Packages

```sh
npm outdated
```

```sh
$ npm outdated
Package           Current  Wanted  Latest  Location
boom                2.7.2   2.7.2   2.9.0  futurestudio-homepage
handlebars          3.0.3   3.0.3   4.0.3  futurestudio-homepage
hapi                8.5.3   8.5.3  10.0.1  futurestudio-homepage
```

You can also use the `outdated` command for your globally installed packages:

```sh
npm outdated -g
```

You see, there are also three packages outdated on my machine.

```sh
$ npm outdated -g
Package            Current  Wanted  Latest  Location
npm-check-updates    2.2.0   2.2.3   2.2.3  lib
pm2                 0.14.7  0.15.5  0.15.5  lib
supervisor           0.7.1   0.8.0   0.8.0  lib
```

#### Options

```sh
$ npm outdated --long=true
Package           Current  Wanted  Latest  Location               Package Type
boom                2.7.2   2.7.2   2.9.0  futurestudio-homepage  dependencies
handlebars          3.0.3   3.0.3   4.0.3  futurestudio-homepage  dependencies
hapi                8.5.3   8.5.3  10.0.1  futurestudio-homepage  dependencies
```

__Useful Options__

- `--long`: of type `boolean`, default value is `false` and possible values are `true|false`
- `--depth`: of type `int` and possible value is `any positive number`

__Note__: There is also the option to print the list of outdated packages as JSON (`--json=true`). The complete overview of options is available on [NPM’s documentation page for](https://docs.npmjs.com/cli/outdated) `outdated`.

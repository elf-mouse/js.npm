## #2 Use Shortcuts to Install Packages

### Install Package

You can shortcut the install command by only using `i` instead of `install`:

```sh
npm i lodash
```

### Install Multiple Packages With One Command

```sh
npm i lodash hapi thinky when
```

### Install Package From Github Repository

```sh
npm i https://github.com/lodash/lodash.git
npm i lodash/lodash

npm i lodash/lodash#es
```

### Install Package and Save as Dependency

The `--save` flag shortcuts to `-S`:

```sh
npm i -S lodash
```

```sh
npm i -S lodash hapi thinky when
```

```json
"dependencies": {
    "hapi": "^9.0.3",
    "lodash": "^3.10.1",
    "thinky": "^2.1.6",
    "when": "^3.7.3"
}
```

### Install Package and Save as devDependency

The `--save-dev` flag shortcuts to `-D`:

```sh
npm i -D mocha istanbul
```

```json
"devDependencies": {
    "istanbul": "^0.3.18",
    "mocha": "^2.2.5"
}
```

### Install Global Packages

The `--global` flag shortcuts to `-g`:

```sh
npm i -g mocha
```

## #1. Install Packages

### Prerequisites

```sh
npm init
```

### Install Package

```sh
npm install lodash
```

### Install Multiple Packages With One Command

```sh
npm install lodash hapi thinky when
```

### Install Package From Github Repository

```sh
npm install https://github.com/lodash/lodash.git

# `username/repository`
npm install lodash/lodash

# `#branchname`
npm install https://github.com/lodash/lodash#es
```

### Install Package and Save as Dependency

```sh
npm install --save lodash
npm install --save lodash hapi thinky when
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

```sh
npm install --save-dev mocha
npm install --save-dev mocha istanbul
```

```json
"devDependencies": {
    "istanbul": "^0.3.18",
    "mocha": "^2.2.5"
}
```

### Install Global Packages

```sh
npm install --global mocha
```

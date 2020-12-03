Q: Resolving EACCES permissions errors when installing packages globally

A: `NPM_CONFIG_PREFIX=~/.npm-global`

Q: Mirrors for China

A:

```bash
# fix `node-sass scripts/install.js`
export SASS_BINARY_SITE=https://npm.taobao.org/mirrors/node-sass/

# fix `node-gyp-install`
export ELECTRON_MIRROR=https://npm.taobao.org/mirrors/electron/

# fix others
export FSEVENTS_BINARY_HOST_MIRROR=https://npm.taobao.org/mirrors/fsevents/
export SQLITE3_BINARY_SITE=https://npm.taobao.org/mirrors/sqlite3/
export phantomjs_cdnurl=https://npm.taobao.org/mirrors/phantomjs
```

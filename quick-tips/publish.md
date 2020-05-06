# `npm version` & `npm dist-tag`

```sh
npm publish # 1.0.0
```

```sh
git add -A && git commit -m "patch"
npm version patch
npm publish # 1.0.1
```

```sh
git add -A && git commit -m "minor"
npm version minor
npm publish # 1.1.0
```

```sh
git add -A && git commit -m "major"
npm version minor
npm publish # 2.0.0
```

---

```sh
npm info
```

```sh
npm dist-tag ls
```

```sh
npm dist-tag add pkg@version latest
npm dist-tag rm pkg@version beta
```

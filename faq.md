Q: `Installing ERROR | Unexpected end of JSON input while parsing near ' : '`

A:

1. 删掉 `package-lock.json`
2. 清除 cache
3. 进入 `npm-cache` 清除 cache
4. 不要用淘宝镜像

```sh
npm cache clean --force

# OR
npm cache verify
```

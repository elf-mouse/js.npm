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

---

Q: `self signed certificate`

A: On Node Package Manager you have two options: bypass or set a certificate file.

```sh
# Bypassing (risky!)
npm config set strict-ssl false --global

# Setting a certificate file
npm config set cafile /path/to/your/cert.pem
```

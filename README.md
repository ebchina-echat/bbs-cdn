# bbs-cdn
全球免费CDN库
## 发版注意

- 修改package.json文件的版本号
```js
// package.json
"version": "x.x.x", // 修改版本
```

```js
// vue.config.js
const fs = require("fs");
const json = JSON.parse(fs.readFileSync("package.json", "utf8"));
const version = json.version;
``
```
- vue 打包 publicPath = `https://cdn.jsdelivr.net/gh/ebchina-echat/bbs-cdn@${version}/dist/`
- 每次覆盖文件夹内容即可
- 提交文件前请注意release版本，版本号用当前打包时间戳,版本类似：1.1589961280414 
获取时间戳api：地址[http://api.m.taobao.com/rest/api3.do?api=mtop.common.getTimestamp](http://api.m.taobao.com/rest/api3.do?api=mtop.common.getTimestamp)

## 获取历史包

- https://cdn.jsdelivr.net/gh/ebchina-echat/bbs-cdn@1.2.0/dist/js/app.7950609e.js

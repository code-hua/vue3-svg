## vue3-svg

> vue3 操作外部svg文件
> 可以通知接口返回svg文件，进行响应的操作
> 该项目适用于大批量使用svg文件使用，以此来提高网站的加载速度

### use

```shell
npm install
# 运行
npm run serve
# 打包
npm run build
```

### 少量svg图片解决方案

- 采用缓存svg解决方案
- 接口返回svg代码，前端通过`v-html`指令进行渲染外部。


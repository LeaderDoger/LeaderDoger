## 运行
在项目被创建后，通过以下步骤安装依赖并启动开发服务器：
```
cd <your-project-name>
npm install
npm run dev
```
当你准备将应用发布到生产环境时，请运行：
`npm run build`
此命令会在 `./dist` 文件夹中为你的应用创建一个生产环境的构建版本。关于将应用上线生产环境的更多内容，请阅读[生产环境部署指南](https://cn.vuejs.org/guide/best-practices/production-deployment.html)。
#### 通过 CDN 使用 Vue[​](https://cn.vuejs.org/guide/quick-start.html#using-vue-from-cdn)

你可以借助 script 标签直接通过 CDN 来使用 Vue <br>
`<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>`


#### 启用 Import maps[​](https://cn.vuejs.org/guide/quick-start.html#enabling-import-maps)

在上面的示例中，我们使用了完整的 CDN URL 来导入，但在文档的其余部分中，你将看到如下代码：
`import { createApp } from 'vue'`

我们可以使用[导入映射表 (Import Maps)](https://caniuse.com/import-maps) 来告诉浏览器如何定位到导入的 `vue`：
```html
<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
    }
  }
</script>
```
## 基础

### 计算属性缓存 vs 方法
`<p>{{ calculateBooksMessage() }}</p>`

```js
// 组件中
function calculateBooksMessage() {
  return author.books.length > 0 ? 'Yes' : 'No'
}
```
不同之处在于**计算属性值会基于其响应式依赖被缓存**。一个计算属性仅会在其响应式依赖更新时才重新计算。这意味着只要 `author.books` 不改变，无论多少次访问 `publishedBooksMessage` 都会立即返回先前的计算结果，而不用重复执行 getter 函数。相比之下，方法调用**总是**会在重渲染发生时再次执行函数。










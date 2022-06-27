# my_test

## 业务逻辑

> 1.yarn add bootstrap 2.在 main.js 中引入 css 3.新建 MyFooter，MyHeader

-   页面级别的新建文件夹 views / pages
-   新建文件夹 utils
    -   配置 axios 并导出

新建了 Mytable 在 MyGoodsList 引入使用
发请求 --> MyTable 渲染

-   配置 axios --> request.js
-   导出 axios
-   import axios from '@/utils/request.js'

-   在 MyGoodsList 中 请求数据拿到数据 给到 MyTable
-   在 MyTable 中声明接受数据 并渲染数据

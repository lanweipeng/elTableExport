# el-table-export
配合Element-UI中的Table组件 导出text, json, csv, xls文件

### 安装 Installation

``` 
npm install el-table-export-lwp --save
```

or

``` 
yarn add el-table-export-lwp
```

### 参数 Arguments

| 参数 | 说明 | 类型 | 可选值 | 默认值 |
| ------ | ------ | ------ | ------ | ------ |
| fileName | 文件名 | String |  — |  export | 
| type | 输出格式 | String |  text / json / csv / xls / |  csv | 
| withBOM | 将BOM头元添加到CSV文件 | Boolean |  — |  false | 
| useFormatter | 输出数据时是否使用table中定义的formatter | Boolean |  — |  true | 

### 例子 DEMO

~~说什么不如上一个demo~~
[demo文件](demo.vue)

``` 
// 引用
import { elTableExport } from "el-table-export-lwp";

/* ⚠ 创建实例时需传入一个 table组件的Vue实例（必选）
 * 支持传入一个全局配置对象（非必选）
 */
let eteInstance = new elTableExport(
    this.$refs.elTable, //必填
    {
    fileName: "export-demo",
    type: "csv",
    withBOM: false,
    },, //必填
    allData, //选填
);
// 创建实例后使用 export() 方法执行导出功能
eteInstance.export().then((result) => {
    console.info('ok');
}).catch((err) => {
    console.info(err);
});
```

### 提示 Tips

* 根据依赖包中文档，注明了在Excel在读取UTF8 CSV文件时需要BOM头。
* table组件的Vue实例不是 `document.querySelector` 等获取的DOM实例，是 `ref` 指定的Vue实例。
* 如需分页,请给allData，不给表示只显示当前页

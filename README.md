# cz-example
cz工具集示例

## Commitizen

全局安装cz

``` javascript
npm install -g commitizen
```

### cz-conventional-changelog

如果想使用符合Angular规范提交说明的cz适配器

``` javascript
// npm
commitizen init cz-conventional-changelog --save --save-exact
// yarn
commitizen init cz-conventional-changelog --yarn --dev --exact
```

> 该命令执行`cz-conventional-changelog`依赖安装和在`pacakge.json`中配置`config.commitizen`适配器路径。

### cz-customizable

如果想定制说明，可以使用该cz适配器

``` javascript
npm install cz-customizable --save-dev
```

该适配器需要手动配置cz的适配器路径，在`pacakge.json`中

``` javascript
"config": {
  "commitizen": {
    "path": "node_modules/cz-customizable"
  }
}
```
新增`.cz-config`定制说明的配置文件（以下是一个汉化示例）：

``` javascript
'use strict';

module.exports = {

  types: [
    {value: '特性',     name: '特性:    一个新的特性'},
    {value: '修复',      name: '修复:    修复一个Bug'},
    {value: '文档',     name: '文档:    变更的只有文档'},
    {value: '格式',    name: '格式:    空格, 分号等格式修复'},
    {value: '重构', name: '重构:    代码重构，注意和特性、修复区分开'},
    {value: '性能',     name: '性能:    提升性能'},
    {value: '测试',     name: '测试:    添加一个测试'},
    {value: '工具',    name: '工具:    开发工具变动(构建、脚手架工具等)'},
    {value: '回滚',   name: '回滚:    代码回退'}
  ],

  scopes: [
    {name: '模块1'},
    {name: '模块2'},
    {name: '模块3'},
    {name: '模块4'}
  ],

  // it needs to match the value for field type. Eg.: 'fix'
  /*
  scopeOverrides: {
    fix: [
      {name: 'merge'},
      {name: 'style'},
      {name: 'e2eTest'},
      {name: 'unitTest'}
    ]
  },
  */
  // override the messages, defaults are as follows
  messages: {
    type: '选择一种你的提交类型:',
    scope: '选择一个scope (可选):',
    // used if allowCustomScopes is true
    customScope: 'Denote the SCOPE of this change:',
    subject: '短说明:\n',
    body: '长说明(可选)，使用"|"换行：\n',
    breaking: '非兼容性说明 (可选):\n',
    footer: '关联关闭的issue(可选)，例如：#31, #34:\n',
    confirmCommit: '确定**提交说明**?'
  },

  allowCustomScopes: true,
  allowBreakingChanges: ['feat', 'fix'],

  // limit subject length
  subjectLimit: 100

};
```

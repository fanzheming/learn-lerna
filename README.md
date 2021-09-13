# learn-lerna

`公司现在用 lerna 管理多模块项目，先学一下。`


# 使用
```bash
npm install -g lerna  全局安装
lerna init 初始化  -> 自动生成packages、lerna.json、package.json
```

在 package.json 中添加:
workspaces -> 使用yarn workspace把node_modules提到最顶层，其他packages中不会生成node_modules
publishConfig -> 如果你的包名是带scope的例如："name": "@zfan/learn-lerna",那需要添加

```json
"workspaces": [
    "packages/*"
  ],
"publishConfig": {
    "access": "public"
  },
```

在lerna.json中添加：
表示使用yarn workspaces ,并且用yarn作为包管理工具下载依赖
```json
"useWorkspaces": true,
"npmClient": "yarn"
```

在 packages 下新建文件夹 -> 等于说是新建模块
添加模块的依赖有两种方式：
1.在各模块下的package.json的dependencies或者devDependencies下直接写，然后运行lerna bootstrap
2.使用lerna add, 如：
```bash
lerna add <依赖> --scope=<模块名>  [--dev]
表示在某个模块下添加依赖，加--dev就是添加开发时依赖

such as:
lerna add axios --scope=zfan-learn-lerna-core   添加axios到zfan-learn-lerna-core模块
learn add lodash  添加lodash到每个模块
```


lerna run  运行某个模块下的package.json下的脚本
larna exec 到某个模块下运行任意命令
learn clean 删除node_modules
learn publish 发包

# 参考
[中文归纳](https://segmentfault.com/a/1190000019350611)
[官网](https://lerna.js.org/)
[github](https://github.com/lerna/lerna#lernajson)
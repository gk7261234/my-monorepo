lerna+yarn workspace+monorepo总结：

简单完整周期：

- 全局安装 npm i -g lerna 
- 初始化项目 lerna init
- 创建npm包 lerna create @gk/xxx
- 添加依赖模块 lerna add xxx **or** lerna add A --scope B (把A添加到B) 
- 发布 lerna publish

其他：

- 把依赖包提升到根目录 lerna bootstrap --hoist (可以在lerna.json配置)
- 清除package依赖 lerna clean

lerna + Monorepo 最佳实践

- 搭建环境 clone 下来项目 yarn install
- 清理环境 
    lerna clean # 清理所有node_modules
    yarn workspace run clean # 执行所有package的clean操作
- 安装 | 删除依赖 
    yarn workspace packageA add packageB # 把B添加到A
    yarn workspace add lodash #给所有package安装lodash
    yarn add -W -D typescript #根目录安装ts

    yarn workspace packageA remove packageA 
    yarn workspace remove lodash
    yarn remove -W -D typescript

- 项目构建 lerna run --stream --sort build
- git代码提交 | 代码风格 规范化
- 发布 lerna publish 
- 添加测试用例 jest

使用
- git clone xx  # 远程拉取代码
- yarn install # 安装依赖
- git add . # 添加到暂存区
- yarn run commit # 改动说明
- lerna publish # 版本发布

问题

OpenSSL SSL_read: Connection was reset, errno 10054
git config --global http.sslVerify "false"

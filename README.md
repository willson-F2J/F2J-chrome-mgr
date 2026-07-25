![image]()


## Chrome 多开管理工具，支持独立窗口，http/socks5 代理，窗口排列，同步器等
#### 同步器仅支持简单操作与win版本，其他的平台同步器功能需要移植C++文件。
#### 本项目一个人维护，时间与能力有限，更多功能期待各路大神加入完善。
#### 此软件遵循AGPL协议，因此如果你想对其进行修改发布，请保持开源。

---
## 安装包下载
### 点击下载 [by-chrome-app](https://github.com/bysstudio/by-chrome-app/releases/tag/main)
####> 本项目基于 [bysstudio/by-chrome-app](https://github.com/bysstudio/by-chrome-app) 二次开发,遵循 AGPL 协议
---

## 免责声明

本代码仅用于技术交流、学习，请勿用于非法、商业用途。本代码不保存任何用户数据，同时也不对用户数据负责，请知悉。

---

## 使用说明
- 前往系统设置页面设置你的缓存目录与Chrome路径。
- 创建代理
- 创建环境
- 关联代理

---

## 已完善功能
- [x] 多窗口管理
- [x] 代理设置
- [x] Puppeteer 接入
- [x] 同步操作（键盘操作存在bug）仅支持简单的同步
- [x] 窗口排列
- [x] 多指纹信息（需要与浏览器内核搭配）

---

## 期待大神开发功能
- [ ] API自动化
- [ ] 完善同步器功能
- [ ] MAC系统
- [ ] 任务编排
- [ ] 批量管理插件
- [ ] 真实指纹库


---

## 本地运行/打包
环境：Node v20.19.1

基于 Puppeteer、Electron、Element-plus、JS、Sqlite3开发

electron框架文档：https://electron-vite.org

UI框架文档：https://element-plus.org/zh-CN/

数据库ORM文档：https://www.knexjs.cn/

项目结构
```text
├──src
│  ├──main                  后端代码与electron主进程
│  │  ├──index.js           主进程
│  │  └──logger             日志配置
│  │  └──server             后端代码
│  │     └──constants       常量参数
│  │     └──db              数据库CRUD
│  │     └──service         服务提供 浏览器多开/ws/同步器/IP代理等
│  │     └──utils           工具库
│  │     └──...             API接口
│  ├──preload               预加载脚本
│  │  ├──index.js
│  │  └──...
│  └──renderer              vue页面代码
│     ├──src
│     ├──index.html
│     └──...
├──window-api              同步器与窗口排列C++源码  基于window-api接口
├──package.json
└──...
```
当运行 electron-vite 时，它会自动寻找主进程、渲染器和预加载脚本的入口文件。默认的入口配置：
- 主进程： <root>/src/main/{index|main}.{js|ts|mjs|cjs}
- 预加载脚本： <root>/src/preload/{index|preload}.{js|ts|mjs|cjs}
- 渲染器： <root>/src/renderer/index.html

### Install

```bash
npm install
```
### Visual Studio Installer 环境配置
![image](https://github.com/user-attachments/assets/537394b9-50b8-47b2-8366-b0c041c0619e)

### 要先编译同步器window-api的C++代码 编译模块并集成到electron
```bash
#进入目录
cd window-api

#配置electron相关信息
set npm_config_target=34.3.0
set npm_config_disturl=https://electronjs.org/headers
set npm_config_runtime=electron
set npm_config_target_arch=x64

#编译
node-gyp rebuild
```
#####  C++重新编译操作（功能不正常时使用）
```bash
#重新编译：
node-gyp clean
node-gyp configure
node-gyp build --verbose
```


### 本地开发
```bash
#把c++编译的node包关联到本项目，只需要运行一次就可以
npm run build:addon

npm run dev
```

### 打包发布
```bash
npm run build:addon

#发布安装版本
npm run build:win

#发布便捷版本
npm run build:portable

```

## 项目参考
Chrome Power [chrome-power-app](https://github.com/zmzimpl/chrome-power-app)


# 内核教程开发
###  指纹内核教程开发，进群联系或留言issues


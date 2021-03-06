# 工程
### 描述
    基于react搭建。主要是为了学习react包括redux,webpack,node等知识。
    对应的node工程地址为：https://github.com/zyd317/reactPracticeNode#readme

### 启动
    npm i webpack@3 -g
    npm i hiproxy -g // 一个用于代替nginx的转发网络请求工具
    npm i
    webpack 编译打包资源
    webpack-dev-server -w --port 8008 将webpack作为启动qzz的服务器
    资源地址如：http://m.flight.qunar.com/build/index.bundle.js
    访问demo页：http://m.flight.qunar.com/demoName

### 目录搭建
```bash
.
├── src
│   ├── components 公共组件(日常收集一些日常编写的组件，具体使用方式见齐readme)
│   ├── initStore.js 初始化每个页面store的配置文件
│   ├── lib.js 合并打包react等库文件
│   ├── indexPage 每个页面的入口组件, 每个页面都是一个工程
│   │   └── index
│   │       ├── index.js
│   │       └── index.scss 首页的样式，也会把该页面js引入的css,一起打包在这个文件里
│   └── utils 根据函数
│       └── reducerUtil.js 一个reducer的基类
├── build webpack 打包输出文件
│   ├── index.bundle.js
│   └── indexStyle.bundle.js
├── LICENSE 证书
├── package.json
├── reame.md
└── webpack.config.js webpack的配置文件
```

### 说明
- 使用hiproxy进行nginx模拟，转发请求。具体配置见./rewrite
- 模块化：module.exports={};require('file');    export {};require {} from 'file';
- redux: abstractReducer -> reducerFactory(return reducer(形如{name: 'moduleName', receive: func})) -> reducerX(extend abstractReducer) -> combineReducer(return combination(负责执行调用reducer)) -> store(构造了combine的store结构(store.getState()={reducerX: {state}}, store.dispatch等))
- reducerUtil: 
- dispatch: 使用this.props.dispatch(this.props已经通过mapDispatchToProps)或者store.dispatch
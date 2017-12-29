# 后台项目文件结构说明

项目通过 vue-cli 构建

#### 总体框架
```shell
├── build              # webpack 相关相关配置文件 (都已经配置好, 一般不需要修改)
├── config             # vue 项目的配置文件 (可配置端口,资源文件路径, 打包路径)
├── node_modules       # 依赖包
├── src                # 项目源代码 (基本编写的代码都是在这个目录下面)
│   ├── assets         # 打包的静态资源文件 (里面的内容会在 build 的时候被打包进去)
│   ├── components     # 页面子组件文件夹
│   ├── libcomponents  # 通用组件文件夹
│   ├── page           # 页面文件夹
│   ├── router         # 路由 (配置项目路由, 依赖 vue-router)
│   ├── store          # vuex相关文件 (依赖 vuex)
│   ├── style          # 样式文件
│   ├── App.vue        # 根组件
│   └── main.js        # 入口文件
├── static             # 不打包在一起的静态资源文件 (build 的时候原封不动拷贝)
├── .babelrc           # babel编译参数
├── .editorconfig      # 代码格式
├── .eslintignore      # eslint 忽略文件配置文件
├── .eslintrc.js       # eslint 配置文件
├── .gitignore         # git 提交忽略文件配置文件
├── .postcssrc.js      # postcss 配置文件
├── index.html         # 主页面
├── package.json       # 项目基本信息
└── README.md          # 项目说明
```

#### 细分目录

**1.** build - [webpack 相关相关配置文件]
>build 文件夹主要是 webpack 的配置。当我们输入npm run dev首先启动的就是dev-server.js，它会去检查 node 及 npm 版本，加载配置文件，启动服务。输入npm run build 会运行 build.js，它根据配置文件，打包生成整个项目的发布文件，默认配置会生成到 dist 文件夹中。

```shell
├── build
│   ├── build.js               # 生成环境构建 (npm run build 运行)
│   ├── check-versions.js      # 检查 node 及 npm 版本
│   ├── dev-client.js          # 开发服务器的热重载 (实现页面自动刷新)
│   ├── dev-server.js          # 开发服务器构建 (npm run dev 运行)
│   ├── utils.js               # 构建相关工具
│   ├── vue-loader.conf.js     # vue-loader 配置项
│   ├── webpack.base.conf.js   # webpack 基础配置
│   ├── webpack.dev.conf.js    # webpack 开发环境配置
│   └── webpack.prod.conf.js   # webpack 生产环境配置
└── ...
```

**2.** config - [vue 项目的配置文件]
>config文件主要是项目的相关配置，常用的就是当端口冲突时配置监听端口，打包输出路径及命名等。

```shell
├── config
│   ├── dev.env.js       # 项目开发环境配置
│   ├── index.js         # 项目主要配置 (包括监听端口, 打包路径等)
│   └── prod.env.js      # 项目生产环境配置
└── ...
```

**3.** node_modules - [依赖包]
>node_modules里面是项目依赖包，其中包括很多基础依赖，自己也可以根据需要安装其他依赖。基本项目所需依赖包已在 package.json 中配置好了，通过 npm i 安装即可 (建议用 cnpm)。
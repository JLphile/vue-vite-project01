# 一.用vite创建项目

- ```cmd
  npm init vue@latest
  ```

- ```cmd
  D:\workspace>npm init vue@latest
  
  Vue.js - The Progressive JavaScript Framework
  
  √ Project name: ... vue-vite-project01
  √ Add TypeScript? ... No / Yes
  √ Add JSX Support? ... No / Yes
  √ Add Vue Router for Single Page Application development? ... No / Yes
  √ Add Pinia for state management? ... No / Yes
  √ Add Vitest for Unit Testing? ... No / Yes
  √ Add Cypress for both Unit and End-to-End testing? ... No / Yes
  √ Add ESLint for code quality? ... No / Yes
  √ Add Prettier for code formatting? ... No / Yes
  
  Scaffolding project in D:\workspace\vue-vite-project01...
  
  Done. Now run:
  
    cd vue-vite-project01
    npm install
    npm run lint
    npm run dev
  
  
  D:\workspace>cd vue-vite-project01
  
  D:\workspace\vue-vite-project01>npm install
  
  added 329 packages in 1m
  
  D:\workspace\vue-vite-project01>
  
  ```

- **问题：**

- # App.vue Doctor

- ### ❗ `vue-tsc` version different

- The `Vue Language Features (Volar)` version is `1.0.8`, but workspace `vue-tsc` version is `0.40.13`, there may have different type checking behavior.

- **解决：**升级 vue-tsc 版本

- ```cmd
  npm i vue-tsc@latest -D
  ```

  

# 二、打包上线

```cmd
npm run build
```



# 三、Vite打包后的dist不能直接在浏览器

## **方案一：**

### 1.原因

Vite 本身依赖于[原生ES模块](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)来做模块加载，而原生ES模块是不支持 `file://` 本地访问的。

### 2.解决办法

**方案一：使用http-server插件启动**

1.安装node.js；（已安装跳过）

2.安装http-server。

```coffeescript
npm install http-server -g
```

或

```sql
yarn global add http-server
```

3、进入dist根目录执行启动项目

```vbscript
http-server
```



## **方案二：使用nginx启动**

1、把dist拷贝至nginx的html目录下（其他目录也行，需在nginx里配置root）；

![img](https://img-blog.csdnimg.cn/c122b32211da4af9b86b3f1e66af2197.png)

2、配置nginx.conf

![img](https://img-blog.csdnimg.cn/88d0de2bbc7341dcb3a49f08e74c3b9e.png)

 3、保存并启动nginx，访问http://127.0.0.1:3000即可。

# 四、element-plus

### 1.安装

```cmd
npm install element-plus --save
```

### 2.Volar 支持[#](https://element-plus.gitee.io/zh-CN/guide/quickstart.html#volar-支持)

如果您使用 Volar，请在 `tsconfig.json` 中通过 `compilerOptions.type` 指定全局组件类型。

```
// tsconfig.json
{
  "compilerOptions": {
    // ...
    "types": ["element-plus/global"]
  }
}
```

### 3.按需导入[#](https://element-plus.gitee.io/zh-CN/guide/quickstart.html#按需导入)

您需要使用额外的插件来导入要使用的组件。

#### 自动导入推荐[#](https://element-plus.gitee.io/zh-CN/guide/quickstart.html#自动导入-推荐)

首先你需要安装`unplugin-vue-components` 和 `unplugin-auto-import`这两款插件

```cmd
npm install -D unplugin-vue-components unplugin-auto-import
```

然后把下列代码插入到你的 `Vite` 或 `Webpack` 的配置文件中

##### Vite[#](https://element-plus.gitee.io/zh-CN/guide/quickstart.html#vite)

```ts
// vite.config.ts
import { defineConfig } from 'vite'
import AutoImport from 'unplugin-auto-import/vite'
import Components from 'unplugin-vue-components/vite'
import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

export default defineConfig({
  // ...
  plugins: [
    // ...
    AutoImport({
      resolvers: [ElementPlusResolver()],
    }),
    Components({
      resolvers: [ElementPlusResolver()],
    }),
  ],
})
```

### 4.App.vue中引入element

```ts
<template>
  <div>  
    <el-row class="mb-4">
      <el-button>Default</el-button>
      <el-button type="primary">Primary</el-button>
    </el-row>    
  </div>
</template>
```



### 5.重启项目

```cmd
npm run dev
```

# 五、配置路由

## 1.src>router>index.ts

```ts
import { createRouter, createWebHistory } from "vue-router";

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: "/",
      redirect: "/home",
    },
    {
      path: "/home",
      name: "home",
      component: () => import("../views/HomeView.vue"),
    },
    {
      path: "/about",
      name: "about",
      // route level code-splitting
      // this generates a separate chunk (About.[hash].js) for this route
      // which is lazy-loaded when the route is visited.
      component: () => import("../views/AboutView.vue"),
    },
  ],
});

export default router;

```

## 2.App.vue

```ts
<template>
  <div>    
    <RouterLink to="/home">首页</RouterLink>
    <RouterLink to="/about">关于</RouterLink>
    <RouterView></RouterView>
  </div>
</template>
```



# 六、编写代码

## 1.App.vue

```vue
<template>
  <div>
    <h1>{{ msg }}</h1>
    <HelloWorld />
  </div>
</template>

<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
const msg = "Hello App";
</script>

<style scoped></style>

```

## 2.src>main.ts 中导入样式表

```ts
import "./assets/main.css"
```

## 3.src>assets>main.css

```javascript
@import "./base.css";

#app {
  max-width: 1280px;
  /* margin: 0 auto; */
  padding: 1rem;
  font-weight: normal;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }
}

```




















# tarojs-plugin-platform-miniprogram

[![](https://img.shields.io/npm/v/@baranwang/tarojs-plugin-platform-miniprogram)](https://www.npmjs.com/package/@baranwang/tarojs-plugin-platform-miniprogram)
[![Node.js Package](https://github.com/baranwang/tarojs-plugin-platform-miniprogram/actions/workflows/npm-publish.yml/badge.svg)](https://github.com/baranwang/tarojs-plugin-platform-miniprogram/actions/workflows/npm-publish.yml)
![](https://img.shields.io/npm/l/@baranwang/tarojs-plugin-platform-miniprogram)

[@tarojs/plugin-platform-weapp](https://github.com/NervJS/taro/tree/next/packages/taro-weapp) 自定义 wxml 支持

## 配置

`config/index.js` 中引入 plugin

```javascript
const config = {
  // ...
  plugins: ["tarojs-plugin-platform-miniprogram"],
  // ...
};

// or

const config = {
  // ...
  plugins: [
    [
      "tarojs-plugin-platform-miniprogram",
      /**
       * @type {import('tarojs-plugin-platform-miniprogram').Options}}
       */
      {
        prefix: "<page-meta></<page-meta>", // or path.resolve(__dirname, './prefix.wxml')
      },
    ],
  ],
  // ...
};
```

修改 `package.json`

```diff
{
  "scripts: {
-   "build:weapp": "taro build --type weapp",
+   "build:weapp": "taro build --type miniprogram",
  }
}
```

## 使用

### 通用

```javascript
const { page } = Taro.getCurrentinstance();

page.setData({
  pageMeta: {
    backgroundTextStyle: 'dark',
    // ...
  },
  navigationBar: {
    // ...
  },
});
```

### React

除了通用方法外，为 React 封装了组件

```tsx
import { PageMeta, NavigationBar } from "tarojs-plugin-platform-miniprogram/dist/components";

export default () => {
  return (
    <>
      <PageMeta backgroundTextStyle='dark'>
        <NavigationBar title='Awesome Taro' />
      </PageMeta>
    </>
  )
}
```
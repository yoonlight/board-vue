# board-vue

## Start

```shell
vue create <name>
vue add vuetify
yarn add axios vue-axios 
yarn add vue-toasted
```

## Default Setting

### link API Server

```js
module.exports = {
  devServer: {
    proxy: {
      "/api": {
        target: "http://localhost:3001/api",
        changeOrigin: true,
        pathRewrite: {
          "^/api": "",
        },
      },
    },
  },
};
```

## Reference

[Event Bus](https://webruden.tistory.com/109)

# board-vue

## Start

```shell
vue create <name>
vue add vuetify
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

<div align="center">
  <a href="https://github.com/webpack/webpack">
    <img width="200" height="200"
      src="https://webpack.js.org/assets/icon-square-big.svg">
  </a>
  <h1>Grpc Webpack Plugin</h1>
  <p>
    A <a href="https://webpack.js.org">webpack</a> plugin that compiles <code>.proto</code> files automatically with <a href="https://github.com/grpc/grpc-web">gRPC-Web</a>.
  </p>
</div>

<h2 align="center">Install</h2>

```shell
yarn add --dev grpc-webpack-plugin
```

<h2 align="center">Usage</h2>

**webpack.config.js**

```js
const GrpcWebPlugin = require('grpc-webpack-plugin');

const path = require('path');
const DIR = path.resolve(__dirname, './proto');
const OUT_DIR = path.resolve(__dirname, './protobuf');

module.exports = {
  mode: 'development',
  plugins: [
    new GrpcWebPlugin({
      protoPath: DIR,
      protoFiles: ['echo.proto'],
      outputType: 'js',
      importStyle: 'commonjs',
      outDir: OUT_DIR,
    }),
    new GrpcWebPlugin({
      protoPath: DIR,
      protoFiles: ['echo.proto'],
      outputType: 'grpc-web',
      importStyle: 'commonjs+dts',
      mode: 'grpcwebtext',
      outDir: OUT_DIR,
    }),
  ]
});
```

<h2 align="center">Options</h2>

|Name|Description|Type|Default|
|---|---|---|---|
|`protoPath`| |`{String}`| |
|`protoFiles`| |`{Array.<string>}`| |
|`outputType`|`'js' \| 'grpc-web'`|`{String}`| |
|`importStyle`|`'closure' \| 'commonjs' \| 'commonjs+dts' \| 'typescript'`|`{String}`|`'closure'`|
|`mode`|`'grpcwebtext' \| 'grpcweb'`|`{String}`|`'grpcwebtext'`|
|`outDir`| |`{String}`|`'.'`|
|`extra`| |`{Array.<string>}`|`[]`|
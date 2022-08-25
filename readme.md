## 前言

通过本组件，您可以简单快速的将项目部署到Lambda。

### template.yaml

````
edition: 1.0.0          #  命令行YAML规范版本，遵循语义化版本（Semantic Versioning）规范
name: functionApp       #  项目名称
access: aws   #  秘钥别名

services:
  function-test: #  服务名称
    component: devscomp/lambda  # 组件名称
    props: #  组件的属性值
      region: ap-southeast-1
      function:
        codeUri: ./index.js
        name: aws-lambda-dome
        handler: index.handler
        runtime: nodejs12.x
        description: Test
      events:
        - name: api-sdk
          type: Api
          properties:
            path: /test/test
            method: ANY

````
> Function 属性可参照： https://docs.aws.amazon.com/zh_cn/lambda/latest/dg/API_CreateFunction.html#API_CreateFunction_RequestBody



### index.js

````
exports.handler = async (event) => {
  // TODO implement
  const response = {
    statusCode: 200,
    body: JSON.stringify('Hello from wss!'),
  };
  return response;
};
````

## 发布本组件

1. 修改 publish.yaml 的版本
2. 执行 npm run publish

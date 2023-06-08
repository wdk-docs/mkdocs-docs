# 构建多个

支持渲染多个 Swagger UI。

## Markdown

在 swagger-ui 标签中添加两个属性：

1. grouped: 同一页面中每个具有分组属性的 swagger-ui 将被收集到单个 Swagger UI 中
2. name: Swagger UI 顶部栏选择器显示文本，默认值为 src 内容

带有多个 OAS 的 Swagger UI 占据了第一个分组 swagger-ui 标签位置。

```html
## Multiple OAS in single Swagger UI

<swagger-ui
    grouped
    name="Pet Store"
    src="https://petstore.swagger.io/v2/swagger.json"
/>
<swagger-ui grouped name="Sample" src="./openapi-spec/sample.yaml" />
<swagger-ui
    grouped
    name="Sample First"
    src="./openapi-spec/sample-first.yaml"
/>
<swagger-ui
    grouped
    name="Sample Second"
    src="./openapi-spec/sample-second.yaml"
/>
<swagger-ui
    grouped
    name="Sample Third"
    src="./openapi-spec/sample-third.yaml"
/>

## Other independent Swagger UI

<swagger-ui src="./openapi-spec/sample.yaml" />
```

## 单个 Swagger UI 中的多个 OAS

<swagger-ui grouped name="Pet Store" src="https://petstore.swagger.io/v2/swagger.json"/>
<swagger-ui grouped name="Sample" src="./openapi-spec/sample.yaml"/>
<swagger-ui grouped name="Sample First" src="./openapi-spec/sample-first.yaml"/>
<swagger-ui grouped name="Sample Second" src="./openapi-spec/sample-second.yaml"/>
<swagger-ui grouped name="Sample Third" src="./openapi-spec/sample-third.yaml"/>

## 其他独立的 Swagger UI

<swagger-ui src="./openapi-spec/sample.yaml"/>

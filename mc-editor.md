# mc-editor 文本编辑器

### Attributes 可选项

参数 | 说明 | 类型 | 可选值 | 默认值 | 同步方式
-|-|-|-|-|-
value | 绑定值 | String | - | - | v-model
width | 组件内容区域宽度 | Number | - | 800 | -
isFullWidth | 组件内容区域宽度是否100% | Boolean | - | false | -
editorConfig | 文本编辑器额外配置项 | Object | - | null | -


### 示例代码

双向同步内容

```html
<mc-editor v-model="formData.content"></mc-editor>
```

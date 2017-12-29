# file-upload 文件上传

### Attributes 可选项

参数 | 说明 | 类型 | 可选值 | 默认值 | 同步方式
-|-|-|-|-|-
width | 组件内容区域宽度 | Number | - | 350 | -
workMode | 工作模式 | String | url-name/url | url-name | -
fileName | 上传后的文件名 | String | - | - | sync
fileUrl | 上传后的文件服务器地址 | String | - | - | sync


### 示例代码

#### url-name 模式

双向同步上传文件地址和文件名

```html
<file-upload :fileUrl.sync="formData.FileUrl" :fileName.sync="formData.FileName"></file-upload>
```

#### url 模式

双向同步上传文件地址

```html
<file-upload :fileUrl.sync="formData.FileUrl2" workMode="url"></file-upload>
```
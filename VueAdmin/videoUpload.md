# video-upload 视频上传

### Attributes 可选项

参数 | 说明 | 类型 | 可选值 | 默认值 | 同步方式
-|-|-|-|-|-
width | 组件内容区域宽度 | Number | - | 400 | -
workMode | 工作模式 | String | upload/outer/upload-outer | upload-outer | -
isOuter | 是否外链开关 | Boolean | - | true | sync
url | 视频地址 | String | - | - | sync


### 示例代码

#### upload-outer 模式 上传外链模式

双向同步视频地址和是否外链开关

```html
<video-upload :isOuter.sync="formData.IsOuter" :url.sync="formData.VideoUrl"></video-upload>
```

#### upload 模式 纯上传模式

双向同步视频地址

```html
<video-upload :url.sync="formData.VideoUrl" workMode="upload"></video-upload>
```

#### outer 模式 纯外链模式

双向同步视频地址

```html
<video-upload :url.sync="formData.VideoUrl" workMode="outer"></video-upload>
```
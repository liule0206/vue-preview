## preview插件
### Usage
```javascript
    import preview from 'components/preview'
```
```html
    <preview :show="show" :options="data" @on-close="close">
    </preview>
```
### Props
* `options`:
1. type `Array`
2. 默认值 `[]`
3. 说明 options图片容器，数组内对象包含 

| 参数名称 | 是否必填 | 默认值 | 说明 
| - | - | - | - |
|`alt`| `否` | `无` | `图片缺失显示文字` |
|`base64`| `否` | `无` | `为false是使用路径显示图片`
|`imgInfo`| `是` | `无` | `数据源可以使base64或者文件路径. 使用路径需添加`*_base64_*`为`*_false_*

* `dis` 
1. type `Number`
2. 默认值 `0`
3. 说明 `默认展示的图片`

* `show`
1. type `Boolean`
2. 默认值 `false` 
3. 说明 `图片预览开关`

### methods
* on-close 
1. 参数 `无`
2. 功能 `点击图片关闭预览`

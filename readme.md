## Comfirm组件
### Usage
```
      import vConfirm from 'components/preview'
```
```
    <preview :show="show" :options="data" @on-close="close">
        申请已通过<br>hgagkahgk<br>gjhlag
    </preview>
```
### Props
| 名字 | 类型 | 默认 | 描述
|:-|-|-|-|
|options | Array |[] |数据源
|dis | Number |0 |默认展示图片
|show |Boolean | false |展示图片预览
### methods

|名字	|参数	|描述
|:-|-|-|
|on-close |无 | 点击图片关闭预览

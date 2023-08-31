## 下拉框选择器
> **组件名：sx-select**

基于原生内置组件[picker](https://uniapp.dcloud.net.cn/component/picker.html)进行了封装，使用原生组件渲染快、性能好，由于原生组件使用比较繁琐

故稍微做了下改造封装，没有任何修改，纯官方原汁原味原生picker



### 安装方式

本组件符合[easycom](https://uniapp.dcloud.io/collocation/pages?id=easycom)规范，`HBuilderX 2.5.5`起，只需将本组件导入项目，在页面`template`中即可直接使用，无需在页面中`import`和注册`components`。

### 基本用法 

- 设置 `title` 属性，可以设置默认选择名称
- 设置 `value` 属性，为默认选择项，可使用v-model进行双向绑定
- 设置`items`属性，为选项列表，格式为json数组
- 设置`itemText`属性，设置**items**属性的文本值
- 设置`itemVlue`属性，设置**items**属性的属性
- 设置`className`属性，为默认标题设置自定义class名称

```html
<sx-select v-model="model" :items="[{title:'男',value:1},{title:'女',value:2}]" />
```



### 自定义插槽

- 自定义插槽基本上可以在页面任意地方进行使用
- 示例1使用了官方的uni-ui组件中的uni-list和uni-list-item进行组合

#### 示例1

```html
<uni-list>
  <sx-select v-model="model" :items="sexItems">
    <template slot-scope="{title}">
      <uni-list-item title="性别" show-arrow :right-text="title" />
    </template>
  </sx-select>
  <sx-select v-model="job" :items="jobItems" title="">
    <template slot-scope="{title}">
      <uni-list-item title="职业" show-arrow :right-text="title" />
    </template>
  </sx-select>
</uni-list>

```



#### 示例2

- 结合了官方UI库uni-icon使用

```html
<sx-select v-model="model" :items="cityItems" title="选择城市">
  <template slot-scope="{title}">
    <text style="font-size: 14px;">{{title}}</text>
    <uni-icons type="bottom"></uni-icons>
  </template>
</sx-select>

```



## API

### Props

| 属性名    | 类型           | 默认值 | 说明                            |
| --------- | -------------- | ------ | ------------------------------- |
| value     | Any | -      | 默认值                          |
| items     | Array          | []     | 对象数组格式，选项列表值        |
| itemText  | String         | text   | 设置**items**属性的文本值       |
| itemValue | String         | text   | 设置**items**属性的属性值       |
| title     | String         | 请选择 | 默认标题显示内容                |
| className | String         | -      | 为标题设置默认class名称设置样式 |

### Events

| 事件称名 | 说明                 | 返回参数 |
| -------- | -------------------- | -------- |
| change   | 当点击完成选择时发出 | -        |

### 名人语录

人的心只容得下一定程度的绝望，海绵已经吸够了水，即使大海从它上面流过，也不能再给它增添一滴水了。——**雨果（法国）**

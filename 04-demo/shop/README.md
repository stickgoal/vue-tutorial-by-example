# shop

> vue practice

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

### element-ui 验证所需要的步骤
- form添加:rules 绑定rules，需要绑定:model
- 在data中加入rules,编写规则
- 提交的submit处理函数中调用form的validate方法

### element-ui的notification和message

主要用于代替alert

```vue
 this.$notify({
          title: '成功',
          message: '这是一条成功的提示消息',
          type: 'success'
        });
        
        
 const h = this.$createElement;

        this.$notify({
          title: '标题名称',
          message: h('i', { style: 'color: teal'}, '这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案')
        });
        
        
           this.$message('校验失败')

``` 

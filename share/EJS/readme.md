# 基本语法

## 流程控制
### if else
```
<div><% if(msg) { %></div>
  <%=msg%>
<% } else {%>
  ....
<% } %>


```
### for
```
  <div><% products && products.forEach(item => { %></div>
    <%=item.goods_name%>
  <% }) %>
```
### 输出
```
<p><%=msg.replace(/dress/, 't-shirts')%></p>
```
### include

```
<% include('component/header.html')%>

<% include('component/procutItem.html', {goods: {}})%>
```

## express 服务端

```

// 默认ejs后缀
app.set('view engine', 'ejs')

// 设置html后缀
app.set('view engine', 'html')
app.engine('.html', require('ejs').__express)

app.get(*, (req, res, next) => {
  res.render('index', {
    msg: 'hello world',
    product: {
      name: 'dreess'
    },
    title: 'I am title ...'
  })
})


//index.html
<p><%=msg%></p>
<% include('header.html', {title: title})%>


<script>
//不转义输出
var product = <%- JSON.stringify(product)%>
// {name: dress}

//转义输出
var product = <%= JSON.stringify(product)%>
{&#34;name&#34;:&#34;dress&#34;}
<script>

```

## 客户端

```
var str = '<p><%=%></p>',
  str2 = '<p><?=msg?></p>'
  data = {msg: 'hello world'}
var template = ejs.compile(str);
template(data);
// => Rendered HTML string

ejs.render(str2, data, {
  delimiter: '?'
})

```
## express layout 中间件


## 源码解析

![](https://raw.githubusercontent.com/Sunnyson303/blog-boilerplate/master/share/EJS/base.png)
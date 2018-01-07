## POST请求
post请求属于HTTP常用请求，意思是：请求源服务器接受请求中的实体作为请求资源的一个新的从属物。

一般用于form表单，输入数据后，通过post请求将数据提交到服务器中。服务器接受到信息之后，对信息进行处理。

![peShTO.jpg](https://s1.ax1x.com/2018/01/07/peShTO.jpg)

在WebApp中的：
1. 新建一个编辑页面的路由与一个编辑页面
2. 用户通过路由打开页面。输入数据，并发送HTTP POST请求吧数据给webapp.
3. webapp收到请求之后，依据路由分发到对应的处理模块。
4. 处理模块用户输入的数据并进行相应处理


新建一个页面路由：

```
/* GET posts create page. */
router.get('/posts/create', function(req, res, next) {
  res.render('create');
});
```
新建一个一个编辑页面：

```
<!DOCTYPE html>
<html>
  <head>
    <link rel='stylesheet' href='/stylesheets/style.css' />
    <link href="https://cdn.bootcss.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.bootcss.com/vue/2.4.4/vue.min.js"></script>
    <script src="https://cdn.bootcss.com/axios/0.16.2/axios.min.js"></script>
  </head>
  <body>
    <div id="app">
      <h1>新建文章</h1>
      <div class="form-group">
        <input type="text" class="form-control" v-model="title" placeholder="输入文字标题">
      </div>
      <div class="form-group">
        <textarea class="form-control" rows="3" v-model="content" placeholder="输入文章内容"></textarea>
      </div>
      <div class="form-group">
        <button class="btn btn-default" v-on:click="submit">提交</button>
      </div>
    </div>
  </body>
</html>
<script>
var vm = new Vue({
  el: '#app',
  data: {
    title: '',
    content: ''
  },
  methods: {
    submit () {
    axios.post('/api/posts',
      {
        title: vm.title,
        content: vm.content
      })
      .then(function(response) {
        alert(JSON.stringify(response.data));
      })
      .catch(function(err) {
        alert(err);
      })
    }
  }
});
</script>
```
当中利用vue将<input>和<textarea>输入的内容与data中的title和content变量进行绑定，提交按钮事件绑定到methods的submit方法中。
 axios采用posts方法来发送数据。
 
 在route.api.js中增加路由'api/posts'的post请求处理
```
/* POST posts */
router.post('/posts', function (req, res, next) {
  var title = req.body.title;
  var content = req.body.content;
  res.send({title, content}); // 收到数据后，又把数据返回给了请求方
});
```

需要注意的两个点：

```
/* GET posts lists */
router.get('/posts', function(req, res, next) {
res.json({postsList: ['文章1', '文章2', '文章3']});
})

/* POST posts */
router.post('/posts', function (req, res, next) {
  var title = req.body.title;
  var content = req.body.content;
  res.send({title, content}); // 收到数据后，又把数据返回给了请求方
});
```
1. api地址同样都是/post，但是HTTP的请求方法不同。GET请求的'api/posts'会分发给router.get。POST请求的'api/posts'给分发给router.post
2. req,是被抽象出来的对象，我们可以通过req.body中拿到用户输入的信息（如title）。为什么body，因为主程序中的中间件已经帮我们吧用户输入的信息整理在body中了

```
app.use(logger('dev'));
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));
app.use(cookieParser());
app.use(express.static(path.join(__dirname, 'public')));

```





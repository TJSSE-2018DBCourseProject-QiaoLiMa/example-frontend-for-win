##食用说明

**需要电脑已安装python**



0.index.html中更改ip

```javascript
 axios.get('http://192.168.1.101:58546/hello')
```

更改为

```
 axios.get('http://<你的ip>:58546/hello')
```





1.自行上网查找并安装git for windows

2.用它附带的git bash工具，在html所在目录下右键git bash here

3.在窗口中输入

```
python -m http.server [端口号]
```

如果电脑已安装nginx，8080端口号可能和nginx冲突（写代码的时候忘记考虑这个了）

但是由于后端中代码写的是8080，没安装过nginx建议使用8080端口号

如果不使用8080需要更改后端Startup.cs中的端口号

```
 app.UseCors(
                options => options.WithOrigins("http://localhost:8080").AllowAnyHeader()
    );
```

更改

```
app.UseCors(
                options => options.WithOrigins("http://localhost:<端口号>").AllowAnyHeader()
    );
```

4.浏览器中访问http://localhost:8080，可以看到一个有按钮的页面

5.开启后台应用后，点击会弹出数据库中testtable1中的id

____



##原理

按钮代码，点击触发reverseMessage

```html
<div id="app-5">
    <button @click="reverseMessage">点击获取</button>
</div>
```



脚本，reverseMessage是一个函数，这个函数发送http请求到http://192.168.1.101:58546/hello

然后输出返回的数据。

```html
<script>

    var app5 = new Vue({
        el: '#app-5',
        methods: {
            reverseMessage: function () {
                axios.get('http://192.168.1.101:58546/hello')
                    .then(function (response) {
                        // handle success
                        console.log(response.data);
                        alert(response.data)
                    })
                    .catch(function (error) {
                        // handle error
                        console.log(error);
                    })
                    .then(function () {
                        // always executed
                    });
            }
        }
    })

</script>

```










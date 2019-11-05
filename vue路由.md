# vue路由

**router :路由器**

**routes:多个路由**

**routes：单个路由**



routes:  path--路径

​		name---该路由的名称

​		component ----该路由对应的组件

**html中**

<router-link>默认情况下，将呈现为<a>标签

用router-link 来定义导航时，通过传递‘to’支柱来指定链接

```
<router-link to="路径"></router-link> 
<router-view></router-view>
```

**javaScript中**

1.定义路由组件

​	import引入其他文件

2.定义路由

​	每个路由应该映射一个组件，

​		path 路径

​		component 组件构造器

3.创建router实例，传值

4.注入路由

**默认路由**


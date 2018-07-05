# Vue-Study-travel
Vue学习之旅

### Vue-roter
- 1.在创建工程的时候，选择安装router-vue.
- 2.在工程中./src/router/index.js文件中导入并设置默认router-view
```js
    import NotFinish from '../components/NotFinish.vue'
    
    export default new Router({
      routes: [
        {
          path: '/',
          name: 'NotFinish',
          component: NotFinish
        }
       ]
    })
```
- 3.默认情况下，工程中的App.vue里会默认配置，表示当前的文件是router-view的入口，所有界面内容显示在此处。
```js
    <router-view></router-view>
```
### 跳转 当想要跳转界面时，比如：点击用户头像，跳转到用户详情界面
- 1.在index.js内添加需要跳转的界面（用户详情界面）
```js
  import NotFinish from '../components/Detail.vue'//导入界面
    
    export default new Router({
      routes: [
        {
          path: '/', //默认的router-view
          name: 'NotFinish',
          component: NotFinish
        },
        {
          path: '/Detail',//添加用户详情界面
          name: 'Detail',
          component: Detail
        }
       ]
    })
```
- 2.在需要跳转的地方添加<router-link></router-link>,该标签会在运行时转换成a标签。
```js
        <!--to的值为index.js中导入的用户详情界面的path-->
        <router-link to="/Detail">
            <!--用户头像-->
            <div class="avatar">王琦</div> 
        </router-link>
```

### 路由传参 跳转时将参数传递给目标界面
- 1.传参
```js
        <!--
            此处使用v-bind:to
            name为index.js中导入的用户详情界面的name
            params即为所要传递的参数，是Object类型
         -->
        <router-link :to="{name: 'Profile',params: {id : msg}}">
            <div class="avatar">王琦</div>
        </router-link>
```
- 2.取参 用户详情界面中
```js
        created:  function () {
            //获取路由传进的参数
            console.log(this.$route.params.id);
        }
```

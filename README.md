# pageAninmate

> vue-router实现webApp切换效果

## 运行方法

``` bash
# 安装依赖
npm install

# 浏览器打开localhost:8080
npm run dev

```

## 演示效果
![](pageAnimate.gif)

## iOS滑动效果，可以切换到ios分支获取代码
![](ios_animate.gif)

## 快速集成
1.复制PageTransittion.vue到项目目录。
2.修改router配置。
```
Router.prototype.goBack = function () {
  this.isBack = true
  window.history.go(-1)
}
const router = new Router({
  routes: [
    {
      path: '/',
      name: 'PageTransition',
      component: PageTransition, // 引入页面切换组件
      children: [{
        path: '',
        component: Index  // 父路由访问页面，例如，访问www.aaa.com/ 显示的是Index组件
      }, {
        path: '/pageA',
        component: PageA  // 子路由组件  例如，访问www.aaa.com/pageA 显示为PageA
      }, {
        path: '/pageB',
        component: PageB // 子路由组件  例如，访问www.aaa.com/pageB 显示为PageB
      }]
    }
  ]
})
```

## 方案实现
### 记录页面状态
要实现页面前进后台动画，首先必须知道页面状态（即是页面是进入下一页，还是后退），我们可以通过改写router.go方法记录回退状态，页面如果需要回退时，调用
```
$router.go(-1)
```

修改router/index.vue
```
// 增强原方法，好处是旧的业务模块不需要任何变动
Router.prototype.go = function () {
  this.isBack = true
  window.history.go(-1)
}

// 或者你可以新建一个方法
Router.prototype.goBack = function () {
  this.isBack = true
  this.go(-1)
}
```
当new Router时，实例就包含go/goBack方法。

### 监听路由变化
使用嵌套路由的方式引入子页面，监听根路由的update钩子做相应操作。
```
beforeRouteUpdate (to, from, next) {
  // 如果isBack为true时，证明是用户点击了回退，执行slide-right动画
   let isBack = this.$router.isBack
   if (isBack) {
      this.transitionName = 'slide-right'
   } else {
      this.transitionName = 'slide-left'
   }
   // 做完回退动画后，要设置成前进动画，否则下次打开页面动画将还是回退
   this.$router.isBack = false
     next()
}
```
### 动画效果
通过transition执行动画
```
  <transition :name="transitionName">
    <router-view class="child-view"></router-view>
  </transition>
```
css代码
```
.child-view {
  position: absolute;
  width:100%;
  transition: all .8s cubic-bezier(.55,0,.1,1);
}
.slide-left-enter, .slide-right-leave-active {
  opacity: 0;
  -webkit-transform: translate(50px, 0);
  transform: translate(50px, 0);
}
.slide-left-leave-active, .slide-right-enter {
  opacity: 0;
  -webkit-transform: translate(-50px, 0);
  transform: translate(-50px, 0);
}
```

### 路由设置
router/index.js
```
const router = new Router({
  routes: [
    {
      path: '/',
      name: 'PageTransition',
      component: PageTransition,
      children: [{
        // 该路由为父路由的默认路由
        path: '',
        component: Index
      }, {
        path: '/pageA',
        component: PageA
      }, {
        path: '/pageB',
        component: PageB
      }]
    }
  ]
})
```







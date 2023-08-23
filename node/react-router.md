# react router

版本 6

## 基本概念
- 路由器 `<BrowserRouter>` 和 `<HashRouter>` 
    - `<BrowserRouter>` 和 `<HashRouter>` 路由 创建 history 对象
    - `<BrowserRouter>` 每一个URL都要在服务器端都要有响应
    - `<HashRouter>`  URL 带# 服务器响应#之前 客户端渲染#
    - 不同之处：存储URL和响应服务器
- 路由匹配器`<Route>` 和 `<Switch>`
    -  `<Switch>` 呈现找到的第一个Route
- 导航`<Link to="">`  `<NavLink to="">` `<Redirect to="">`

  > 路由模式： history `<BrowserRouter>` 和 `<HashRouter>`hash


## bash

```bash
yarn add react-router-dom
```

## idea

- BrowserRouter 包裹 `<APP>`(根组件) 路由是整个项目
- 使用hook的组件必须是先包裹在Router中的
```html
<!-- 路由模式 -->
<Router>
    <!-- 只有第一个与当前 URL 匹配到的子 <Route> 才会被渲染 -->
    <Switch>
        <!-- 路由匹配 -->
        <!--path
            exact
          -->
        <Route exact path='/'>
            <!-- 页面跳转 -->
            <Link></Link>
        </Route>
        <!-- 动态路由 -->
        <Route path="/:id">
            <p>ove</p>
        </Route>
        <Route>
            <Link></Link>
        </Route>
    </Switch>
</Router>
```

### Route
- path
  - 如果路由的 path 与当前位置完全匹配时，一个 `match 对象 `就会被创建
- exact
- 渲染路由： 1-子组件 2-属性 component/element
- 当使用 component 属性来渲染路由时，`match 、location 及 history `这些路由属性是隐式地传给被渲染的组件的
- 子组件可以使用hook来取`match 、location 及 history `
### 嵌套路由/动态路由
- 带路径参数
### 权限路由
- Redirect：to= {pathname:'/xxx',state:{from:location}}
- state:{from:location}存储当前位置信息
- pathname:'/xxx' 重定向的地址

### hooks
- useRouteMatch() 
    - {path, url, params{}}
    - match.path指的是返回当前组件所对应的path 路径参数形参 url/:name
    - match.url指的是当前组件真实的url 路径参数实参 url/shoes
- useParams() 
    - {param: } 来自Route:path={xx/:param} 路径参数键值对
- useLocaton()
    - 当前url的location对象，url改变时会更新 {pathname:'/xx',state:{}}
    - 配合Redireact
- useHistory() 
    - 返回history对象可以导航 history.push('/pathname')
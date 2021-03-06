# angular Route导航

| 名称 | 简介 |
| - | :---: |
| Routes | 路由的配置信息|
| RouterOutlet | 路由的展示容器 |
| Router | 路由执行对象，可以用其navigate(),navigateByUrl()跳转指定路由 |
| RouterLink | html中与a标签配合的跳转 |
| ActivatedRoute | 激活的路由对象，保存了路由地址，路由参数等 |

## 路由时传递参数

| 方式 | 写法 |
| - | :---: |
| 在查询参数中传递参数 | /product?id=1&name=2 => ActivatedRoute.queryParams[id] |
| 在路由路径传递参数 | {path:/product/:id} =>/product/1 => ActivatedRoute.params[id] |
| 在路由配置传递参数 | {path:/product,component:ProductComponent,data:[{isProd:true}]} => ActivatedRoute.data[0][isProd] |

## 路由重定向
``` javascript
  { path: '', redirectTo: '/home', pathMatch: 'full' },
  { path: 'home', component: HomeComponent },
```

## 子路由
> children属性，其他配置同上一层
> router-outlet 写到对应的父路由中

``` javascript
  {path:'product', component: ProductComponent,children:[
    { path: '', component: ProductDscComponent },
    { path: 'seller/:id', component: SellerInfoComponent },
  ]},
```

## 辅助路由
```
<router-outlet></router-outlet>
<router-outlet name="aux"></router-outlet>

{path:'xxx', component:XxxComponent, outlet:'aux'}
{path:'yyy', component:YyyComponent, outlet:'aux'}

<a [routerLink] ="['/home', {outlets:{aux: 'xxx'}}]">Xxx</a>
<a [routerLink] ="['/product', {outlets:{aux: 'yyy'}}]">Yyy</a>
```
## 路由守卫

| 名称 | 简介 |
| - | :---: |
| CanActivate | 处理导航到某处的路由|
| CanDeactivate | 处理从当前路由离开的情况 |
| Resolve | 路由激活前获取路由情况 |










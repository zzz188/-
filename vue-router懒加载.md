# vue-router懒加载

## 异步加载

component:resolve => require(['组件路径'],resolve),

resolve是vue-router的懒加载属性，主要用于异步加载只加载需要用的组件，此外还有新写法。

const about = () => import('组件路径')  或
component：（）=> import（'组件路径')
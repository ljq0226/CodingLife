

## Discribing the UI

###  Your First Component



####   What a component is

组件是 React 应用程序的基础、核心概念，通过在各个组件中编写UI，代码逻辑，再将组件以HTML标签的形式组合起来构建应用。

####     What role components play in a React application

React 应用是由各个组件所构成的

####   How to write your first React component
```jsx
//组件命名需首字母大写
export default function Profile(){
	return (
		<> //最外层需要一个包裹标签
			<div>Hello React!</div>
		</>
	)//在return 后面的所有代码将会被忽略
} 
```

+ 组件在 Browser 中被渲染成return 返回的HTML元素
+ 如果组件结构较大，可分解为多个子组件，嵌套使用

### Importing and Exporting Components

####   What a root component file is
应用入口文件为 root Component (不同框架入口文件不同)

####  How to import and export a component

```
分为两种，默认导出(default) 和具名导出(named)
export default function Test {} 引入 import Test from './Test.jsx'

  	
export function Test {} 引入 import {Test} from './Test.jsx'
```


-   Why React mixes markup with rendering logic
-   How JSX is different from HTML
-   How to display information with JSX
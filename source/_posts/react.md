---
title: react 学习
date: 2017-07-15 23:30:00
tags: react
comments: true
---

#### 父组件向子组件传函数

定义父组件
<!-- more -->

```jsx
import React,  from 'react'
import Test from './Test'

export default class UIForm extends PureComponent {
handleChange = (e) => {
    console.log(e)
  }
  render () {
    return (
      <div>
        <div>
           <Test handleChange={this.handleChange} />
        </div>
      </div>
    )
  }
}
```

定义子组件
```jsx
import React from 'react'

export default class Test extends React.Component {
  onChange =(e) => {
    this.props.handleChange(e.target.value)
  }
  render () {
    return <input ref={(ref) => (this.ref = ref)} onChange={(e) => this.props.handleChange(e.target.value)} />
  }
}
```

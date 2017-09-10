---
title: react-study
date: 2017-09-10 15:38:20
tags: react
---
> react首先面临的问题就是如何实现组件之间的传值，首当其冲就是父子组件之间的传值，原来是用angular开发，自从接触到react发现，更喜欢这种开发方式，感觉很舒服。
<!--  more -->

- 父组件向子组件传值比较简单的，this.props就能实现，具体实现方式为：

```js
//子组件
//在子组件中直接用this.props.dataPlaceholder将值传递过来并且用placeholder接收
class InputComponent extends Component {

  render() {
    return(
      <Input style = { InputStyle } placeholder={this.props.dataPlaceholder} onChange={this.props.onChange} onBlur={this.props.inputOnBlur}/>
    )
  }
}

export default InputComponent;

//父组件
//父组件中定义一个名为dataPlaceholder的自定义属性
class NewCouponName extends Component {

  render() {
    // const { onChange }
    return(
      <div className="coupon-input">
        <span>*名字</span>
        <InputComponent dataPlaceholder="10个字以内" onBlur={this.inputOnBlur} />
      </div>
    )
  }
}

export default NewCouponName
```
- 子组件想父组件传参

```js
//父组件
//在父组件中要写一个方法来接收子组件传过来的值

  //  接收搜索的函数
   handleSearchValue(params){
     let searchData = this.state.searchData;
     const pagination = { ...this.state.pagination }
     this.setState({
       pagination:{
         current:1,
       },
       page:1,
       searchData:{
         ...params,
       }
     },()=>{
       let {searchData } = this.state;
       this.getData({
           pageSize: pagination.pageSize,
           page: 1,
           ...searchData,
         });
     });
   }

  //子组件
  //子组件在获取值的时候，调用父组件传过来的方法，并将获取的值传递过去

   handleSearch = (e) => {
    e.preventDefault();
    this.props.form.validateFields((err, value,) => {
      if (err) {
        return;
      }
      // 将子组件search文件中的值，传给父组件
      this.props.handleSearchValue({
        ...values,
      })
    });

  }
```
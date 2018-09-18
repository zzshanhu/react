```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import './index.css';

  class LikeButton extends Component{
    /*
    * defaultProps是对props中各个属性的默认配置
    * 组件没有属性传进来，会直接显示默认属性
    * */
      static defaultProps = {
          likedText: '取消',
          unLikedText: '点赞'
      };
    constructor() {
        super();
        //state实例对象，在构造函数里面初始化
        this.state = {isLiked: false};
    }
    /*
      * setState方法由父类Component提供，当调用这个函数时，
      * React.js会更新组件的状态state，并且重新调用render方法，再把render方法所渲染的最新内容显示到页面上
      * 只能用此方法修改组件的状态，接受一个对象或者函数作为参数
      * */
    handleClickOnLike(){
    /*
    * 调用state时，state不会马上被修改，而是先把这个对象放在一个更新队列里面，稍后提取并合并state
    * */
      console.log(this.state.isLiked);

      // this.props.likedText = '取消';  一旦props穿件来就不能改变

      this.setState((prevState) => {
        return {
            isLiked: !this.state.isLiked,
            count: 0, //prevSate返回count为0
        }
      });

      this.setState((prevState) => {
        return {
            count: prevState.count + 1, //prevSate返回count为1
        }
      });

      this.setState((prevState) => {
        return {
            count: prevState.count + 2, //prevSate返回count为3
        }
      });
      /*
      * 以上进行了三次setState，实际上组件只会重新渲染一次
      * 消息队列的同一个消息中的setState先进行合并再重新渲染组件
      * 因此不需要担心多次进行setState会带来的性能问题
      * */
      console.log(this.state.isLiked);
      console.log(this.state.count);
  }
  render(){
    /*
    * 组件内部通过this.props的方式获取到组件的参数
    * 如果this.props里有需要的属性就采用相应的属性，没有就用默认的属性
    * 在使用组件时，可以把参数放在标签的属性当中，所有的属性都会作为props对象的键值
    * 任何类型的数据都可以作为组件的参数，包括字符串、数字、对象、数组甚至函数
    * */
    const likedText = this.props.likedText || '取消';
    const unLikedText = this.props.unLikedText || '点赞';
    return(
        <button onClick={this.handleClickOnLike.bind(this)}>
            {this.state.isLiked ? likedText : unLikedText}
        </button>
    )
  }
}

ReactDOM.render(
    <LikeButton likedText="已赞" unLikedText="点赞"/>,
    document.getElementById('root')
);
```

```
import React, { Component } from 'react';
import ReactDOM from 'react-dom';
import './index.css';

const users = [
    { username: 'hahaha', age: '21', gender: 'male'},
    { username: 'heihei', age: '22', gender: 'male'},
    { username: 'xixixi', age: '23', gender: 'female'},
    { username: 'hehehe', age: '24', gender: 'female'}
];

/*
* 把展示用户数据的JSX结构抽离成一个组件User
* 通过props把user数据作为组件的配置参数传进去
* 对于用表达式套数组罗列到页面上的元素，都要为每个元素加上key属性，必须是每个元素唯一的标识
* */
class User extends Component{
  render(){
    const { user } = this.props;
    return(
        <div>
          <div>姓名：{user.username}</div>
          <div>年龄：{user.age}</div>
          <div>性别：{user.gender}</div>
          <hr />
        </div>
    )
  }
}
class Index extends Component{
  render(){
    return(
        <div>
            {users.map((user, i) => <User key={i} user={user}></User>)}
        </div>
    )
  }
}

ReactDOM.render(
    <Index />,
    document.getElementById('root')
);
```

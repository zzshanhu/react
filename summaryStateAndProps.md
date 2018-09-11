## state VS props
（一） state   
   1.主要用于组件保存、控制、修改自己的可变状态。   
   2.在组件内部初始化，可以被组件资深修改，外部不能访问也不能修改。   
   3.通过this.setState方法进行更新，setState会导致组件重新渲染。   
   4.没有state的组件叫无状态组件，设置了state的叫做有状态组件。
   5.状态会带来管理的复杂性，为了降低代码维护的难度，和增加组件的可复用性，尽量多地写无状态组件，尽量少地写有状态组件。
（二） props   
   1.主要作用是让使用该组件的父组件可以传入参数来配置该组件。   
   2.是外部传进来的配置参数，组件内部无法控制也无法修改。   
   3.除非外部组件主动传入新的props，否则组件的props永远保持不变。   
 #### 一个组件的state中的数据可以通过props传给子组件，一个组件可以使用外部传入的props来初始化自己的state。
 #### state是让组件控制自己的状态，props是让外部对组件自己进行配置
···
   class HelloWorld extends Component {
      constructor(){
         super()
      }
      sayHi(){
         alert('Hello World');
      }
      render () {
       return (
         <div onClick={this.sayHi.bind(this)}>Hello World</div>
       )
     }
   }
···

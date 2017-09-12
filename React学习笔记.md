##React笔记

###1、安装

```
1、安装 createReactApp : npm install -g create-react-app
2、创建工程项目 ：create-react-app my-app
3、启动项目：cd my-app/    npm start
```

###2、定义组件

```
import React from 'react';	//导入React

//定义并导出CommentBox类，集成自React.Component
export default class CommentBox extends React.Component{
    render(){ //重写render方法，进行布局
        return(
            <div className="ui commentBox">
                <h1>评论</h1>
                <div className="ui devider"></div>
            </div>
         )
    }
}
```

###3、组件组合

```
//CommentList类

import React from 'react';

export default class CommentList extends React.Component{
    render(){
        return(
            <div className={"ui commentForm"}>
            评论列表
            </div>
        )
    }
}
```

```
//CommentForm类

import React from "react";

export default class CommentForm extends React.Component{
    render(){
        return(
            <form className={"ui commentForm"}>
                <div className={"field"}>
                    <input type={"text"} placeholder={"姓名"}/>
                </div>
                <div className={"field"}>
                    <input type={"text"} placeholder={"评论"}/>
                </div>
                <button type={"submit"} className={"ui blue button"}>
                    添加评论
                </button>
            </form>
        )
    }
}
```

//将CommentList和CommentForm 组合到 CommentBox

```
import React from 'react';	//导入React

//定义并导出CommentBox类，集成自React.Component
export default class CommentBox extends React.Component{
    render(){ //重写render方法，进行布局
        return(
            <div className="ui commentBox">
                <h1>评论</h1>
                <div className="ui devider"></div>
                <CommentForm />	//将CommentForm添加到 CommentBox
                <CommentList /> //将CommentList添加到 CommentBox
            </div>
         )
    }
}
```

###4、属性props
给CommentList添加评论数据

```
//CommentNode类,用于显示每一条评论的信息
impirt React from 'react';

export default class CommentNode extends React.Component{
	render(){
		return(
			<div className='ui comment node'>
				<div className='content'>
					//auther显示的内容从父节点传递过来
					<span className='auther'>{this.props.auther}</span>
				</div>
				<div className='metadata'>
					//data显示的内容从父节点传递过来
					<spann className='data'>{this.props.data}</span>
				</div>
				//text显示的内容从父节点传递过来
				<div className='text'>{this.props.children}</div>
			</div>
		)
	}
}
```

```
//CommentList类

import React from 'react';
import CommentNode form 'CommentNode';

export default class CommentList extends React.Component{
    render(){
        return(
            <div className={"ui commentForm"}>
            		//定义CommentNode组件，会将auther、data、children传递给CommentNode组件，
            		<CommentNode auther="xiaobai" data="1分钟">你好</CommentNode>
            		<CommentNode auther="xiaohong" data="2分钟">你也好</CommentNode>
            </div>
        )
    }
}
```

###5、从爸爸获取数据

```
//index.js
//假设 comment 数据是从服务器获取的
var comment = [
    {"auther":"xiaobai", "data":"1分钟前", "text":"你好"},
    {"auther":"xiaohong", "data":"2分钟前", "text":"你好"},
];

//给CommentBox 添加data属性，将 comment数据传递给CommentBox
ReactDOM.render(<CommentBox data={comment}/>,
    document.getElementById('root'));
      
      
//CommentBox
export default class CommentBox extends React.Component{
    render() {
        return(
            <div className="ui commentBox">
                <h1>评论</h1>
                <div className="ui devider"></div>
                
                //为 CommentList 添加data属性，并将上层传递下来的data属性 传递给CommentList
                <CommentList data={this.props.data}/>
                <CommentForm/>
            </div>
        )
    }
}


//CommentList
export default class CommentList extends React.Component{
    render(){
			
		//获取上层传下来的data数据
        let comments = this.props.data.map(comment =>{
            return (
            
                //将data数据解析，赋值给CommentNode的属性
                <CommentNode auther={comment.auther} data={comment.data}>
                    {comment.text}
                </CommentNode>
            );
        });

        return(
            <div className={"ui commentForm"}>
                {comments}
            </div>
        )
    }
}

//CommentNode 获取各个属性并显示
export default class CommentNode extends React.Component{
    render(){
        return(
            <div className={'ui comment node'}>
                <div className={'content'}>
                    <span className={'auther'}>{this.props.auther}</span>
                </div>
                <div className={'metadata'}>
                    <span className={'data'}>{this.props.data}</span>
                </div>
                <div className={'text'}>{this.props.children}</div>
            </div>
        )
    }
}
```

###6、组件状态state、setState
state是组件的私有属性，可以通过this.state访问组件的state；this.setState设置组件的state，组件的状态改变后组件会自动更新；

```
//安装jQuery 
 jspm install jquery
```
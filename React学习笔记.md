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

###4、从爸爸获取数据
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
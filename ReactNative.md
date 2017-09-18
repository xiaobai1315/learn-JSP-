###安装RN
```
1、安装Node.js : brew install node
2、安装RN命令行工具：npm install -g react-native-cli
3、新建项目：react-native init appName;
```

###创建样式

```
export default class reactnativeapp extends Component{
	render(){
		return(
			<View>
				style={{
					backgroundColor:'red',
					height:100,
				}}
			</View>
		);
	}
}


//使用样式
<View style=styles.container>
	<Text style=styles.title></Text>
</View>

//通过StyleSheet定义样式
let styles = StyleSheet.create({
	container:{
		backgroundColor:'red',	//背景色
		height:100,	//高度
		margin:30,	//view周围的边距
        borderWidth:1,	//边框宽度
        borderColor:'black',	//边框颜色
        borderRadius:15,	//圆角
        shadowColor:'green',	//阴影颜色
        shadowOpacity:0.6,	//阴影透明度
        shadowOffset:{	//阴影的偏移
            height:1,
            widget:0
        },
    title:{
    	 fontSize:30,	//字体大小
        color:'green',	//字体颜色
        textAlign:'center',	//对齐方式
        fontStyle:'italic',	//字体
        letterSpacing:2,	//字间距
        lineHeight:33,	//行高
        fontFamily:'Helvetica Neue',	//字体
        fontWeight:'300',	//字体加粗
        textDecorationLine:'underline',	//下划线
        textDecorationStyle:'double',	//下划线样式
    }
        
	}
});


//padding 是内边距
//margin 是外边距
```

###布局 Flexbox
view中添加3个View，设置他们的布局

```
export default class reactnativeapp extends Component{
    render(){
        return(
            <View style={styles.container}>
                <View style={[styles.item, styles.itemOne]}>
                    <Text style={styles.itemText}>1</Text>
                </View>

                <View style={[styles.item, styles.itemTwo]}>
                    <Text style={styles.itemText}>2</Text>
                </View>

                <View style={[styles.item, styles.itemThree]}>
                    <Text style={styles.itemText}>3</Text>
                </View>

            </View>
        );
    }
}

let styles = StyleSheet.create({
    container:{
        justifyContent:'space-between',   
        
        backgroundColor:'red',
        flex:1,
        paddingTop:23,
        alignItems:'baseline'  //flex-start flex-end center stretch baseline
    },
    item:{
        backgroundColor:'white',
        borderWidth:1,
        borderColor:'black',
        margin:10
    },
    itemOne:{},
    itemTwo:{},
    itemThree:{},
    itemText:{
        fontSize:33,
        fontFamily:'Helvetica Neue',
        fontWeight:'200',
        padding:30,
    },
});

```

###FlexBox 布局内容
在React中，Flexbox有6种容器属性，6种项目属性。而在React Native中，有4个容器属性，2个项目属性，分别是：

容器属性：flexDirection   flexWrap   justifyContent  alignItems

项目属性：flex  alignSelf

####flexDirection容器属性: `row | row-reverse | column | column-reverse`

```
该属性决定主轴的方向（即项目的排列方向）。

row：主轴为水平方向，起点在左端。

row-reverse：主轴为水平方向，起点在右端。

column(默认值)：主轴为垂直方向，起点在上沿。

column-reverse：主轴为垂直方向，起点在下沿。
```

####3.2:flexWrap容器属性: `nowrap | wrap | wrap-reverse`

```
默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。

nowrap(默认值)：不换行
wrap：换行，第一行在上方
wrap-reverse：换行，第一行在下方。（和wrap相反）

```


####3.3:justifyContent容器属性: `flex-start | flex-end | center | space-between | space-around`

```
定义了伸缩项目在主轴线的对齐方式

flex-start(默认值)：伸缩项目向一行的起始位置靠齐。

flex-end：伸缩项目向一行的结束位置靠齐。

center：伸缩项目向一行的中间位置靠齐。

space-between：两端对齐，项目之间的间隔都相等。

space-around：伸缩项目会平均地分布在行里，两端保留一半的空间。
```

####3.4:alignItems容器属性: `flex-start | flex-end | center | baseline | stretch`

```
定义项目在交叉轴上如何对齐，可以把其想像成侧轴（垂直于主轴）的“对齐方式”。

flex-start：交叉轴的起点对齐。

flex-end：交叉轴的终点对齐 。

center：交叉轴的中点对齐。

baseline：项目的第一行文字的基线对齐。

stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
```

####3.5:flex项目属性:

```
“flex-grow”、“flex-shrink”和“flex-basis”三个属性的缩写， 其中第二个和第三个参数（flex-shrink、flex-basis）是可选参数。默认值为“0 1 auto”。

宽度 ＝ 弹性宽度 * ( flexGrow / sum( flexGorw ) )
```


####3.6:alignSelf项目属性:

“auto | flex-start | flex-end | center | baseline | stretch”

```
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。

默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
```

###资料

```
http://www.cnblogs.com/wujy/p/5841685.html
```

###自定义文本组件
`注意：自定义的组件必须要用大写字母开头，否则会报错`

```
class HeaderText extends Component{
    render(){
        return(
            <Text>
                {this.props.children}
            </Text>
        );
    }
}

export default class reactnativeapp extends Component{
    render(){
        return(
            <View style={styles.container}>

                <HeaderText>
                    good morning
                </HeaderText>

            </View>
        );
    }
}
```

###Image

```
<Image 
	style=styles.image
	source={{url:'www.'}}
/>
	
let styles = StyleSheet.create{
	image:{
		width:100,
		height:100,
		margin:10
	}
}
```

###view
属性

1：allowFontScaling bool（iOS特有）：控制字体是否要根据iOS的“文本大小”辅助选项来进行缩放。

2：numberOfLines number ：用来当文本过长的时候裁剪文本。包括折叠产生的换行在内，总的行数不会超过这个属性的限制；

3：onLayout function：当挂载或者布局变化以后调用，参数为如下的内容：{nativeEvent: {layout: {x, y, width, height}}}

4：onPress function：当文本被点击以后调用此回调函数

5：testID string：用来在端到端测试中标记这个视图。

6：suppressHighlighting bool（iOS特有）：当为true时，如果文本被按下，则没有任何视觉效果。默认情况下，文本被按下时会有一个灰色的、椭圆形的高光

```
<View style={styles.view1}>
                    <Text style={styles.text}
                          numberOfLines={2}  //文本的行数
                          onPress={()=>{  //文本点击事件
                              AlertIOS.prompt('Secure Text', null, null, 'secure-text')
                          }}
                          suppressHighlighting={true}  //文本点击后是否高亮，
                          onLayout={()=>{  //文本挂载或重新布局时调用，类似iOS的 lauouySubviews,文字字体改变也会触发这个事件
                              AlertIOS.prompt('Secure Text', null, null, 'secure-text')
                          }}
                    >
                        行宫
                        唐代：元稹
                        寥落古行宫，宫花寂寞红。
                        白头宫女在，闲坐说玄宗。
                    </Text>
                </View>

```

样式style

1：color string

2：fontFamily string

3：fontSize number

4：fontStyle enum('normal', 'italic')

5：fontWeight enum("normal", 'bold', '100', '200', '300', '400', '500', '600', '700', '800', '900')

指定字体的粗细。大多数字体都支持'normal'和'bold'值。并非所有字体都支持所有的数字值。如果某个值不支持，则会自动选择最接近的值。

6：letterSpacing number 字符间距

7：lineHeight number 行高

8：textAlign enum("auto", 'left', 'right', 'center', 'justify')

指定文本的对齐方式。其中'justify'值仅iOS支持。

9：（android） textAlignVertical enum('auto', 'top', 'bottom', 'center')

10：（ios）textDecorationColor string  线的颜色

11：textDecorationLine enum("none", 'underline', 'line-through', 'underline line-through') 横线位置

12：（ios）textDecorationStyle enum("solid", 'double', 'dotted', 'dashed')  线的样式

13：（ios）writingDirection enum("auto", 'ltr', 'rtl')  文字方向
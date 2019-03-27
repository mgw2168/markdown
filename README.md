# markdown基本语法

## 1.标题

```
# 一级标题  注意：符号跟文字之间有空格
## 二级标题
### 三级标题
...... 以此类推
```

## 2.分割线

```
*** 或 ---
```

## 3. 块引用

```
> 块引用
> * 块内列表
```

效果如下：

> 块引用
>
> - 块内列表

------

## 4. 表格

```
字段 | 名称 |     列表     
:--: | :--: | :---------: 
 id  |      | 主键，自增长 
name | 名字 |              
age  | 年龄 |              注： 其中冒号‘：’表示以什么方式居中
```

**也可以使用：Ctrl+t快速插入表格**



| 字段 | 名称 |     备注     |
| :--: | :--:| :----------: |
|  id  |      | 主键，自增长 |
| name | 名字 |              |
| age  | 年龄 |              |

## 5. 插入代码段

```
使用 ``` 或者 *** 回车即可
```

例如：

```python
def aaa(n):
	print('hello world!)
```

## 6. 插入链接

```
使用 [链接文字](链接地址)
例如： [百度](https://www.baidu.com/)
```

效果如下：

链接： [百度](http://www.baidu.com/"百度一下") 

## 7.插入表情：

使用`:happy:`输入高兴的表情，使用`:sad:`输入悲伤的表情，使用`:cry:`输入哭的表情等。以此类推！

:happy:

:pensive:

:cry:

## 8.下划线：

用HTML的语法，`<u>underline</u>` 将产生下划线

效果：<u>有下划线的文字</u>

## 9. 删除线：

使用 `~~ ` 包裹文字：**注意英文下输入**

效果: ~~删除线~~

## 10. 强调内容：

```Chinese
**使用两个 * 号强调的内容**
__使用两个下划线强调内容__	     注：符号和文字之间没有空格
```

效果如下：

**使用两个` * ` 号强调的内容**

__使用两个` _` 号强调的内容__

## 11. 斜体

标准的 Markdown 中` *`和 `_ ` 包裹的内容会斜体显示 ，也就是一对单星号*

效果： *斜体显示*

## 12. 插入图片

插图的最基础格式是：

```
![Alt text](图片链接 "optional title")
```

> Alt text：图片的Alt标签，用来描述图片的关键词，可以不写。最初的本意是当图片因为某种原因不能被显示时而出现的替代文字，后来又被用于SEO，可以方便搜索引擎根据Alt text里面的关键词搜索到图片。 图片链接：可以是图片的本地地址或者是网址。"optional title"：鼠标悬置于图片上会出现的标题文字，可以不写。

#### 1. 插入本地图片

只需要在基础语法的括号中填入图片的位置路径即可，支持绝对路径和相对路径。
例如：

```
![avatar](/home/picture/1.png)
```

> 缺点：
>
> 不灵活不好分享，本地图片的路径更改或丢失都会造成markdown文件调不出图。

#### 2. 插入网络图片

只需要在基础语法的括号中填入图片的网络链接即可，现在已经有很多免费/收费图床和方便传图的小工具可选

```
![avatar](http://www.pptok.com/wp-content/uploads/2012/08/xunguang-4.jpg)
```

效果图：

![avatar](http://www.pptok.com/wp-content/uploads/2012/08/xunguang-4.jpg)

> 缺点：
>
> 图片存在网络服务器，比较依赖网络

#### 3. 把图片存入markdown文件

##### A: 用base64转码工具把图片转成一段字符串，然后把字符串填到基础格式中链接的那个位置。

- 基础用法：

  `  ![avatar](data:image/png;base64,iVBORw0......` 

  这个时候会发现插入的这一长串字符串会把整个文章分割开，非常影响编写文章时的体验。如果能够把大段的base64字符串放在文章末尾，然后在文章中通过一个id来调用，文章就不会被分割的这么乱了.

- 高级用法：

  比如：

  ` ![avatar][base64str]`

  ` [base64str]:data:image/xxx.png;base64,iVBORw0......`

##### B: 最后，怎么得来base64的图片编码？？

1. 使用python 将图片转化为 base64 字符串

   ```python 
   import base64
   f=open('723.png','rb') #二进制方式打开图文件
   ls_f=base64.b64encode(f.read()) #读取文件内容，转换为base64编码
   f.close()
   print(ls_f)
   ```

2. base64字符串转化为图片

   ```python
   import base64
   bs='iVBORw0KGgoAAAANSUhEUg....' # 太长了省略
   imgdata=base64.b64decode(bs)
   file=open('2.jpg','wb')
   file.write(imgdata)
   file.close()
   ```

#### 4. 当然这不是最好的办法

最好的办法是你将图片上传到第三方平台，比如七牛云，百度云，京东云，网易云等，将获取图片链接，填入即可

**具体方法百度:  [markdown结合图床神器](http://www.baidu.com/s?ie=utf-8&f=3&rsv_bp=1&rsv_idx=1&tn=baidu&wd=%20markdown%E7%BB%93%E5%90%88%E5%9B%BE%E5%BA%8A%E7%A5%9E%E5%99%A8&oq=markdown%2520%25E7%25BB%2593%25E5%2590%2588%25E5%259B%25BE%25E5%25BA%258A%25E7%25A5%259E%25E5%2599%25A8&rsv_pq=ac633d3700011371&rsv_t=58d1djLjxHVXex6%2FCgPqp6sdzwOVqeLmAf%2FpYGfmf7EtY1A%2BebN4kg195u4&rqlang=cn&rsv_enter=0&inputT=7556&rsv_sug3=270&prefixsug=%2520markdown%25E7%25BB%2593%25E5%2590%2588%25E5%259B%25BE%25E5%25BA%258A%25E7%25A5%259E%25E5%2599%25A8&rsp=0&rsv_sug4=9746&rsv_sug=1) **

**MPic-图床神器下载链接：** [点击链接下载](http://mpic.lzhaofu.cn/)

## 13. 任务列表

```
-[ ] 吃饭
-[ ] 逛街
-[ ] 看电影

语法： 
-[空格]空格 文字—–代表没有选中的复选框
-[x]空格 文字——代表选中的复选框
```

## 14. 列表：

输入+, -, *,创建无序的列表，使用任意数字开头，创建有序列表，例如：

```
**无序列表:热门语言排行榜**
* java
* python
* C
```

**无序列表:热门语言**

- java
- python
- C

## 15. 实现页内跳转

```python
# 1. 定义锚点
<span id="jump">请点击跳转</span>

# 2. 使用markdown语法
[要跳转到的内容](#jump)
```

## 16. 实现目录
**在要生成目录的地方写：[TOC]  即可按照标题生成目录
有些markdown编辑器需要写： @[TOC]** 
> 案例：
 ```
 [TOC]
 
#  马什么梅
## 马冬梅
### 马冬什么
#### 马冬梅
##### 什么冬梅
###### 马冬梅
 ```
**效果图:**

![效果图](images/image01.png)

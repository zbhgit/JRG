## form表单简单介绍
form元素表示了文档中一个区域，这个区域包含交互控制元件，用来向web服务器提交信息

> 简单示例

```
	<!-- 其中用到的属性
    	action：表单提交信息到指定的URL处理
    	name： 设定当前表单标识
    	method：设置提交信息的方式，有get和post两种方式
    	 -->
    	<form action="url" name="form" method="GET" enctype="multipart/form-data">
    		<input type="text" name="username">
    	</form>
```
[更多属性请参考](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Forms)


### form表单中常用的标签

首先介绍 input 标签

> 单行文本域 type属性 text
 
 ```
     <label>用户名：</label>
     <input type="text" name="username" placeholder="请输入用户名">
 ```
        
    
显示效果
    
   <label>用户名：</label><input type="text" name="username" placeholder="请输入用户名">

----------

> 密码域 type属性 password

 ```
     <label for="password">姓名：</label>
     <input type="password" id="password" placeholder="请输入密码">
 ```
        
    
显示效果
    
   <label for="password">姓名：</label>
                   <input type="password" id="password" placeholder="请输入密码">

----------

> 单选框 type属性 radio

 ```
     <label>性别：</label>
     <input type="radio" name="sex" value="男">男
      <input type="radio" name="sex" value="女">女
 ```
        
    
显示效果
    
   <label>性别：</label>
   <input type="radio" name="sex" value="男">男
   <input type="radio" name="sex" value="女">女

----------

> 复选框 type属性 checkbox

 ```
      <label>爱好：</label>
      <input type="checkbox" name="hobby" value="sing">唱歌
      <input type="checkbox" name="hobby" value="dance">跳舞
      <input type="checkbox" name="hobby" value="play">玩
 ```
        
    
显示效果
    
<label>爱好：</label>
     <input type="checkbox" name="hobby" value="sing">唱歌
      <input type="checkbox" name="hobby" value="dance">跳舞
      <input type="checkbox" name="hobby" value="play">玩

----------

> 按钮 type属性 button，submit, reset

 ```
     <input type="button" value="普通按钮">
     <input type="submit" value="提交按钮">
     <input type="reset" value="重置按钮">

 ```
        
    
显示效果
    
   <input type="button" value="普通按钮">
   <input type="submit" value="提交按钮">
   <input type="reset" value="重置按钮">

----------

> 隐藏域 属性

 ```
     <input type="hidden" name="field＿name" value="value">
 ```
        
    
显示效果：这个是不可见的
    
   <input type="hidden" name="field＿name" value="value">
  

----------



> select标签简单示例

 ```
      <label >MyCar</label>
      <select name="car" >
          <option value="boyue">博越</option>
          <option value="borui">博瑞</option>
          <option value="lingke">领克</option>
      </select>
 ```
        
    
显示效果
    
   <label >MyCar</label>
         <select name="car" >
             <option value="boyue">博越</option>
             <option value="borui">博瑞</option>
             <option value="lingke">领克</option>
         </select>

----------

> 多行文本域

 ```
     <label >留言：</label>
     <textarea name="article" id="" cols="30" rows="10">
         多行文本
     </textarea>
 ```
        
    
显示效果
    
  <label >留言：</label>
                  <textarea name="article" id="" cols="30" rows="10">
                      多行文本
                  </textarea>

----------


    这次只是简单记录，并有介绍各个标签及其属性的详细特点
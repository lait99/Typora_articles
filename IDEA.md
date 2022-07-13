# IDEA

## 1.IDEA修改字体大小

​	file==>settings 搜索"change font size"==》edit

## 2.设置编码

​	file==>settings 搜索"encoding"==》File Encodings

## 3.设置jdk

​	file==>Project Structure

## 4.设置主题

​	file==>settings 搜索"theme"

## 5.设置小写也进行代码提示

​	file==>settings 搜索"completion"==》code complation，取消Match case

## 6.开启自动导包

​	file==>settings 搜索"auto import"==》auto import,全勾
​	只有一个包的自动导，多个的不会自动导入

## 7.设置行注释“//”放在行最前方还是代码前

​	file==>settings 搜索"code style"==》java==》Code Generation ==》Comment Code,
​	勾选“Line comment at first column”，在行前
​	取消勾选，在代码前

## 8.快捷键兼容，设置其他开发工具快捷键模式，例如eclipse等

​	file==>settings 搜索"keymap"==》eclipse
​	自定义快捷键

### 	1）Alt+/		//代码提示

​		file==>settings 搜索"keymap"==>搜索"complation"==》basic

### 	2）Alt+Shift+S	//生成代码，get,set,构造方法等

​		file==>settings 搜索"keymap"==>搜索"Generate"==》Code==》Generate

### 	3）Alt+Shift+R（新版已设置）	//改名字	

​		file==>settings 搜索"keymap"==>搜索"rename"

### 	4）Ctrl+1（新版已设置）	//提示，代码报错等解决方案

​		file==>settings 搜索"keymap"==>搜索"intention"

### 	5）	Ctrl+2，L	//自动补充接收返回值

​		file==>settings 搜索"keymap"==>搜索"variable"

### 	6）Ctrl+N	//new

​		file==>settings 搜索"keymap"==>搜索"new"

### 	7）Ctrl+F	//查找

​		搜索"find"

### 	8）Ctrl+R	//替换

​		搜索"replace"

### 	9）Ctrl+M	//全屏

​		搜索"hide all"==>hide all tool windows

### 	10）Ctrl+上/下	//行上移

​		搜索"move line"

### 	11）Alt+Ctrl+下	//复制

​		搜索"duplicate line"
​		关闭快捷键ctrl+alt+方向键旋转屏幕
​		Alt+Ctrl+F12打开显卡控制面板关闭

### 	12）两次 Shift	//搜索全部

​	

## 9.常用快捷键

​	1）Ctrl+Shift+T	//搜索类
​	2）F4	//查看当前类的继承关系

## 10.快速模板

​	file==>settings 搜索"template"==>"Live template"
​	//修改预定义模板
​	main	public static void main(String[] args) {
​	syso	System.out.println();
​	syst	System.out.println("HelloWorld.main");
​	//自定义模板
​	htmlzs:
​	<!-- $aaa$ start -->
​    <!-- $aaa$ end -->
​	//自定义代码模板
​	File | Settings | Editor | File and Code Templates

## 11.其他设置

### 	1）修改过文件标星号

​		File | Settings | Editor | General | Editor Tabs ，勾选Mark modified(*)

### 	2）方法代码只有一行，自动显示为一行

​		File | Settings | Editor | General | Code Folding ， 取消勾选 One-line methods

### 	3）显示行号

​		单个文件：行号列，右击勾选Show Line Numbers
​		全局：File | Settings | Editor | General | Appearance ， 勾选Show Line Numbers

### 	4）软换行

​		单个文件：行号列，右击勾选Soft-Wrap
​		File | Settings | Editor | General , Soft-wrap these files 增加*.java
​		重新打开文件

### 	5）设置代码检查

​		搜索inspection
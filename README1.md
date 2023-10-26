# 学生宿舍管理系统

#### 介绍
JavaWeb学生宿舍管理系统项目

#### 软件架构
基于JSP+servlet+JavaBean三层架构


#### 安装教程
##### 一、配置项目依赖
1. 将src/com/util/DbUtil.java下的userName与userPwd修改为自己的数据库名以及密码。

![img.png](DocImages/img.png)
> **注：** 这一步必须要做，否则会跳转到空白页且控制台报错`java.sql.SQLNonTransientConnectionException: Public Key Retrieval is not allowed`

2. 选择`File`目录下的`ProjectStructure`，配置项目的SDK以及语言。
![img_6.png](DocImages/img_6.png)
   
3. 若模块Modules为空，则点击`+`，选择`Import Module`，选中当前项目`StudentDorm`，然后一直点<kbd>next</kbd>即可。【如果不为空，可跳过Modules配置】

![img_5.png](DocImages/img_5.png)
![img_7.png](DocImages/img_7.png)
![img_9.png](DocImages/img_9.png)
> **注：** 需要注意的是，导入模块时，`Libraries`与`Modules`均只需要导入一次（实测IDEA 2021会导入两次，最后一次应取消选择）
> ![img_10.png](DocImages/img_10.png)
> ![img_8.png](DocImages/img_8.png)

4. 检查`Modules`中`studentDorm`下的`Web`配置，`Deployment Descriptors
   `中的`Path`为`web/WEB-INF/web.xml`，`Web Resource Direciories
   `中的`Web Resource Directory`为`web`文件夹，点击确定后就可以发现，项目中的Web文件有特殊图标。
![img_11.png](DocImages/img_11.png)
![img_14.png](DocImages/img_14.png)

5. 检查`Libraries`中的`lib`资源中是否将`web/WEB-INF/lib`中的所有jar包全部导入。
![img_13.png](DocImages/img_13.png)
   
6. 检查`Facets`中是否有Web依赖，没有的化可以自行添加。
![img_15.png](DocImages/img_15.png)
   
7. 最后，新建`Artifacts`，选择`+`中`Web Application Exploded`下的`From Modules`，选中之前`Mudules`中创建好的项目模块，点击<kbd>ok</kbd>，再将右侧`Available Elements`未放到`Output Root`中的资源放入即可。

![img_16.png](DocImages/img_16.png)
![img_17.png](DocImages/img_17.png)
![img_18.png](DocImages/img_18.png)
![img_19.png](DocImages/img_19.png)
##### 二、配置Tomcat服务器

2. 点击右上角<kbd>Add Configuration</kbd>，选择Tomcat下的Local。

![img_1.png](DocImages/img_1.png)
![img_2.png](DocImages/img_2.png)
![img_3.png](DocImages/img_3.png)

3. 点击当前界面中的<kbd>Configure</kbd>，配置（<font color=red><b>仅支持Tomcat9及以下版本</b></font>）`Tomcat_Home`、`Tomcat base directory`以及`Classes`【其中`classes`是Tomcat的lib目录中的jar包】

<font color=red>Tomcat10相较于Tomcat9发生了一些重要变化，并不向下兼容</font>。所有实现的api的主要包已经从javax变成jakarta。影响了JSP标准标签库（JSTL）的正常使用（JSTL太老了，它是通过旧的Servlet和jsp的包名找对应的方法的，但是新版的tomcat10的包名改了它就找不到了）
![img_4.png](DocImages/img_4.png)

4. 选择`jre`（jdk11以上集成了jre，并没有单独jre，可以直接选择jdk），确认即可
5. 点击`Deployment`中的`+`，添加`Artifact`，点击<kbd>ok</kbd>即可。
![img_20.png](DocImages/img_20.png)
![img_21.png](DocImages/img_21.png)
最后，点击运行。
![img_22.png](DocImages/img_22.png)
> **注:** 如果出现问题，诸如`out目录里面的classes文件夹中java代码都没有被编译`或是`not found for the web module`均可关闭idea，然后删除项目目录下的.idea文件（.iml文件可选删），然后重新打开idea进行配置。

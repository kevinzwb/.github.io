# 配置
- JDK提供对Servlet的支持。编写Servlet时候直接继承HttpServlet，并并覆盖需要的方法即可。

- 除了Servlet类文件，Web容器还需要配置Servlet的类文件与访问方式。这个配置在Web应用程序的描述文件web.xml里完成。
  - <servlet> </servlet>为Servlet配置的开始标签与结束标签，中间部分是一个Servlet的配置信息
  - <servlet-name>
  - <servlet-class>
  - <init-pararm>标签配置一个初始化参数
  - <load-on-startup>配置该Servlet的加载方式
  
- 配置访问方式<servlet-mapping>
  - <servlet-name>：访问方式的名称
  - <url-pattern>: 配置访问方式
  - 可以配置多个<url-pattern>
  
- 利用MyEclipse将程序部署在Tomcat下


# 请求与响应
- Web编程的过程就是通过请求分析客户需要什么信息或者进行了什么操作，然后进行一系列的处理，最后通过响应结果显示给客户。

- 客户端浏览器发出的请求被封装成为一个HttpServletRequest对象。

- 服务器对客户端浏览器做出的响应被封装成一个HttpServletResponse对象。

# 读取web.xml参数
- 初始化参数<init-param>
  - 将常量信息储存在web.xml配置文件。需求变化时只需要修改一下配置文件就可以了，而不会修改源程序，也不会重新编译，维护起来相当方便。
  - 可以把某些变量放在web.xml里，需要修改时，只需要修改web.xml，并重启服务器即可。

- 上下文参数<context-param>

- 资源注射：不需要Servlet主动去读取资源，Tomcat启动的时候会把web.xml里配置信息主动注射到Servlet里。
  - 通过Annotation注解完成。这是一种特殊的接口，以@符号为标志。
  - 注射的原理是通过JNDI（Java Naming and Directory Interface)获取资源.
  
# 提交信息
- Web程序的任务就是实现服务器与客户端浏览器之间的信息交互。Servlet的任务就是正确地获取这些信息，并根据信息做出不同的响应。
- Get用于从服务器获取信息
- Post用于向服务器提交信息
- 相比于FTP文件上传，Web文件上传速度慢一些，但是使用方面，不需要客户端，只需要一个浏览器。
- Web文件上传采用POST的方式，需要设置FORM的enctype属性为multipart/form-data


# 带进度条的文件上传
- UploadServlet只是实现了普通的文件上传，并附带普通文本域的提交。
- 如果需要显示上传进度条，实时显示等，需要配合使用Ajax技术。

- 实时显示上传进度就是服务器在处理上传文件的同时，将上传进度的信息例如文件总长度，以上传多少，传输速率等写入Session中。
客户端浏览器利用Ajax技术再新开一个独立的线程从Session中获取上传进度信息，并实时显示。Ajax技术能够不刷新页面获取服务器数据。

- 上传进度条
- 上传监听器
- 监听上传进度
- 读取上传进度
- 显示上传进度

# 生命周期

- Servlet的生命周期由Web服务器来维护，遵循Servlet规范。
- 服务器会在启动时，或者第一次Servlet时初始化一个Servlet对象，然后用这个Servlet对象去处理所有客户端请求。服务器关闭时才销毁这个Servlet对象。
  - 省去了开辟与销毁Servlet的开销
  - 增加了服务器维护Servlet的复杂度
  
- 无论请求多少次Servlet，最多只有一个Servlet实例。多个客户端并发请求Servlet时候，服务器会启动多个线程分别执行该Servlet的service（）方法。

- 注解

# 跳转
- Servlet之间可以互相跳转，因而可以很容易地把一项任务按模块分开。
- MVC框架中使用Servlet，分为三个独立的模块，业务处理模块，视图模块，控制模块。

- 转向是通过RequestDispatcher对象的forward方法来实现的。forward是MV框架中常用的一种技术。
Forward不仅可以跳转到本应用的另一个Servlet，JSP页面，也可以跳转到另一个文件。

- 重定向利用服务器返回的状态码来实现的。客户端浏览器请求服务器的时候，服务器端会返回一个状态码。服务器端通过HttpServletResponse的setStatus方法设置状态码。

- 自动刷新不仅可以实现一段时间之后自动跳转到另一个页面，还可以实现一段时间之后自动刷新本页面。

# 线程安全

- 由于Servlet只会有一个实例，多个用户同时请求同一个Servlet时候，Tomcat会派生出多条线程执行Servlet的代码，
因此Servlet有线程不安全的隐患。

- 多线程并发读写会导致数据不同步的问题。解决的方法是尽量不要定义name属性，而是要把name变量分别定义到doGet（）与doPost（）方法内。
  - 可以使用synchronized语句块来解决问题，但是会造成线程的等待。
  
# 总结
**在Java Web程序中，Servlet负责接收用户请求HttpServletRequest，在doGet()，doPost()方法中做相应的处理，并将回应HttpServletResponse反馈给用户。
Servlet可以设置初始化参数，供Servlet内部使用。一个Servlet类只会有一个实例，在它初始化时调用init（）方法，销毁时请调用destory()方法
Servlet需要在web.xml中配置，一个Servlet可以设置多个URL访问。Servlet不是线程安全的，因此要谨慎使用类的变量。**


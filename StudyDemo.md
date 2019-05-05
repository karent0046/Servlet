# Servlet

## 一.概念

Servlet 是 Server 与 Applet 的缩写，是服务端小程序的意思。使用 Java 语言编写的服务 器端程序，可以像生成动态的 WEB 页，Servlet 主要运行在服务

器端，并由服务器调用执行， 是一种按照 Servlet 标准来开发的类。 是 SUN 公司提供的一门用于开发动态 Web 资源的技术。


提供 Servlet 功能的服务器，叫做 Servlet 容器，其常见容器有很多，如Tomcat, Jetty, WebLogic Server, WebSphere, JBoss 等等。

## 二.生命周期


Servlet没有 main()方法，不能独立运行，它的运行完全由 Servlet 引擎来控制和调度。 


所谓生命周期，指的是 servlet 容器何时创建 servlet 实例、何时调用其方法进行请求的处理、 何时并销毁其实例的整个过程。

 
### 实例和初始化时机


当请求到达容器时，容器查找该 servlet 对象是否存在，如果不存在，则会创建实例并 进行初始化。


### 就绪/调用/服务阶段


有请求到达容器，容器调用 servlet 对象的 service()方法,处理请求的方法在整个声明周 期中可以被多次调用； 


HttpServlet 的 service()方法，会依据请求方式来调用 doGet()或者 doPost()方法。但是， 这两个 do 方法默认情况下，会抛出异常，需要子类去 override。


### 销毁时机


当容器关闭时（应用程序停止时），会将程序中的 Servlet 实例进行销毁。


   上述的生命周期可以通过 Servlet 中的生命周期方法来观察。在 Servlet 中有三个生命周 期方法，不由用户手动调用，而是在特定的时机有容器自动调用，观察
   

这三个生命周期方法 即可观察到 Servlet 的生命周期。



## 三.Servlet的XML配置

tomcat 3.0以下配置servlet需要配置xml

XML配置案例:

```
<servlet>
    <servlet-name>servlet01</servlet-name>
    <servlet-class>com.shsxt.servlet.Servlet01</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>servlet01</servlet-name>
    <url-pattern>/ser01</url-pattern>
  </servlet-mapping>
 ```
 
servlet-name：Servlet 对象的名称

servlet-class：创建 Servlet 对象所要调用的类

load-on-startup：Servlet 容器启动时加载 Servlet 对象的顺序

servlet-mapping/servlet-name：要与 servlet 中的 servlet-name 配置节内容对应

url-pattern：客户访问的 Servlet 的相对 URL 路径

**说明： url-pattern 可以配多个（一个 servlet 可以通过多个 url-pattern 访问）当多个 servlet 配置成了同一个 url-pattern
通配符"*"只能放在最前面或最后面，不能放中间且不能单独存在（以/分割的，不能和单词组成整体）。越精确越
优先。常规配置即可。**

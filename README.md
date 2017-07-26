# eyes-world-server
## back-end

* 一、成立GitHub工作组----https://github.com/eyes-world/eyes-world-server

* 二、确定使用的技术栈：SSM（Spring+springMVC+MyBatis）

* 三、开始工作

  * 1）用maven构建SpringMVC工程：
    mvn命令构建---pom添加各种依赖---创建目录结构

  * 2）建立数据库日志：
    创建sql日志，确定数据库表设计

  * 3）编程规范：
       
    * 接口注释：
        
```java

        方法注释：
        /**
        *方法功能
        *@params 参数名
        *@return
        **/
        
	成员变量注释：
        //
```

  * 4）dao层和entity实体类的编写：
    
    * entity包：采用javabean的形式对数据表进行映射（javabean，对数据表的数据进行封装）
    
    * dao层：编写接口（数据库的增删查改接口），使用MyBatis进行从实体类到数据库的关系映射（接口+SQL编写）
     
      * a）配置mybatis（mapper目录、mybatis-config.xml）http://www.mybatis.org/mybatis-3/zh/index.html

      * b）mybatis整合spring（spring目录、spring-dao.xml）http://docs.spring.io/spring/docs/4.1.7.RELEASE/spring-framework-reference/
     
      * c）单元测试

  * 5）Service层编写（DAO拼接等逻辑）
    
    * a）service包：dao拼接业务接口（从用户角度设计接口：与前端交互所需要的接口、上传的图片对象、用户的个人资料、用户评论等）
        
				impl实现类的编写
    
      * exception包：异常处理，对用户操作可能出现的异常进行封装
    
      * dto包：数据传输层，屏蔽后端实体类，将前端需要的数据进行封装，为service包的接口提供相应的类（javabean，图片类，用户个人资料，用户评论等）
    
    * b）单元测试，配置logback：https://logback.qos.ch/manual/configuration.html
        
      * 在要测试的接口中ctrl+shift+t：选择要测试的方法，创建测试类

  * 6）Web层编写（前端交互、Restful规范、SpringMVC实现restful接口、bootstrap做页面样式布局、jquery做交互实现）
       
    * a）确定用户交互的流程
       
    * b）设计Restful接口（GET/POST/PUT/DELETE请求的URL设计）
                
      * /模块/资源/{标识}/集合...
             
      * GET     /tvos/user/{user_id}/photos --->用户相片列表
             
      * POST   /tvos/user/{user_id}/{md5}/photos --->用户私有相片列表
             
      * GET   /user/{user_id}/info --->用户信息列表
        
    * c）使用SpringMVC（基于Handler开发）
               
      * 登录交互、页面跳转逻辑

### Spring

#### Spring Security
##### Q1. 什么是Spring Security？核心功能？
1. Spring Security是基于Spring的安全框架.它提供全面的安全性解决方案,同时在Web请求级别和调用级别确认和授权
2. 在Spring Framework基础上,Spring Security充分利用了依赖注入(DI)和面向切面编程(AOP)功能
3. 为应用系统提供声明式的安全访问控制功能,建晒了为企业安全控制编写大量重复代码的工作,是一个轻量级的安全框架,并且很好集成Spring MVC

spring security 的核心功能主要包括：
1. 认证(Authentication)：指的是验证某个用户是否为系统中的合法主体，也就是说用户能否访问该系统。
2. 授权(Authorization)：指的是验证某个用户是否有权限执行某个操作
3. 攻击防护：指的是防止伪造身份

##### Q2. Spring Security的原理?
基于Filter技术实现?
1. 首先SpringSecurity是基于Filter技术实现的。
2. Spring通过DelegatingFilterProxy建立Web容器和Spring ApplicationContext的联系，而SpringSecurity使用FilterChainProxy 注册SecurityFilterChain。

认证模块的实现？
1. SecurityContextHolder(用于存储授权信息)
2. 除了手动授权外，SpringSecurity通过AuthenticationManager和ProviderManager进行授权。其中AuthenticationProvider代表不同的认证机制（最常用的账号/密码）

授权模块的实现？
1. 认证完成之后，SpringSecurity通过AccessDecisionManager 完成授权操作。
2. 除了全局的授权配置之外，也可以通过@PreAuthorize, @PreFilter, @PostAuthorize , @PostFilter注解实现方法级别的权限控制。

##### Q3. Spring Security基于用户名和密码的认证模式流程？
1. 请求的用户名密码可以通过表单登录，基础认证，数字认证三种方式从HttpServletRequest中获得，用于认证的数据源策略有内存，数据库，ldap,自定义等。
2. 拦截未授权的请求，重定向到登录页面
3. 表单登录的过程，进行账号密码认证
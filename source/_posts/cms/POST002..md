---
title: 库内新增对象Products的流程说明
tags: cms
category: cms
date: 2018-03-10 16:44:36
---
![image](http://ovi3ob9p4.bkt.clouddn.com/TIETU/CT0150.jpg)

cms开发——库内新增对象Products的流程说明
<!--more-->
### 第一步：Entity

1. `com.jeecms.cms.entity.assist.base`下建立模型基础类`BaseCmsProducts.java`
2. `com.jeecms.cms.entity.assist`  下建立对象类继承继承模型CmsProducts.java
3. `com.jeecms.cms.entity.assist.hbm` 配置hibernate对象映射CmsProducts.hbm.xml
4. `src .ehcache-hibernate.xml` 缓存对象配置：

```xml
 <cache name="com.jeecms.cms.entity.assist.CmsProducts" 
maxElementsInMemory="100" eternal="false" timeToIdleSeconds="600" timeToLiveSeconds="7200" overflowToDisk="true"/>
```

### 第二步：Dao

1. `com.jeecms.cms.dao.assist`数据库交互持久层DAO接口和实现`ProductsDao.java` `ProductsDaoImpl.java` 
2. 配置`WebRoot/WEB-INF/config/jeecms-context.xml`文件:

```xml
<bean id="cmsproductsDao" 
class="com.jeecms.cms.dao.assist.impl.CmsProductsDaoImpl"/>
```

### 第三步：Service

1. `com.jeecms.cms.manager.assist`业务层接口和实现，`ProductsMng.java , ProductsMngImpl.java`
2. 配置`WebRoot/WEB-INF/config/jeecms-context.xml`文件:

```xml
<bean id="cmsProductsMng" 
class="com.jeecms.cms.manager.assist.impl.CmsProductsMngImpl"/>
```

### 第四步：Action

1. `com.jeecms.cms.action.front` 写Action与前台对接，`ProductsAct.java`
2. XML配置：`jeecms-servlet-front-action.xml` 

```xml
<bean id="productsAct" 
class="com.jeecms.cms.action.front.ProductsAct"/>
```

3. `com.jeecms.cms.action.admin.assist` （加、删、改）写Action与后台对接`CmsProductsAct.java` 
4. XML配置：`jeecms-servlet-admin-action.xml` 

```xml
<bean id="cmsProductsAct" 
class="com.jeecms.cms.action.admin.assist.CmsProductsAct"/>
```

### 第五步：Directive

1. `com.jeecms.cms.action.directive` (设置并返回标签对象`[@cms_products_page]`)
2. 配置`WebRoot/WEB-INF/config/jeecms-context.xml`文件:

```xml
<bean id="cms_products_page" 

class="com.jeecms.cms.action.directive.CmsProductsDirective"/>

<bean id="staticPageSvc" class="com.jeecms.cms.staticpage.StaticPageSvcImpl">

    <property name="tplMessageSource" ref="tplMessageSource"/>

    <property name="freeMarkerConfigurer">

      <bean class="org.springframework.web.servlet.view.freemarker.FreeMarkerConfigurer">

        <property name="freemarkerVariables">

          <map>
```

3.  此处添加标签的配置信息：

   ```xml
        <entry key="cms_products_page" value-ref="cms_products_page"/>
   ```

4. 配置`WebRoot/WEB-INF/config/ Jeecms-servlet-front.xml`文件:

```xml
<bean id="freemarkerConfig" class="org.springframework.web.servlet.view.freemarker.FreeMarkerConfigurer">
    <property name="freemarkerVariables">
      <map>
```

5. 此处添加标签的配置信息： 

```xml
<entry key="cms_products_page" value-ref="cms_products_page" />
```

### 特别注意点：

1. 对象模板位置控制：`com.jeecms.cms.action.front.ProductsAct.java`

```java
// 方案路径site.getSolutionPath()=”/WEB-INF/t/cms/www/default”
// TPLDIR_SPECIAL="special" 模板位置
// PRODUCTS_INDEX= "tpl.productsIndex"; 模板名称
return FrontUtils.getTplPath(request, site.getSolutionPath(),TPLDIR_SPECIAL, PRODUCTS_INDEX);
```

2. `PRODUCTS_INDEX`对象需要在国际化处进行设置：`WebRoot/WEB-INF/languages/jeecms_tpl/messages_zh_CN.properties` ：

```xml
tpl.productsIndex=products_index
```

### 国际化文件说明：

1. `WEB-INF/languages/fck`  友情提示
2. `WEB-INF/languages/jeecms_admin`  (后台)功能页面，如：首页》内容统计 `statistic.function.content=内容统计`

3. `WEB-INF/languages/jeecms_front`  (前台)友情提示，如：验证码错误。

4. `WEB-INF/languages/jeecms_tpl`    (前台)功能页面，如：投票内容页， `tpl.tagDetail=voteIndex`

5. `WEB-INF/languages/jeecore_admin` 功能按钮、提示信息，如：`global.submit=提交，global.confirm.logout=您确定退出吗？`

# medicalmanage
Java：190 基于SSM的药品管理系统
> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

系统的用户分管理员和销售两个角色的权限子模块。

管理员统计药品销售量，可以导出药品出入库记录，管理药品以及报损信息。

销售员管理药品，对药品进行销售，入库，出库以及报损。

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：Java、Spring、SpringMVC、Mybatis，SSM

前端：vue

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://www.codegym.top](http://www.codegym.top/)



# 运行截图

## 功能模块截图

![img](https://i-blog.csdnimg.cn/img_convert/5ca9a60044d9a8162e0517b1082cc81c.png)

![img](https://i-blog.csdnimg.cn/img_convert/3f14141d2b7e96185e3fb5fb7ef5cc5a.png)

![image20241220000730872](https://i-blog.csdnimg.cn/img_convert/90ecaa439de05bbdd5f1d586adbfb129.png)

###

### 项目截图

![ssm175基于web的药品管理系统vue0](https://i-blog.csdnimg.cn/img_convert/1b49fae25c7e3547361618bdc18ec7d1.png)

![ssm175基于web的药品管理系统vue1](https://i-blog.csdnimg.cn/img_convert/9dda2332aa579958f8276a80489bbf95.png)

![ssm175基于web的药品管理系统vue2](https://i-blog.csdnimg.cn/img_convert/1876d3e002dd4d69c394775b79d4b838.png)

![ssm175基于web的药品管理系统vue3](https://i-blog.csdnimg.cn/img_convert/cf1f03915f0ed2c342e886213bd8c997.png)

![ssm175基于web的药品管理系统vue4](https://i-blog.csdnimg.cn/img_convert/32c57ac7d30cb3d576fb81cd5fb1cb52.png)

![ssm175基于web的药品管理系统vue5](https://i-blog.csdnimg.cn/img_convert/d9d483ca419ad92d8f99c532377e66cb.png)

![ssm175基于web的药品管理系统vue6](https://i-blog.csdnimg.cn/img_convert/8748bc4978b51df88899f0ac8b5c7dc1.png)

![ssm175基于web的药品管理系统vue7](https://i-blog.csdnimg.cn/img_convert/3bddfd81e206075a8d674f13e0da6082.png)

![ssm175基于web的药品管理系统vue8](https://i-blog.csdnimg.cn/img_convert/2f5b294dec5eab1f600794f696d51706.png)

### 代码

```
  RestClient client = RestClientFactory.getClient(thingsBoardConfig.getUrl());
        // Get current user
        Optional<User> userOptional = ThingsBoardUtils.getAdminLoginUser(client,thingsBoardConfig);
        userOptional.orElseThrow(() -> new IllegalStateException("No logged in user has been found"));
        List<Tenant> loadedTenants = new ArrayList<>();
        PageLink pageLink = new PageLink(10);
        PageData<Tenant> pageData;
        Function<JsonNode, Integer> intMapper = jsonNode -> {
            if (jsonNode.isInt()) {
                return jsonNode.asInt();
            }
            return 0; // 如果不是整数，则返回0
        };
        do {
            pageData = client.getTenants(pageLink);
            loadedTenants.addAll(pageData.getData());
            if (pageData.hasNext()) {
                pageLink = pageLink.nextPageLink();
            }
        } while (pageData.hasNext());
```

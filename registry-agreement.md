## 注册中心协议

### A. 系统组件

在registry中的namespace.**components.service_pool**字段，保存如下结构的服务池，描述该命名空间下的所有服务信息：

**namespace**.components.**service_tag**

```json
{
  "service_list": {
    "lemon_cloud_user": {
      "service_introduce": "This is a lemon cloud user center service",
      "endpoints": [
        {
          "host": "192.168.1.1",
          "port": 33385
        },
        {
          "host": "192.168.1.2",
          "port": 33385
        }
      ]
    }
  }
}
```

每个服务需要到指定空间下存储系统设置的定义：**namespace**.settings_define.**service_tag**，例：

````
cn.lemonit.cloud.settings_define.lemon_cloud_user
````

实际服务的系统设置存储在：**namespace**.settings_value.**service_tag**，例：

```
cn.lemonit.cloud.settings_value.lemon_cloud_user
```





每个服务对外暴露三种接口：

1. 管理接口：/adm
2. 服务间接口：/svc
3. 面向用户接口：/usr
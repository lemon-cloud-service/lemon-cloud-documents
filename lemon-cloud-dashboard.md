# Lemon Cloud Dashboard 

## . workspace标准

### 1. workspsace.yaml

在工作区文件夹中，



### 2. 文件目录结构

/static/: 所有的静态资源均放到此目录，dashboard会开放http静态服务器并将目录指向此处

/static/service_management/：所有可供访问的服务管理模块相关的静态资源均放到此目录中

/static/service_management/$service_key/：按照服务划分，以$service_key对文件夹进行命名，每个服务一个文件夹

/static/service_management/$service_key/management_modules.yml：每个服务下可以有多个管理模块，该文件必须存在，否则不认为这是一个有效的服务数据资源文件夹。管理模块必须在此文件中进行注册才可以被系统识别，具体的配置规则可以参考***Z.1.***

/override.yml：如果需要对资源的访问地址进行覆盖重写，可以在此文件中按照规定格式进行填写，具体配置规则可以参考***Z.2.***

****

## Z. 配置文件规则定义

### 1. lc_service.json配置规则

每个业务静态数据资源文件夹中必须存在此文件，通过此文件进行对业务UI模块进行相关配置，格式如下：

```json
{
  "service": {
    "service_key": "lemon_cloud_user",
    "service_icon_url": "xxxxxx",
    "management_module_list": [
      {
        "module_key": "user_group_manage",
        "module_name": "用户组管理",
        "module_introduce": "所有用户组的管理",
        "module_icon_url": "yyyyyy",
        "index_url": "zzzzzzz"
      }
    ]
  }
}
```



### 2. lc_override.json配置规则

对于需要覆盖重写的模块信息进行填写即可，没有配置则按照约定从工作区读取，格式如下：

```json
{
  "services": [
    {
      "service_key": "lemon_cloud_user",
      "service_icon_url": "xxxxxx",
      "management_module_list": [
        {
          "module_key": "user_group_manage",
          "module_name": "用户组管理",
          "module_introduce": "所有用户组的管理",
          "module_icon_url": "yyyyyy",
          "index_url": "zzzzzzz"
        }
      ]
    }
  ]
}
```




## 0. 注册中心协议

##### A. 服务实例 [service_instance]

在registry中的**namespace**.components中，保存所有的服务实例信息，需要不断续期，一段时间不续期（离线）后自动删除，具体格式为：**namespace**.service_instance.**service_key.service_instance_key**，举例：

```
cn.lemonit.cloud.service_instance.lemon_cloud_user.instance_key_abcdefg
```

##### B. 服务基本信息 [service_base_info]

在registry中注册每一个服务的服务基本信息，如服务名称、服务tag等，该部分信息一旦注册不会自动删除，除非人为删除，格式为：**namespace**.service_base_info.**service_key**，举例：

```
cn.lemonit.cloud.service_base_info.lemon_cloud_user
```

##### C. 系统设置定义 [system_settings_define]

每个服务需要到指定空间下存储系统设置的定义，说明需要哪些系统设置项目，一以及系统设置项目的类型，具体的格式为：**namespace**.system_settings_define.**service_key**，例：

````
/system_settings_valuue/cn.lemonit.cloud/lemon_cloud_user
````

##### D. 系统设置实际存储值 [system_settings_value]

当系统设置实际被设置值的时候，实际是将设置的值存储在了该位置（不同系统设置组做了区分）格式如下：**namespace**.system_settings_value.**service_key.settings_group_key.settings_item_key**，例：

```
/system_settings_value/cn.lemonit.cloud/lemon_cloud_user
```

##### E. 服务私有数据沙盒 [data_sandbox]

每个服务都有私有的数据沙盒空间，从业务角度规定来看，服务间不可互相访问对方沙箱中的数据，沙箱中的数据为键值对的形式存储，存储位置为：**namespace**.data_sandbox.**service_key**



## 2.  



每个服务对外暴露三种接口：

1. 管理接口：/adm
2. 服务间接口：/svc
3. 面向用户接口：/usr



单点docker启动ETCD命令

```shell
docker run \
  -d \
  -p 2379:2379 \
  -p 2380:2380 \
  --name etcd \
  quay.io/coreos/etcd \
  /usr/local/bin/etcd \
  --name s1 \
  --data-dir /etcd-data \
  --listen-client-urls http://0.0.0.0:2379 \
  --advertise-client-urls http://0.0.0.0:2379 \
  --listen-peer-urls http://0.0.0.0:2380 \
  --initial-advertise-peer-urls http://0.0.0.0:2380 \
  --initial-cluster s1=http://0.0.0.0:2380 \
  --initial-cluster-token tkn \
  --initial-cluster-state new
```


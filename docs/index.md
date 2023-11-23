# Demo服务实例部署文档

## 概述

Salt基于Python构建，是一个事件驱动的自动化工具和框架，用于部署、配置和管理复杂的IT系统。使用Salt来自动化公共基础设施管理任务，并确保基础设施的所有组件都以一致的期望状态运行。

Salt在配置管理上就有很多的用途，包括:

- 管理操作系统的部署和配置；
- 安装和配置软件应用程序和服务；
- 管理服务器、虚拟机、容器、数据库、web服务器、网络设备等；
- 确保配置的一致性，防止配置漂移。
  
Salt是配置管理的理想选择，因为它是可插拔的、可定制的，并且可以很好地与许多现有技术兼容。Salt使您能够部署和管理应用程序，这些应用程序使用运行在几乎任何操作系统上的任何技术栈，包括不同类型的网络设备，如来自各种供应商的交换机和路由器。

除了配置管理，Salt还可以:

- 自动化和编排例程IT处理，例如调度服务器停机时间或升级操作系统或应用程序所需的常见任务；
- 创建具有自我意识的、自我修复的系统，能够自动响应中断、常见管理问题或其他重要事件。

本文向您介绍如何开通计算巢上的Salt服务，以及部署流程和使用说明。

## 计费说明

Salt在计算巢上的费用主要涉及：

- 所选vCPU与内存规格
- 系统盘类型及容量

计费方式包括：

- 按量付费（小时）
- 包年包月

预估费用在创建实例时可实时看到。


## 部署架构

参见主页描述。

## RAM账号所需权限

Salt服务需要对ECS、VPC等资源进行访问和创建操作，若您使用RAM用户创建服务实例，需要在创建服务实例前，对使用的RAM用户的账号添加相应资源的权限。添加RAM权限的详细操作，请参见[为RAM用户授权](https://help.aliyun.com/document_detail/121945.html)。所需权限如下表所示。


| 权限策略名称 | 备注 |
|--- | --- |
| AliyunECSFullAccess | 管理云服务器服务（ECS）的权限 |
|AliyunVPCFullAccess  |管理专有网络（VPC）的权限|
|AliyunROSFullAccess  |管理资源编排服务（ROS）的权限|
|AliyunComputeNestUserFullAcces |管理计算巢服务（ComputeNest）的用户侧权限|


## 部署流程

### 部署步骤

单击[部署链接](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-a672bb7a007945619bfb&ServiceVersion=draft)，进入服务实例部署界面，根据界面提示，填写参数完成部署。

### 部署参数说明

您在创建服务实例的过程中，需要配置服务实例信息。下文介绍SaltStack服务实例输入参数的详细信息。

| 参数组 | 示例 | 说明 |
| --- | --- | --- |
| 服务实例名称 | salt-xxxx | 实例的名称（可使用默认值，无需修改） |
| 地域 | 华北2（北京） | 选中服务实例的地域，建议就近选中，以获取更短的网络时延 |
|Minion节点数量|2|扮演Minion节点的主机数量|
|ECS实例规格|ecs.g6.large|Master节点与Minion节点主机的实例规格|
|系统盘类型|cloud_essd|Master节点与Minion节点主机的系统盘类型|
|可用区|可用区G|Master节点与Minion节点主机部署的可用区|
|ECS实例密码|Test123456|登陆ECS实例需要的密码|
|是否新建VPC和VSwitch||若勾选该按钮，则会自动创建一个VPC实例和一个VSwitch实例；若不勾选该按钮，则需要选择已有的VPC实例ID与VSwitch实例ID|

### 验证结果

1. 查看服务实例。服务实例创建成功后，部署时间大约需要5分钟。部署完成后，页面上可以看到对应的服务实例。 
2. 通过服务实例访问salt-master主机实例，使用密码登录。
3. 通过以下命令确保SaltStack安装成功：
   
   ```shell
   [root@i-master ~]# salt --version
    salt 3005.4

   [root@iZbp1fro523s3ndnxxjuo9Z ~]# salt-key
   Accepted Keys:
   ${your minion ecs instance ids here}
   Denied Keys:
   Unaccepted Keys:
   Rejected Keys:

   [root@iZbp1fro523s3ndnxxjuo9Z ~]# salt '*' test.ping
   ${your minion ecs instance ids here}:
   True
   ```


## 帮助文档

请访问Salt官网文档获取更多使用帮助：[使用文档](https://docs.saltproject.io/en/latest/contents.html)
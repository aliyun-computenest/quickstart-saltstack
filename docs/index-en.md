# SaltStack Service Instance Deployment Documentation

## Overview

Salt is an event-driven automation tool and framework built on Python, used for deploying, configuring, and managing complex IT systems. Use Salt to automate public infrastructure management tasks and ensure that all components of the infrastructure run in a consistent desired state.

Salt has many uses in configuration management, including:

- Managing operating system deployment and configuration;
- Installing and configuring software applications and services;
- Managing servers, virtual machines, containers, databases, web servers, network devices, etc.;
- Ensuring configuration consistency and preventing configuration drift.

Salt is an ideal choice for configuration management because it is pluggable, customizable, and compatible with many existing technologies. Salt enables you to deploy and manage applications using any technology stack running on almost any operating system, including different types of network devices such as switches and routers from various vendors.

In addition to configuration management, Salt can also:

- Automate and orchestrate routine IT processes, such as scheduling server downtime or common tasks required for upgrading operating systems or applications;
- Create self-aware, self-healing systems capable of automatically responding to interruptions, common management issues, or other important events.

This document introduces how to activate the Salt service on Compute Nest, along with the deployment process and usage instructions.

## Billing Information

The costs for Salt on Compute Nest mainly involve:

- The selected vCPU and memory specifications;
- The system disk type and capacity.

Estimated costs can be viewed in real-time during instance creation.

## Deployment Architecture

See the homepage description.

## Required Permissions for RAM Accounts

The Salt service requires access and creation operations for resources such as ECS and VPC. If you use a RAM user to create a service instance, you must add the corresponding resource permissions to the RAM user account before creating the service instance. For detailed operations on adding RAM permissions, please refer to [Authorize RAM Users](https://help.aliyun.com/document_detail/121945.html). The required permissions are listed in the table below.

| Permission Policy Name | Description |
| --- | --- |
| AliyunECSFullAccess | Permission to manage Elastic Compute Service (ECS) |
| AliyunVPCFullAccess | Permission to manage Virtual Private Cloud (VPC) |
| AliyunROSFullAccess | Permission to manage Resource Orchestration Service (ROS) |
| AliyunComputeNestUserFullAccess | User-side permission to manage Compute Nest service |

## Deployment Process

### Deployment Steps

Click the [Deployment Link](https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-a672bb7a007945619bfb&ServiceVersion=draft) to enter the service instance deployment interface. Follow the prompts on the interface to fill in the parameters and complete the deployment.

### Deployment Parameter Description

During the process of creating a service instance, you need to configure the service instance information. The following section details the input parameters for the SaltStack service instance.

| Parameter Group | Example | Description |
| --- | --- | --- |
| Service Instance Name | salt-xxxx | The name of the instance (default value can be used, no modification needed) |
| Region | China (Beijing) | Select the region for the service instance. It is recommended to select the nearest region to obtain lower network latency. |
| Minion Node Count | 2 | The number of host instances acting as Minion nodes |
| ECS Instance Type | ecs.g6.large | The instance specification for both Master and Minion node hosts |
| System Disk Type | cloud_essd | The system disk type for both Master and Minion node hosts |
| Zone | Zone G | The availability zone where Master and Minion node hosts are deployed |
| ECS Instance Password | Test123456 | The password required to log in to the ECS instances |
| Create New VPC and VSwitch | | If checked, a VPC instance and a VSwitch instance will be automatically created. If unchecked, you need to select an existing VPC instance ID and VSwitch instance ID. |

### Verification Results

1. **View Service Instance:** After the service instance is successfully created, the deployment takes approximately 5 minutes. Once completed, the corresponding service instance will be visible on the page.
2. **Access Salt-Master:** Access the salt-master host instance via the service instance and log in using the password.
3. **Verify SaltStack Installation:** Ensure SaltStack is installed successfully by running the following commands:

## Help Documentation

Please visit the official Salt documentation for more usage assistance: [Usage Documentation](https://docs.saltproject.io/en/latest/contents.html).

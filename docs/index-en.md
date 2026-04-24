
<body>

    <h1>SaltStack Service Instance Deployment Documentation</h1>

    <h2>Overview</h2>
    <p>Salt is an event-driven automation tool and framework built on Python, used for deploying, configuring, and managing complex IT systems. Use Salt to automate public infrastructure management tasks and ensure that all components of the infrastructure run in a consistent desired state.</p>

    <p>Salt has many uses in configuration management, including:</p>
    <ul>
        <li>Managing operating system deployment and configuration;</li>
        <li>Installing and configuring software applications and services;</li>
        <li>Managing servers, virtual machines, containers, databases, web servers, network devices, etc.;</li>
        <li>Ensuring configuration consistency and preventing configuration drift.</li>
    </ul>

    <p>Salt is an ideal choice for configuration management because it is pluggable, customizable, and compatible with many existing technologies. Salt enables you to deploy and manage applications using any technology stack running on almost any operating system, including different types of network devices such as switches and routers from various vendors.</p>

    <p>In addition to configuration management, Salt can also:</p>
    <ul>
        <li>Automate and orchestrate routine IT processes, such as scheduling server downtime or common tasks required for upgrading operating systems or applications;</li>
        <li>Create self-aware, self-healing systems capable of automatically responding to interruptions, common management issues, or other important events.</li>
    </ul>

    <p>This document introduces how to activate the Salt service on Compute Nest, along with the deployment process and usage instructions.</p>

    <h2>Billing Information</h2>
    <p>The costs for Salt on Compute Nest mainly involve:</p>
    <ul>
        <li>The selected vCPU and memory specifications;</li>
        <li>The system disk type and capacity.</li>
    </ul>
    <p>Estimated costs can be viewed in real-time during instance creation.</p>

    <h2>Deployment Architecture</h2>
    <p>See the homepage description.</p>

    <h2>Required Permissions for RAM Accounts</h2>
    <p>The Salt service requires access and creation operations for resources such as ECS and VPC. If you use a RAM user to create a service instance, you must add the corresponding resource permissions to the RAM user account before creating the service instance. For detailed operations on adding RAM permissions, please refer to <a href="https://help.aliyun.com/document_detail/121945.html" target="_blank">Authorize RAM Users</a>. The required permissions are listed in the table below.</p>

    <table>
        <thead>
            <tr>
                <th>Permission Policy Name</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>AliyunECSFullAccess</td>
                <td>Permission to manage Elastic Compute Service (ECS)</td>
            </tr>
            <tr>
                <td>AliyunVPCFullAccess</td>
                <td>Permission to manage Virtual Private Cloud (VPC)</td>
            </tr>
            <tr>
                <td>AliyunROSFullAccess</td>
                <td>Permission to manage Resource Orchestration Service (ROS)</td>
            </tr>
            <tr>
                <td>AliyunComputeNestUserFullAccess</td>
                <td>User-side permission to manage Compute Nest service</td>
            </tr>
        </tbody>
    </table>

    <h2>Deployment Process</h2>

    <h3>Deployment Steps</h3>
    <p>Click the <a href="https://computenest.console.aliyun.com/service/instance/create/cn-hangzhou?type=user&ServiceId=service-a672bb7a007945619bfb&ServiceVersion=draft" target="_blank">Deployment Link</a> to enter the service instance deployment interface. Follow the prompts on the interface to fill in the parameters and complete the deployment.</p>

    <h3>Deployment Parameter Description</h3>
    <p>During the process of creating a service instance, you need to configure the service instance information. The following section details the input parameters for the SaltStack service instance.</p>

    <table>
        <thead>
            <tr>
                <th>Parameter Group</th>
                <th>Example</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Service Instance Name</td>
                <td>salt-xxxx</td>
                <td>The name of the instance (default value can be used, no modification needed)</td>
            </tr>
            <tr>
                <td>Region</td>
                <td>China (Beijing)</td>
                <td>Select the region for the service instance. It is recommended to select the nearest region to obtain lower network latency.</td>
            </tr>
            <tr>
                <td>Minion Node Count</td>
                <td>2</td>
                <td>The number of host instances acting as Minion nodes</td>
            </tr>
            <tr>
                <td>ECS Instance Type</td>
                <td>ecs.g6.large</td>
                <td>The instance specification for both Master and Minion node hosts</td>
            </tr>
            <tr>
                <td>System Disk Type</td>
                <td>cloud_essd</td>
                <td>The system disk type for both Master and Minion node hosts</td>
            </tr>
            <tr>
                <td>Zone</td>
                <td>Zone G</td>
                <td>The availability zone where Master and Minion node hosts are deployed</td>
            </tr>
            <tr>
                <td>ECS Instance Password</td>
                <td>Test123456</td>
                <td>The password required to log in to the ECS instances</td>
            </tr>
            <tr>
                <td>Create New VPC and VSwitch</td>
                <td></td>
                <td>If checked, a VPC instance and a VSwitch instance will be automatically created. If unchecked, you need to select an existing VPC instance ID and VSwitch instance ID.</td>
            </tr>
        </tbody>
    </table>

    <h3>Verification Results</h3>
    <ol>
        <li><strong>View Service Instance:</strong> After the service instance is successfully created, the deployment takes approximately 5 minutes. Once completed, the corresponding service instance will be visible on the page.</li>
        <li><strong>Access Salt-Master:</strong> Access the salt-master host instance via the service instance and log in using the password.</li>
        <li><strong>Verify SaltStack Installation:</strong> Ensure SaltStack is installed successfully by running the following commands:</li>
    </ol>

    <pre><code>[root@i-master ~]# salt --version
 salt 3005.4

[root@iZbp1fro523s3ndnxxjuo9Z ~]# salt-key
Accepted Keys:
${your minion ecs instance ids here}
Denied Keys:
Unaccepted Keys:
Rejected Keys:

[root@iZbp1fro523s3ndnxxjuo9Z ~]# salt '*' test.ping
${your minion ecs instance ids here}:
    True</code></pre>

    <h2>Help Documentation</h2>
    <p>Please visit the official Salt documentation for more usage assistance: <a href="https://docs.saltproject.io/en/latest/contents.html" target="_blank">Usage Documentation</a>.</p>

</body>

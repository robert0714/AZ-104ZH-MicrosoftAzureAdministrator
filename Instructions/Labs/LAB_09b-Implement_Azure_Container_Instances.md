﻿---
lab:
    title: '09b - 实现 Azure 容器实例'
    module: '模块 09 - 无服务器计算'
---

# 实验室 09b - 实现 Azure 容器实例
# 学生实验室手册

## 实验室场景

Contoso 希望为其虚拟化工作负荷找到一个新平台。你确定了许多可以用来实现此目标的容器映像。由于你想要尽量减少容器管理，因此你计划评估 Azure 容器实例在 Docker 映像部署中的使用。 

## 目标

在本实验室中，你将：

+ 任务 1：使用 Azure 容器实例部署 Docker 映像
+ 任务 2：查看 Azure 容器实例的功能

## 预计用时：20 分钟

## 说明

### 练习 1：

#### 任务 1：使用 Azure 容器实例部署 Docker 映像

在此任务中，你将为 Web 应用程序创建一个新的容器实例。 

1. 登录到 [Azure 门户](https://portal.azure.com)。

1. 在 Azure 门户中，搜索以找到 **“容器实例”**，然后，在 **“容器实例”** 边栏选项卡中，单击 **“+ 添加”**。 

1. 在 **“创建容器实例”** 边栏选项卡中的 **“基本”** 选项卡，指定以下设置（ 保留其他设置的默认值）：

    | 设置 | 数值 |
    | ---- | ---- |
    | 订阅 | 你在本实验室中使用的 Azure 订阅的名称 |
    | 资源组 | 一个新的资源组名称 **az104-09b-rg1** |
    | 容器名称 | **az104-9b-c1** |
    | 区域 | 你可以预配 Azure 容器实例的区域的名称 |
    | 映像源 | **快速入门映像** |
    | 图像 | **microsoft/aci-helloworld (Linux)** |

1. 点击 **“下一步： 网络 >”** ，并在 **“创建容器实例”** 边栏选项卡的 **“网络”** 选项卡指定以下设置（保留其他设置的默认值）：

    | 设置 | 数值 |
    | --- | --- |
    | DNS 名称标签 | 任何有效的、全局唯一的 DNS 主机名 |
	
    >**说明**：你的容器可在 dns-name-label.region.azurecontainer.io. 公开访问。如果你收到一条 **“DNS 名称标签不可用”** 的错误消息，请指定其他值。

1. 点击 **“下一步： 高级>”**，查看 **“创建容器实例”** 边栏选项卡中的 **“高级”** 选项卡，不要做任何更改，单击 **“查看 + 创建”**，然后单击 **“创建”**。 

    >**说明**：等待部署完成。该操作需约 5 分钟。

    >**说明**：在等待期间，你可能对[示例应用程序背后的代码](https://github.com/Azure-Samples/aci-helloworld)感兴趣。如要查看它，请浏览 \app 文件夹。 

#### 任务 2：查看 Azure 容器实例的功能

在此任务中，你将查看容器实例的部署。

1. 在“部署”边栏选项卡中，单击 **“前往资源”** 链接。

1. 在容器实例 **“概述”** 边栏选项卡中，验证 **“状态”** 是否报告为 **“运行”**。 

1. 复制容器实例的值 **“FQDN”**，打开一个新的浏览器选项卡，然后导航到相应的 URL。

1. 验证 **“欢迎使用 Azure 容器实例”** 的页面是否显示。

1. 关闭新的浏览器标签页，返回到 Azure 门户，在“容器实例”边栏选项卡的 **“设置”** 部分，单击 **“容器”**，然后单击 **“日志”**。 

1. 验证你是否看到代表通过在浏览器中显示应用程序生成的 HTTP GET 请求的日志条目。

#### 清理资源

   >**说明**：请记得移除任何你不再使用的新创建的 Azure 资源。移除未使用的资源，确保不产生意外费用。

1. 打开 Azure 门户 **“Cloud Shell”** 导航窗中的 **“PowerShell”** 会话。

1. 通过运行以下命令，列出本模块在实验室中创建的所有资源组：

   ```pwsh
   Get-AzResourceGroup -Name 'az104-09b*'
   ```

1. 通过运行以下命令，删除本模块在实验室中创建的所有资源组：

   ```pwsh
   Get-AzResourceGroup -Name 'az104-09b*' | Remove-AzResourceGroup -Force -AsJob
   ```

    >**注意**：该命令异步执行（由-AsJob参数确定），因此尽管此后你可以立即在同一 PowerShell 会话中运行另一个 PowerShell 命令，但实际上要花几分钟才能移除资源组。

#### 评价

在本实验室中，你已：

- 使用 Azure 容器实例部署 Docker 映像
- 查看了 Azure 容器实例的功能
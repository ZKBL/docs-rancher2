---
title: 项目资源配额
weight: 2515
---

如果多个团队共享一个集群，某个团队可能会使用过多的可用资源，例如 CPU、内存、存储、服务、Kubernetes 对象（如 Pod 或 Secret）等。你可以应用 _资源配额_ 来防止过度消耗资源。资源配额是 Rancher 用来限制项目或命名空间可用资源的功能。

本文介绍如何在现有项目中创建资源配额。

你也可以在创建新项目时设置资源配额。有关详细信息，请参阅[创建新项目]({{<baseurl>}}/rancher/v2.6/en/cluster-admin/projects-and-namespaces/#creating-projects)。

Rancher 中的资源配额包含与 [Kubernetes 原生版本](https://kubernetes.io/docs/concepts/policy/resource-quotas/)相同的功能。Rancher 还扩展了资源配额的功能，让你将资源配额应用于项目。有关资源配额如何与 Rancher 中的项目一起使用的详细信息，请参阅[此页面](./quotas-for-projects)。

### 将资源配额应用于现有项目

修改资源配额的使用场景如下：

- 限制某个项目和项目下的命名空间能使用的资源
- 在资源配额已生效的情况下，对项目可用的资源进行扩容或缩容

1. 点击左上角 **☰ > 集群管理**。
1. 在**集群**页面，进入要应用资源配额的集群，然后单击 **Explore**。
1. 单击**集群 > 项目/命名空间**。
1. 找到要添加资源配额的项目。在该项目中选择 **⋮ > 编辑配置**。

1. 展开**资源限额**并单击**添加资源**。你也可以编辑现有配额。

1. 选择资源类型。有关类型的更多信息，请参阅[配额类型参考](./quota-type-reference)。

1. 输入**项目限制**和**命名空间默认限制**的值。

   | 字段 | 描述 |
   | ----------------------- | -------------------------------------------------------------------------------------------------------- |
   | 项目限制 | 项目的总资源限制。 |
   | 命名空间默认限制 | 每个命名空间的默认资源限制。此限制会沿用到项目中的每个命名空间。项目中所有命名空间的限制之和不应超过项目限制。 |

1. **可选**：添加更多配额。

1. 单击**创建**。

**结果**：资源配额已应用到你的项目和命名空间。如果你后续需要添加更多命名空间，Rancher 会验证项目是否可以容纳该命名空间。如果项目无法分配资源，你仍然可以创建命名空间，但命名空间将获得的资源配额为 0。然后 Rancher 将不允许你创建任何受此配额限制的资源。
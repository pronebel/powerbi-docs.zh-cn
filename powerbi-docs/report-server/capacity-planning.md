---
title: Power BI 报表服务器容量计划指南
description: 本文通过共享各种工作负载的加载测试执行结果，提供 Power BI 报表服务器的容量计划指南。
author: parthsha
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 3/5/2018
ms.author: pashah
ms.openlocfilehash: 3631c814876c5fbb14fa2bab376b212137858b2a
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71946118"
---
# <a name="capacity-planning-guidance-for-power-bi-report-server"></a>Power BI 报表服务器容量计划指南
Power BI 报表服务器是自助式 BI 和企业报表解决方案，客户可以在本地（防火墙后）进行部署。 它将 Power BI Desktop 的交互式报表功能与 SQL Server Reporting Services 的本地服务器平台相结合。 随着企业中对分析和报表的大量日益频繁使用，对衡量企业用户群所需的硬件基础结构和软件许可证进行预算可能会成为一项挑战。 本文旨在通过共享针对报表服务器的各种工作负载的大量加载测试执行的结果，提供 Power BI 报表服务器的容量计划指南。 虽然组织的报表、查询和使用模式差异巨大，但是本文中显示的结果，以及所用的实际测试和测试执行方式的详细描述，均可用作部署 Power BI 报表服务器早期阶段计划过程中的任何用户的参考点。

## <a name="executive-summary"></a>执行摘要
我们针对 Power BI 报表服务器执行两种不同类型的工作负载；每个工作负载由呈现不同类型的报表、以及执行各种 Web 门户操作组成。 

* 在“Power BI 报表重负载”工作负载中，最常执行的操作（即 60% 的时间中执行的操作）是呈现 Power BI 报表。
* 在“分页报表重负载”工作负载中，最常执行的操作是呈现分页报表。

在 Power BI 报表服务器的四服务器拓扑和不超过 5% 的用户将在任何一个时间访问报表服务器的预期下，下表介绍了 Power BI 报表服务器以至少 99% 的可靠性能够处理的最大用户数。 

| 工作负载 | 8 核/32 GB RAM | 16 核/64 GB RAM |
| --- | --- | --- |
| **Power BI 报表重负载** (>60%) |1,000 个用户 |3,000 个用户 |
| **分页 (RDL) 报表重负载** (> 60%) |2,000 个用户 |3,200 个用户 |

在每个运行中，最过载的资源是 CPU。 因此，与增加内存或硬盘空间量相比，增加 Power BI 报表服务器的内核数将能更好地提升系统的可靠性。 

## <a name="test-methodology"></a>测试方法
所用的测试拓扑均基于 Microsoft Azure 虚拟机，而不是供应商特定的物理硬件。 所有计算机均托管在美国地区中。 这反映了本地和公有云中硬件虚拟化的总趋势。 

### <a name="power-bi-report-server-topology"></a>Power BI 报表服务器拓扑
Power BI 报表服务器部署由以下虚拟机组成：

* Active Directory 域控制器：SQL Server 数据库引擎、SQL Server Analysis Services 和 Power BI 报表服务器需要它来安全地对所有请求进行身份验证。
* SQL Server 数据库引擎和 SQL Server Analysis Services：这是我们存储报表的所有数据库的位置，以便在呈现它们时使用。
* Power BI 报表服务器
* Power BI 报表服务器数据库。 报表服务器数据库托管在 Power BI 报表服务器以外的其他计算机上，以便它不需要与 SQL Server 数据库引擎竞争内存、CPU、网络和磁盘资源。

![](media/capacity-planning/report-server-topology.png)

请参阅附录 1.1 Power BI 报表服务器拓扑和附录 1.2 Power BI 报表服务器虚拟机配置，了解拓扑中所用的每台虚拟机的全面配置。

### <a name="tests"></a>测试
负载测试运行中所用的测试在名为 [Reporting Services LoadTest](https://github.com/Microsoft/Reporting-Services-LoadTest) 的 GitHub 项目公开可用。 此工具可以让用户研究 SQL Server Reporting Services 和 Power BI 报表服务器的性能、可靠性、可伸缩性和可恢复性特征。 此项目包含四组测试用例：

* 模拟呈现 Power BI 报表的测试、
* 模拟呈现移动报表的测试、
* 模拟呈现小型和大型分页报表的测试以及 
* 模拟执行各种类型的 Web 门户操作的测试。 

所有测试均编写用于执行端到端操作（例如，呈现报表、创建新数据源等）。 它们通过向报表服务器（通过 API）发出一个或多个 Web 请求完成此操作。 在实际情况中，用户可能需要执行几个中间操作才能完成其中的一个端到端操作。 例如，要呈现报表，用户将需要转到 Web 门户，导航到报表所在的文件夹，然后单击该报表来呈现它。 虽然测试不执行完成端到端任务所需的所有操作，但它们仍会处理 Power BI 报告服务器所遇到的大部分负载。 可以通过浏览 GitHub 项目详细了解所使用的不同类型报表以及执行的操作的多样性。

### <a name="workloads"></a>工作负载
测试中使用了 2 个工作负载配置文件：Power BI 报表重负载和分页报表重负载。 下表介绍了针对报表服务器执行的请求的分布。

| 活动 | Power BI 报表重负载，出现频率 | 分页报表重负载，出现频率 |
| --- | --- | --- |
| **呈现 Power BI 报表** |60% |10% |
| **呈现分页 (RDL) 报表** |30% |60% |
| **呈现移动报表** |5% |20% |
| **Web 门户操作** |5% |10% |

### <a name="user-load"></a>用户负载
对于每个测试运行，测试均基于在这两个工作负载之一中指定的频率执行。 测试从 20 个并发用户对报表服务器发出请求开始。 然后逐渐增加用户负载，直到可靠性降低至 99% 目标以下。

## <a name="results"></a>结果
### <a name="concurrent-user-capacity"></a>并发用户容量
如上文所述，测试从 20 个并发用户对报表服务器发出请求开始。 然后逐渐增加并发用户的数量，直到所有请求的 1% 失败。 下表中的结果告诉我们，服务器能够在峰值负载下处理的且请求失败率不超过 1% 的并发用户请求数。

| 工作负载 | 8 核/32 GB | 16 核/64 GB |
| --- | --- | --- |
| **Power BI 报表重负载** |50 个并发用户 |150 个并发用户 |
| **分页报表重负载** |100 个并发用户 |160 个并发用户 |

### <a name="total-user-capacity"></a>总用户容量
在 Microsoft，我们有一个 Power BI 报表服务器的生产部署，几个团队已使用过。 当我们分析此环境的实际使用情况时，我们观察到，任何给定时间（即使在每日的峰值负载期间）的并发用户数往往不超过总用户群的 5%。 将此 5% 并发率用作基准，我们推测，总用户群 Power BI 报表服务器能够处理 99% 的可靠性。

| 工作负载 | 8 核/32 GB | 16 核/64 GB |
| --- | --- | --- |
| **Power BI 报表重负载** |1,000 个用户 |3,000 个用户 |
| **分页报表重负载** |2,000 个用户 |3,200 个用户 |

### <a name="view-results"></a>查看结果
选择一个报表，查看负载测试的结果。

| 工作负载 | 8 核/32 GB | 16 核/64 GB |
| --- | --- | --- |
| **Power BI 报表重负载** |[视图 - 8 核](https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[视图 - 16 核](https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |
| **分页报表重负载** |[视图 - 8 核](https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |[视图 - 16 核](https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) |

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiMDhhNGY4NGQtNGRhYy00Yzk4LTk2MzAtYzFlNWI5NjBkMGFiIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDBiODk1OGUtYTAyOC00MzVhLThmZmYtNzVjNTFjNzMwYzkwIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiNDFiZWYzMTktZGIxNS00MzcwLThjODQtMmJkMGRiZWEzNjhlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

<iframe width="640" height="360" src="https://msit.powerbi.com/view?r=eyJrIjoiOTU0YjJkYTgtNDg4Yy00NzlhLWIwMGYtMzg4YWI2MjNmOTZjIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

## <a name="summary"></a>摘要
对于每个负载测试运行，CPU 是 Power BI 报表服务器计算机上的峰值负载点中最过载的资源。 因此，应增加的第一个资源是内核数。 或者，可以考虑通过在拓扑中添加更多托管 Power BI 报表服务器的服务器来进行纵向扩展。

本文中显示的结果源自执行一个特定的报表集，该报表集使用一个以特定方式重复的特定数据集。 它是一个有用的参考点，但请记住，使用情况将取决于报表、查询、使用模式以及 Power BI 报表服务器的部署。

## <a name="appendix"></a>附录
### <a name="1-topology"></a>1 拓扑
**1.1 Power BI 报表服务器拓扑**

为专注于不同配置下的 Power BI 报表服务器行为，修复了每种类型的计算机（托管 Power BI 报表服务器的计算机除外）的 VM 配置。 根据具有高级存储磁盘的第二代 (v2) D 系列计算机对每台计算机进行了预配。 可以在 https://azure.microsoft.com/pricing/details/virtual-machines/windows/ 上的“常规用途”下找到有关每个 VM 大小的详细信息。

| 虚拟机类型 | 处理器 | 内存 | Azure VM 大小 |
| --- | --- | --- | --- |
| **Active Directory 域控制器** |双核 |7 GB |Standard_DS2_v2 |
| **SQL Server 数据库引擎和 Analysis Services** |16 核 |56 GB |Standard_DS5_v2 |
| **报表服务器数据库** |16 核 |56 GB |Standard_DS5_v2 |

**1.2 Power BI 报表服务器虚拟机配置** 

不同的处理器和内存配置用于托管 Power BI 报表服务器的虚拟机。 和其他 VM 不同，此计算机根据具有高级存储磁盘的第三代 (v3) D 系列计算机进行了预配。 可以在 https://azure.microsoft.com/pricing/details/virtual-machines/windows/ 上的“常规用途”下找到有关此 VM 大小的详细信息。

| 虚拟机 | 处理器 | 内存 | Azure VM 大小 |
| --- | --- | --- | --- |
| **Power BI 报表服务器（小型）** |8 核 |32 GB |Standard_D8S_v3 |
| **Power BI 报表服务器（大型）** |16 核 |64 GB |vStandard_D16S_v3 |

### <a name="2-run-the-loadtest-tool"></a>2 运行 LoadTest 工具
如果想针对自己的 Power BI 报表服务器部署或 Power BI 报表服务器的 Microsoft Azure 部署运行 Reporting Services LoadTest 工具，请遵循以下步骤。

1. 从 GitHub 中克隆 Reporting Services LoadTest 项目 (https://github.com/Microsoft/Reporting-Services-LoadTest) )。
2. 在项目目录中，将找到一个名为 RSLoadTests.sln 的解决方案文件。 在 Visual Studio 2015 或更高版本中打开此文件。
3. 确定是要针对自己的 Power BI 报表服务器部署，还是针对 Microsoft Azure 中的 Power BI 报表服务器部署运行此工具。 如果要对自己的部署运行此工具，请转到步骤 5。
4. 按照 https://github.com/Microsoft/Reporting-Services-LoadTest#create-a-sql-server-reporting-services-load-environment-in-azure 上列出的说明操作，在 Azure 中创建 Power BI 报表服务器环境。
5. 部署完环境后，按照 https://github.com/Microsoft/Reporting-Services-LoadTest#load-test-execution 上列出的说明操作来运行测试。

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)



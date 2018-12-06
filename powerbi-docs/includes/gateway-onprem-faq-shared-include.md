## <a name="general"></a>常规
**问：** 这项 Windows 服务的实际名称是什么？  
**答：** 网关在服务中被称为本地数据网关服务

**问：** 网关的要求是什么？  
**答：** 请参阅主要的[网关文章](../service-gateway-onprem.md)中的要求部分。

**问：** 网关支持哪些数据源？  
**答：** 请参阅主要的[网关文章](../service-gateway-onprem.md)中的数据源表。

**问：** 我是否需要一个云数据源的网关，如 Azure SQL 数据库？  
**答：** 不！ 该服务可连接到数据源而无需网关。

**问：** 是否有任何从云到网关的入站连接？  
**答：** 不能。 网关使用到 Azure 服务总线的出站连接。

**问：** 如果我阻止了出站连接怎么办？ 我需要打开什么？  
**答：** 请参阅[端口](../service-gateway-onprem.md#ports)和网关使用的主机的列表。

**问：** 网关是否必须安装在与数据源相同的计算机上？  
**答：** 不能。 网关将使用所提供的连接信息连接到数据源。 从这个方面来讲，可以将网关看作是一个客户端应用程序。 它只需要能够连接到所提供的服务器名称即可。

**问：** 什么是来自网关的数据源的运行查询延迟？ 什么是最佳的体系结构？  
**答：** 建议使用尽可能接近数据源的网关以避免网络延迟。 如果你可以在实际数据源上安装网关，这将使引入的延迟最小化。 同时也要考虑数据中心。 例如，如果你的服务正在使用美国西部的数据中心，并且你拥有一个托管在 Azure VM 中的 SQL Server，你也会想要一个在美国西部的 Azure VM。 这将最小化延迟，并且避免 Azure VM 上的传出费用。

**问：** 是否对网络带宽有要求？  
**答：** 建议为你的网络连接配备较高的吞吐量。 每个环境都不同，而且这也依赖于所发送的数据量。 使用 ExpressRoute 可以帮助保证本地和 Azure 数据中心之间的吞吐量级别。

你可以使用第三方 [Azure 速度测试应用](http://azurespeedtest.azurewebsites.net/)来帮助测量吞吐量。

**问：** 网关 Windows 服务能够通过 Azure Active Directory 帐户运行吗？  
**答：** 不能。 Windows 服务需要具有有效的 Windows 帐户。 默认情况下，它将通过服务 SID 运行，*NT SERVICE\PBIEgwService* 。

**问：** 结果如何发送回云？  
**答：** 通过 Azure 服务总线的方式完成。 有关详细信息，请参阅[工作方式](../service-gateway-onprem.md#how-the-gateway-works)。

**问：** 我的凭据存储在哪里？  
**答：** 你为数据源输入的凭据加密存储在网关云服务中。 凭据加密存储在本地网关中。

**问：** 可否将网关置于外围网络（也称为 DMZ、隔离区和屏蔽子网）？  
**答：** 网关需要与数据源相连接。 如果数据源不可在外围网络中访问，网关可能无法连接到它。 例如，你的 SQL Server 可能不在外围网络中。 并且你不能从外围网络连接到 SQL Server。 如果将网关置于外围网络中，它将无法访问该 SQL Server。

**问：** 是否可以强制网关使用 Azure 服务总线的 HTTPS 流入量来代替 TCP？  
**答：** 是的。 尽管这会大大降低性能。 你会想要修改 *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* 文件。 你会想要将值从 `AutoDetect` 更改为 `Https`。 默认情况下，此文件位于 *C:\Program Files\On-premises data gateway* 。

**问：** 需要将 Azure 数据中心 IP 列表列入允许列表吗？ 在何处可以获取此列表？  
**答：** 如果你要拦截出站 IP 流量，则可能需要将 Azure 数据中心 IP 列表列入允许列表。 目前，网关使用 IP 地址以及完全限定的域名与 Azure 服务总线进行通信。 Azure 数据中心 IP 列表每周更新一次。 可以下载 [Microsoft Azure 数据中心 IP 列表](https://www.microsoft.com/download/details.aspx?id=41653)。

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>高可用性/灾难恢复
**问：** 是否有任何可通过网关启用的高可用性方案的计划？  
答：需要，这是 Power BI 团队主动投资的领域。 请继续关注 [Power BI 博客](https://powerbi.microsoft.com/blog/)获取有关此功能的后续更新。

**问：** 那些选项可以使用灾难恢复？  
**答：** 你可以使用恢复密钥来还原或移动网关。 在安装网关时，提供恢复密钥。

**问：** 恢复密钥的好处是什么？  
**答：** 它提供了一种方法来迁移或恢复你的网关设置。 这也可用于灾难恢复。

## <a name="troubleshooting"></a>故障排除
**问：** 网关日志的位置在哪里？  
**答：** 请参阅[疑难解答文章](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting)的工具部分。

**问：** 如何查看正在发送到本地数据源的查询？  
**答：** 可以启用查询跟踪。  这将包括正在发送的查询。 请记住在完成故障排除后，需要将其更改回原始值。 启用查询跟踪可能会使日志变大。

你还可以查看用于跟踪查询的数据源工具。 例如，针对 SQL Server 和 Analysis Services，你可以使用扩展事件或 SQL 事件探查器。


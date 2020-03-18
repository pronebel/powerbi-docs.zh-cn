---
title: 创建 SSL 证书
description: 编写有关为开发人员服务器手动创建证书的说明
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380263"
---
# <a name="create-an-ssl-certificate"></a>创建 SSL 证书

本文介绍如何创建 SSL 证书。

要在 Windows 8 或更高版本上使用 `New-SelfSignedCertificate` cmdlet 生成证书，请运行以下命令：

```cmd
pbiviz --install-cert
```

要使用工具，需要安装适用于 Windows 7 的 OpenSSL。 OpenSSL 实用工具必须在命令行中可用。

要安装 OpenSSL，请转到 [OpenSSL](https://www.openssl.org) 或 [OpenSSL 二进制文件](https://wiki.openssl.org/index.php/Binaries)站点。

## <a name="create-a-certificate-mac-os-x"></a>创建证书 (Mac OS X)

通常，可以在 Linux 或 Mac OS X 操作系统中使用 OpenSSL 实用程序。

还可以通过运行以下命令之一来安装该实用工具：

* 在 Brew 包管理器中  ：

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* 使用 MacPorts  ：

    ```cmd
    sudo port install openssl
    ```

安装用于生成新证书的 OpenSSL 实用程序后，请运行以下命令：

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>创建证书 (Linux)

如果 OpenSSL 实用程序在 Linux 操作系统中不可用，可使用以下命令之一进行安装：

* 对于 APT 包管理器  ：

    ```cmd
    sudo apt-get install openssl
    ```

* 对于 Yellowdog 更新器  ：

    ```cmd
    yum install openssl
    ```

* 对于 Redhat 包管理器  ：

    ```cmd
    rpm install openssl
    ```

如果你的操作系统中可以使用 OpenSSL 实用程序，请运行以下命令生成新证书：

```cmd
pbiviz --install-cert
```

或者，转到 [OpenSSL](https://www.openssl.org) 或 [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) 站点获取 OpenSSL 实用程序。

## <a name="generate-the-certificate-manually"></a>手动生成证书

可指定由任何工具生成证书。

如果已在系统中安装 OpenSSL 实用程序，请运行以下命令生成新证书：

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

通常可以通过运行以下命令之一来查找 PowerBI-visuals-tools web 服务器证书：

* 工具的全局实例：

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* 工具的本地实例：

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

如果使用 PEM 格式，请将证书文件保存为“PowerBICustomVisualTest_public.crt”，并将 privateKey 保存为“PowerBICustomVisualTest_public.key”   。

如果使用 PFX 格式，请将证书文件保存为“PowerBICustomVisualTest_public”  。

如果 PFX 证书文件需要密码，请执行以下操作：
1. 在配置文件中，指定：

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. 在 `server` 部分，通过替换“YOUR PASSPHRASE”占位符来指定密码  ：

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```
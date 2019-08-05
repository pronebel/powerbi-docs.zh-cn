---
title: 创建 SSL 证书
description: 编写有关为开发人员服务器手动创建证书的说明
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425427"
---
# <a name="creating-ssl-certificate"></a>创建 SSL 证书

在 Windows 8 或更高版本上使用 powershell New-SelfSignedCertificate cmdlet 运行以下命令生成证书。

要使用工具，需要安装适用于 Windows 7 的 OpenSSL   。 Util `openssll` 须在命令行中可用。

有关 OpenSSL 安装，请访问 [https://www.openssl.org](https://www.openssl.org) 或 [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>创建证书 (Mac OS X)

通常 OpenSSL util 可用于 Linux 或 Mac OS X 操作系统。

除此之外，可从以下位置安装

Brew 包管理器 

```cmd
brew install openssl
brew link openssl --force
```

或使用 MacPorts 

```cmd
sudo port install openssl
```

安装 OpenSSL 后（用于生成新的证书调用）：

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>创建证书 (Linux)

OpenSSL util 不适用于你的 Linux 操作系统，可使用以下命令进行安装。

对于 APT 包管理器  ：

```cmd
sudo apt-get install openssl
```

对于 Yellowdog 更新器  ：

```cmd
yum install openssl
```

对于 Redhat 包管理器  ：

```cmd
rpm install openssl
```

如果 OpenSSl 已可用于你的操作系统，则调用

```cmd
pbiviz --create-cert
```

来生成新证书。

或者从 [https://www.openssl.org](https://www.openssl.org) 或 [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) 获取

## <a name="generate-certificate-manually"></a>手动生成证书

可指定由任何工具生成的证书。

如果在系统中安装了 OpenSSL，可以运行以下命令生成新证书

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

通常，PowerBI-visuals-tools Web 服务器证书位于

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

（工具的全局实例）

或

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

（工具的本地实例）。

如果使用 PEM 格式，应将证书文件保存为 `PowerBICustomVisualTest_public.cer`，将私钥保存为 `PowerBICustomVisualTest_public.key`。
如果使用 PFX 格式，请将证书文件保存为 `PowerBICustomVisualTest_public.pfx`。

如果 PFX 证书文件需要密码，应使用以下格式

```cmd
\PowerBI-visuals-tools\config.json
```

在服务器部分指定：

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

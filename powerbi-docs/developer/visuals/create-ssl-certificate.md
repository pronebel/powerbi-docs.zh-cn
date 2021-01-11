---
title: 在 Power BI 嵌入式分析中为 Power BI 视觉对象创建 SSL 证书以增强嵌入式 BI 见解
description: 了解如何使用 Windows、Mac 或 Linux 中的 Power BI 视觉对象工具来生成 SSL 证书，或手动生成 SSL 证书。 使用 Power BI 嵌入式分析改进嵌入式 BI 见解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 7897d25f3ac49c0f1b728f2aaf05b8612de67055
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885513"
---
# <a name="create-an-ssl-certificate"></a>创建 SSL 证书

本文介绍如何为 Power BI 视觉对象生成和安装安全套接字层 (SSL) 证书。

对于 Windows、macOS X 和 Linux 过程，必须安装 Power BI 视觉对象工具 pbiviz 包。 有关详细信息，请参阅[设置用于开发 Power BI 视觉对象的环境](./environment-setup.md)。 

## <a name="create-a-certificate-on-windows"></a>在 Windows 上创建证书

若要在 Windows 8 或更高版本上使用 PowerShell cmdlet `New-SelfSignedCertificate` 生成证书，请运行以下命令：

```powershell
pbiviz --install-cert
```

对于 Windows 7，`pbiviz` 工具要求可从命令行获取 OpenSSL 实用工具。 若要安装 OpenSSL，请转到 [OpenSSL](https://www.openssl.org) 或 [OpenSSL 二进制文件](https://wiki.openssl.org/index.php/Binaries)。

有关安装证书的详细信息和说明，请参阅[为 Windows 创建和安装证书](./environment-setup.md#create-and-install-a-certificate)。

## <a name="create-a-certificate-on-macos-x"></a>在 macOS X 上创建证书

通常，可以在 macOS X 操作系统中使用 OpenSSL 实用工具。

还可以通过运行以下命令之一来安装 OpenSSL 实用工具：

- 在 Brew 包管理器中：
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- 使用 MacPorts：
  
  ```cmd
  sudo port install openssl
  ```

安装 OpenSSL 实用工具后，请运行以下命令以生成新证书：

```cmd
pbiviz --install-cert
```

有关详细信息和说明，请参阅[创建和安装证书](./environment-setup.md#create-and-install-a-certificate)中的 OSX 选项卡。

## <a name="create-a-certificate-on-linux"></a>在 Linux 上创建证书

通常，可以在 Linux 操作系统中使用 OpenSSL 实用工具。

在开始之前，请运行以下命令，确保已安装 `openssl` 和 `certutil`：

```sh
which openssl
which certutil
```

如果未安装 `openssl` 和 `certutil`，请安装 `openssl` 和 `libnss3` 实用工具。

### <a name="create-the-ssl-configuration-file"></a>创建 SSL 配置文件

创建名为 /tmp/openssl.cnf 的文件，其中包含以下文本：

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>生成根证书颁发机构

若要生成根证书颁发机构 (CA) 以对本地证书进行签名，请运行以下命令：

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>生成 localhost 的证书 

若要使用生成的 CA 和 openssl.cnf 生成 `localhost` 的证书，请运行以下命令：

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>添加根证书

若要将根证书添加到 Chrome 浏览器的数据库，请运行：

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

若要将根证书添加到 Mozilla Firefox 浏览器的数据库，请运行：

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

若要添加系统范围的根证书，请运行：

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>删除根证书

若要删除根证书，请运行：

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>手动生成证书

还可以使用 OpenSSL 手动生成 SSL 证书。 可以指定任何工具以生成证书。

如果已安装 OpenSSL 实用工具，请运行以下命令生成新证书：

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

通常可以通过运行以下命令之一来查找 `PowerBI-visuals-tools` Web 服务器证书：

- 工具的全局实例：
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- 工具的本地实例：
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM 格式

如果使用隐私增强邮件 (PEM) 证书格式，请将证书文件另存为 PowerBIVisualTest_public.crt，并将私钥另存为 PowerBIVisualTest_private.key。

### <a name="pfx-format"></a>PFX 格式

如果使用个人信息交换 (PFX) 证书格式，请将证书文件另存为 PowerBIVisualTest_public.pfx。

如果 PFX 证书文件需要密码，请执行以下操作：

1. 在配置文件中，指定：
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. 在“`server`”部分中，通过替换 \<YOUR PASSPHRASE> 占位符来指定密码：

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>后续步骤
- [开发 Power BI 圆形卡片视觉对象](develop-circle-card.md)
- [Power BI 视觉对象示例](samples.md)
- [将 Power BI 视觉对象发布到 AppSource](office-store.md)
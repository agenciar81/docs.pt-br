---
title: Instale o .NET Core no Gerenciador de pacotes Ubuntu 19.04 - .NET Core
description: Use um gerenciador de pacotes para instalar o .NET Core SDK e o tempo de execução no Ubuntu 19.04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: c7b30d2760a0a83a0fdd7ff5fa35b2f3d490494f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920672"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 Package Manager - Instalar .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Este artigo descreve como usar um gerenciador de pacotes para instalar o .NET Core no Ubuntu 19.04. Se você estiver instalando o tempo de execução, sugerimos que você instale o [tempo de execução do ASP.NET Core,](#install-the-aspnet-core-runtime)pois inclui os tempos de execução do .NET Core e do ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Registrar a chave e o feed da Microsoft

Antes de instalar o .NET, você precisará:

- Registre a chave da Microsoft.
- Registre o repositório do produto.
- Instale as dependências necessárias.

Isso só precisa ser feito uma vez por computador.

Abra um terminal e execute os seguintes comandos.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Atualize os produtos disponíveis para instalação e instale o .NET Core SDK. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote dotnet-sdk-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="install-the-aspnet-core-runtime"></a>Instale o tempo de execução do ASP.NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do ASP.NET Core. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote aspnetcore-runtime-3.1,** consulte a [solucionar problemas na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Atualize os produtos disponíveis para instalação e instale o tempo de execução do .NET Core. Em seu terminal, execute os seguintes comandos.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o tempo de execução do dotnet-3.1**do pacote, consulte a [seção 'Solucionar problemas' na](#troubleshoot-the-package-manager) seção 'Gerenciador de pacotes'.

## <a name="how-to-install-other-versions"></a>Como instalar outras versões

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Solucionar problemas do gerenciador de pacotes

Esta seção fornece informações sobre erros comuns que você pode obter ao usar o gerenciador de pacotes para instalar o .NET Core.

### <a name="unable-to-locate"></a>Não é possível localizar

Se você receber uma mensagem de erro semelhante a **Não conseguir localizar o pacote {o pacote .NET Core},** execute os seguintes comandos.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Se isso não funcionar, você pode executar uma instalação manual com os seguintes comandos.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Falhou em buscar

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

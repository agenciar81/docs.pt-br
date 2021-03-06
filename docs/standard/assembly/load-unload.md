---
title: Como carregar e descarregar assemblies
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155770"
---
# <a name="how-to-load-and-unload-assemblies"></a>Como carregar e descarregar assemblies
Os assemblies referenciados pelo seu programa serão automaticamente carregados pelo Common Language Runtime, mas também é possível carregar dinamicamente assemblies específicos no domínio do aplicativo atual. Para obter mais informações, consulte [como carregar assemblies em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

No .NET Framework, não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados. No .NET Core, a classe <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> manipula o descarregamento de assemblies. Para obter mais informações, consulte [como usar e depurar o descarregamento de assembly no .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>carregar ou descarregar assemblies

Para carregar um assembly em um domínio de aplicativo, use um dos vários métodos de carga contidos nas classes <xref:System.AppDomain> e <xref:System.Reflection.Assembly>. Para obter mais informações, consulte [como carregar assemblies em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Observe que o .NET Core dá suporte apenas a um único domínio de aplicativo.

Para descarregar um assembly no .NET Framework, você deve descarregar todos os domínios de aplicativo que o contêm. Para descarregar um domínio de aplicativo, use o método <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](../../framework/app-domains/how-to-unload-an-application-domain.md).

Se você quiser descarregar alguns assemblies, mas não outros em um aplicativo .NET Framework, considere criar um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, descarregar esse domínio de aplicativo. Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies no .NET](index.md)
- [Como carregar assemblies em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

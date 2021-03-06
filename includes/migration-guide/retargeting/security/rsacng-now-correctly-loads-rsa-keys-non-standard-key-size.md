---
ms.openlocfilehash: 6d9f4b630e95d9a63393da3ae0ecd83c2b994712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859356"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a>Agora, RSACng carrega corretamente as chaves RSA de tamanho não padrão

|   |   |
|---|---|
|Detalhes|Nas versões do .NET Framework anteriores a 4.6.2, os clientes com tamanhos de chave não padrão para certificados RSA não conseguiam acessá-las por meio dos métodos de extensão <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name> e <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=name>.  Uma <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> com uma mensagem &quot;O tamanho de chave solicitado não é compatível&quot; é gerada. Esse problema foi corrigido no .NET Framework 4.6.2. Da mesma forma, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> e <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> agora funcionam com tamanhos de chave não padrão sem gerar um <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>.|
|Sugestão|Se houver qualquer lógica de tratamento de exceções dependente do comportamento anterior, em que um <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> é gerado quando tamanhos de chave não padrão são usados, considere remover essa lógica.|
|Escopo|Microsoft Edge|
|Versão|4.6.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType></li></ul>|


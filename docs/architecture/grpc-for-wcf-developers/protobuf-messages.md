---
title: Mensagens Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como as mensagens Protobuf são definidas em IDL e geradas C#no.
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543034"
---
# <a name="protobuf-messages"></a>Mensagens de Protobuf

Esta seção aborda como declarar mensagens de buffer de protocolo (Protobuf) em arquivos `.proto`. Ele explica os conceitos fundamentais de números e tipos de campo e examina o C# código que o compilador de `protoc` gera. 

O restante do capítulo examinará mais detalhadamente como os diferentes tipos de dados são representados em Protobuf.

## <a name="declaring-a-message"></a>Declarando uma mensagem

No Windows Communication Foundation (WCF), uma classe `Stock` para um aplicativo de comércio no mercado de ações pode ser definida como o exemplo a seguir:

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Para implementar a classe equivalente em Protobuf, você deve declará-la no arquivo `.proto`. O compilador de `protoc` irá gerar a classe .NET como parte do processo de compilação.

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

A primeira linha declara a versão de sintaxe que está sendo usada. A versão 3 da linguagem foi lançada em 2016. É a versão que recomendamos para os serviços gRPCs.

A linha de `option csharp_namespace` especifica o namespace a ser usado para os C# tipos gerados. Essa opção será ignorada quando o arquivo de `.proto` for compilado para outros idiomas. Os arquivos Protobuf geralmente contêm opções específicas de idioma para vários idiomas.

A definição da mensagem de `Stock` especifica quatro campos. Cada um tem um tipo, um nome e um número de campo.

## <a name="field-numbers"></a>Números de campo

Os números de campo são uma parte importante do Protobuf. Eles são usados para identificar campos nos dados binários codificados, o que significa que eles não podem mudar de versão para versão do seu serviço. A vantagem é que a compatibilidade com versões anteriores e a compatibilidade com o encaminhamento são possíveis. Os clientes e serviços simplesmente ignorarão os números de campo que não conhecem, desde que a possibilidade de valores ausentes seja manipulada.

No formato binário, o número do campo é combinado com um identificador de tipo. Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte. Os números de 16 a 2.047 levam 2 bytes. Você pode ficar mais alto se precisar de mais de 2.047 campos em uma mensagem por qualquer motivo. Os identificadores de byte único para os números de campo de 1 a 15 oferecem melhor desempenho, portanto, você deve usá-los para os campos mais básicos e usados com frequência.

## <a name="types"></a>Tipos

As declarações de tipo estão usando os tipos de dados escalares nativos do Protobuf, que são abordados em mais detalhes na [próxima seção](protobuf-data-types.md). O restante deste capítulo abordará os tipos internos do Protobuf e mostrará como eles se relacionam com os tipos .NET comuns.

> [!NOTE]
> O Protobuf não dá suporte nativo a um tipo de `decimal`, portanto, `double` é usado em vez disso. Para aplicativos que exigem precisão decimal completa, consulte a [seção sobre decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.

## <a name="the-generated-code"></a>O código gerado

Quando você cria seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus C# tipos nativos para tipos. O tipo de `Stock` gerado teria a seguinte assinatura:

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

O código real gerado é muito mais complicado do que isso. O motivo é que cada classe contém todo o código necessário para serializar e desserializar para o formato de fio binário.

### <a name="property-names"></a>Nomes de propriedade

Observe que o compilador Protobuf aplicou `PascalCase` aos nomes de propriedade, embora eles fossem `snake_case` no arquivo `.proto`. O [Guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda o uso de `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.

>[!div class="step-by-step"]
>[Anterior](protocol-buffers.md)
>[Próximo](protobuf-data-types.md)

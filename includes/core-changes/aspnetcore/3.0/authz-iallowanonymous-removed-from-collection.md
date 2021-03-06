---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901585"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorização: IAllowAnonymous removido de AuthorizationFilterContext. Filters

A partir de ASP.NET Core 3,0, o MVC não adiciona [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) para atributos [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) que foram descobertos em controladores e métodos de ação. Essa alteração é abordada localmente para derivações de <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, mas é uma alteração significativa para <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> e <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementações. Essas implementações encapsuladas em um atributo [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) são uma maneira [popular](https://stackoverflow.com/a/41348219/608220) e com suporte para obter autorização baseada em atributo fortemente tipada quando a configuração e a injeção de dependência são necessárias.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> apareceu na coleção [AuthorizationFilterContext. Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) . O teste da presença da interface era uma abordagem válida para substituir ou desabilitar o filtro em métodos individuais do controlador.

#### <a name="new-behavior"></a>Novo comportamento

`IAllowAnonymous` não aparece mais na coleção de `AuthorizationFilterContext.Filters`. `IAsyncAuthorizationFilter` implementações que dependem do comportamento antigo normalmente causam respostas intermitentes HTTP 401 não autorizadas ou HTTP 403 Proibido.

#### <a name="reason-for-change"></a>Motivo da alteração

Uma nova estratégia de roteamento de ponto de extremidade foi introduzida no ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Ação recomendada

Pesquise os metadados do ponto de extremidade para `IAllowAnonymous`. Por exemplo:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Um exemplo dessa técnica é visto neste [método HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

{1&gt;Nenhum&lt;1}

<!--

#### Affected APIs

Not detectable via API analysis

-->

---
title: Alterações recentes – .NET Framework para o .NET Core
titleSuffix: ''
description: Lista as alterações significativas de .NET Framework para o .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449382"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Alterações recentes de migração do .NET Framework para o .NET Core

Se você estiver migrando um aplicativo do .NET Framework para o .NET Core, as alterações significativas listadas neste artigo poderão afetar você. As alterações significativas são agrupadas por categoria e dentro dessas categorias, pela versão do .NET Core na qual elas foram introduzidas.

> [!NOTE]
> Este artigo não é uma lista completa de alterações significativas entre o .NET Framework e o .NET Core. As alterações significativas mais importantes são adicionadas aqui, pois estamos cientes delas.

## <a name="corefx"></a>CoreFx

- [Alteração no valor padrão de UseShellExecute](#change-in-default-value-of-useshellexecute)
- [UnauthorizedAccessException gerado por FileSystemInfo. Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Criptografia

- [O parâmetro booliano de SignedCms. ComputeSignature é respeitado](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Windows Forms suporte foi adicionado ao .NET Core na versão 3,0. Se você estiver migrando um aplicativo Windows Forms do .NET Framework para o .NET Core, as alterações significativas listadas aqui podem afetar seu aplicativo.

- [Controles removidos](#removed-controls)
- [Evento CellFormatting não gerado se ToolTip for mostrado](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control. DefaultFont alterado para Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernização do FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute removido de alguns tipos de Windows Forms](#serializableattribute-removed-from-some-windows-forms-types)
- [Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade EnableVisualStyleValidation](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Não há suporte para a opção de compatibilidade UseLegacyImages](#uselegacyimages-compatibility-switch-not-supported)
- [Alteração de acesso para AccessibleObject. RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [APIs duplicadas removidas do Windows Forms](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Core 3,1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Confira também

- [APIs que sempre lançam exceções no .NET Core](unsupported-apis.md)
- [.NET Framework tecnologias não disponíveis no .NET Core](../porting/net-framework-tech-unavailable.md)

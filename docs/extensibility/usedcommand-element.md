---
title: Element UsedCommand | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698824"
---
# <a name="usedcommand-element"></a>UsedCommand, element
Umożliwia vsPackage dostęp do polecenia, które jest zdefiniowane w innym pliku vsct. Na przykład jeśli vsPackage używa standardowego polecenia **Kopiuj,** które jest zdefiniowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłokę, można dodać polecenie do menu lub paska narzędzi bez ponownego implementowania go.

## <a name="syntax"></a>Składnia

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagany. Identyfikator GUID pary identyfikatorów GUID identyfikujący polecenie.|
|id|Wymagany. Identyfikator pary identyfikatorów GUID identyfikującej polecenie.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak||

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupy UsedCommand elementów i innych usedcommands grup.|

## <a name="remarks"></a>Uwagi
 Dodając polecenie do `<UsedCommands>` elementu, VSPackage informuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowisko, że VSPackage wymaga polecenia. Należy dodać `<UsedCommand>` element dla każdego polecenia, którego wymaga pakiet, który może nie być uwzględniony we wszystkich wersjach i konfiguracjach programu Visual Studio. Na przykład jeśli pakiet wywołuje polecenie, które jest specyficzne dla języka Visual C++, polecenie nie `<UsedCommand>` będzie dostępne dla użytkowników visual web developer, chyba że dołączysz element polecenia.

## <a name="example"></a>Przykład

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Zobacz też
- [UsedCommands, element](../extensibility/usedcommands-element.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

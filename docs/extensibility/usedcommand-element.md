---
title: UsedCommand, element | Microsoft Docs
description: Element UsedCommand umożliwia pakietowi VSPackage dostęp do polecenia zdefiniowanego w innym pliku vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9d120353b9d6191bfcaae38151eb970ab1071b99
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903050"
---
# <a name="usedcommand-element"></a>UsedCommand, element
Umożliwia pakietowi VSPackage dostęp do polecenia zdefiniowanego w innym pliku vsct. Jeśli na przykład pakiet VSPackage używa standardowego polecenia **Kopiowania** zdefiniowanego przez powłokę, możesz dodać polecenie do menu lub paska narzędzi bez jego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ponownego implementowania.

## <a name="syntax"></a>Składnia

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID pary identyfikatorów GUID, który identyfikuje polecenie.|
|identyfikator|Wymagane. Identyfikator pary identyfikatorów GUID, który identyfikuje polecenie.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak||

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[UsedCommands, element](../extensibility/usedcommands-element.md)|Grupy UżywaneGrupygrupy i inne używaneGrupy używanegrupy.|

## <a name="remarks"></a>Uwagi
 Dodając polecenie do `<UsedCommands>` elementu , pakiet VSPackage informuje środowisko, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakiet VSPackage wymaga polecenia . Należy dodać element dla dowolnego polecenia wymaganego przez pakiet, który może nie być uwzględniony we wszystkich wersjach i konfiguracjach `<UsedCommand>` Visual Studio. Na przykład jeśli pakiet wywołuje polecenie specyficzne dla Visual C++, polecenie nie będzie dostępne dla użytkowników programu Visual Web Developer, chyba że dołączyć `<UsedCommand>` element dla polecenia.

## <a name="example"></a>Przykład

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Zobacz także
- [UsedCommands, element](../extensibility/usedcommands-element.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

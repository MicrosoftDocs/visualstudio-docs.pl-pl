---
title: CommandPlacements, element | Microsoft Docs
description: Element CommandPlacements grupuje elementy CommandPlacement i inne grupowania CommandPlacements. Element CommandPlacements jest opcjonalny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901893"
---
# <a name="commandplacements-element"></a>CommandPlacements, element
Element CommandPlacements grupuje elementy CommandPlacement i inne grupowania CommandPlacements.

 Element CommandPlacements jest opcjonalny. Jeśli żadne polecenia, grupy ani menu nie muszą znajdować się w lokalizacji pomocniczej, nie trzeba uwzględniać tej sekcji w pliku *vsct.*

## <a name="syntax"></a>Składnia

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Commandplacements|Grupuje elementy CommandPlacement i inne grupowania CommandPlacements.|
|[CommandPlacement, element](../extensibility/commandplacement-element.md)|Umożliwia uwzględnianie przycisków, grup i menu w więcej niż jednej grupie lub menu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia.|

## <a name="example"></a>Przykład

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Zobacz także
- [CommandPlacement, element](../extensibility/commandplacement-element.md)
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

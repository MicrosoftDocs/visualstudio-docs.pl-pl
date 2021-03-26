---
title: CommandPlacements — element | Microsoft Docs
description: Element CommandPlacements Grupuje elementy CommandPlacement i inne grupowania CommandPlacements. Element CommandPlacements jest opcjonalny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3547d1c5b94285ce113b3a3c112568aa5a9a5f65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089605"
---
# <a name="commandplacements-element"></a>CommandPlacements, element
Element CommandPlacements Grupuje elementy CommandPlacement i inne grupowania CommandPlacements.

 Element CommandPlacements jest opcjonalny. Jeśli żadna z poleceń, grup lub menu nie musi być uwzględniona w lokalizacji dodatkowej, nie trzeba uwzględniać tej sekcji w pliku *. vsct* .

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
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|CommandPlacements|Grupuje elementy CommandPlacement i inne grupy CommandPlacements.|
|[CommandPlacement, element](../extensibility/commandplacement-element.md)|Umożliwia uwzględnienie przycisków, grup i menu w więcej niż jednej grupie lub menu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element polecenia](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia.|

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
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

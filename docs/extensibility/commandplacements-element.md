---
title: CommandPlacements, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb22359c936caacef81f4c9b81993a46d47ccc0b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341885"
---
# <a name="commandplacements-element"></a>CommandPlacements, element
CommandPlacements, element grupy elementów CommandPlacement i inne grupy CommandPlacements.

 CommandPlacements, element jest opcjonalne. Jeśli nie poleceń, grup lub menu muszą być zawarte w lokalizacji dodatkowej, nie masz do uwzględnienia w tej sekcji w swojej *vsct* pliku.

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
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|CommandPlacements|Grupuje elementy CommandPlacement i inne grupy CommandPlacements.|
|[CommandPlacement, element](../extensibility/commandplacement-element.md)|Włącza przyciski, grup i menu, mają zostać uwzględnione w więcej niż jednej grupie lub menu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń.|

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
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
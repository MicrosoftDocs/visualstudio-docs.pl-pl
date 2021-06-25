---
title: CommandPlacement, element | Microsoft Docs
description: Element CommandPlacement umożliwia włączenie przycisków, grup i menu do więcej niż jednej grupy lub menu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69be89fb2773be9de632b8059cf217303daaede7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901997"
---
# <a name="commandplacement-element"></a>CommandPlacement, element
Element CommandPlacement umożliwia włączenie przycisków, grup i menu do więcej niż jednej grupy lub menu. Za pomocą CommandPlacement elementu, nie trzeba całkowicie ponownie zdefiniować te elementy, aby zmodyfikować wygląd interfejsu użytkownika.

 Aby uzyskać więcej informacji, zobacz Create reusable groups of buttons (Tworzenie [grup przycisków wielokrotnego użytku).](../extensibility/creating-reusable-groups-of-buttons.md)

## <a name="syntax"></a>Składnia

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID zestawu poleceń, zgodnie z definicją w [elemencie Symbols](../extensibility/symbols-element.md).|
|identyfikator|Wymagane. Identyfikator menu, grupy lub polecenia do umieszczenia, zgodnie z definicją w `Symbols Element` .|
|priority|Wymagane. Określa położenie wizualne elementu w jego elemencie nadrzędnym.|
|Warunek|Opcjonalny. Zobacz [Aattributes warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Wymagane. Menu lub grupa, która hostuje element do umieszczenia.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandPlacements, element](../extensibility/commandplacements-element.md)|Określa grupy elementów CommandPlacements i CommandPlacement.|

## <a name="example"></a>Przykład

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Zobacz także
- [CommandPlacements, element](../extensibility/commandplacements-element.md)
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: CommandPlacement — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739743"
---
# <a name="commandplacement-element"></a>CommandPlacement, element
Element CommandPlacement umożliwia uwzględnienie przycisków, grup i menu w więcej niż jednej grupie lub menu. Za pomocą elementu CommandPlacement nie trzeba całkowicie ponownie definiować tych elementów, aby modyfikować wygląd interfejsu użytkownika.

 Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md).

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
|guid|Wymagany. Identyfikator GUID zestawu poleceń, zgodnie z definicją w [elemencie Symbols](../extensibility/symbols-element.md).|
|identyfikator|Wymagany. Identyfikator menu, grupy lub polecenia, które mają zostać umieszczone, zgodnie z definicją w `Symbols Element` .|
|priority|Wymagany. Określa położenie wizualizacji elementu w jego elemencie nadrzędnym.|
|Warunek|Opcjonalny. Zobacz [warunkowe Aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Wymagany. Menu lub Grupa, która zawiera element, który ma zostać umieszczony.|

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

## <a name="see-also"></a>Zobacz też
- [CommandPlacements, element](../extensibility/commandplacements-element.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: Element dowodzenia | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739743"
---
# <a name="commandplacement-element"></a>Element połówka polecenia
CommandPlacement Element umożliwia przyciski, grupy i menu, które mają być zawarte w więcej niż jednej grupie lub menu. Za pomocą CommandPlacement element, nie trzeba całkowicie ponownie zdefiniować te elementy w celu zmodyfikowania wyglądu interfejsu użytkownika.

 Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md).

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
|Identyfikator GUID|Wymagany. Identyfikator guid zestawu poleceń, zgodnie z definicją w [symbolach elementu](../extensibility/symbols-element.md).|
|id|Wymagany. Identyfikator menu, grupy lub polecenia, które mają zostać umieszczone, zgodnie z definicją w pliku `Symbols Element`.|
|priority|Wymagany. Określa położenie wizualne elementu w jego elemencie nadrzędnym.|
|Warunek|Element opcjonalny. Zobacz [Warunkowe aattributes](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny|Wymagany. Menu lub grupa, w których znajduje się element, który ma zostać umieszczony.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Połowisku](../extensibility/commandplacements-element.md)|Określa grupy commandplacements i CommandPlacement elementów.|

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
- [Element Połowisku](../extensibility/commandplacements-element.md)
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

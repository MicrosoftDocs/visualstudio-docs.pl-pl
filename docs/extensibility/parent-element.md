---
title: Element nadrzędny | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702218"
---
# <a name="parent-element"></a>Element nadrzędny
Elementem nadrzędnym przycisku lub pola kombi może być tylko grupa. Nadrzędnym menu lub grupy może być inne menu lub grupa. W [komenda Element](../extensibility/commandplacement-element.md), ten element jest wymagany; we wszystkich innych przypadkach jest to opcjonalne. Jeśli ten element zostanie pominięty, element nadrzędny `Group_Undefined:0` zostanie dorozumiany.

## <a name="syntax"></a>Składnia

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|id|Wymagany. Identyfikator polecenia GUID/ID.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które VSPackage zapewnia zintegrowanemu środowisku programistycznemu (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|
|[Element przycisków](../extensibility/buttons-element.md)|Elementy [elementu przycisku](../extensibility/button-element.md) grupy.|
|[Element Menu](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje VSPackage.|
|[Element Grupy](../extensibility/groups-element.md)|Zawiera wpisy definiujące grupy poleceń programu VSPackage.|

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

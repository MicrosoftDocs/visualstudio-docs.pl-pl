---
title: Element nadrzędny | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702218"
---
# <a name="parent-element"></a>Element nadrzędny
Element nadrzędny przycisku lub pola kombi może być tylko grupą. Element nadrzędny menu lub grupy może być dowolnym innym menu lub grupą. W [elemencie CommandPlacement](../extensibility/commandplacement-element.md), ten element jest wymagany; we wszystkich innych przypadkach jest to opcjonalne. Jeśli ten element zostanie pominięty, `Group_Undefined:0` zostanie implikowany element nadrzędny elementu.

## <a name="syntax"></a>Składnia

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|identyfikator|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element polecenia](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które pakietu VSPackage zapewnia zintegrowane środowisko programistyczne (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|
|[Element Buttons](../extensibility/buttons-element.md)|Grupuje elementy [elementu Button](../extensibility/button-element.md) .|
|[Element menu](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje pakietu VSPackage.|
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy poleceń elementu pakietu VSPackage.|

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

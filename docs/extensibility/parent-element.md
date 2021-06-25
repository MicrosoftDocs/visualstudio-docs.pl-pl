---
title: Element nadrzędny | Microsoft Docs
description: Element nadrzędny określa, że element jest elementem nadrzędnym przycisku, pola kombi, menu lub grupy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901555"
---
# <a name="parent-element"></a>Element nadrzędny
Element nadrzędny przycisku lub pola kombi może być tylko grupą. Element nadrzędny menu lub grupy może być dowolnym innym menu lub grupą. W [elemencie CommandPlacement ten](../extensibility/commandplacement-element.md)element jest wymagany; We wszystkich innych wystąpieniach jest to opcjonalne. Jeśli ten element zostanie pominięty, zostanie implikowany element `Group_Undefined:0` nadrzędny .

## <a name="syntax"></a>Składnia

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.|
|identyfikator|Wymagane. Identyfikator identyfikatora GUID/ID polecenia.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia, które pakiet VSPackage zapewnia zintegrowanemu środowisku projektowemu (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje [elementy elementów przycisku.](../extensibility/button-element.md)|
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu implementowanych przez pakiet VSPackage.|
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy definiujące grupy poleceń dla pakietów VSPackage.|

## <a name="see-also"></a>Zobacz też
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

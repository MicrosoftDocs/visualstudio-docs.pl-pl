---
title: Element bitmapy | Microsoft Docs
description: Element Bitmap definiuje mapę bitową. Mapa bitowa jest ładowana z zasobu lub z pliku. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 32f07857f2d04989b0de021988b2961d4a1553d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068222"
---
# <a name="bitmap-element"></a>Element Bitmap
Definiuje mapę bitową. Mapa bitowa jest ładowana z zasobu lub z pliku.

## <a name="syntax"></a>Składnia

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID identyfikatora polecenia GUID/ID.<br /><br /> Atrybut GUID dla mapy bitowej nie jest skojarzony z żadną pakietu VSPackage lub inną grupą poleceń.  Powinna być unikatowa dla definicji mapy bitowej i nie powinna być używana w żadnym innym celu.|
|resID|Identyfikator identyfikatora polecenia GUID/ID. Wymagany jest atrybut resID lub href.<br /><br /> Atrybut resID jest IDENTYFIKATORem zasobu liczb całkowitych, który określa pasek mapy bitowej, który ma zostać załadowany podczas scalania tabeli poleceń.  Po załadowaniu tabeli poleceń mapy bitowe określone przez identyfikator zasobu zostaną załadowane z zasobu tego samego modułu.|
|usedList|Wymagany, jeśli jest obecny atrybut resID. Wybiera dostępne obrazy na pasku mapy bitowej.|
|Tag|Ścieżka do mapy bitowej. Wymagany jest atrybut resID lub href.<br /><br /> Ścieżka include szuka wskazanego pliku obrazu, który jest osadzony w danych binarnych.  Podczas scalania tabeli poleceń obraz jest kopiowany i nie są wymagane żadne dodatkowe Wyszukiwanie zasobów ani obciążenie.  Jeśli atrybut usedList nie istnieje, wszystkie obrazy na pasku są dostępne. **Uwaga:**  Obrazy mogą być dostarczane w jednym z kilku formatów, które zawierają pliki *BMP*, *PNG* i *. gif*.  Wcześniejsze wersje kompilatora nie obsługują obrazów mapy bitowej 32-bitowych, które mają informacje alfa dla częściowej przejrzystości. Obejście tych wersji ma zastosowanie w formacie *PNG* .|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Bitmapy, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|

## <a name="example"></a>Przykład

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

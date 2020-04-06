---
title: Element mapy bitowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739995"
---
# <a name="bitmap-element"></a>Element bitmapy
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
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.<br /><br /> Atrybut guid dla mapy bitowej nie jest skojarzony z żadnym VSPackage ani inną grupą poleceń.  Powinien być unikatowy dla definicji mapy bitowej i nie powinien być używany do żadnych innych celów.|
|Resid|Identyfikator polecenia GUID/ID. Wymagany jest atrybut resID lub href.<br /><br /> Atrybut resID jest identyfikatorem zasobu liczby całkowitej, który określa pasek mapy bitowej, który ma zostać załadowany podczas scalania tabeli poleceń.  Po załadowaniu tabeli poleceń mapy bitowe określone przez identyfikator zasobu zostaną załadowane z zasobu tego samego modułu.|
|usedList|Wymagane, jeśli atrybut resID jest obecny. Wybiera dostępne obrazy w pasku mapy bitowej.|
|Href|Ścieżka do mapy bitowej. Wymagany jest atrybut resID lub href.<br /><br /> Ścieżka dołączania jest wyszukiwana pod kątem wskazanego pliku obrazu, który jest osadzony w wynikowym pliku binarnym.  Podczas scalania tabeli poleceń obraz jest kopiowany i nie jest wymagane żadne dodatkowe wyszukiwanie lub ładowanie zasobów.  Jeśli atrybut usedList nie jest obecny, wszystkie obrazy w pasku są dostępne. **Uwaga:**  Obrazy mogą być dostarczane w jednym z kilku formatów, które obejmują *.bmp*, *.png*i *.gif*.  Wcześniejsze wersje kompilatora nie obsługiwały obrazów bitmapowych 32-bitowych, które miały informacje alfa dla częściowej przezroczystości. Rozwiązaniem dla tych wersji jest użycie formatu *png.*|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Mapy bitowe](../extensibility/bitmaps-element.md)|Grupy Elementy mapy bitowej.|

## <a name="example"></a>Przykład

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

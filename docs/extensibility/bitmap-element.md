---
title: Bitmap, element | Microsoft Docs
description: Element Bitmap definiuje mapę bitową. Mapa bitowa jest ładowana z zasobu lub z pliku. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8f3daf25a3ffe025bcdef65dbaa6def942d0fb4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903323"
---
# <a name="bitmap-element"></a>Bitmap, element
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
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.<br /><br /> Atrybut guid mapy bitowej nie jest skojarzony z żadnym pakietem VSPackage ani inną grupą poleceń.  Powinna być unikatowa w definicji mapy bitowej i nie powinna być używana do żadnego innego celu.|
|Resid|Identyfikator identyfikatora GUID/ID polecenia. Wymagany jest atrybut resID lub href.<br /><br /> Atrybut resID jest identyfikatorem zasobu liczby całkowitej, który określa pasek mapy bitowej, który ma zostać załadowany podczas scalania tabeli poleceń.  Podczas ładowania tabeli poleceń mapy bitowe określone przez identyfikator zasobu zostaną załadowane z zasobu tego samego modułu.|
|usedList|Wymagane, jeśli atrybut resID jest obecny. Wybiera dostępne obrazy na pasku mapy bitowej.|
|Href|Ścieżka do mapy bitowej. Wymagany jest atrybut resID lub href.<br /><br /> Ścieżka dołączania jest wyszukiwana dla wskazanego pliku obrazu, który jest osadzony w wynikowym pliku binarnym.  Podczas scalania tabeli poleceń obraz jest kopiowany i nie jest wymagane żadne dodatkowe wyszukiwania ani ładowania zasobów.  Jeśli atrybut usedList nie jest obecny, wszystkie obrazy na pasku są dostępne. **Uwaga:**  Obrazy mogą być dostarczane w jednym z kilku formatów, które *obejmują*.bmp, *.png* i *.gif*.  Wcześniejsze wersje kompilatora nie obsługiły 32-bitowych obrazów map bitowych, które miały informacje alfa w celu częściowej przezroczystości. Obejściem dla tych wersji jest użycie *.png* formatu.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|

## <a name="example"></a>Przykład

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Zobacz także
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: Elementy podrzędne (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa3bf24178f1096cd05e8471c18f466fdd8ee17f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914256"
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość dynamiczna XElement)

Pobiera służy do pobierania wszystkie elementy zależne bieżącego elementu, które odpowiadają określonej rozwiniętą nazwę indeksatora.

## <a name="syntax"></a>Składnia

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonego elementów podrzędnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.

Elementy w kolekcji zwracane są w kolejności dokumentu źródła XML.

Ta właściwość używa odroczonego wykonania.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)
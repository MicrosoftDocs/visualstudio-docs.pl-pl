---
title: Elementy podrzędne (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fab6b90489624955ddd567492d12f54d8de2686f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637348"
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobierania wszystkich elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.

## <a name="syntax"></a>Składnia

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonych elementów potomnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.

Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.

Ta właściwość używa wykonania odroczonego.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)
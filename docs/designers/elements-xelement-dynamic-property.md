---
title: Elementy (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d92e9ebd1e5be9f3535dcac136bb46ba33975f0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637319"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobierania elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.

## <a name="syntax"></a>Składnia

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę żądanych elementów podrzędnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.

Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.

Ta właściwość używa wykonania odroczonego.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Elementy potomne](../designers/descendants-xelement-dynamic-property.md)
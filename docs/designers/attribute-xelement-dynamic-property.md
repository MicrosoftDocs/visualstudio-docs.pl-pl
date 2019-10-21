---
title: Atrybut (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d7fc1aa0419863e933bdc0a828455fcda8671fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637398"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobierania wystąpienia atrybutu, który odpowiada określonej rozwiniętej nazwie.

## <a name="syntax"></a>Składnia

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `XAttribute Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonego atrybutu i zwraca odpowiednie <xref:System.Xml.Linq.XAttribute> lub `null`, jeśli nie ma atrybutu o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Wartość](../designers/value-xattribute-dynamic-property.md)
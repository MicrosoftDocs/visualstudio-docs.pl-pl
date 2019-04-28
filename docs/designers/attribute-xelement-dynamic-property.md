---
title: Atrybut (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926926"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość dynamiczna XElement)

Pobiera indeksatora używane do pobierania wystąpienia atrybutu, który odpowiada określony rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `XAttribute Item(String expandedName)`. Ten indeksator rozwiniętą nazwę określonego atrybutu przyjmuje i zwraca odpowiedni <xref:System.Xml.Linq.XAttribute>, lub `null` Jeśli istnieje atrybut o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Wartość](../designers/value-xattribute-dynamic-property.md)
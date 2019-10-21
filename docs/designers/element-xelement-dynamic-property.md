---
title: Element (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637324"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)

Pobiera indeksator używany do pobrania wystąpienia elementu podrzędnego, który odnosi się do określonej rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje rozszerzony parametr name i zwraca odpowiednie <xref:System.Xml.Linq.XElement> lub `null`, jeśli nie ma elementu o określonej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metodzie klasy <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)
---
title: Element (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 520df74dae14fe672eb7d3db1bdc23a0a6437b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976761"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)

Pobiera indeksatora używane do pobierania elementu podrzędnego wystąpienia elementu, który odpowiada określony rozwiniętej nazwy.

## <a name="syntax"></a>Składnia

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje parametr rozwiniętej nazwy i zwraca odpowiedni <xref:System.Xml.Linq.XElement>, lub `null` Jeśli nie ma żadnego elementu o podanej nazwie.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metody <xref:System.Xml.Linq.XContainer?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)
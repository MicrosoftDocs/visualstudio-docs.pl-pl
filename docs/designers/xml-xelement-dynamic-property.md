---
title: XML (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931250"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (właściwość dynamiczna XElement)

Pobiera niesformatowany XML zawartości elementu.

## <a name="syntax"></a>Składnia

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Właściwość wartości/zwracana wartość

A <xref:System.String> reprezentujący niesformatowany zawartość XML elementu.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> metody <xref:System.Xml.Linq.XNode?displayProperty=fullName> klasy, za pomocą `SaveOptions` parametr <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Wartość](../designers/value-xelement-dynamic-property.md)
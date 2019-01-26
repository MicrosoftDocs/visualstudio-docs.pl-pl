---
title: XML (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cadfd6f02cbe431cb5a74db4a3b7008d05d9c05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026986"
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
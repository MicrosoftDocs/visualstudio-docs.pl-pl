---
title: XML (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633524"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (właściwość dynamiczna XElement)

Pobiera niesformatowaną zawartość XML elementu.

## <a name="syntax"></a>Składnia

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

@No__t_0, która reprezentuje niesformatowaną zawartość XML elementu.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna metodzie <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> klasy <xref:System.Xml.Linq.XNode?displayProperty=fullName> z parametrem `SaveOptions` ustawionym na <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Wartość](../designers/value-xelement-dynamic-property.md)
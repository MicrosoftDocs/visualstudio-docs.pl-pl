---
title: Wartość (właściwość dynamiczna XAttribute)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634522"
---
# <a name="value-xattribute-dynamic-property"></a>Wartość (właściwość dynamiczna XAttribute)

Pobiera lub ustawia wartość atrybutu XML.

## <a name="syntax"></a>Składnia

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

@No__t_0 zawierający wartość tego atrybutu.

## <a name="exceptions"></a>Wyjątki

|Typ wyjątku|Warunek|
| - |---------------|
|<xref:System.ArgumentNullException>|Ustawienie `value` jest `null`.|

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna z właściwością <xref:System.Xml.Linq.XAttribute.Value%2A> klasy <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ale ta właściwość dynamiczna obsługuje również powiadomienia o zmianach.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Właściwości dynamiczne klasy XAttribute](../designers/value-xattribute-dynamic-property.md)
- [Atrybut](../designers/attribute-xelement-dynamic-property.md)
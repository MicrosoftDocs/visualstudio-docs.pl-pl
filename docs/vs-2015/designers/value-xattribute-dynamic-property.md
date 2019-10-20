---
title: Wartość (właściwość dynamiczna XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664046"
---
# <a name="value-xattribute-dynamic-property"></a>Wartość (właściwość dynamiczna XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera lub ustawia wartość atrybutu XML.

## <a name="syntax"></a>Składnia

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 @No__t_0 zawierający wartość tego atrybutu.

## <a name="exceptions"></a>Wyjątki

|Typ wyjątku|Warunek|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Ustawienie `value` jest `null`.|

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna z właściwością <xref:System.Xml.Linq.XAttribute.Value%2A> klasy <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ale ta właściwość dynamiczna obsługuje również powiadomienia o zmianach.

## <a name="see-also"></a>Zobacz też
 [atrybut](../designers/attribute-xelement-dynamic-property.md) <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName> [Właściwości dynamicznej klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)

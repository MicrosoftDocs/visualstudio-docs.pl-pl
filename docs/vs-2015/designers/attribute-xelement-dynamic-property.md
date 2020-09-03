---
title: Atrybut (właściwość dynamiczna XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657979"
---
# <a name="attribute-xelement-dynamic-property"></a>Atrybut (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera indeksator używany do pobierania wystąpienia atrybutu, który odpowiada określonej rozwiniętej nazwie.

## <a name="syntax"></a>Składnia

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Indeksator typu `XAttribute Item(String expandedName)` . Ten indeksator przyjmuje rozwiniętą nazwę określonego atrybutu i zwraca odpowiednie <xref:System.Xml.Linq.XAttribute> lub `null` Jeśli nie ma atrybutu o określonej nazwie.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna z <xref:System.Xml.Linq.XElement.Attribute%2A> metodą <xref:System.Xml.Linq.XElement?displayProperty=fullName> klasy.

## <a name="see-also"></a>Zobacz też
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[Wartość](../designers/value-xattribute-dynamic-property.md) [właściwości dynamicznych klasy XElement](../designers/xelement-class-dynamic-properties.md)

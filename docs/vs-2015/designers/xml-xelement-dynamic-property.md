---
title: XML (właściwość dynamiczna XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663843"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera niesformatowaną zawartość XML elementu.

## <a name="syntax"></a>Składnia

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 <xref:System.String>Reprezentujący niesformatowaną zawartość XML elementu.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna z <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> metodą <xref:System.Xml.Linq.XNode?displayProperty=fullName> klasy z `SaveOptions` parametrem ustawionym na <xref:System.Xml.Linq.SaveOptions> .

## <a name="see-also"></a>Zobacz też
 [Wartość](../designers/value-xelement-dynamic-property.md) [właściwości dynamicznych klasy XElement](../designers/xelement-class-dynamic-properties.md)

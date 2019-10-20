---
title: Elementy podrzędne (właściwość dynamiczna XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664786"
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera indeksator używany do pobierania wszystkich elementów podrzędnych bieżącego elementu, który jest zgodny z określoną rozwiniętą nazwą.

## <a name="syntax"></a>Składnia

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość
 Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonych elementów potomnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi
 Ta właściwość jest równoważna z metodą <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> klasy <xref:System.Xml.Linq.XContainer>.

 Elementy w zwracanej kolekcji znajdują się w kolejności dokumentu źródłowego XML.

 Ta właściwość używa wykonania odroczonego.

## <a name="see-also"></a>Zobacz też
 [Elementy](../designers/elements-xelement-dynamic-property.md) [właściwości dynamicznych klasy XElement](../designers/xelement-class-dynamic-properties.md)

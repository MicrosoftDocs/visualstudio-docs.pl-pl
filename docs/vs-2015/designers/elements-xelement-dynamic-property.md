---
title: Elementy (właściwość dynamiczna XElement) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 158e200a33b4783df9f63f42a1eca7bb8957d449
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145684"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera służy do pobierania elementy podrzędne bieżącego elementu, które odpowiadają określonej rozwiniętą nazwę indeksatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator ma rozwiniętej nazwy wymaganymi podrzędnymi elementami i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.  
  
 Elementy w kolekcji zwracane są w kolejności dokumentu źródła XML.  
  
 Ta właściwość używa odroczonego wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Element](../designers/element-xelement-dynamic-property.md)   
 [Elementy potomne](../designers/descendants-xelement-dynamic-property.md)

---
title: Elementy podrzędne (właściwość dynamiczna XElement) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c89e04346a4b08d6ee7bbc0012ef52f3b648512
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789355"
---
# <a name="descendants-xelement-dynamic-property"></a>Elementy podrzędne (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera służy do pobierania wszystkie elementy zależne bieżącego elementu, które odpowiadają określonej rozwiniętą nazwę indeksatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator przyjmuje rozwiniętą nazwę określonego elementów podrzędnych i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.  
  
 Elementy w kolekcji zwracane są w kolejności dokumentu źródła XML.  
  
 Ta właściwość używa odroczonego wykonania.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)

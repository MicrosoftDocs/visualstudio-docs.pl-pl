---
title: Element (właściwość dynamiczna XElement) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e7789a94c38f7c6d7db22d9214b19857e4c62055
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195166"
---
# <a name="element-xelement-dynamic-property"></a>Element (właściwość dynamiczna XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera indeksatora używane do pobierania elementu podrzędnego wystąpienia elementu, który odpowiada określony rozwiniętej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Indeksator typu `XElement Item(String expandedName)`. Ten indeksator przyjmuje parametr rozwiniętej nazwy i zwraca odpowiedni <xref:System.Xml.Linq.XElement>, lub `null` Jeśli nie ma żadnego elementu o podanej nazwie.  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Element%2A> metody <xref:System.Xml.Linq.XContainer?displayProperty=fullName> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)

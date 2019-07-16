---
title: Wartość (właściwość dynamiczna XAttribute) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187510"
---
# <a name="value-xattribute-dynamic-property"></a>Wartość (właściwość dynamiczna XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera lub ustawia wartość atrybutu XML.  
  
## <a name="syntax"></a>Składnia  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Element <xref:System.String> zawierający wartość tego atrybutu.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|Podczas ustawiania, `value` jest `null`.|  
  
## <a name="remarks"></a>Uwagi  
 Ta właściwość jest równoważna <xref:System.Xml.Linq.XAttribute.Value%2A> właściwość <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> klasy, ale ta właściwość dynamiczna obsługuje również powiadomienia o zmianach.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)   
 [Atrybut](../designers/attribute-xelement-dynamic-property.md)

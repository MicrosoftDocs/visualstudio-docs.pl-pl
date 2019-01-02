---
title: Elementy (właściwość dynamiczna XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01bca0771fb02ab8442132eaff4759fe7277ad6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837056"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (właściwość dynamiczna XElement)

Pobiera służy do pobierania elementy podrzędne bieżącego elementu, które odpowiadają określonej rozwiniętą nazwę indeksatora.

## <a name="syntax"></a>Składnia

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Indeksator typu `IEnumerable<XElement> Item(String expandedName)`. Ten indeksator ma rozwiniętej nazwy wymaganymi podrzędnymi elementami i zwraca pasujące elementy podrzędne w <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekcji.

## <a name="remarks"></a>Uwagi

Ta właściwość jest równoważna <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> metody <xref:System.Xml.Linq.XContainer> klasy.

Elementy w kolekcji zwracane są w kolejności dokumentu źródła XML.

Ta właściwość używa odroczonego wykonania.

## <a name="see-also"></a>Zobacz także

- [Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Elementy potomne](../designers/descendants-xelement-dynamic-property.md)
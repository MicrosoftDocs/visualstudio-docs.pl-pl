---
title: LINQ to XML właściwości dynamiczne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff0b31512711b8888b05fcfde191c8cb5c47d99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664262"
---
# <a name="linq-to-xml-dynamic-properties"></a>Właściwości dynamiczne LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta sekcja zawiera informacje referencyjne na temat właściwości dynamicznych w LINQ to XML. W szczególnych przypadkach te właściwości są uwidaczniane przez klasy <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które znajdują się w przestrzeni nazw <xref:System.Xml.Linq>.

 Jak wyjaśniono w temacie [Omówienie powiązania danych WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), Każda właściwość dynamiczna jest równoważna z standardową właściwością publiczną lub metodą w tej samej klasie. Tych standardowych członków należy używać w większości celów; właściwości dynamiczne są udostępniane w ramach scenariuszy powiązań danych LINQ to XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich tych klas, zobacz tematy dotyczące <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>.

 W odniesieniu do ich rozwiązanych wartości właściwości dynamiczne w tej sekcji należą do dwóch kategorii:

- Proste, takie jak `Value` właściwości w klasach <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które rozpoznają się z jedną wartością.

- Indeksowane wartości, takie jak [elementy](../designers/elements-xelement-dynamic-property.md) i właściwości [potomne](../designers/descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, które są rozpoznawane jako typ indeksatora. Aby można było rozpoznać typy indeksatora do żądanej wartości lub kolekcji, należy do nich przekazywać parametry rozszerzonej nazwy.

  Wszystkie właściwości dynamiczne zwracające wartość indeksowaną typu <xref:System.Collections.Generic.IEnumerable%601> używają wykonywania deffered. Aby uzyskać więcej informacji o odroczonym wykonywaniu, zobacz [wprowadzenie do zapytań LINQC#()](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>W tej sekcji

|Temat|Opis|
|-----------|-----------------|
|[Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)|Zawiera szczegółowe informacje na temat właściwości dynamicznych uwidocznionych przez klasę <xref:System.Xml.Linq.XAttribute>.|
|[Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)|Zawiera szczegółowe informacje na temat właściwości dynamicznych uwidocznionych przez klasę <xref:System.Xml.Linq.XElement>.|

## <a name="reference"></a>Tematy pomocy
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Zobacz też
 [Powiązanie danych WPF z](../designers/wpf-data-binding-with-linq-to-xml.md) [powiązaniem danych LINQ to XML WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [wprowadzeniem do zapytań LINQC#()](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)

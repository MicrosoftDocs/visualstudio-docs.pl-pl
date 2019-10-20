---
title: Właściwości dynamiczne LINQ to XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5993639a1bd6db1b814615bc75c1a57b64212185
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635261"
---
# <a name="linq-to-xml-dynamic-properties"></a>Właściwości dynamiczne LINQ to XML

Ta sekcja zawiera informacje referencyjne na temat właściwości dynamicznych w LINQ to XML. W szczególnych przypadkach te właściwości są uwidaczniane przez klasy <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które znajdują się w przestrzeni nazw <xref:System.Xml.Linq>.

Jak wyjaśniono w temacie [Omówienie powiązania danych WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), Każda właściwość dynamiczna jest równoważna z standardową właściwością publiczną lub metodą w tej samej klasie. Tych standardowych członków należy używać w większości celów; właściwości dynamiczne są udostępniane w ramach scenariuszy powiązań danych LINQ to XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich tych klas, zobacz tematy dotyczące <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>.

W odniesieniu do ich rozwiązanych wartości właściwości dynamiczne w tej sekcji należą do dwóch kategorii:

- Proste, takie jak `Value` właściwości w klasach <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement>, które rozpoznają się z jedną wartością.

- Indeksowane wartości, takie jak [elementy](../designers/elements-xelement-dynamic-property.md) i właściwości [potomne](../designers/descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, które są rozpoznawane jako typ indeksatora. Aby można było rozpoznać typy indeksatora do żądanej wartości lub kolekcji, należy do nich przekazywać parametry rozszerzonej nazwy.

Wszystkie właściwości dynamiczne zwracające wartość indeksowaną typu <xref:System.Collections.Generic.IEnumerable%601> korzystają z odroczonego wykonania. Aby uzyskać więcej informacji o odroczonym wykonywaniu, zobacz [wprowadzenie do zapytań LINQC#()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Tematy pomocy

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Powiązanie danych WPF z LINQ to XML przegląd](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)

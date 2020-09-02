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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664262"
---
# <a name="linq-to-xml-dynamic-properties"></a>Właściwości dynamiczne LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta sekcja zawiera informacje referencyjne na temat właściwości dynamicznych w LINQ to XML. W szczególnych przypadkach te właściwości są uwidaczniane <xref:System.Xml.Linq.XAttribute> przez <xref:System.Xml.Linq.XElement> klasy i, które znajdują się w <xref:System.Xml.Linq> przestrzeni nazw.

 Jak wyjaśniono w temacie [Omówienie powiązania danych WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), Każda właściwość dynamiczna jest równoważna z standardową właściwością publiczną lub metodą w tej samej klasie. Tych standardowych członków należy używać w większości celów; właściwości dynamiczne są udostępniane w ramach scenariuszy powiązań danych LINQ to XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich tych klas, zobacz <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> Tematy pomocy i.

 W odniesieniu do ich rozwiązanych wartości właściwości dynamiczne w tej sekcji należą do dwóch kategorii:

- Proste, takie jak `Value` właściwości w <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> klasach i, które rozwiązują do pojedynczej wartości.

- Indeksowane wartości, takie jak [elementy](../designers/elements-xelement-dynamic-property.md) i właściwości elementów [podrzędnych](../designers/descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement> , które są rozpoznawane jako typ indeksatora. Aby można było rozpoznać typy indeksatora do żądanej wartości lub kolekcji, należy do nich przekazywać parametry rozszerzonej nazwy.

  Wszystkie właściwości dynamiczne, które zwracają wartość indeksowaną typu <xref:System.Collections.Generic.IEnumerable%601> Użyj deffered wykonywania. Aby uzyskać więcej informacji o odroczonym wykonywaniu, zobacz [wprowadzenie do zapytań LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>W tej sekcji

|Temat|Opis|
|-----------|-----------------|
|[Właściwości dynamiczne klasy XAttribute](../designers/xattribute-class-dynamic-properties.md)|Zawiera szczegółowe informacje o właściwościach dynamicznych uwidocznionych przez <xref:System.Xml.Linq.XAttribute> klasę.|
|[Właściwości dynamiczne klasy XElement](../designers/xelement-class-dynamic-properties.md)|Zawiera szczegółowe informacje o właściwościach dynamicznych uwidocznionych przez <xref:System.Xml.Linq.XElement> klasę.|

## <a name="reference"></a>Dokumentacja
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Zobacz też
 [Powiązanie danych WPF z](../designers/wpf-data-binding-with-linq-to-xml.md) [powiązaniem danych LINQ to XML WPF z LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [wprowadzeniem do zapytań LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)

---
title: LINQ to XML właściwości dynamiczne
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78930e2f7aa1547bac0a2743a83e0b596e0c1510
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990670"
---
# <a name="linq-to-xml-dynamic-properties"></a>Właściwości dynamiczne LINQ to XML

Ta sekcja zawiera informacje na temat właściwości dynamicznych w składniku LINQ to XML. W szczególności te właściwości są udostępniane przez <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klasy, które znajdują się w <xref:System.Xml.Linq> przestrzeni nazw.

Zgodnie z opisem w temacie [powiązanie danych — omówienie WPF za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), każdy z właściwości dynamicznych jest odpowiednikiem standardowa publiczna właściwość lub metoda w tej samej klasy. Te składniki standardowe należy używać w przypadku większości celów; właściwości dynamiczne znajdują się w szczególności dla programu LINQ to scenariusze powiązania danych XML. Aby uzyskać więcej informacji na temat standardowych elementów członkowskich w ramach tych zajęć, zobacz <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> tematy referencyjne.

W odniesieniu do ich rozwiązane wartości właściwości dynamicznych w tej sekcji można podzielić na dwie kategorie:

- Te proste, takie jak `Value` właściwości w <xref:System.Xml.Linq.XAttribute> i <xref:System.Xml.Linq.XElement> klas, które nawiązują do pojedynczej wartości.

- Indeksowane wartości, takich jak [elementy](../designers/elements-xelement-dynamic-property.md) i [elementy podrzędne](../designers/descendants-xelement-dynamic-property.md) właściwości <xref:System.Xml.Linq.XElement>, który rozpoznać jako typ indeksatora. W przypadku typów indeksatora jest rozpoznawana przez żądaną wartość lub kolekcję parametrem rozwiniętej nazwy muszą być przekazywane do nich.

Wszystkie właściwości dynamicznych, które zwracają indeksowanej wartości typu <xref:System.Collections.Generic.IEnumerable%601> stosować odroczone wykonania. Aby uzyskać więcej informacji na temat odroczonego wykonania zobacz [wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Tematy pomocy

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych WPF za pomocą LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Powiązanie danych WPF za pomocą LINQ to XML — Przegląd](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)

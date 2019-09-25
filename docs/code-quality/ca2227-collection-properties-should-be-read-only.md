---
title: 'CA2227: Właściwości kolekcji powinny być tylko do odczytu'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 3d097a67c9a62a6847ff6ab0bb882257c082ca6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231302"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Właściwości kolekcji powinny być tylko do odczytu

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Zewnętrzna, modyfikowalna właściwość jest typu, który implementuje <xref:System.Collections.ICollection?displayProperty=fullName>. Ta reguła ignoruje tablice, indeksatory (właściwości o nazwie "Item") i zestawy uprawnień.

## <a name="rule-description"></a>Opis reguły

Właściwość kolekcji zapisywalnej umożliwia użytkownikowi zastąpienie kolekcji zupełnie inną kolekcją. Właściwość tylko do odczytu uniemożliwia zamienienie kolekcji, ale nadal zezwala na ustawianie poszczególnych członków. Jeśli zastępowanie kolekcji jest celem, preferowanym wzorcem projektu jest dołączenie metody usuwania wszystkich elementów z kolekcji i metody ponownego wypełnienia kolekcji. <xref:System.Collections.ArrayList.Clear%2A> Zobacz i <xref:System.Collections.ArrayList.AddRange%2A> metody klasy,abyzapoznaćsięzprzykłademtegowzorca.<xref:System.Collections.ArrayList?displayProperty=fullName>

Serializacji binarne i XML obsługują właściwości tylko do odczytu, które są kolekcjami. Klasa ma określone wymagania dotyczące typów, które implementują <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection> i aby można było je serializować. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, ustaw właściwość tylko do odczytu. Jeśli projekt jest wymagany, należy dodać metody, aby wyczyścić i ponownie wypełnić kolekcję.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Możesz pominąć ostrzeżenie, jeśli właściwość jest częścią klasy [transfer danych obiektu (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) .

W przeciwnym razie nie pomijaj ostrzeżeń z tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typ z właściwością kolekcji zapisywalnej i pokazuje, jak można zamienić kolekcję bezpośrednio. Ponadto pokazuje preferowany sposób zastąpienia właściwości kolekcji tylko do odczytu przy użyciu `Clear` metod i. `AddRange`

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)
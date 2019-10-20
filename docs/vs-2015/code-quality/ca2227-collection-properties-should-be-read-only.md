---
title: 'CA2227: właściwości kolekcji powinny być tylko do odczytu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658867"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Właściwości kolekcji powinny być tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Widoczna na zewnątrz właściwość z możliwością zapisu jest typem, który implementuje <xref:System.Collections.ICollection?displayProperty=fullName>. Tablice, indeksatory (właściwości o nazwie "Item") i zestawy uprawnień są ignorowane przez regułę.

## <a name="rule-description"></a>Opis reguły
 Właściwość kolekcji zapisywalnej umożliwia użytkownikowi zastąpienie kolekcji zupełnie inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. Jeśli zastępowanie kolekcji jest celem, preferowanym wzorcem projektu jest dołączenie metody usuwania wszystkich elementów z kolekcji i metody ponownego wypełnienia kolekcji. Przykład ten wzorzec zawiera <xref:System.Collections.ArrayList.Clear%2A> i <xref:System.Collections.ArrayList.AddRange%2A> metod klasy <xref:System.Collections.ArrayList?displayProperty=fullName>.

 Serializacji binarne i XML obsługują właściwości tylko do odczytu, które są kolekcjami. Klasa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> ma określone wymagania dotyczące typów, które implementują <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable?displayProperty=fullName>, aby można było je serializować.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustaw właściwość tylko do odczytu i, jeśli to konieczne, Dodaj metody, aby wyczyścić i ponownie wypełnić kolekcję.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ z właściwością kolekcji zapisywalnej i pokazuje, jak można zamienić kolekcję bezpośrednio. Ponadto jest pokazywany preferowany sposób zamiany właściwości kolekcji tylko do odczytu przy użyciu metod `Clear` i `AddRange`.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)

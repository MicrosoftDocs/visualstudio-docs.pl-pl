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
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540533"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Właściwości kolekcji powinny być tylko do odczytu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Na zewnątrz widocznej do zapisu właściwość jest typu, który implementuje <xref:System.Collections.ICollection?displayProperty=fullName> . Tablice, indeksatory (właściwości o nazwie "Item") i zestawy uprawnień są ignorowane przez regułę.

## <a name="rule-description"></a>Opis reguły
 Właściwość kolekcji zapisywalnej umożliwia użytkownikowi zastąpienie kolekcji zupełnie inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków. Jeśli zastępowanie kolekcji jest celem, preferowanym wzorcem projektu jest dołączenie metody usuwania wszystkich elementów z kolekcji i metody ponownego wypełnienia kolekcji. Zobacz <xref:System.Collections.ArrayList.Clear%2A> i <xref:System.Collections.ArrayList.AddRange%2A> metody klasy, <xref:System.Collections.ArrayList?displayProperty=fullName> Aby zapoznać się z przykładem tego wzorca.

 Serializacji binarne i XML obsługują właściwości tylko do odczytu, które są kolekcjami. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>Klasa ma określone wymagania dotyczące typów, które implementują <xref:System.Collections.ICollection> i <xref:System.Collections.IEnumerable?displayProperty=fullName> Aby można było je serializować.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustaw właściwość tylko do odczytu i, jeśli to konieczne, Dodaj metody, aby wyczyścić i ponownie wypełnić kolekcję.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ z właściwością kolekcji zapisywalnej i pokazuje, jak można zamienić kolekcję bezpośrednio. Ponadto, preferowany sposób zastąpienia właściwości kolekcji tylko do odczytu przy użyciu `Clear` metod i `AddRange` jest pokazywany.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)

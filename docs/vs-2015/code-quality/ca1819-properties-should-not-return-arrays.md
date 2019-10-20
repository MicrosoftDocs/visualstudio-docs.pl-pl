---
title: 'CA1819: właściwości nie powinny zwracać tablic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c85efc3e601eb9e0d887043c50b30587e51321e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668373"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Właściwości nie powinny zwracać tablic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Właściwość publiczna lub chroniona w typie publicznym zwraca tablicę.

## <a name="rule-description"></a>Opis reguły
 Tablice zwracane przez właściwości nie są chronione przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. W odniesieniu do nich mogą używać właściwości jako właściwości indeksowanej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, ustaw właściwość jako metodę lub zmień właściwość w celu zwrócenia kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Atrybuty mogą zawierać właściwości, które zwracają tablice, ale nie mogą zawierać właściwości, które zwracają kolekcje. Można pominąć ostrzeżenie, które jest zgłaszane dla właściwości atrybutu, który pochodzi z [System. Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->określonej. W przeciwnym razie nie pomijaj ostrzeżenia z tej reguły.

## <a name="example-violation"></a>Przykładowe naruszenie

### <a name="description"></a>Opis
 Poniższy przykład pokazuje właściwość, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie tej reguły, ustaw właściwość jako metodę lub zmień właściwość w celu zwrócenia kolekcji zamiast tablicy.

## <a name="change-the-property-to-a-method-example"></a>Zmiana właściwości na przykład metody

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenie, zmieniając właściwość na metodę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Przykład zwracania kolekcji

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenie, zmieniając właściwość w celu zwrócenia

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.,

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Zezwalanie użytkownikom na modyfikowanie właściwości

### <a name="description"></a>Opis
 Możesz chcieć zezwolić konsumentowi klasy na modyfikowanie właściwości. Poniższy przykład pokazuje właściwość odczytu/zapisu, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Komentarze
 Poniższy przykład naprawia naruszenie, zmieniając właściwość w celu zwrócenia <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Używaj właściwości wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)

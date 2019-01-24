---
title: 'CA1819: Właściwości nie powinny zwracać tablic | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 48f1b0c0860f8dfc38a83856570cdcdfa6f6ffc7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786796"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Właściwości nie powinny zwracać tablic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Właściwość publiczna lub chroniona w typie publicznym zwraca tablicę.

## <a name="rule-description"></a>Opis reguły
 Tablice zwracane przez właściwości nie są zabezpieczony przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. W szczególności mogą użyć właściwości jako indeksowana właściwość.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Atrybuty mogą zawierać właściwości, które zwracają tablice, ale nie może zawierać właściwości, które zwracają kolekcje. Można pominąć ostrzeżenia, które jest wywoływane dla właściwości atrybutu, która jest pochodną klasy [System.Attribute] (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->) klasy. W przeciwnym razie nie Pomijaj ostrzeżeń dla tej reguły.

## <a name="example-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 Poniższy przykład pokazuje właściwości, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji zamiast tablicy.

## <a name="change-the-property-to-a-method-example"></a>Zmień właściwości, na przykład metody

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Zwraca przykład kolekcji

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Zezwalanie użytkownikom na modyfikowanie właściwości

### <a name="description"></a>Opis
 Możesz chcieć umożliwia konsumentowi klasy zmodyfikować właściwości. Poniższy przykład pokazuje właściwości odczytu/zapisu, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Komentarze
 Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)

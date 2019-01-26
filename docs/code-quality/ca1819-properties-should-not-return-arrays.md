---
title: 'CA1819: Właściwości nie powinny zwracać tablic'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a7fe25198e46c1f6860dc73198bea860ac16896d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003169"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Właściwości nie powinny zwracać tablic

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Właściwość publiczna lub chroniona w typie publicznym zwraca tablicę.

## <a name="rule-description"></a>Opis reguły

Tablice zwracane przez właściwości nie są zabezpieczony przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zazwyczaj użytkownicy nie wiedzą, niekorzystny wydajności ma wywołanie takiej właściwości. W szczególności mogą użyć właściwości jako indeksowana właściwość.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można pominąć ostrzeżenia, które jest wywoływane dla właściwości atrybutu, która jest pochodną <xref:System.Attribute> klasy. Atrybuty mogą zawierać właściwości, które zwracają tablice, ale nie może zawierać właściwości, które zwracają kolekcje.

Można pominąć to ostrzeżenie, jeśli właściwość jest częścią [obiekt transferu danych (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) klasy.

W przeciwnym razie nie Pomijaj ostrzeżeń dla tej reguły.

## <a name="example-violation"></a>Przykład naruszenia

Właściwość, która narusza tę regułę można znaleźć w poniższym przykładzie:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Aby naprawić naruszenie tej zasady, ustawić właściwość jako metodę lub zmień wartość właściwości do zwrócenia kolekcji zamiast tablicy.

### <a name="change-the-property-to-a-method"></a>Zmień wartość właściwości na metodę

Poniższy przykład usuwa naruszenia, zmieniając właściwość do metody:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Zmień wartość właściwości do zwrócenia kolekcji

Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Zezwalaj użytkownikom na modyfikowanie właściwości

Możesz chcieć umożliwia konsumentowi klasy zmodyfikować właściwości. Właściwości odczytu/zapisu, która narusza tę regułę można znaleźć w poniższym przykładzie:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

Poniższy przykład naprawia naruszenia, zmieniając właściwość do zwrócenia <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)
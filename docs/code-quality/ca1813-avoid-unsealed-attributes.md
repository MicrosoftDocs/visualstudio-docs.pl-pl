---
title: 'CA1813: Unikaj niezapieczętowanych atrybutów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a17c5bdc9e21bdf877206b1dc28596c251049455
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714749"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Unikaj niezapieczętowanych atrybutów

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Publiczny typ dziedziczy z <xref:System.Attribute?displayProperty=fullName>, nie jest abstrakcyjna i nie jest zapieczętowany (`NotInheritable` w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły

.NET dostarcza metody do pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Na przykład <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> wyszukiwania dla podanego typu atrybutu lub dowolny typ atrybutu, który rozszerza podanego typu atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Zapieczętuj typ atrybutu lub ułatwiają abstrakcyjne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły. Pomiń tylko wtedy, gdy definiujesz hierarchii atrybutów i nie można zapieczętować ten atrybut lub ułatwiają abstrakcyjne.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje niestandardowy atrybut, który spełnia tę regułę.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Oznacz atrybuty atrybutem Attributeusage](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
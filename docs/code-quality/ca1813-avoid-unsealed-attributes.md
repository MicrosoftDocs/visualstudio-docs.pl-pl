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
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233593"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Unikaj niezapieczętowanych atrybutów

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ publiczny dziedziczy z <xref:System.Attribute?displayProperty=fullName>, nie jest abstrakcyjny i nie jest zapieczętowany (`NotInheritable` w Visual Basic).

## <a name="rule-description"></a>Opis reguły

.NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Na przykład <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> wyszukuje określony typ atrybutu lub dowolny typ atrybutu, który rozszerza określony typ atrybutu. Opieczętowanie atrybutu eliminuje wyszukiwanie w hierarchii dziedziczenia i może zwiększyć wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zapieczętować typ atrybutu lub uczynić go abstrakcyjnym.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły. Pomiń tylko w przypadku definiowania hierarchii atrybutów i nie można zapieczętować atrybutu ani uczynić abstrakcyjnym.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje niestandardowy atrybut, który spełnia tę regułę.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1019 Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018 Oznacz atrybuty atrybutem AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
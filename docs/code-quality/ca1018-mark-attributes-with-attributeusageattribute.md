---
title: 'CA1018: Oznacz atrybuty atrybutem AttributeUsage'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a1ed8610ce84279f5fde3b802d976a3e766d99
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236252"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Oznacz atrybuty atrybutem AttributeUsage

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
<xref:System.AttributeUsageAttribute?displayProperty=fullName> Atrybut nie występuje w atrybucie niestandardowym.

## <a name="rule-description"></a>Opis reguły
Podczas definiowania atrybutu niestandardowego należy oznaczyć go przy użyciu <xref:System.AttributeUsageAttribute> , aby wskazać, gdzie w kodzie źródłowym można zastosować atrybut niestandardowy. Znaczenie i zamierzone użycie atrybutu określi jego prawidłowe lokalizacje w kodzie. Na przykład można zdefiniować atrybut, który identyfikuje osoby odpowiedzialne za utrzymanie i udoskonalenie każdego typu w bibliotece, a odpowiedzialność jest zawsze przypisana na poziomie typu. W takim przypadku kompilatory powinny włączyć atrybut dla klas, wyliczeń i interfejsów, ale nie powinien włączać go dla metod, zdarzeń lub właściwości. Zasady i procedury organizacyjne określają, czy atrybut powinien być włączony dla zestawów.

<xref:System.AttributeTargets?displayProperty=fullName> Wyliczenie definiuje elementy docelowe, które można określić dla atrybutu niestandardowego. W przypadku pominięcia <xref:System.AttributeUsageAttribute>atrybut niestandardowy będzie prawidłowy dla wszystkich obiektów docelowych, zgodnie z <xref:System.AttributeTargets> definicją `All` wartości wyliczenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, określ elementy docelowe dla atrybutu przy użyciu <xref:System.AttributeUsageAttribute>. Zobacz Poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Przed wykluczeniem komunikatu należy usunąć naruszenie tej reguły. Nawet jeśli atrybut dziedziczy <xref:System.AttributeUsageAttribute>, atrybut powinien być obecny, aby uprościć konserwację kodu.

## <a name="example"></a>Przykład
W poniższym przykładzie zdefiniowano dwa atrybuty. `BadCodeMaintainerAttribute`niepoprawnie pomija <xref:System.AttributeUsageAttribute> instrukcję i `GoodCodeMaintainerAttribute` poprawnie implementuje atrybut opisany wcześniej w tej sekcji. Należy zauważyć, że `DeveloperName` właściwość jest wymagana przez CA1019 reguły [projektowania: Zdefiniuj metody dostępu dla argumentów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) atrybutów i są one dołączane do kompletności.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1019 Zdefiniuj metody dostępu dla argumentów atrybutów](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
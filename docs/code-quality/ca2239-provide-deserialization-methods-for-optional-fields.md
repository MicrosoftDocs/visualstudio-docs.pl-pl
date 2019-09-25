---
title: 'CA2239: Udostępnij metody deserializacji dla pól opcjonalnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cf2e30956879c0c61bb57d65b89445962f34959a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237891"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Udostępnij metody deserializacji dla pól opcjonalnych

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ ma pole oznaczone <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atrybutem, a typ nie zapewnia metod obsługi zdarzeń deserializacji.

## <a name="rule-description"></a>Opis reguły
<xref:System.Runtime.Serialization.OptionalFieldAttribute> Atrybut nie ma wpływu na Serializacja; pole oznaczone atrybutem jest serializowane. Jednak pole jest ignorowane podczas deserializacji i zachowuje wartość domyślną skojarzoną z jej typem. Procedury obsługi zdarzeń deserializacji należy zadeklarować, aby ustawić pole podczas procesu deserializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Dodaj do typu metody obsługi zdarzeń deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli pole ma być ignorowane podczas procesu deserializacji, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia typ z opcjonalnym polem i deserializacji metody obsługi zdarzeń.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA2236 Wywoływanie metod klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
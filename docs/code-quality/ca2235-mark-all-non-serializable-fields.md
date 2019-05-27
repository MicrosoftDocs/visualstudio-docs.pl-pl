---
title: 'CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177389"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły

Typ możliwy do serializacji to taki, który jest oznaczony przy użyciu <xref:System.SerializableAttribute?displayProperty=fullName> atrybutu. Gdy typ jest serializowana, <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> wyjątek jest generowany, jeśli typ zawiera pola wystąpienia typu, który nie jest możliwy do serializacji *i* nie implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu.

> [!TIP]
> CA2235 nie jest wyzwalana, na przykład pól typów, które implementują <xref:System.Runtime.Serialization.ISerializable> ponieważ zapewniają one logikę serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zastosować <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybutu do pola, które nie jest możliwy do serializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Tylko Pomijaj ostrzeżeń dla tej reguły, jeśli <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> typ został zadeklarowany, umożliwiająca wystąpień pola, aby być serializacji i deserializacji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano dwa typy: taki, który narusza regułę i taki, który spełnia reguły.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Uwagi

Reguła CA2235 nie zostaną przeanalizowane typy, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejsu (chyba że są one również oznaczone <xref:System.SerializableAttribute> atrybutu). Jest to spowodowane [reguły CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) już zaleca się oznaczenie typy, które implementują <xref:System.Runtime.Serialization.ISerializable> współpracować z usługą <xref:System.SerializableAttribute> atrybutu.

## <a name="related-rules"></a>Powiązane reguły

- [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Wywołuj metody klasy bazowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
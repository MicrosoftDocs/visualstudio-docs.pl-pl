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
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238101"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły

Typ możliwy do serializacji to taki, który jest oznaczony <xref:System.SerializableAttribute?displayProperty=fullName> atrybutem. Gdy typ jest serializowany, zgłaszany jest <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> wyjątek, jeśli typ zawiera pole wystąpienia typu, którego nie można serializować *i* nie implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu.

> [!TIP]
> CA2235 nie uruchamia się w przypadku pól wystąpienia typów, które <xref:System.Runtime.Serialization.ISerializable> implementują, ponieważ udostępniają własne logiki serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zastosuj <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybut do pola, którego nie można serializować.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły, jeśli <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> zadeklarowano typ, który zezwala na wystąpienia pola do serializacji i deserializacji.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono dwa typy: jeden, który narusza regułę i jeden, który spełnia daną regułę.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Uwagi

Reguła CA2235 nie analizuje typów, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejs (chyba że są również oznaczone <xref:System.SerializableAttribute> atrybutem). Wynika to z faktu, że [reguła CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) już zaleca oznaczanie typów, <xref:System.SerializableAttribute> które implementują <xref:System.Runtime.Serialization.ISerializable> interfejs przy użyciu atrybutu.

## <a name="related-rules"></a>Powiązane reguły

- [CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236 Wywoływanie metod klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238 Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239 Zapewnianie metod deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
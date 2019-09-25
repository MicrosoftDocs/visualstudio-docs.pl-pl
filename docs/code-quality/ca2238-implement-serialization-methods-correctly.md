---
title: 'CA2238: Poprawnie implementuj metody serializacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b0bbe31f0431b259f60c1fe68a8d9edeffc572d9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237912"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Poprawnie implementuj metody serializacji

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Przerywanie — Jeśli metoda jest widoczna poza zestawem.<br /><br /> Bez przerywania — Jeśli metoda nie jest widoczna poza zestawem.|

## <a name="cause"></a>Przyczyna
Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.

## <a name="rule-description"></a>Opis reguły
Metoda jest oznaczona programem obsługi zdarzeń serializacji przez zastosowanie jednego z następujących atrybutów zdarzeń serializacji:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Procedury obsługi zdarzeń serializacji przyjmują jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, Return `void`i mają `private` widoczność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Popraw sygnaturę, zwracany typ lub widoczność programu obsługi zdarzeń serializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje prawidłowo zadeklarowane procedury obsługi zdarzeń serializacji.

[!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
[!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2236 Wywoływanie metod klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239 Zapewnianie metod deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
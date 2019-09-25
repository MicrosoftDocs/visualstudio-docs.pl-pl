---
title: 'CA2229: Zaimplementuj konstruktory serializacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d148efb87c8516b34342a8c9d16b63364a2eae16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231009"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Zaimplementuj konstruktory serializacji

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, nie jest obiektem delegowanym ani interfejsem, a jeden z następujących warunków jest spełniony:

- Typ nie ma konstruktora, który przyjmuje <xref:System.Runtime.Serialization.SerializationInfo> obiekt <xref:System.Runtime.Serialization.StreamingContext> i obiekt (podpis konstruktora serializacji).

- Typ jest niezapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest chroniony (rodzina).

- Typ jest zapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest prywatny.

## <a name="rule-description"></a>Opis reguły

Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs. Konstruktor serializacji jest wymagany do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj naruszenia reguły. Typ nie może być deserializowany i nie będzie działać w wielu scenariuszach.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który spełnia regułę.

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>

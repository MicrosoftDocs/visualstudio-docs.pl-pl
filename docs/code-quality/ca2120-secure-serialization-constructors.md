---
title: 'CA2120: Zabezpiecz konstruktory serializacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38de3597d3693b072fec12f64211af4469851627
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232542"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpiecz konstruktory serializacji

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, nie jest delegatem lub interfejsem i jest zadeklarowany w zestawie, który zezwala częściowo zaufanym obiektom wywołującym. Typ ma konstruktora, który przyjmuje <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> obiekt <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> i obiekt (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale co najmniej jeden z zwykłych konstruktorów w typie jest zabezpieczony.

## <a name="rule-description"></a>Opis reguły
Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs. Konstruktor serializacji jest wymagany i jest używany do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Ponieważ Konstruktor serializacji przydziela i inicjuje obiekty, sprawdzenia zabezpieczeń, które są obecne na zwykłych konstruktorach, muszą być również obecne w konstruktorze serializacji. Jeśli naruszasz tę regułę, wywołujący, którzy nie mogą w inny sposób utworzyć wystąpienia, mogą w tym celu użyć konstruktora serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy chronić Konstruktor serializacji z wymaganiami bezpieczeństwa, które są takie same jak chroniące inne konstruktory.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj naruszenia reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
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
ms.openlocfilehash: 15fd1596fdede3d13d603e7df222395a7ef7a277
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927909"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpiecz konstruktory serializacji

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu, jest delegat lub interfejsu i jest zadeklarowana w zestawie, który umożliwia częściowo zaufanych wywołań. Typ ma konstruktora przyjmującego <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> obiektu i <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> obiektu (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale co najmniej jeden z regularnych konstruktorów typu jest zabezpieczony.

## <a name="rule-description"></a>Opis reguły
 Ta reguła ma znaczenie dla typów, które obsługują niestandardowej serializacji. Typ obsługuje niestandardowej serializacji, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu. Konstruktor serializacji jest wymagane i jest używana do deserializować lub ponownie utworzyć obiekty, które zostały zserializowanym przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Ponieważ Konstruktor serializacji przydziela i inicjuje obiektów, w również musi znajdować się na Konstruktor serializacji kontrole zabezpieczeń, które znajdują się w regularnych konstruktorów. Możesz spełniają tej reguły, wywołań, które w przeciwnym razie nie można utworzyć wystąpienia wystarczą konstruktora serializacji w tym celu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy chronić Konstruktor serializacji z zapotrzebowaniem na zasoby zabezpieczeń, które są identyczne z tymi ochrony innych konstruktorów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenie reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
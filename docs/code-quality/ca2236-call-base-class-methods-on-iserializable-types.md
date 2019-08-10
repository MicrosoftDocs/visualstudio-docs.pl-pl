---
title: 'CA2236: Wywołuj metody klasy bazowej dla typów ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f0075a6296e839030448c0209c77f1717a5fcb1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920123"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołuj metody klasy bazowej dla typów ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, i jeden z następujących warunków jest spełniony:

- Typ implementuje Konstruktor serializacji, czyli Konstruktor z <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> podpisem parametru, ale nie wywołuje konstruktora serializacji typu podstawowego.

- Typ implementuje metodę, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ale nie <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> wywołuje metody typu podstawowego.

## <a name="rule-description"></a>Opis reguły
W procesie serializacji niestandardowej Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę, aby serializować jej pola i Konstruktor serializacji w celu deserializacji pól. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, Metoda typu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> podstawowego i Konstruktor serializacji powinny być wywoływane do serializacji/deserializacji pól typu podstawowego. W przeciwnym razie typ nie będzie serializowany i deserializowany poprawnie. Należy pamiętać, że jeśli typ pochodny nie dodaje żadnych nowych pól, typ nie musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody ani konstruktora serializacji ani wywoływać odpowiedników typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, wywołaj metodę typu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> podstawowego lub konstruktora serializacji z odpowiedniej metody typu pochodnego lub konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia typ pochodny, który spełnia reguły przez wywołanie konstruktora serializacji i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy bazowej.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239 Zapewnianie metod deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
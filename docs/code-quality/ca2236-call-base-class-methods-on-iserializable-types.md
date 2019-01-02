---
title: 'CA2236: Wywołuj metody klasy bazowej typu ISerializable'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2cdbd9a3af7c22e2afa29efdff411903c81b6620
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862097"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołuj metody klasy bazowej typu ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ pochodzi od typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i jeden z następujących warunków jest spełniony:

- Typ implementuje konstruktora serializacji, to znaczy konstruktora o <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> podpis parametru, ale nie wywołuje konstruktor serializacji typu podstawowego.

- Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody, ale nie mogą wywoływać <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody typu podstawowego.

## <a name="rule-description"></a>Opis reguły
 W procesie serializacji niestandardowej typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody do wykonywania serializacji jej pola i Konstruktor serializacji, aby deserializować pola. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody i serializacja konstruktora powinna być wywoływana do serializacji/cofania-serialize pola typu podstawowego. W przeciwnym razie typu nie można serializować i deserializowany poprawnie. Jeśli typ pochodny nie dodasz nowe pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda ani konstruktora serializacji lub zadzwoń odpowiedniki typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda lub Konstruktor serializacji z odpowiadającej pochodne typu metoda lub Konstruktor.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ pochodny spełniającego reguły przez wywołanie konstruktora serializacji i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy bazowej.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
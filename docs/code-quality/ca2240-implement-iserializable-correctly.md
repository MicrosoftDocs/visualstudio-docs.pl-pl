---
title: 'CA2240: Poprawnie zaimplementuj interfejs ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2640fddcde0d8777363a3c56e398e7ff307a20c7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237879"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Poprawnie zaimplementuj interfejs ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ widoczny na zewnątrz można przypisać do <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i jeden z następujących warunków jest spełniony:

- Typ dziedziczy, ale nie przesłania <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody i typu deklaruje pola wystąpienia, które nie są oznaczone <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybutem.

- Typ nie jest zapieczętowany i typ implementuje metodę, która <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nie jest widoczna na zewnątrz i nie jest zaimplementowana.

## <a name="rule-description"></a>Opis reguły
Pola wystąpienia, które są zadeklarowane w typie, który <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> dziedziczy interfejs, nie są automatycznie dołączane do procesu serializacji. Aby uwzględnić pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę i Konstruktor serializacji. Jeśli pola nie powinny być serializowane, Zastosuj <xref:System.NonSerializedAttribute> atrybut do pól, aby jawnie wskazać decyzję.

W przypadku typów, które nie są zapieczętowane, implementacje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody powinny być widoczne na zewnątrz. W związku z tym metoda może być wywoływana przez typy pochodne i jest możliwy do zastąpienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, ustaw <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę jako widoczną i Zastąp i upewnij się, że wszystkie pola wystąpienia są zawarte w procesie serializacji lub jawnie oznaczone <xref:System.NonSerializedAttribute> atrybutem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono dwa możliwe do serializacji typy, które naruszają daną regułę.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Przykład
W poniższym przykładzie zostały naprawione dwa poprzednie naruszenia, zapewniając <xref:System.Runtime.Serialization.ISerializable.GetObjectData> w ten sposób zastępujące implementację klasy Book i dostarczając `GetObjectData` implementację klasy Library.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2236 Wywoływanie metod klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238 Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237 Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239 Zapewnianie metod deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
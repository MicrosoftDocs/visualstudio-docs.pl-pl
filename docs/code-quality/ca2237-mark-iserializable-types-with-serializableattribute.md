---
title: 'CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237940"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ widoczny na zewnątrz implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, a typ nie jest oznaczony <xref:System.SerializableAttribute?displayProperty=fullName> atrybutem. Reguła ignoruje typy pochodne, których typ podstawowy nie jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły
Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą <xref:System.SerializableAttribute> być oznaczone atrybutem, nawet jeśli typ używa niestandardowej procedury serializacji przez implementację <xref:System.Runtime.Serialization.ISerializable> interfejsu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zastosuj <xref:System.SerializableAttribute> atrybut do typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły dla klas wyjątków, ponieważ muszą one być serializowane w celu poprawnego działania w domenach aplikacji.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę. Usuń znaczniki komentarza <xref:System.SerializableAttribute> linii atrybutu, aby spełnić regułę.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2236 Wywoływanie metod klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238 Poprawnie Implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239 Zapewnianie metod deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Bezpieczne konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)
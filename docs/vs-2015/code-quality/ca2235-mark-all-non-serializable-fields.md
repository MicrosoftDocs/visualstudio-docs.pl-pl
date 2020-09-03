---
title: 'CA2235: Oznacz wszystkie pola, które nie są możliwe do serializacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fab79fd4daab98c6cade9271b32c45b5ae4b4332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545200"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły
 Typ możliwy do serializacji to taki, który jest oznaczony <xref:System.SerializableAttribute?displayProperty=fullName> atrybutem. Gdy typ jest serializowany, <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> zgłaszany jest wyjątek, jeśli typ zawiera pole wystąpienia typu, którego nie można serializować.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastosuj <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybut do pola, którego nie można serializować.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> , Jeśli zadeklarowano typ, który zezwala na wystąpienia pola do serializacji i deserializacji.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę i typ, który spełnia regułę.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

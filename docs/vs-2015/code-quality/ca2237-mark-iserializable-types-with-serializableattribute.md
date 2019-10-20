---
title: 'CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c548eb76ba36099d0cef5b651a095f35d64e033c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666692"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Należy oznaczyć typ ISerializable atrybutem SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz implementuje interfejs <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, a typ nie jest oznaczony atrybutem <xref:System.SerializableAttribute?displayProperty=fullName>. Reguła ignoruje typy pochodne, których typ podstawowy nie jest możliwy do serializacji.

## <a name="rule-description"></a>Opis reguły
 Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone atrybutem <xref:System.SerializableAttribute>, nawet jeśli typ używa niestandardowej procedury serializacji za pośrednictwem implementacji interfejsu <xref:System.Runtime.Serialization.ISerializable>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zastosuj atrybut <xref:System.SerializableAttribute> do typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły dla klas wyjątków, ponieważ muszą one być serializowane w celu poprawnego działania w domenach aplikacji.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę. Usuń znaczniki komentarza z wiersza atrybutu <xref:System.SerializableAttribute> w celu spełnienia reguły.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy podstawowej w typach ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

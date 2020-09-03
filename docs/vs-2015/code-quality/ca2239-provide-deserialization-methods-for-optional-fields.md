---
title: 'CA2239: zapewnianie metod deserializacji dla pól opcjonalnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfbb9082d557c8e67ddebf0237293364d54a65cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545135"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Udostępnij metody deserializacji dla pól opcjonalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ ma pole oznaczone <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atrybutem, a typ nie zapewnia metod obsługi zdarzeń deserializacji.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>Atrybut nie ma wpływu na Serializacja; pole oznaczone atrybutem jest serializowane. Jednak pole jest ignorowane podczas deserializacji i zachowuje wartość domyślną skojarzoną z jej typem. Procedury obsługi zdarzeń deserializacji należy zadeklarować, aby ustawić pole podczas procesu deserializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj do typu metody obsługi zdarzeń deserializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli pole ma być ignorowane podczas procesu deserializacji, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ z opcjonalnym polem i deserializacji metody obsługi zdarzeń.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

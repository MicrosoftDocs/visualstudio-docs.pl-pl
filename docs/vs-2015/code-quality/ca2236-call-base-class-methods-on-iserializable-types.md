---
title: 'CA2236: wywołaj metody klasy bazowej dla typów ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545187"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołuj metody klasy bazowej dla typów ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, i jeden z następujących warunków jest spełniony:

- Typ implementuje Konstruktor serializacji, czyli Konstruktor z <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> podpisem parametru, ale nie wywołuje konstruktora serializacji typu podstawowego.

- Typ implementuje metodę, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ale nie wywołuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody typu podstawowego.

## <a name="rule-description"></a>Opis reguły
 W procesie serializacji niestandardowej Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę, aby serializować jej pola i Konstruktor serializacji w celu deserializacji pól. Jeśli typ pochodzi z typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, Metoda typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> i Konstruktor serializacji powinny być wywoływane do serializacji/deserializacji pól typu podstawowego. W przeciwnym razie typ nie będzie serializowany i deserializowany poprawnie. Należy pamiętać, że jeśli typ pochodny nie dodaje żadnych nowych pól, typ nie musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody ani konstruktora serializacji ani wywoływać odpowiedników typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj metodę typu podstawowego <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> lub konstruktora serializacji z odpowiedniej metody typu pochodnego lub konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ pochodny, który spełnia reguły przez wywołanie konstruktora serializacji i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody klasy bazowej.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

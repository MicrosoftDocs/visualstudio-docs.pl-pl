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
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666706"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Wywołanie metod klasy bazowej typu ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ pochodzi z typu, który implementuje interfejs <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> i jest spełniony jeden z następujących warunków:

- Typ implementuje Konstruktor serializacji, czyli Konstruktor z podpisem parametru <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, ale nie wywołuje konstruktora serializacji typu podstawowego.

- Typ implementuje metodę <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>, ale nie wywołuje metody <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> typu podstawowego.

## <a name="rule-description"></a>Opis reguły
 W procesie serializacji niestandardowej Typ implementuje metodę <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>, aby serializować swoje pola i Konstruktor serializacji w celu deserializacji pól. Jeśli typ pochodzi z typu, który implementuje interfejs <xref:System.Runtime.Serialization.ISerializable>, typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metoda i Konstruktor serializacji należy wywołać, aby serializować/deserializować pola typu podstawowego. W przeciwnym razie typ nie będzie serializowany i deserializowany poprawnie. Należy pamiętać, że jeśli typ pochodny nie dodaje żadnych nowych pól, typ nie musi implementować metody <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> ani konstruktora serializacji ani wywoływać odpowiedników typu podstawowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj typ podstawowy <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę lub Konstruktor serializacji z odpowiedniej metody typu pochodnego lub konstruktora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ pochodny, który spełnia kryteria, wywołując Konstruktor serializacji i metodę <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> klasy bazowej.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2240: Zaimplementuj poprawnie interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Zaimplementuj poprawnie metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Określ metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

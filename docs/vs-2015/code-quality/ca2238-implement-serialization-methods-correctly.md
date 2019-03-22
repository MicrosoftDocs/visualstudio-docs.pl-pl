---
title: 'CA2238: Poprawnie Implementuj metody serializacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d9c23ef8da970a29057c0e299d5b8d12dda524
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355000"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Poprawnie implementuj metody serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA2238: Poprawnie Implementuj metody serializacji](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Przerywanie — Jeśli metoda jest widoczna spoza zestawu.<br /><br /> Bez podziału — Jeśli metoda nie jest widoczna spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.  
  
## <a name="rule-description"></a>Opis reguły  
 Metoda wyznaczono obsługi zdarzeń serializacji, stosując jedną z następujących atrybutów serializacji, zdarzenia:  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Programy obsługi zdarzeń serializacji przyjmować jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, wróć `void`i mieć `private` widoczności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, popraw podpisu, zwracany typ lub widoczności programu obsługi zdarzeń serializacji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje poprawnie zadeklarowane serializacji procedury obsługi zdarzeń.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2236: Wywołuj metody klasy bazowej typu ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Oznacz wszystkie pola nieprzeznaczone do](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

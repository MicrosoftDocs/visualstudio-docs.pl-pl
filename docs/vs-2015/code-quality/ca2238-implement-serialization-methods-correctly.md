---
title: 'CA2238: Zaimplementuj poprawnie metody serializacji | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 98e825fd5543b928569b99218c9054aff666e0fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545148"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Poprawnie implementuj metody serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA2238: Implementuj poprawnie metody serializacji](/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).

|Element|Wartość|
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Przerywanie — Jeśli metoda jest widoczna poza zestawem.<br /><br /> Bez przerywania — Jeśli metoda nie jest widoczna poza zestawem.|

## <a name="cause"></a>Przyczyna
 Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.

## <a name="rule-description"></a>Opis reguły
 Metoda jest oznaczona programem obsługi zdarzeń serializacji przez zastosowanie jednego z następujących atrybutów zdarzeń serializacji:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Procedury obsługi zdarzeń serializacji przyjmują jeden parametr typu <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , Return `void` i mają `private` widoczność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Popraw sygnaturę, zwracany typ lub widoczność programu obsługi zdarzeń serializacji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje prawidłowo zadeklarowane procedury obsługi zdarzeń serializacji.

 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

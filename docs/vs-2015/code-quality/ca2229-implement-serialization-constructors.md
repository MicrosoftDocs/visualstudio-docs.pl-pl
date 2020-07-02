---
title: 'CA2229: Implementuj konstruktory serializacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540494"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Zaimplementuj konstruktory serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, nie jest obiektem delegowanym ani interfejsem, a jeden z następujących warunków jest spełniony:

- Typ nie ma konstruktora, który przyjmuje <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> obiekt i <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> obiekt (podpis konstruktora serializacji).

- Typ jest niezapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest chroniony (rodzina).

- Typ jest zapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest prywatny.

## <a name="rule-description"></a>Opis reguły
 Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs. Konstruktor serializacji jest wymagany do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenia reguły. Typ nie może być deserializowany i nie będzie działać w wielu scenariuszach.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który spełnia regułę.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>

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
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662842"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Należy zaimplementować konstruktory serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ implementuje interfejs <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, nie jest obiektem delegowanym ani interfejsem, a jeden z następujących warunków jest spełniony:

- Typ nie ma konstruktora, który przyjmuje obiekt <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> i obiekt <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (sygnatura konstruktora serializacji).

- Typ jest niezapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest chroniony (rodzina).

- Typ jest zapieczętowany i modyfikator dostępu dla jego konstruktora serializacji nie jest prywatny.

## <a name="rule-description"></a>Opis reguły
 Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje interfejs <xref:System.Runtime.Serialization.ISerializable>. Konstruktor serializacji jest wymagany do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu metody <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenia reguły. Typ nie może być deserializowany i nie będzie działać w wielu scenariuszach.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który spełnia regułę.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName><xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>

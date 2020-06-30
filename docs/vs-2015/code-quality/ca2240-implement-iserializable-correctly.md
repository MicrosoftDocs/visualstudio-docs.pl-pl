---
title: 'CA2240: Zaimplementuj poprawnie interfejs ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543666"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Poprawnie zaimplementuj interfejs ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz można przypisać do <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejsu i jeden z następujących warunków jest spełniony:

- Typ dziedziczy, ale nie przesłania <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody i typu deklaruje pola wystąpienia, które nie są oznaczone <xref:System.NonSerializedAttribute?displayProperty=fullName> atrybutem.

- Typ nie jest zapieczętowany i typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę, która nie jest widoczna na zewnątrz i nie jest zaimplementowana.

## <a name="rule-description"></a>Opis reguły
 Pola wystąpienia, które są zadeklarowane w typie, który dziedziczy <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, nie są automatycznie dołączane do procesu serializacji. Aby uwzględnić pola, typ musi implementować <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę i Konstruktor serializacji. Jeśli pola nie powinny być serializowane, Zastosuj <xref:System.NonSerializedAttribute> atrybut do pól, aby jawnie wskazać decyzję.

 W przypadku typów, które nie są zapieczętowane, implementacje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody powinny być widoczne na zewnątrz. W związku z tym metoda może być wywoływana przez typy pochodne i jest możliwy do zastąpienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ustaw <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodę jako widoczną i Zastąp i upewnij się, że wszystkie pola wystąpienia są zawarte w procesie serializacji lub jawnie oznaczone <xref:System.NonSerializedAttribute> atrybutem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa możliwe do serializacji typy, które naruszają daną regułę.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie zostały naprawione dwa poprzednie naruszenia, zapewniając zastępowanie implementację [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) w klasie Book i przez udostępnienie implementacji <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> w klasie Library.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpiecz konstruktory serializacji](../code-quality/ca2120-secure-serialization-constructors.md)

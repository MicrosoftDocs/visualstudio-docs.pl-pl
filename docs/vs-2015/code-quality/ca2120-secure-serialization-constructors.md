---
title: 'CA2120: Zabezpieczanie konstruktorów serializacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10cfa03adb74871fb42a6e1c2ce4ab4ba6bcae75
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544342"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpiecz konstruktory serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs, nie jest delegatem lub interfejsem i jest zadeklarowany w zestawie, który zezwala częściowo zaufanym obiektom wywołującym. Typ ma konstruktora, który przyjmuje <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> obiekt i <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> obiekt (podpis konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale co najmniej jeden z zwykłych konstruktorów w typie jest zabezpieczony.

## <a name="rule-description"></a>Opis reguły
 Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfejs. Konstruktor serializacji jest wymagany i jest używany do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Ponieważ Konstruktor serializacji przydziela i inicjuje obiekty, sprawdzenia zabezpieczeń, które są obecne na zwykłych konstruktorach, muszą być również obecne w konstruktorze serializacji. Jeśli naruszasz tę regułę, wywołujący, którzy nie mogą w inny sposób utworzyć wystąpienia, mogą w tym celu użyć konstruktora serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy chronić Konstruktor serializacji z wymaganiami bezpieczeństwa, które są takie same jak chroniące inne konstruktory.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenia reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>

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
ms.openlocfilehash: 2b734a5de257273312e5125c5f481ff889cd33e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664753"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpieczaj konstruktory serializacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ implementuje interfejs <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, nie jest delegatem lub interfejsem i jest zadeklarowany w zestawie, który zezwala częściowo zaufanym obiektom wywołującym. Typ ma konstruktora, który przyjmuje obiekt <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> i obiekt <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (sygnatura konstruktora serializacji). Ten konstruktor nie jest zabezpieczony przez sprawdzanie zabezpieczeń, ale co najmniej jeden z zwykłych konstruktorów w typie jest zabezpieczony.

## <a name="rule-description"></a>Opis reguły
 Ta reguła ma zastosowanie do typów, które obsługują serializację niestandardowe. Typ obsługuje serializacji niestandardowej, jeśli implementuje interfejs <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>. Konstruktor serializacji jest wymagany i służy do deserializacji lub ponownego tworzenia obiektów, które zostały zserializowane przy użyciu metody <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>. Ponieważ Konstruktor serializacji przydziela i inicjuje obiekty, sprawdzenia zabezpieczeń, które są obecne na zwykłych konstruktorach, muszą być również obecne w konstruktorze serializacji. Jeśli naruszasz tę regułę, wywołujący, którzy nie mogą w inny sposób utworzyć wystąpienia, mogą w tym celu użyć konstruktora serializacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy chronić Konstruktor serializacji z wymaganiami bezpieczeństwa, które są takie same jak chroniące inne konstruktory.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj naruszenia reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Oznacz typy ISerializable za pomocą atrybutu SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName><xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>

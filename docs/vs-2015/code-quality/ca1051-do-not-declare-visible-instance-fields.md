---
title: 'CA1051: Nie deklaruj widocznych pól wystąpień | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672516"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Nie deklaruj widocznych pól wystąpień
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz ma pole o widocznym zewnętrznym wystąpieniu.

## <a name="rule-description"></a>Opis reguły
 Głównym zastosowaniem pola powinno być to, co szczegółowo opisuje implementacja. Pola powinny być `private` lub `internal` i powinny być uwidocznione przy użyciu właściwości. Uzyskiwanie dostępu do właściwości w taki sposób, aby uzyskać dostęp do pola, a kod w metodzie dostępu do właściwości może ulec zmianie jako funkcje typu rozwinięte bez wprowadzania istotnych zmian. Właściwości, które po prostu zwracają wartość pola prywatnego lub wewnętrznego, są zoptymalizowane do wykonywania na wartości nominalnej z dostępem do pola. bardzo mały wzrost wydajności jest skojarzony z użyciem widocznych zewnętrznie pól nad właściwościami.

 Widoczne na zewnątrz odnoszą się do `public`, `protected` i `protected internal` (`Public`, `Protected` i `Protected Friend` w Visual Basic) Poziomy ułatwień dostępu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wprowadzić wartość pola `private` lub `internal` i uwidocznić ją przy użyciu właściwości widocznej zewnętrznie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pola widoczne na zewnątrz nie zapewniają żadnych korzyści, które nie są dostępne dla właściwości. Ponadto pola publiczne nie mogą być chronione przez [żądania połączeń](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Zobacz [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ (`BadPublicInstanceFields`) naruszający tę regułę. `GoodPublicInstanceFields` pokazuje skorygowany kod.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Zobacz też
 [Wymagania dotyczące linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)

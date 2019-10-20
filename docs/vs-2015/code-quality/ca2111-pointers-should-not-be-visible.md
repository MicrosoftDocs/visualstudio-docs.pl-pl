---
title: 'CA2111: wskaźniki nie powinny być widoczne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0d5546c6f6a2f5dbd0c6063f4a1dfd40ce1d7bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658738"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Wskaźniki nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Pole Public lub Protected <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.IntPtr> i <xref:System.UIntPtr> są typami wskaźników, które są używane w celu uzyskania dostępu do pamięci niezarządzanej. Jeśli wskaźnik nie jest prywatny, wewnętrzny lub tylko do odczytu, złośliwy kod może zmienić wartość wskaźnika, potencjalnie zezwalając na dostęp do dowolnego miejsca w pamięci lub powodując awarie aplikacji lub systemu.

 Jeśli zamierzasz zabezpieczyć dostęp do typu, który zawiera pole wskaźnika, zobacz [CA2112: zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zabezpiecz wskaźnik przez udostępnienie go tylko do odczytu, wewnętrznego lub prywatnego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli nie korzystasz z wartości wskaźnika.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia wskaźniki, które naruszają i spełniają regułę. Zwróć uwagę, że nieprywatne wskaźniki również naruszają zasadę [CA1051: Nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.IntPtr?displayProperty=fullName><xref:System.UIntPtr?displayProperty=fullName>

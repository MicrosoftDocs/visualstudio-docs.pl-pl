---
title: 'CA2111: Wskaźniki nie powinny być widoczne | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8497433088e4c49868a76dd3281d02a5e79babe5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794968"
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
 Publiczny lub chroniony <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> pole nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.IntPtr> i <xref:System.UIntPtr> są typami wskaźnika, które są używane do uzyskiwania dostępu do niezarządzanej pamięci. Jeżeli wskaźnik nie jest prywatny, wewnętrzny ani tylko do odczytu, złośliwy kod może zmienić wartość wskaźnika, potencjalnie umożliwiając dostęp do dowolnego miejsca w pamięci lub powodując błędy aplikacji lub systemu.

 Jeśli zamierzasz bezpieczny dostęp do typu, która zawiera pole wskaźnika, zobacz [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zabezpiecz wskaźnik, czyniąc ją tylko do odczytu, wewnętrzny lub prywatny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli użytkownik nie należy polegać na wartość wskaźnika.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia wskaźników, które naruszają i spełniać reguły. Zwróć uwagę, że wskaźniki nieprywatny również narusza regułę [CA1051: Nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.IntPtr?displayProperty=fullName><xref:System.UIntPtr?displayProperty=fullName>

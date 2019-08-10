---
title: 'CA2111: Wskaźniki nie powinny być widoczne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 416e45337dafd11a00e98b9adda9f16b02139f9c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921653"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Wskaźniki nie powinny być widoczne

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Publiczne lub chronione <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> pole nie jest tylko do odczytu.

## <a name="rule-description"></a>Opis reguły
 <xref:System.IntPtr>i <xref:System.UIntPtr> są typami wskaźników, które są używane w celu uzyskania dostępu do pamięci niezarządzanej. Jeśli wskaźnik nie jest prywatny, wewnętrzny lub tylko do odczytu, złośliwy kod może zmienić wartość wskaźnika, potencjalnie zezwalając na dostęp do dowolnego miejsca w pamięci lub powodując awarie aplikacji lub systemu.

Jeśli zamierzasz zabezpieczyć dostęp do typu, który zawiera pole wskaźnika, zobacz [CA2112: Zabezpieczone typy nie powinny ujawniać](../code-quality/ca2112-secured-types-should-not-expose-fields.md)pól.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Zabezpiecz wskaźnik przez udostępnienie go tylko do odczytu, wewnętrznego lub prywatnego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły, jeśli nie korzystasz z wartości wskaźnika.

## <a name="example"></a>Przykład
Poniższy kod przedstawia wskaźniki, które naruszają i spełniają regułę. Zwróć uwagę, że nieprywatne wskaźniki również naruszają zasadę [CA1051: Nie deklaruj widocznych pól](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)wystąpień.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2112 Zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051 Nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
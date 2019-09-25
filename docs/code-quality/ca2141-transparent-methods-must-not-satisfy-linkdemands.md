---
title: Metody CA2141:Transparent nie mogą spełniać LinkDemands
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0365d82917b8cfbaf291d557a6ac2d95c220562a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232121"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>Metody CA2141:Transparent nie mogą spełniać LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda przezroczysta pod względem zabezpieczeń wywołuje metodę w zestawie, który nie jest oznaczony <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA) lub metoda przezroczysta zabezpieczeń <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` spełnia dla typu lub metody.

## <a name="rule-description"></a>Opis reguły
Spełnienie LinkDemand jest operacją uwzględniającą zabezpieczenia, która może spowodować niepożądane podwyższenie poziomu uprawnień. Kod przezroczysty zabezpieczeń nie może spełniać LinkDemands, ponieważ nie podlega tym samym wymaganiom inspekcji zabezpieczeń co kod krytyczny dla bezpieczeństwa. Jawne metody w regułach zabezpieczeń zestaw na poziomie 1 spowodują, że wszystkie LinkDemands ich spełniają wszystkie wymagania w czasie wykonywania, co może spowodować problemy z wydajnością. W przypadku zestawów reguł zabezpieczeń z zestawem 2 poziom przezroczystych metod nie będzie kompilować w kompilatorze just-in-Time (JIT), jeśli spróbuje spełnić LinkDemand.

W zestawach, które używają zabezpieczeń poziomu 2, próbuje za pomocą przejrzystej metody zabezpieczeń, aby spełnić LinkDemand lub wywołać metodę w zestawie innym niż APTCA <xref:System.MethodAccessException>, podnosi a; w zestawach poziomu 1, LinkDemand staną się pełnym zapotrzebowaniem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, oznacz metodę dostępu przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu lub <xref:System.Security.SecuritySafeCriticalAttribute> lub Usuń LinkDemand z metody, do której uzyskano dostęp.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W tym przykładzie metoda przezroczysta próbuje wywołać metodę, która ma LinkDemand. Ta reguła zostanie włączona na tym kodzie.

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]
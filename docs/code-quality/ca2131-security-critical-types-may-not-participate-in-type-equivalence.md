---
title: 'CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 802442a71eed3267a71fad9a5a208c9ee82cb556
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232349"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ jest częścią równoważności typu i albo sam typ, albo element członkowski lub pole typu, jest oznaczone <xref:System.Security.SecurityCriticalAttribute> atrybutem.

## <a name="rule-description"></a>Opis reguły
Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach zawierających metody krytyczne lub pola, które uczestniczą w równoważeniu typu. Gdy środowisko CLR wykryje taki typ, nie załaduje go <xref:System.TypeLoadException> w czasie wykonywania. Zazwyczaj ta reguła uruchamiana jest tylko wtedy, gdy użytkownicy implementują równoważenie typu ręcznie, zamiast wykonać je, opierając się na otokach tlbimp i kompilatorach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń atrybut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższych przykładach pokazano interfejs, metodę i pole, które spowodują, że ta reguła zostanie uruchomiona.

[!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Zobacz także
[Kod przezroczysty pod względem zabezpieczeń, poziom 2](/dotnet/framework/misc/security-transparent-code-level-2)
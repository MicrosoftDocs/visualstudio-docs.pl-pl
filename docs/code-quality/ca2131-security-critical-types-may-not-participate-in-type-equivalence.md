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
ms.openlocfilehash: 9b5cc0920e56b9fc27ef120d3328f2ba528b54dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796822"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ uczestniczy w równoważeniu typu i albo sam typ lub element członkowski lub pole o typie, jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach zawierających metody krytyczne lub pola, które uczestniczą w równoważeniu typu. Gdy CLR wykryje taki typ, nie jest on ładować je za pomocą <xref:System.TypeLoadException> w czasie wykonywania. Zazwyczaj ta reguła uruchamiana jest tylko wtedy, gdy użytkownicy implementują równoważenie typu ręcznie, zamiast wykonać je, opierając się na otokach tlbimp i kompilatorach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń atrybut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach pokazano interfejs, metody i pola, które spowodują wyzwolenie tej reguły.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Zobacz także
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](/dotnet/framework/misc/security-transparent-code-level-2)
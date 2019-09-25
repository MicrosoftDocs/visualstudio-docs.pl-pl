---
title: 'CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231984"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Metody przezroczyste nie powinny używać żądań zabezpieczeń

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ tranparent lub metoda jest deklaratywnie oznaczona z <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` zapotrzebowaniem <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> lub metoda wywołuje metodę.

## <a name="rule-description"></a>Opis reguły
Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Przejrzysty pod względem bezpieczeństwa kod powinien używać pełnych żądań do podejmowania decyzji związanych z zabezpieczeniami, a kod krytyczny pod względem zabezpieczeń nie powinien opierać się na kodzie przezroczystym do wykonywania pełnego żądania. Każdy kod, który wykonuje kontrole zabezpieczeń, na przykład wymagania dotyczące zabezpieczeń, powinien być w zamian bezpieczny-krytyczny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Ogólnie rzecz biorąc, aby naprawić naruszenie tej zasady, oznacz metodę <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem. Możesz również usunąć żądanie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Pliki reguł w następującym kodzie, ponieważ metoda przezroczysta powoduje deklaratywne zapotrzebowanie na zabezpieczenia.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Zobacz także
[CA2142 Kod przezroczysty nie powinien być chroniony za pomocą LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
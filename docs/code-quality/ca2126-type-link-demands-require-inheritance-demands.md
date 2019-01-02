---
title: 'CA2126: Linkdemand dla typu wymagają żądań dziedziczenia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 834f120994070e055fe5ac417d1fb39830c7bcef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904143"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Linkdemand dla typu wymagają żądań dziedziczenia

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Niezamknięty typ publiczny jest chroniony za pomocą zapotrzebowania na łącza ma metodę, którą można przesłonić, a typ ani metoda nie jest chroniony za pomocą żądania dziedziczenia.

## <a name="rule-description"></a>Opis reguły
 Zapotrzebowania na łącza na metodę lub jego typ deklarujący wymaga bezpośredniego obiektu wywołującego metody ma określone uprawnienie. Żądania dziedziczenia metody wymaga przesłanianie metody ma określone uprawnienie. Żądania dziedziczenia w danym typie wymaga Klasa pochodna ma określone uprawnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, bezpiecznego typu lub metody za pomocą żądania dziedziczenia dla danego uprawnienia zapotrzebowania na łącza.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Nie ujawniaj pośrednio metod żądaniami linkdemand](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Zastąpienie konsolidacji powinny być identyczne z bazowym](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
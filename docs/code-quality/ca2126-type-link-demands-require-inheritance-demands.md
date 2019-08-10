---
title: 'CA2126: Żądania LinkDemand dla typu wymagają żądań dziedziczenia'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920766"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Żądania LinkDemand dla typu wymagają żądań dziedziczenia

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Publiczny niezapieczętowany typ jest chroniony z zapotrzebowaniem na link, ma metodę zastąpiania, a ani typ ani Metoda nie są chronione za pomocą żądania dziedziczenia.

## <a name="rule-description"></a>Opis reguły
Żądanie linku do metody lub jego typu deklarującego wymaga natychmiastowego wywołującego metody, aby miało określone uprawnienie. Żądanie dziedziczenia dla metody wymaga, aby Metoda zastępująca miała określone uprawnienie. Żądanie dziedziczenia typu wymaga, aby Klasa pochodna miała określone uprawnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zabezpiecz typ lub metodę z zapotrzebowaniem na dziedziczenie dla tego samego uprawnienia co link do żądania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2108 Przejrzyj Zabezpieczenia deklaratywne dla typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112 Zabezpieczone typy nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122 Nie ujawniaj pośrednio metod z wymaganiami dotyczącymi linków](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: Przesłonięcie żądań konsolidacji powinno być identyczne z podstawowym](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Wymagania dotyczące linków](/dotnet/framework/misc/link-demands)
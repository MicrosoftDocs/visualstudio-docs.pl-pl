---
title: 'CA2126: wymagania dotyczące linków typu wymagają wymagania dziedziczenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7bc7c9639d12cc6981c91320104a1565bb1f94e9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609032"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: Typ żądań konsolidacji wymaga żądań dziedziczenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cpp/FxCop.Security.TypesWithLinkDemands.cpp#1)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/cs/FxCop.Security.TypesWithLinkDemands.cs#1)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.TypesWithLinkDemands/vb/FxCop.Security.TypesWithLinkDemands.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2108: Przejrzyj zabezpieczenia deklaratywne typów wartości](../code-quality/ca2108-review-declarative-security-on-value-types.md)

 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

 [CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Zobacz też
 [Zasady bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) — [wymagania](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) dotyczące żądań [linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48)

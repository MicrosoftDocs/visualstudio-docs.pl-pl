---
title: 'CA2117: typy APTCA powinny mieć tylko rozszerzone typy podstawowe APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09fa055fbf1b11e06b1dde32df5a316a3ec39848
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658657"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy APTCA powinny rozszerzać tylko typy bazowe APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony w zestawie z atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> dziedziczy z typu zadeklarowanego w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły
 Domyślnie typy publiczne lub chronione w zestawach o silnych nazwach są niejawnie chronione przez [żądania dziedziczenia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) dla pełnego zaufania. Zestawy o silnych nazwach oznaczone atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) nie mają tej ochrony. Ten atrybut powoduje wyłączenie żądania dziedziczenia. Sprawia to, że uwidocznione typy zadeklarowane w zestawie dziedziczą przez typy, które nie mają pełnego zaufania.

 Gdy atrybut APTCA jest obecny w w pełni zaufanym zestawie, a typ w zestawie dziedziczy z typu, który nie zezwala częściowo zaufanym obiektom wywołującym, możliwe jest wykorzystanie zabezpieczeń. Jeśli dwa typy `T1` i `T2` spełniają następujące warunki, złośliwe obiekty wywołujące mogą używać typu `T1` do pomijania niejawnego pełnego żądania dziedziczenia, które chroni `T2`:

- `T1` to typ publiczny zadeklarowany w w pełni zaufanym zestawie, który ma atrybut APTCA.

- `T1` dziedziczy z typu `T2` poza jego zestawem.

- zestaw `T2` nie ma atrybutu APTCA i dlatego nie powinien dziedziczyć typów w częściowo zaufanych zestawach.

  Częściowo zaufany typ `X` może dziedziczyć po `T1`, co daje dostęp do dziedziczonych członków zadeklarowanych w `T2`. Ponieważ `T2` nie ma atrybutu APTCA, jego bezpośredni typ pochodny (`T1`) musi spełniać żądanie dziedziczenia dla pełnego zaufania; `T1` ma pełne zaufanie i dlatego spełnia to sprawdzenie. Zagrożenie bezpieczeństwa polega na tym, że `X` nie uczestniczy w spełnianiu wymagań dotyczących dziedziczenia chroniących `T2` od niezaufanego podklasy. Z tego powodu typy z atrybutem APTCA nie mogą obejmować typów, które nie mają atrybutu.

  Innym problemem związanym z zabezpieczeniami i może być bardziej powszechny, jest to, że typ pochodny (`T1`) może za pośrednictwem błędu programisty uwidocznić chronione elementy członkowskie z typu, który wymaga pełnego zaufania (`T2`). W takim przypadku niezaufane obiekty wywołujące uzyskują dostęp do informacji, które powinny być dostępne tylko w w pełni zaufanych typach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli typ raportowany przez naruszenie znajduje się w zestawie, który nie wymaga atrybutu APTCA, usuń go.

 Jeśli atrybut APTCA jest wymagany, Dodaj żądanie dziedziczenia dla pełnego zaufania do typu. Chroni to przed dziedziczeniem przez niezaufane typy.

 Istnieje możliwość naprawienia naruszenia przez dodanie atrybutu APTCA do zestawów typów podstawowych raportowanych przez naruszenie. Nie wykonuj tej operacji bez wcześniejszego przeprowadzenia intensywnego przeglądu zabezpieczeń całego kodu w zestawach i wszystkich kodów, które są zależne od zestawów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że chronione elementy członkowskie uwidocznione przez typ nie bezpośrednio lub pośrednio nie zezwalają niezaufanym obiektom wywołującym na dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example"></a>Przykład
 W poniższym przykładzie są używane dwa zestawy i aplikacja testowa do zilustrowania luki w zabezpieczeniach wykrytej przez tę regułę. Pierwszy zestaw nie ma atrybutu APTCA i nie powinien dziedziczyć przez częściowo zaufane typy (reprezentowane przez `T2` w poprzedniej dyskusji).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Przykład
 Drugi zestaw, reprezentowany przez `T1` w poprzedniej dyskusji, jest w pełni zaufany i zezwala częściowo zaufanym wywołującym.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Przykład
 Typ testowy, reprezentowany przez `X` w poprzedniej dyskusji, znajduje się w częściowo zaufanym zestawie.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zapoznaj się z Shady glen 2/22/2003 12:00:00!** 
**z testu: Sunny łąki** 
**spotykają się w Sunny łąki 2/22/2003 12:00:00 am!**
## <a name="related-rules"></a>Powiązane reguły
 [CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Zobacz też
 [Zasady bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework zestawy wywoływane przez częściowo zaufany kod](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [przy użyciu bibliotek z nieczęściowo zaufanych](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [żądań dziedziczenia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) kodu

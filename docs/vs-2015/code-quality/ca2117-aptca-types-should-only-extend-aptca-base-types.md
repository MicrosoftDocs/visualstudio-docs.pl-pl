---
title: 'CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy bazowe APTCA | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 078b7f5535dc80261917ef662b3a2f0069cb33a8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687298"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony w zestawie przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybut dziedziczy z typu zadeklarowana w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły
 Domyślnie, typy publiczne lub chronione w zestawy o silnych nazwach niejawnie są chronione przez [Inheritancedemand](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) pełne zaufanie. Zestawy o silnych nazwach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Ten atrybut wyłącza żądania dziedziczenia. Dzięki temu narażonych typy zadeklarowane w zestawie dziedziczonych przez typy, które nie mają pełnego zaufania.

 Gdy atrybut APTCA jest obecny w całkowicie zaufanym zestawie i typ w zestawie dziedziczy z typu, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest luki w zabezpieczeniach. Jeśli dwa typy `T1` i `T2` spełniać następujące warunki, złośliwe obiekty wywołujące mogą używać typu `T1` pomijanie dziedziczenia niejawne pełnego zaufania, który chroni `T2`:

- `T1` Typ publiczny jest zadeklarowany w pełni zaufanym zestawie, który ma atrybut APTCA.

- `T1` dziedziczy z typu `T2` spoza jej zestawu.

- `T2`w zestawie nie ma atrybut aptca i w związku z tym, nie powinny być dziedziczone przez typy w częściowo zaufanych zestawów.

  Częściowo zaufanych typu `X` może dziedziczyć `T1`, który daje ona dostęp do dziedziczonych elementów członkowskich zadeklarowanych w `T2`. Ponieważ `T2` nie ma atrybut APTCA jego natychmiastowego typu pochodnego (`T1`) muszą spełniać dziedziczenia pełne zaufanie; `T1` relacją pełnego zaufania i w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w spełniającej dziedziczenia, która chroni `T2` z podklasy niezaufanych. Z tego powodu typy z atrybutem APTCA musi obejmuje typy, które nie mają atrybutu.

  Inny problem z zabezpieczeniami i może być bardziej powszechne, co jest to, że typ pochodny (`T1`) za pośrednictwem błąd programisty, udostępnić chronionych elementów członkowskich z typu, który wymaga pełnego zaufania (`T2`). W takiej sytuacji niezaufanych wywołujących uzyskać dostęp do informacji, które powinny być dostępne tylko dla typów w pełni zaufany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 W przypadku typu zgłoszone przez naruszenie w zestawie, który nie wymaga atrybut aptca, należy go usunąć.

 Jeśli atrybut aptca jest wymagana, należy dodać dziedziczenia dla pełnego zaufania do typu. Chroni to przed dziedziczenie przez niezaufane typy.

 Istnieje możliwość naprawić naruszenie, dodając atrybut aptca do zestawów typów podstawowych zgłoszone przez naruszenia. Zrobienie tego bez pierwszy przeprowadzenie przeglądu zabezpieczeń intensywnie korzystających z całego kodu w zestawach i cały kod, który jest zależny od zestawów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, upewnij się, że chronionych elementów członkowskich udostępnianych przez danego typu nie bezpośrednio lub pośrednio Zezwalaj niezaufanych wywołujących dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto dwa zestawy, a aplikacja testowa, aby zilustrować luki w zabezpieczeniach wykryte przez tę regułę. Pierwszy zestaw nie ma atrybut aptca i nie powinny być dziedziczone przez częściowo zaufany typów (reprezentowane przez `T2` w poprzednim dyskusji).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Przykład
 Drugi zestaw, reprezentowane przez `T1` w poprzedniej dyskusji jest w pełni zaufany i umożliwia częściowo zaufanych wywołań.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Przykład
 Typ testu, reprezentowane przez `X` w poprzedniej dyskusji znajduje się w częściowo zaufanym zestawem.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Spełniać na shady glen 2/22/2003 12:00:00 AM! ** 
 **z testu: słoneczna łąki**
**końców słoneczna łąki 2/22/2003 12:00:00 AM!**
## <a name="related-rules"></a>Powiązane reguły
 [CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [zestawy .NET Framework wywoływane przez częściowo zaufany kod](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [używanie bibliotek pochodzących z częściowo zaufanego kodu](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [żądań dziedziczenia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)

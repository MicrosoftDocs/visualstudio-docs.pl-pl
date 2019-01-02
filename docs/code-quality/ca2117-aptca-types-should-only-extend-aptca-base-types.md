---
title: 'CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy bazowe APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc2086038187093397d53e80b1a26f2006c32c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873356"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy bazowe APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ publiczny lub chroniony w zestawie przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybut dziedziczy z typu zadeklarowana w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły

Domyślnie, typy publiczne lub chronione w zestawy o silnych nazwach niejawnie są chronione przez [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) pełne zaufanie. Zestawy o silnych nazwach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Ten atrybut wyłącza żądania dziedziczenia. Narażone typy zadeklarowane w zestawie bez dziedziczenia są dziedziczone przez typy, które nie mają pełnego zaufania.

Gdy atrybut APTCA jest obecny w całkowicie zaufanym zestawie i typ w zestawie dziedziczy z typu, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest luki w zabezpieczeniach. Jeśli dwa typy `T1` i `T2` spełniać następujące warunki, złośliwe obiekty wywołujące mogą używać typu `T1` pomijanie dziedziczenia niejawne pełnego zaufania, który chroni `T2`:

- `T1` Typ publiczny jest zadeklarowany w pełni zaufanym zestawie, który ma atrybut APTCA.

- `T1` dziedziczy z typu `T2` spoza jej zestawu.

- `T2`w zestawie nie ma atrybut aptca i w związku z tym, nie powinny być dziedziczone przez typy w częściowo zaufanych zestawów.

Częściowo zaufanych typu `X` może dziedziczyć `T1`, który daje ona dostęp do dziedziczonych elementów członkowskich zadeklarowanych w `T2`. Ponieważ `T2` nie ma atrybut APTCA jego natychmiastowego typu pochodnego (`T1`) muszą spełniać dziedziczenia pełne zaufanie; `T1` relacją pełnego zaufania i w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w spełniającej dziedziczenia, która chroni `T2` z podklasy niezaufanych. Z tego powodu typy z atrybutem APTCA musi obejmuje typy, które nie mają atrybutu.

Inny problem z zabezpieczeniami i może być bardziej powszechne, co jest to, że typ pochodny (`T1`) za pośrednictwem błąd programisty, udostępnić chronionych elementów członkowskich z typu, który wymaga pełnego zaufania (`T2`). W przypadku wystąpienia tego narażenia niezaufanych wywołujących uzyskać dostęp do informacji, które powinny być dostępne tylko dla typów w pełni zaufany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

W przypadku typu zgłoszone przez naruszenie w zestawie, który nie wymaga atrybut aptca, należy go usunąć.

Jeśli atrybut aptca jest wymagana, należy dodać dziedziczenia dla pełnego zaufania do typu. Żądania dziedziczenia chroni przed dziedziczenie przez niezaufane typy.

Istnieje możliwość naprawić naruszenie, dodając atrybut aptca do zestawów typów podstawowych zgłoszone przez naruszenia. Zrobienie tego bez pierwszy przeprowadzenie przeglądu zabezpieczeń intensywnie korzystających z całego kodu w zestawach i cały kod, który jest zależny od zestawów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Aby bezpiecznie pominąć ostrzeżenie od tej reguły, upewnij się, że chronionych elementów członkowskich udostępnianych przez danego typu nie bezpośrednio lub pośrednio Zezwalaj niezaufanych wywołujących dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto dwa zestawy, a aplikacja testowa, aby zilustrować luki w zabezpieczeniach wykryte przez tę regułę. Pierwszy zestaw nie ma atrybut aptca i nie powinny być dziedziczone przez częściowo zaufany typów (reprezentowane przez `T2` w poprzednim dyskusji).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Drugi zestaw, reprezentowane przez `T1` w poprzedniej dyskusji jest w pełni zaufany i umożliwia częściowo zaufanych wywołań.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Typ testu, reprezentowane przez `X` w poprzedniej dyskusji znajduje się w częściowo zaufanym zestawem.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Ten przykład generuje następujące wyniki:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Powiązane reguły

[CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Używanie bibliotek pochodzących z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)

---
title: 'CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 832d2c9fc1d4b9138a7cd1bc39868b3c4bf1b814
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232640"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ publiczny lub chroniony w zestawie z <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybutem dziedziczy z typu zadeklarowanego w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły

Domyślnie typy publiczne lub chronione w zestawach o silnych nazwach są niejawnie chronione przez [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) do pełnego zaufania. Zestawy o silnych nazwach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA) nie mają tej ochrony. Ten atrybut powoduje wyłączenie żądania dziedziczenia. Typy uwidocznione zadeklarowane w zestawie bez żądania dziedziczenia są dziedziczone przez typy, które nie mają pełnego zaufania.

Gdy atrybut APTCA jest obecny w w pełni zaufanym zestawie, a typ w zestawie dziedziczy z typu, który nie zezwala częściowo zaufanym obiektom wywołującym, możliwe jest wykorzystanie zabezpieczeń. Jeśli dwa typy `T1` i `T2` spełnią poniższe warunki, złośliwe obiekty wywołujące mogą użyć `T1` typu, aby pominąć niejawne, pełne zaufanie `T2`żądania dziedziczenia, które chroni:

- `T1`jest typem publicznym zadeklarowanym w w pełni zaufanym zestawie, który ma atrybut APTCA.

- `T1`dziedziczy po typie `T2` poza jego zestawem.

- `T2`zestaw nie ma atrybutu APTCA i dlatego nie powinien dziedziczyć typów w częściowo zaufanych zestawach.

Częściowo zaufany typ `X` może `T1`dziedziczyć po, co daje dostęp do dziedziczonych członków zadeklarowanych `T2`w. Ponieważ `T2` nie ma atrybutu APTCA, jego bezpośredni typ pochodny (`T1`) musi spełniać żądanie dziedziczenia dla pełnego zaufania; `T1` ma pełne zaufanie i dlatego spełnia to sprawdzenie. Zagrożenie bezpieczeństwa polega `X` na tym, że nie uczestniczy w spełnianiu wymagań dotyczących dziedziczenia chroniących `T2` przed niezaufanym podklasą. Z tego powodu typy z atrybutem APTCA nie mogą obejmować typów, które nie mają atrybutu.

Innym problemem związanym z bezpieczeństwem, a może być bardziej powszechny, jest to`T1`, że typ pochodny () może za pośrednictwem błędu programisty uwidocznić chronione elementy`T2`Członkowskie z typu, który wymaga pełnego zaufania (). W przypadku wystąpienia tego narażenia niezaufane obiekty wywołujące uzyskują dostęp do informacji, które powinny być dostępne tylko w w pełni zaufanych typach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Jeśli typ raportowany przez naruszenie znajduje się w zestawie, który nie wymaga atrybutu APTCA, usuń go.

Jeśli atrybut APTCA jest wymagany, Dodaj żądanie dziedziczenia dla pełnego zaufania do typu. Żądanie dziedziczenia chroni przed dziedziczeniem przez typy niezaufane.

Istnieje możliwość naprawienia naruszenia przez dodanie atrybutu APTCA do zestawów typów podstawowych raportowanych przez naruszenie. Nie wykonuj tej operacji bez wcześniejszego przeprowadzenia intensywnego przeglądu zabezpieczeń całego kodu w zestawach i wszystkich kodów, które są zależne od zestawów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że chronione elementy członkowskie uwidocznione przez typ nie bezpośrednio lub pośrednio nie zezwalają niezaufanym obiektom wywołującym na dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example"></a>Przykład

W poniższym przykładzie są używane dwa zestawy i aplikacja testowa do zilustrowania luki w zabezpieczeniach wykrytej przez tę regułę. Pierwszy zestaw nie ma atrybutu APTCA i nie powinien być dziedziczony przez częściowo zaufane typy (reprezentowane przez `T2` w poprzedniej dyskusji).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Drugi zestaw, reprezentowany przez `T1` w poprzedniej dyskusji, jest w pełni zaufany i zezwala częściowo zaufanym wywołującym.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Typ testowy, reprezentowany przez `X` w poprzedniej dyskusji, znajduje się w częściowo zaufanym zestawie.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Ten przykład generuje następujące wyniki:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Powiązane reguły

[CA2116 Metody APTCA powinny wywoływać tylko metody APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Korzystanie z bibliotek z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)

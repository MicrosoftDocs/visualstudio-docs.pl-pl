---
title: 'CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09817e9248fdc28f56ac0162e783bf72643ee5c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232689"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda w zestawie z <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybutem wywołuje metodę w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły

Domyślnie publiczne lub chronione metody w zestawach o silnych nazwach są niejawnie chronione przez [wymagania linku](/dotnet/framework/misc/link-demands) do pełnego zaufania; tylko w pełni zaufane obiekty wywołujące mogą uzyskać dostęp do zestawu o silnej nazwie. Zestawy o silnych nazwach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA) nie mają tej ochrony. Ten atrybut wyłącza żądanie linku, dzięki czemu zestaw jest dostępny dla obiektów wywołujących, które nie mają pełnego zaufania, takich jak kod wykonywany z intranetu lub Internetu.

Gdy atrybut APTCA jest obecny w w pełni zaufanym zestawie, a zestaw wykonuje kod w innym zestawie, który nie zezwala częściowo zaufanym obiektom wywołującym, możliwe jest wykorzystanie zabezpieczeń. Jeśli dwie metody `M1` i `M2` spełniają poniższe warunki, złośliwe obiekty wywołujące mogą użyć metody `M1` , aby pominąć niejawne, pełne żądanie linku, które chroni `M2`:

- `M1`to metoda publiczna zadeklarowana w w pełni zaufanym zestawie, który ma atrybut APTCA.

- `M1`wywołuje metodę `M2` spoza `M1`zestawu.

- `M2`zestaw nie ma atrybutu APTCA i dlatego nie powinien być wykonywany przez lub w imieniu wywołujących częściowo zaufanych.

Częściowo zaufany obiekt wywołujący `X` może wywołać metodę `M1`, `M1` powodując wywołanie `M2`. Ponieważ `M2` nie ma atrybutu APTCA, jego bezpośredni obiekt wywołujący (`M1`) musi spełniać żądanie linku do pełnego zaufania; `M1` ma pełne zaufanie i dlatego spełnia to sprawdzenie. Zagrożenie bezpieczeństwa polega `X` na tym, że nie uczestniczy w spełnianiu wymagań łącza chroniących `M2` przed niezaufanymi wywołaniami. W związku z tym metody z atrybutem APTCA nie mogą wywoływać metod, które nie mają atrybutu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Jeśli atrybut APCTA jest wymagany, użyj żądania do ochrony metody, która wywołuje cały zestaw zaufania. Dokładne uprawnienia, których wymagasz, zależą od funkcjonalności uwidocznionej przez metodę. Jeśli jest to możliwe, należy chronić metodę z zapotrzebowaniem na pełne zaufanie, aby upewnić się, że podstawowe funkcje nie są widoczne dla częściowo zaufanych wywołujących. Jeśli nie jest to możliwe, wybierz zestaw uprawnień, które skutecznie chronią dostępne funkcje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że funkcje uwidocznione przez metodę nie bezpośrednio lub pośrednio nie zezwalają obiektom wywołującym na dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example-1"></a>Przykład 1
W poniższym przykładzie są używane dwa zestawy i aplikacja testowa do zilustrowania luki w zabezpieczeniach wykrytej przez tę regułę. Pierwszy zestaw nie ma atrybutu APTCA i nie powinien być dostępny dla częściowo zaufanych wywołujących (reprezentowane przez `M2` w poprzedniej dyskusji).

[!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Przykład 2
Drugi zestaw jest w pełni zaufany i zezwala na częściowo zaufane obiekty wywołujące ( `M1` reprezentowane przez w poprzedniej dyskusji).

[!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Przykład 3
Aplikacja testowa (reprezentowana przez `X` w poprzedniej dyskusji) jest częściowo zaufana.

[!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Ten przykład generuje następujące wyniki:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Powiązane reguły

- [CA2117 Typy APTCA powinny stanowić tylko rozszerzone typy podstawowe APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Korzystanie z bibliotek z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Wymagania dotyczące linków](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)
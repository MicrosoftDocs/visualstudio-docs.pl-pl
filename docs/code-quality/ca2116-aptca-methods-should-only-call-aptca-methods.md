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
ms.openlocfilehash: 03948506d928f7d638b21c1fa4bc0a35818ec09a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926918"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda w zestawie przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atrybut wywołuje metodę w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły

Domyślnie metody publiczne lub chronione w zestawy o silnych nazwach niejawnie są chronione przez [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands) pełne zaufanie; tylko w pełni zaufanych obiektów wywołujących mogą uzyskiwać dostęp do zestawu z silną nazwą. Zestawy o silnych nazwach oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) nie mają tej ochrony. Ten atrybut wyłącza zapotrzebowania na łącza, udostępnienie zestawu obiektów wywołujących, które nie mają pełnego zaufania, na przykład kod wykonywany z intranetu lub Internetu.

Gdy atrybut APTCA jest obecny w zestawie całkowicie zaufanym i wykonuje kod w innym zestawie, który nie zezwala na dostęp częściowo zaufanych wywołań, możliwe jest luki w zabezpieczeniach. Jeśli dwie metody `M1` i `M2` spełniać następujące warunki, złośliwe obiekty wywołujące za pomocą metody `M1` można pominąć zapotrzebowanie na łącza niejawne pełnego zaufania, który chroni `M2`:

- `M1` Metoda publiczna zadeklarowano w pełni zaufanym zestawie, który ma atrybut APTCA.

- `M1` wywołuje metodę `M2` poza `M1`w zestawie.

- `M2`w zestawie nie ma atrybut aptca i w związku z tym, nie powinien być wykonywany przez lub w imieniu obiektów wywołujących, które są częściowo zaufany.

Częściowo zaufany obiekt wywołujący `X` można wywołać metodę `M1`, powodując `M1` do wywołania `M2`. Ponieważ `M2` nie ma atrybut APTCA jej bezpośredniego obiektu wywołującego (`M1`) musi spełniać zapotrzebowania na łącza, aby uzyskać pełne zaufanie; `M1` relacją pełnego zaufania i w związku z tym spełnia to sprawdzenie. To zagrożenie bezpieczeństwa, ponieważ `X` nie uczestniczy w spełnia żądanie łącza, które chroni `M2` z niezaufanych wywołujących. W związku z tym metody z atrybutem APTCA nie mogą wywoływać metody, które nie mają atrybutu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli atrybut APCTA jest wymagana, należy używać żądanie do ochrony metodę, która wywołuje zestawów pełnego zaufania. Uprawnienia można żądanie będzie zależeć od funkcji udostępnianych przez metodę. Jeśli jest to możliwe, należy chronić metody żądanie, aby uzyskać pełne zaufanie upewnić się, że podstawową funkcjonalność nie jest narażony na częściowo zaufanych wywołań. Jeśli nie jest to możliwe, wybierz zestaw uprawnień wydajnie chroni narażonych funkcji.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, upewnij się, czy funkcje udostępniane przez metodę bezpośrednio lub pośrednio uniemożliwia wywołującym uzyskania dostępu do poufnych informacji, operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example-1"></a>Przykład 1
 W poniższym przykładzie użyto dwa zestawy, a aplikacja testowa, aby zilustrować luki w zabezpieczeniach wykryte przez tę regułę. Pierwszy zestaw nie ma atrybut aptca i nie powinny być dostępne dla częściowo zaufanych wywołań (reprezentowane przez `M2` w poprzednim dyskusji).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Przykład 2
 Drugi zestaw jest w pełni zaufany i umożliwia częściowo zaufanych wywołań (reprezentowane przez `M1` w poprzednim dyskusji).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Przykład 3
 Aplikacja testowa (reprezentowane przez `X` w poprzednim dyskusji) jest częściowo zaufany.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Ten przykład generuje następujące wyniki:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Powiązane reguły

- [CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy bazowe APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Używanie bibliotek pochodzących z częściowo zaufanego kodu](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)
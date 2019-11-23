---
title: 'CA2116: metody APTCA powinny wywoływać tylko metody APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9de5178b585275ef410ad3179ba320b663536bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658677"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Metody APTCA powinny wywoływać tylko metody APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda w zestawie z atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> wywołuje metodę w zestawie, który nie ma atrybutu.

## <a name="rule-description"></a>Opis reguły
 Domyślnie publiczne lub chronione metody w zestawach o silnych nazwach są niejawnie chronione przez [wymagania linku](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) do pełnego zaufania; tylko w pełni zaufane obiekty wywołujące mogą uzyskać dostęp do zestawu o silnej nazwie. Zestawy o silnych nazwach oznaczone atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) nie mają tej ochrony. Ten atrybut wyłącza żądanie linku, dzięki czemu zestaw jest dostępny dla obiektów wywołujących, które nie mają pełnego zaufania, takich jak kod wykonywany z intranetu lub Internetu.

 Gdy atrybut APTCA jest obecny w w pełni zaufanym zestawie, a zestaw wykonuje kod w innym zestawie, który nie zezwala częściowo zaufanym obiektom wywołującym, możliwe jest wykorzystanie zabezpieczeń. Jeśli dwie metody `M1` i `M2` spełniają następujące warunki, złośliwe obiekty wywołujące mogą użyć metody `M1`, aby pominąć niejawne żądania pełnego zaufania, które chroni `M2`:

- `M1` to metoda publiczna zadeklarowana w w pełni zaufanym zestawie, który ma atrybut APTCA.

- `M1` wywołuje metodę `M2` poza zestawem `M1`.

- zestaw `M2`nie ma atrybutu APTCA i dlatego nie powinien być wykonywany przez lub w imieniu wywołujących częściowo zaufanych.

  Częściowo zaufany `X` wywołujący może wywoływać metodę `M1`, co sprawia, że `M1` wywoływania `M2`. Ponieważ `M2` nie ma atrybutu APTCA, jego bezpośredni obiekt wywołujący (`M1`) musi spełniać żądanie linku do pełnego zaufania; `M1` ma pełne zaufanie i dlatego spełnia to sprawdzenie. Zagrożenie bezpieczeństwa wynika z faktu, że `X` nie uczestniczy w spełnianiu wymagań łącza, które chroni `M2` przed niezaufanymi wywołaniami. W związku z tym metody z atrybutem APTCA nie mogą wywoływać metod, które nie mają atrybutu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli atrybut APCTA jest wymagany, użyj żądania do ochrony metody, która wywołuje cały zestaw zaufania. Dokładne uprawnienia, których wymagasz, zależą od funkcjonalności uwidocznionej przez metodę. Jeśli jest to możliwe, należy chronić metodę z zapotrzebowaniem na pełne zaufanie, aby upewnić się, że podstawowe funkcje nie są widoczne dla częściowo zaufanych wywołujących. Jeśli nie jest to możliwe, wybierz zestaw uprawnień, które skutecznie chronią dostępne funkcje. Aby uzyskać więcej informacji na temat wymagań, zobacz [wymagania](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że funkcje uwidocznione przez metodę nie bezpośrednio lub pośrednio nie zezwalają obiektom wywołującym na dostęp do poufnych informacji, operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example"></a>Przykład
 W poniższym przykładzie są używane dwa zestawy i aplikacja testowa do zilustrowania luki w zabezpieczeniach wykrytej przez tę regułę. Pierwszy zestaw nie ma atrybutu APTCA i nie powinien być dostępny dla częściowo zaufanych wywołujących (reprezentowane przez `M2` w poprzedniej dyskusji).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Przykład
 Drugi zestaw jest w pełni zaufany i dopuszcza częściowo zaufane obiekty wywołujące (reprezentowane przez `M1` w poprzedniej dyskusji).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Przykład
 Aplikacja testowa (reprezentowana przez `X` w poprzedniej dyskusji) jest częściowo zaufana.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Żądanie pełnego zaufania: żądanie nie powiodło się.** **wywołano
ClassRequiringFullTrust. DoWork.**
## <a name="related-rules"></a>Powiązane reguły
 [CA2117: Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Zobacz też
 [Wskazówki dotyczące bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework zestawy wywoływane przez częściowo zaufany kod](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [przy użyciu bibliotek z częściowo zaufanego kodu](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [żądania](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [linku](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) żądają [danych i modelowania](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

---
title: 'CA2223: Składowe powinny różnić się nie tylko zwracanym typem'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e4e7aa59d273242bd8b97fd4f2777b7edcb5990
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806670"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Składowe powinny różnić się nie tylko zwracanym typem

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dwa publiczne lub chronione elementy członkowskie są opatrzone sygnaturami, które są identyczne, z wyjątkiem typu zwracanego.

## <a name="rule-description"></a>Opis reguły
 Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest specyfikacja Common Language Specification, ani nie jest wspólną cechą języków programowania .NET. Gdy członkowie różnią się tylko typem zwracanym, deweloperów i narzędzia programistyczne mogą nie poprawnie ich rozróżnienie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmiany projektu elementów członkowskich, tak, że są unikatowe, tylko na podstawie jego nazwy i typy parametrów ani nie ujawniaj elementów członkowskich.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład w języka Microsoft intermediate language (MSIL), zawiera typ, który narusza tę regułę. Należy zauważyć, że ta zasada nie naruszył przy użyciu języka C# lub Visual Basic.

```
.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary
```
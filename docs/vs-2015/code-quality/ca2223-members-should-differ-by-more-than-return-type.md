---
title: 'CA2223: składowe powinny różnić się nie tylko zwracanym typem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4c1071617572af44a73f98953fd435623190e0e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540845"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Składowe powinny różnić się nie tylko zwracanym typem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dwa publiczne lub chronione elementy członkowskie mają podpisy identyczne z wyjątkiem typu zwracanego.

## <a name="rule-description"></a>Opis reguły
 Chociaż środowisko uruchomieniowe języka wspólnego zezwala na używanie typów zwracanych do rozróżnienia między identycznymi elementami członkowskimi, ta funkcja nie znajduje się w Common Language Specification ani nie jest powszechną funkcją języków programowania .NET. Gdy elementy członkowskie różnią się tylko typem zwracanym, deweloperzy i narzędzia programistyczne mogą nie rozróżnić się między nimi.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić projekt elementów członkowskich tak, aby były unikatowe, na podstawie ich nazw i typów parametrów lub nie ujawniać elementów członkowskich.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie w języku pośrednim firmy Microsoft (MSIL) przedstawiono typ naruszający tę regułę. Należy zauważyć, że tej reguły nie można naruszać przy użyciu języka C# lub Visual Basic .NET.

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

---
title: 'CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234833"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ wartości widocznej dla Component Object Model (com) jest oznaczony <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atrybutem ustawionym na. <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły

<xref:System.Runtime.InteropServices.LayoutKind>typy układów są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ tych typów może się zmieniać między wersjami programu .NET, które dzielą klientów COM, którzy oczekują określonego układu. Jeśli atrybut nie C#jest określony, Visual Basic i C++ kompilatory określają [LayoutKind.](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) autodla typów wartości. <xref:System.Runtime.InteropServices.StructLayoutAttribute>

O ile nie zostanie oznaczona inaczej, wszystkie publiczne, nieogólne typy są widoczne dla modelu COM, a wszystkie typy niepubliczne i ogólne są niewidoczne dla modelu COM. Aby jednak zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności modelu COM. Zestaw zawierający <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> musi być oznaczony zestawem do `false` , a typ <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być oznaczony z ustawioną na `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu na [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) lub [LayoutKind. sekwencyjnie](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)lub ustaw typ jako niewidoczny dla modelu com.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który narusza regułę i typ, który spełnia regułę.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1408: Nie używaj AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
---
title: 'CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: d9c39e61af994e31a59e75872749464aee0b7093
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54977177"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ wartości widocznych Component Object Model (COM) jest oznaczony za pomocą <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> ustawioną wartość atrybutu <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

<xref:System.Runtime.InteropServices.LayoutKind> typy układu są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ tych typów może się zmieniać między wersjami programu .NET Framework, co spowoduje przerwanie klientów modelu COM, które oczekują określonego układu. Jeśli <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut nie jest określony, C#, Visual Basic, a następnie określ Kompilatory języka C++ [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) dla typów wartości.

Chyba że oznaczony inaczej, wszystkie typy publiczne, nieogólną są widoczne dla modelu COM, a wszystkie typy bez publicznego i ogólny są niewidoczne dla modelu COM. Aby zmniejszyć liczbę fałszywych alarmów, ta reguła wymaga widoczność COM typu, który ma być jawnie określony. Muszą być oznaczone zawierające zestaw <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> równa `false` i typ musi być oznaczony przez <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) lub [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), lub ukrywanie typu modelu COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, typ, który narusza regułę i typ, który spełnia reguły.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikuj typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
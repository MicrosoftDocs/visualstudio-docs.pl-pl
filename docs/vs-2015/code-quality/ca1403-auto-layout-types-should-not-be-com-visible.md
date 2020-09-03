---
title: 'CA1403: typy układów Autoukładu nie powinny być widoczne dla modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534930"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typy z automatycznym układem nie powinny być widoczne dla modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ wartości widocznej dla Component Object Model (COM) jest oznaczony <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> atrybutem ustawionym na <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 <xref:System.Runtime.InteropServices.LayoutKind> typy układów są zarządzane przez środowisko uruchomieniowe języka wspólnego. Układ tych typów może się zmieniać między wersjami .NET Framework, co spowoduje przerwanie klientów COM, którzy oczekują określonego układu. Należy pamiętać, że jeśli <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut nie jest określony, kompilatory języka C# i [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] języka C++ określają <xref:System.Runtime.InteropServices.LayoutKind> układ dla typów wartości.

 O ile nie zostanie oznaczona inaczej, wszystkie publiczne typy nieogólne są widoczne dla modelu COM. wszystkie typy niepubliczne i ogólne są niewidoczne dla modelu COM. Jednak aby zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności COM typu; zestaw zawierający musi być oznaczony <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> zestawem do `false` , a typ musi być oznaczony z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną na `true` .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień wartość <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu na <xref:System.Runtime.InteropServices.LayoutKind> lub <xref:System.Runtime.InteropServices.LayoutKind> lub ustaw typ jako niewidoczny dla modelu com.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę i typ, który spełnia regułę.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie do interfejsu klasy](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [kwalifikowanie typów .NET do](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [współdziałania z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

---
title: 'CA1411: Metody rejestracji modelu COM nie powinny być widoczne | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c35f1d5f2c3593bfbbd0779bfdd9971d48d3ed7a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823738"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Metody rejestracji modelu COM nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda, która jest oznaczona za pomocą <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu jest widoczna na zewnątrz.

## <a name="rule-description"></a>Opis reguły
 Gdy zestaw jest rejestrowany z Component Object Model (COM), wpisy są dodawane do rejestru dla poszczególnych typów widocznych dla modelu COM w zestawie. Metody, które są oznaczone <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> i <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atrybuty są wywoływane podczas procesu rejestrowania i wyrejestrowania z odpowiednio do uruchomienia kodu użytkownika, które są specyficzne dla zarejestrować/wyrejestrować te typy. Ten kod nie powinien zostać wywołany poza tymi procesami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień dostępność metody `private` lub `internal` (`Friend` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwie metody, które naruszają zasady.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1410: Metody rejestracji modelu COM powinny być dopasowane](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Rejestrowanie zestawów do użycia z modelem COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (narzędzie rejestracji zestawów)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)

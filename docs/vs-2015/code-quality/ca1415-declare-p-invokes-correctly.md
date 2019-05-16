---
title: 'CA1415: Poprawnie Zadeklaruj P-Invoke | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57482b720b1a7801fc75e06a5eb5d05d3b1a1417
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691846"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Poprawnie zadeklaruj elementy P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału — Jeśli P/Invoke, która deklaruje parametru nie są widoczne poza zestawem. Przerywanie — Jeśli P/Invoke, która deklaruje parametr są widoczne poza zestawem.|

## <a name="cause"></a>Przyczyna
 Metoda wywołania platformy nieprawidłowo zadeklarowano.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Obecnie ta reguła będzie wyglądać dla deklaracji metod, których platformą docelową funkcji Win32, które mają wskaźnikiem do parametru struktury OVERLAPPED wywołania platformy, a odpowiadający parametr zarządzalny nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy poprawnie zadeklarować platformy wywołania metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano wywołanie platformy metody, które naruszają reguły i spełniać reguły.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

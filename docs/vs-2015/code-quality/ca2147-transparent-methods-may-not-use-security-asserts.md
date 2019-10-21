---
title: 'CA2147: Metody przezroczyste nie mogą używać potwierdzeń zabezpieczeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f2bd0042b6f9a8e46939ab34c86294218fb79f4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610158"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Jawne metody nie mogą używać potwierdzeń zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Kod, który jest oznaczony jako <xref:System.Security.SecurityTransparentAttribute> nie ma wystarczających uprawnień do potwierdzenia.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje wszystkie metody i typy w zestawie, który jest na 100% przezroczysty lub mieszany przezroczysty/krytyczny, i flaguje wszelkie deklaratywne lub bezwzględne użycie <xref:System.Security.CodeAccessPermission.Assert%2A>.

 W czasie wykonywania wszystkie wywołania <xref:System.Security.CodeAccessPermission.Assert%2A> z przezroczystego kodu spowodują, że <xref:System.InvalidOperationException> zostanie zgłoszone. Może to wystąpić w obu zestawach przezroczystych na 100%, a także w mieszanych, przejrzystych i krytycznych zestawach, w których metoda lub typ są zadeklarowane jako przezroczyste, ale zawierają deklaracyjne lub bezwzględne potwierdzenie.

 W [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 wprowadzono funkcję o nazwie *przezroczystość*. Poszczególne metody, pola, interfejsy, klasy i typy mogą być przezroczyste lub krytyczne.

 Kod przezroczysty nie może podwyższyć poziomu uprawnień zabezpieczeń. W związku z tym wszelkie uprawnienia udzielone lub żądanie są automatycznie przenoszone przez kod do domeny wywołującej lub aplikacji hosta. Przykłady podniesienia uprawnień obejmują potwierdzenia, LinkDemands, SuppressUnmanagedCode i kod `unsafe`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, należy oznaczyć kod, który wywołuje potwierdzenie z <xref:System.Security.SecurityCriticalAttribute>, lub usunąć potwierdzenie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj komunikatu z tej reguły.

## <a name="example"></a>Przykład
 Ten kod zakończy się niepowodzeniem, jeśli `SecurityTestClass` jest przezroczysty, gdy metoda `Assert` zgłosi <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Przykład
 Jedną z opcji jest zapoznania się z kodem Metoda SecurityTransparentMethod w poniższym przykładzie, a jeśli metoda jest uważana za bezpieczną dla podniesienia uprawnień, Oznacz SecurityTransparentMethod z bezpiecznym krytycznym warunkiem, że jest to wymagane przez szczegółowe, kompletne i bezproblemowe zabezpieczenia Inspekcja musi być wykonywana na metodzie wraz z wszelkimi wywołaniami, które występują w ramach metody pod potwierdzeniem:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Inna opcja polega na usunięciu potwierdzenia z kodu i umożliwieniu wszelkich kolejnych operacji we/wy na plikach, które przekraczają SecurityTransparentMethod do obiektu wywołującego. Umożliwia to sprawdzanie zabezpieczeń. W takim przypadku Inspekcja zabezpieczeń nie jest zwykle konieczna, ponieważ wymagania dotyczące uprawnień będą przepływać do obiektu wywołującego i/lub domeny aplikacji. Wymagania dotyczące uprawnień są ściśle kontrolowane za poorednictwem zasad zabezpieczeń, środowiska hostingu i uprawnień do kodu źródłowego.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)

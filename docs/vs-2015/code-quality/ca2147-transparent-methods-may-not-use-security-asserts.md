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
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546383"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Kod, który jest oznaczony jako <xref:System.Security.SecurityTransparentAttribute> nie ma wystarczających uprawnień do potwierdzenia.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje wszystkie metody i typy w zestawie, który jest na 100% przezroczysty lub mieszany przezroczysto-krytyczny, i flaguje wszelkie deklaratywne lub bezwzględne użycie <xref:System.Security.CodeAccessPermission.Assert%2A> .

 W czasie wykonywania wszystkie wywołania <xref:System.Security.CodeAccessPermission.Assert%2A> z przezroczystego kodu spowodują, że <xref:System.InvalidOperationException> zostaną zgłoszone. Może to wystąpić w obu zestawach przezroczystych na 100%, a także w mieszanych, przejrzystych i krytycznych zestawach, w których metoda lub typ są zadeklarowane jako przezroczyste, ale zawierają deklaracyjne lub bezwzględne potwierdzenie.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]2,0 wprowadzono funkcję o nazwie *przezroczystość*. Poszczególne metody, pola, interfejsy, klasy i typy mogą być przezroczyste lub krytyczne.

 Kod przezroczysty nie może podwyższyć poziomu uprawnień zabezpieczeń. W związku z tym wszelkie uprawnienia udzielone lub żądanie są automatycznie przenoszone przez kod do domeny wywołującej lub aplikacji hosta. Przykłady podniesienia uprawnień obejmują potwierdzenia, LinkDemands, SuppressUnmanagedCode i `unsafe` kod.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, należy oznaczyć kod, który wywołuje potwierdzenie z <xref:System.Security.SecurityCriticalAttribute> lub usunąć potwierdzenie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj komunikatu z tej reguły.

## <a name="example"></a>Przykład
 Ten kod zakończy się niepowodzeniem `SecurityTestClass` , jeśli jest przezroczysty, gdy `Assert` metoda wygeneruje <xref:System.InvalidOperationException> .

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Przykład
 Jedną z opcji jest zapoznania się z kodem Metoda SecurityTransparentMethod w poniższym przykładzie, a jeśli metoda jest uważana za bezpieczną dla podniesienia uprawnień, Oznacz SecurityTransparentMethod z bezpiecznym krytycznym warunkiem, że należy wykonać szczegółową, kompletną i bezproblemową inspekcję zabezpieczeń na metodzie wraz z dowolnymi wywołaniami, które występują w ramach metody pod potwierdzeniem:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Inna opcja polega na usunięciu potwierdzenia z kodu i umożliwieniu wszelkich kolejnych operacji we/wy na plikach, które przekraczają SecurityTransparentMethod do obiektu wywołującego. Umożliwia to sprawdzanie zabezpieczeń. W takim przypadku Inspekcja zabezpieczeń nie jest zwykle konieczna, ponieważ wymagania dotyczące uprawnień będą przepływać do obiektu wywołującego i/lub domeny aplikacji. Wymagania dotyczące uprawnień są ściśle kontrolowane za poorednictwem zasad zabezpieczeń, środowiska hostingu i uprawnień do kodu źródłowego.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)

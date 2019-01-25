---
title: 'CA2147: Metody przezroczyste nie mogą używać zabezpieczeń potwierdza | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e8ac2e907e3c13a019e5f534faf86ae425ae30a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770542"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Metody przezroczyste nie mogą używać asercji zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Kod, który jest oznaczony jako <xref:System.Security.SecurityTransparentAttribute> nie udzielono uprawnień wystarczających do potwierdzenia.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje wszystkie metody i typy w zestawie, który jest albo 100% przezroczysty lub mieszany przezroczysto krytyczny i zaznacza deklaratywne lub imperatywne użycie elementu <xref:System.Security.CodeAccessPermission.Assert%2A>.

 W czasie wszelkie wywołania do wykonywania <xref:System.Security.CodeAccessPermission.Assert%2A> z przezroczystego kodu spowoduje, że <xref:System.InvalidOperationException> zostanie wygenerowany. Taka sytuacja może wystąpić, oba zestawy przezroczyste 100%, a także na pulpicie zestawów mieszanych przezroczysto krytyczny, w którym jest zadeklarowana jako przezroczysty metody lub typu, ale zawiera Assert zaznacza deklaratywne lub imperatywne.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 wprowadzono funkcję o nazwie *przezroczystości*. Poszczególne metody, pola, interfejsy, klas i typów może być przezroczysty lub krytyczny.

 Przezroczysty kod nie jest dozwolony do podniesienia uprawnień zabezpieczeń. W związku z tym wszelkie uprawnienia udzielone lub żądać go automatycznie są przekazywane za pośrednictwem kodu domeny aplikacji obiektu wywołującego lub hosta. Wybierającym przykłady potwierdzenia, LinkDemands, SuppressUnmanagedCode, i `unsafe` kodu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, albo oznaczyć kod, który wywołuje Assert, za pomocą <xref:System.Security.SecurityCriticalAttribute>, lub usuń Assert.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj wiadomości od tej reguły.

## <a name="example"></a>Przykład
 Ten kod zakończy się niepowodzeniem, jeśli `SecurityTestClass` są przezroczyste, kiedy `Assert` metoda zgłasza wyjątek <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Przykład
 Jedną z opcji jest na Przegląd kodu metody SecurityTransparentMethod w poniższym przykładzie, a jeśli metoda jest uważane za bezpieczne o podniesienie uprawnień, należy oznaczyć SecurityTransparentMethod z bezpieczny krytyczny takie rozwiązanie wymaga zabezpieczeń szczegółowe, kompletne i błędów Inspekcja odbywa się na metodzie, wraz z dowolnym wezwaniem występujących w ramach metody Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Innym rozwiązaniem jest usunięcie Asercja z kodu i pozwól dowolnego pliku kolejnych operacji We/Wy przepływu żądania uprawnień poza SecurityTransparentMethod do obiektu wywołującego. Umożliwia to sprawdzanie zabezpieczeń. W tym przypadku nie inspekcji zabezpieczeń zwykle wdrożenia, ponieważ żądania uprawnień będą przepływać do obiektu wywołującego i/lub w domenie aplikacji. Żądania uprawnień ściśle są kontrolowane przez zasady zabezpieczeń, hostowania środowiska i przyznaje uprawnienia kodu źródłowego.

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)

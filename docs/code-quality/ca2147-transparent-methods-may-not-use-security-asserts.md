---
title: 'CA2147: Metody przezroczyste nie mogą używać zabezpieczeń asercji'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4daf5d4183c8226a0bed613c5e175ddbd620f43a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912496"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Metody przezroczyste nie mogą używać zabezpieczeń asercji

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

 .NET Framework 2.0 wprowadzono funkcję o nazwie *przezroczystości*. Poszczególne metody, pola, interfejsy, klas i typów może być przezroczysty lub krytyczny.

 Przezroczysty kod nie jest dozwolony do podniesienia uprawnień zabezpieczeń. W związku z tym wszelkie uprawnienia udzielone lub żądać go automatycznie są przekazywane za pośrednictwem kodu domeny aplikacji obiektu wywołującego lub hosta. Wybierającym przykłady potwierdzenia, LinkDemands, SuppressUnmanagedCode, i `unsafe` kodu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, albo oznaczyć kod, który wywołuje Assert, za pomocą <xref:System.Security.SecurityCriticalAttribute>, lub usuń Assert.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj wiadomości od tej reguły.

## <a name="example"></a>Przykład
 Ten kod zakończy się niepowodzeniem, jeśli `SecurityTestClass` są przezroczyste, kiedy `Assert` metoda zgłasza wyjątek <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Przykład
 Jedną z opcji jest na Przegląd kodu metody SecurityTransparentMethod w poniższym przykładzie, a jeśli metoda jest uważane za bezpieczne o podniesienie uprawnień, Oznaczaj SecurityTransparentMethod bezpieczny krytyczny. Wymaga to, czy inspekcji zabezpieczeń szczegółowe, kompletne i wolny od błędów odbywa się na metodzie, wraz z dowolnym wezwaniem występujących w ramach metody Assert:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Innym rozwiązaniem jest usunięcie Asercja z kodu i pozwól dowolnego pliku kolejnych operacji We/Wy przepływu żądania uprawnień poza SecurityTransparentMethod do obiektu wywołującego. Umożliwia to sprawdzanie zabezpieczeń. W tym przypadku nie inspekcji zabezpieczeń wdrożenia, ponieważ żądania uprawnień będą przepływać do obiektu wywołującego i/lub w domenie aplikacji. Żądania uprawnień ściśle są kontrolowane przez zasady zabezpieczeń, hostowania środowiska i przyznaje uprawnienia kodu źródłowego.

## <a name="see-also"></a>Zobacz także
 [Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)
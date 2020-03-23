---
title: 'DA0007: Unikaj używania wyjątków dla przepływu sterowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26819be7cd001e87a6f94ac97d29c8a5e67f3932
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777702"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków do przepływu sterowania

|||
|-|-|
|Identyfikator reguły|DA0007|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Wszystkie|
|Komunikat|Duża liczba wyjątków są konsekwentnie generowane. Należy rozważyć zmniejszenie użycia wyjątków w logice programu.|
|Typ wiadomości|Ostrzeżenie|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Wysoki wskaźnik .NET Framework obsługi wyjątków zostały wywołane w danych profilowania. Należy rozważyć użycie innych logiki przepływu sterowania, aby zmniejszyć liczbę wyjątków, które są generowane.

## <a name="rule-description"></a>Opis reguły
 Podczas gdy użycie obsługi wyjątków do połowu błędów i innych zdarzeń, które zakłócają wykonywanie programu jest dobrą praktyką, użycie obsługi wyjątków w ramach logiki wykonywania programu regularnego może być kosztowne i należy unikać. W większości przypadków wyjątki powinny być używane tylko w przypadku okoliczności, które występują rzadko i nie są oczekiwane. Wyjątki nie powinny być używane do zwracania wartości jako część typowego przepływu programu. W wielu przypadkach można uniknąć wywoływania wyjątków przez sprawdzanie poprawności wartości i przy użyciu logiki warunkowej, aby zatrzymać wykonywanie instrukcji, które powodują problem.

 Aby uzyskać więcej informacji, zobacz sekcję [Zarządzanie wyjątkami](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) **w rozdziale 5 — poprawa wydajności kodu zarządzanego** w woluminie **poprawy wydajności aplikacji .NET i skalowalności** biblioteki **wzorce i praktyki firmy Microsoft** w sieci MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie wiadomość w oknie Lista błędów, aby przejść do widoku Znaczniki. Znajdź kolumnę zawierającą **.NET CLR@ProcessInstance\\Exceptions( ) # pomiarów programu Excels Thrown/sec.** Określ, czy istnieją określone fazy wykonywania programu, gdzie obsługa wyjątków jest częstsza niż inne. Korzystając z profilu próbkowania, spróbuj zidentyfikować instrukcje throw i try/catch bloków, które generują częste wyjątki. Jeśli to konieczne, dodaj logikę do bloków catch, aby ułatwić zrozumienie, które wyjątki są obsługiwane najczęściej. Jeśli to możliwe, zastąp często wykonywane instrukcje throw lub catch bloków z prostą logiką kontroli przepływu lub kod sprawdzania poprawności.

 Na przykład, jeśli okaże się, że aplikacja obsługiwała częste wyjątki DivideByZeroException, dodawanie logiki do programu w celu sprawdzenia mianowników z wartościami zerowymi zwiększa wydajność aplikacji.

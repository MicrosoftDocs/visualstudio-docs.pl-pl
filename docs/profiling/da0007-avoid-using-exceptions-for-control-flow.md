---
title: 'DA0007: Unikaj używania wyjątków dla przepływu sterowania | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: 9509168878d18ea3074dd91b4929313a959138c2
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911026"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków do przepływu sterowania

|||
|-|-|
|Identyfikator reguły|DA0007|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Wszystkie|
|Komunikat|Często są zgłaszane duże liczby wyjątków. Rozważ zmniejszenie użycia wyjątków w logice programu.|
|Typ komunikatu|Ostrzeżenie|

 Podczas profilowania przy użyciu metod próbkowania, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 W danych profilowania wywołano wysoką częstotliwość obsługi wyjątków .NET Framework. Rozważ użycie innej logiki przepływu sterowania, aby zmniejszyć liczbę zgłaszanych wyjątków.

## <a name="rule-description"></a>Opis reguły
 Chociaż używanie obsługi wyjątków do przechwytywania błędów i innych zdarzeń, które zakłócają wykonywanie programu, jest dobrym sposobem, korzystanie z programu obsługi wyjątków jako części zwykłej logiki wykonywania programu może być kosztowne i powinno być nieuniknione. W większości przypadków wyjątki powinny być używane tylko w przypadku sytuacji, w których występują rzadko i nie są oczekiwane. Wyjątków nie należy używać do zwracania wartości jako części typowego przepływu programu. W wielu przypadkach można uniknąć wywoływania wyjątków przez sprawdzenie poprawności wartości i użycie logiki warunkowej do zatrzymania wykonywania instrukcji, które powodują wystąpienie problemu.

 Aby uzyskać więcej informacji, zobacz sekcję [Zarządzanie wyjątkami](/previous-versions/msp-n-p/ff647790(v=pandp.10)#scalenetchapt05_topic24) w **rozdziale 5 — Poprawianie wydajności kodu zarządzanego** w celu **zwiększenia wydajności aplikacji .NET i skalowalności** **wzorców i praktyk firmy Microsoft** Biblioteka w witrynie MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku znaczniki. Znajdź kolumnę zawierającą wyjątki środowiska **.NET CLR (@ProcessInstance)\\liczbę pomiarów w programie Excel/s** . Ustal, czy istnieją określone fazy wykonywania programu, w których obsługa wyjątków jest częściej niż inne. Przy użyciu profilu próbkowania spróbuj identyfikować instrukcje throw i bloki try/catch generujące częste wyjątki. W razie potrzeby Dodaj logikę do bloków catch, aby ułatwić zrozumienie, które wyjątki są najczęściej obsługiwane. Jeśli to możliwe, Zastąp często wykonywane instrukcje throw lub bloki catch z prostą logiką sterowania przepływem lub kodem walidacji.

 Na przykład jeśli okaże się, że aplikacja obsługiwała częste wyjątki DivideByZeroException, dodanie logiki do programu w celu sprawdzenia, czy nie ma żadnych wartości, zwiększa wydajność aplikacji.
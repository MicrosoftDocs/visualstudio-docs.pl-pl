---
title: DA0007 — Unikaj używania wyjątków dla przepływu sterowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a33d5b8d18f18fb6bf7a2420603d994d845ce8f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520799"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków w przepływie sterowania

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0007|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Wszystko|
|Komunikat|Często są zgłaszane duże liczby wyjątków. Rozważ zmniejszenie użycia wyjątków w logice programu.|
|Typ wiadomości|Ostrzeżenie|

 Podczas profilowania przy użyciu metod próbkowania, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 W danych profilowania wywołano wysoką częstotliwość obsługi wyjątków .NET Framework. Rozważ użycie innej logiki przepływu sterowania, aby zmniejszyć liczbę zgłaszanych wyjątków.

## <a name="rule-description"></a>Opis reguły
 Chociaż używanie obsługi wyjątków do przechwytywania błędów i innych zdarzeń, które zakłócają wykonywanie programu, jest dobrym sposobem, korzystanie z programu obsługi wyjątków jako części zwykłej logiki wykonywania programu może być kosztowne i powinno być nieuniknione. W większości przypadków wyjątki powinny być używane tylko w przypadku sytuacji, w których występują rzadko i nie są oczekiwane. Wyjątków nie należy używać do zwracania wartości jako części typowego przepływu programu. W wielu przypadkach można uniknąć wywoływania wyjątków przez sprawdzenie poprawności wartości i użycie logiki warunkowej do zatrzymania wykonywania instrukcji, które powodują wystąpienie problemu.

 Aby uzyskać więcej informacji, zobacz sekcję [Zarządzanie wyjątkami](/previous-versions/msp-n-p/ff647790(v=pandp.10)#exception-management) w **rozdziale 5 — Poprawianie wydajności kodu zarządzanego** w artykule **Poprawianie wydajności i skalowalności aplikacji .NET** w bibliotece **wzorców i praktyk firmy Microsoft** w witrynie MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku znaczniki. Znajdowanie kolumny zawierającej wyjątki środowiska **.NET CLR ( @ProcessInstance ) liczba \\ zgłoszonych w programie Excel/s** . Ustal, czy istnieją określone fazy wykonywania programu, w których obsługa wyjątków jest częściej niż inne. Przy użyciu profilu próbkowania spróbuj identyfikować instrukcje throw i bloki try/catch generujące częste wyjątki. W razie potrzeby Dodaj logikę do bloków catch, aby ułatwić zrozumienie, które wyjątki są najczęściej obsługiwane. Jeśli to możliwe, Zastąp często wykonywane instrukcje throw lub bloki catch z prostą logiką sterowania przepływem lub kodem walidacji.

 Na przykład jeśli okaże się, że aplikacja obsługiwała częste wyjątki DivideByZeroException, dodanie logiki do programu w celu sprawdzenia, czy nie ma żadnych wartości, zwiększa wydajność aplikacji.

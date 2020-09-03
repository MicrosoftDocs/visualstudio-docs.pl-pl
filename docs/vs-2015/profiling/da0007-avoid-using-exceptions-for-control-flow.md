---
title: 'DA0007: Unikaj używania wyjątków dla przepływu sterowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bae47d5fd759de66777c4e1472603d3bf4a193d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843935"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Unikaj używania wyjątków w przepływie sterowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0007 |  
| Kategoria |. Użycie platformy NET Framework |  
| Metody profilowania | Wszystkie |  
| Komunikat | Często są zgłaszane duże liczby wyjątków. Rozważ zmniejszenie użycia wyjątków w logice programu. |  
| Typ komunikatu | Ostrzeżenie |  
  
 Podczas profilowania przy użyciu metod próbkowania, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.  
  
## <a name="cause"></a>Przyczyna  
 W danych profilowania wywołano wysoką częstotliwość obsługi wyjątków .NET Framework. Rozważ użycie innej logiki przepływu sterowania, aby zmniejszyć liczbę zgłaszanych wyjątków.  
  
## <a name="rule-description"></a>Opis reguły  
 Chociaż używanie obsługi wyjątków do przechwytywania błędów i innych zdarzeń, które zakłócają wykonywanie programu, jest dobrym sposobem, korzystanie z programu obsługi wyjątków jako części zwykłej logiki wykonywania programu może być kosztowne i powinno być nieuniknione. W większości przypadków wyjątki powinny być używane tylko w przypadku sytuacji, w których występują rzadko i nie są oczekiwane. Wyjątków nie należy używać do zwracania wartości jako części typowego przepływu programu. W wielu przypadkach można uniknąć wywoływania wyjątków przez sprawdzenie poprawności wartości i użycie logiki warunkowej do zatrzymania wykonywania instrukcji, które powodują wystąpienie problemu.  
  
 Aby uzyskać więcej informacji, zobacz sekcję [Zarządzanie wyjątkami](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic24) w **rozdziale 5 — Poprawianie wydajności kodu zarządzanego** w celu **zwiększenia wydajności aplikacji .NET i skalowalności** biblioteki **wzorców i praktyk firmy Microsoft** w witrynie MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku znaczniki. Znajdź kolumnę zawierającą wyjątki środowiska **.NET CLR ( @ProcessInstance ) \\ liczba zgłoszonych wyjątków/s** . Ustal, czy istnieją określone fazy wykonywania programu, w których obsługa wyjątków jest częściej niż inne. Przy użyciu profilu próbkowania spróbuj identyfikować instrukcje throw i bloki try/catch generujące częste wyjątki. W razie potrzeby Dodaj logikę do bloków catch, aby ułatwić zrozumienie, które wyjątki są najczęściej obsługiwane. Jeśli to możliwe, Zastąp często wykonywane instrukcje throw lub bloki catch z prostą logiką sterowania przepływem lub kodem walidacji.  
  
 Na przykład jeśli okaże się, że aplikacja obsłuży częste wyjątki DivideByZeroException, dodanie logiki do programu w celu sprawdzenia, czy nie ma żadnych wartości, spowoduje zwiększenie wydajności aplikacji.

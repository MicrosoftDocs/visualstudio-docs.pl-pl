---
title: 'DA0504: maksymalny zestaw roboczy w bajtach dla profilowanego procesu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a181ecb66c3735eb34ab3c866c3c68b2397781f6
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779327"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maksymalny rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu

|||
|-|-|
|Identyfikator zasady|DA0504|
|Kategoria|Zarządzanie zasobami|
|Metoda profilowania|Wszystkie|
|Komunikat|Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik zestawu roboczego procesu mierzy użycie pamięci fizycznej przez proces profilowania. Raportowana wartość jest maksimum zaobserwowane we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacje programu|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia maksymalną ilość pamięci fizycznej (w bajtach), która aktualnie jest używana przez proces. Zestaw roboczy procesu przedstawia strony z przestrzeni adresowej procesu, która znajduje się obecnie w pamięci fizycznej. Ta reguła raportuje maksymalną wartość zestawu roboczego procesu, gdy profilowanie było aktywne.

 Raportowana wartość obejmuje strony rezydentne z udostępnionych segmentów pamięci, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołują się odwołania do procesów, są uwzględniane w zliczanych segmentach pamięci współdzielonej. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu udostępnionych segmentów pamięci.

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, która jest aktywnie używana przez proces. Ma także wpływ na ilość pamięci fizycznej (lub pamięci RAM), która jest dostępna do uruchamiania aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Aby uzyskać więcej informacji na temat procesów zestawów roboczych, zobacz [zestaw roboczy](/windows/win32/memory/working-set) w dokumentacji zarządzania pamięcią systemu Windows w witrynie MSDN.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Ta zasada zbiera dane pomiarów z funkcji monitorowania wydajności systemu Windows i raportuje je tylko w celu uzyskania informacji. Służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach testowych.

 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź kolumny licznika **Process\Working** i **pamięć \ strony/s** . Następnie Znajdź maksymalną wartość **zestawu Process\Working** i porównaj ją z wartością **pamięć \ strony/s** . Często wartość maksymalna zestawu roboczego jest skojarzona z interwałem, w którym występuje zmniejszona aktywność we/wy stronicowania, szczególnie jeśli maszyna jest ograniczona do pamięci.

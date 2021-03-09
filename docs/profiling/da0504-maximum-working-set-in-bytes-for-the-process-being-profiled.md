---
title: DA0504 — maksymalny zestaw roboczy w bajtach dla profilowanego procesu | Microsoft Docs
description: Ten komunikat przedstawia maksymalną ilość pamięci fizycznej (w bajtach), która aktualnie jest używana przez proces.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7810646f14c61683fc3fc5e3e70eee33ba01dde1
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465793"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maksymalny zestaw roboczy w bajtach dla profilowanego procesu

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0504|
|Kategoria|Zarządzanie zasobami|
|Metoda profilowania|Wszystko|
|Komunikat|Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik zestawu roboczego procesu mierzy użycie pamięci fizycznej przez proces profilowania. Raportowana wartość jest maksimum zaobserwowane we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia maksymalną ilość pamięci fizycznej (w bajtach), która aktualnie jest używana przez proces. Zestaw roboczy procesu przedstawia strony z przestrzeni adresowej procesu, która znajduje się obecnie w pamięci fizycznej. Ta reguła raportuje maksymalną wartość zestawu roboczego procesu, gdy profilowanie było aktywne.

 Raportowana wartość obejmuje strony rezydentne z udostępnionych segmentów pamięci, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołują się odwołania do procesów, są uwzględniane w zliczanych segmentach pamięci współdzielonej. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu udostępnionych segmentów pamięci.

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, która jest aktywnie używana przez proces. Ma także wpływ na ilość pamięci fizycznej (lub pamięci RAM), która jest dostępna do uruchamiania aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Aby uzyskać więcej informacji na temat procesów zestawów roboczych, zobacz [zestaw roboczy](/windows/win32/memory/working-set) w dokumentacji zarządzania pamięcią systemu Windows w witrynie MSDN.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Ta zasada zbiera dane pomiarów z funkcji monitorowania wydajności systemu Windows i raportuje je tylko w celu uzyskania informacji. Służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach testowych.

 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź kolumny licznika **Process\Working** i **pamięć \ strony/s** . Następnie Znajdź maksymalną wartość **zestawu Process\Working** i porównaj ją z wartością **pamięć \ strony/s** . Często wartość maksymalna zestawu roboczego jest skojarzona z interwałem, w którym występuje zmniejszona aktywność we/wy stronicowania, szczególnie jeśli maszyna jest ograniczona do pamięci.

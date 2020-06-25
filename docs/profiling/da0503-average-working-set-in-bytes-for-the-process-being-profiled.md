---
title: DA0503 — średni zestaw roboczy w bajtach dla profilowanego procesu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bc22ec0c1ec618ed38c9860a110b1130c291ed1
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332277"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu

|||
|-|-|
|Identyfikator reguły|DA0503|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystko|
|Komunikat|Te informacje zostały zebrane tylko w celu uzyskania informacji. Licznik zestawu roboczego procesu mierzy użycie pamięci fizycznej przez proces profilowania. Raportowana wartość to średnia obliczona dla wszystkich interwałów pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia średnią ilość pamięci fizycznej używanej aktualnie przez proces w bajtach (zestaw roboczy). Zestaw roboczy procesu przedstawia strony z przestrzeni adresowej procesu, która znajduje się obecnie w pamięci fizycznej.

 Raportowana wartość obejmuje rezydentne strony z udostępnionych segmentów pamięci, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołują się odwołania do procesów, są uwzględniane w zliczanych segmentach pamięci współdzielonej. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu udostępnionych segmentów pamięci.

 Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny.

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, która jest aktywnie używana przez proces. Ma także wpływ na ilość pamięci fizycznej (lub pamięci RAM), która jest dostępna do uruchamiania aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Jeśli pamięć fizyczna jest ograniczona, wartość zestawu roboczego procesu to APT, tak aby system operacyjny próbował zrównoważyć użycie pamięci przez aktywne procesy przez okresowe przycinanie dość nieaktywnych stron z procesów zestawów roboczych.

 Aby uzyskać więcej informacji na temat procesów zestawów roboczych, zobacz [zestaw roboczy](/windows/win32/memory/working-set) w dokumentacji zarządzania pamięcią systemu Windows w witrynie MSDN.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Wartość reguły służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.

 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [Widok znaczników](../profiling/marks-view.md) danych profilowania. Znajdź **Process\Working zestawu** i kolumny **pamięć \ strony/s** . Porównaj dwie kolumny i ustal, czy istnieją określone fazy wykonywania programu, które są prawdopodobnie skojarzone ze zwiększoną aktywnością we/wy stronicowania.

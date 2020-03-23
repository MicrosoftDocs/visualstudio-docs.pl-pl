---
title: 'DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 8c9d309d7bf10cee07cc30c4568d2dfa59d1be56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777453"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Średnia robocza ustawiona w bajtach dla profilowanego procesu

|||
|-|-|
|Identyfikator reguły|DA0503|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystkie|
|Komunikat|Informacje te zostały zebrane wyłącznie w celu uzyskania informacji. Licznik Zestaw roboczy procesu mierzy użycie pamięci fizycznej przez proces, który są profilowania. Zgłoszona wartość jest średnią obliczoną we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje o średniej ilości pamięci fizycznej, która jest obecnie używany w bajtach (zestaw roboczy). Zestaw roboczy procesu reprezentuje strony z przestrzeni adresowej procesu, które obecnie znajdują się w pamięci fizycznej.

 Zgłoszona wartość obejmuje strony rezydentne z segmentów pamięci współużytkowanej, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołania do procesu są uwzględniane w segmentach pamięci współużytkowanej, które są zliczane. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu segmentów pamięci współużytkowanej.

 Zgłoszona wartość jest średnią we wszystkich interwałach pomiaru, w których profilowany proces był aktywny.

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, z jakiej aktywnie korzysta proces. Ma również wpływ na ilość pamięci fizycznej (lub pamięci RAM) dostępne do uruchomienia aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Jeśli pamięć fizyczna jest ograniczona, wartość zestawu roboczego procesu może się znacznie różnić, ponieważ systemy operacyjne próbują zrównoważyć użycie pamięci w aktywnych procesach, okresowo przycinając dość nieaktywne strony z zestawów roboczych procesu.

 Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [Zestaw roboczy](/windows/win32/memory/working-set) w dokumentacji zarządzania pamięcią systemu Windows w msdn.

## <a name="how-to-use-rule-data"></a>Jak korzystać z danych reguły
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.

 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [znaczników](../profiling/marks-view.md) danych profilowania. Znajdź kolumnę **Proces\Zestaw roboczy** i **Kolumna Pamięć\Strony/s.** Porównaj dwie kolumny i określ, czy istnieją określone fazy wykonywania programu, które wydają się być skojarzone ze zwiększoną aktywnością we/wy stronicowania.

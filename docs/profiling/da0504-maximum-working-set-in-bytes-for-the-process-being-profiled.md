---
title: 'DA0504: Maksymalny zestaw roboczy w bajtach dla profilowanego procesu | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779327"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maksymalny rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu

|||
|-|-|
|Identyfikator reguły|DA0504|
|Kategoria|Zarządzanie zasobami|
|Metoda profilowania|Wszystkie|
|Komunikat|Informacje te zostały zebrane wyłącznie w celu uzyskania informacji. Licznik Zestaw roboczy procesu mierzy użycie pamięci fizycznej przez proces, który są profilowania. Zgłoszona wartość jest maksymalną obserwowaną we wszystkich odstępach czasu pomiaru.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje o maksymalnej ilości pamięci fizycznej w bajtach, z których obecnie korzysta proces. Zestaw roboczy procesu reprezentuje strony z przestrzeni adresowej procesu, które obecnie znajdują się w pamięci fizycznej. Ta reguła raportuje maksymalną wartość dla zestawu roboczego procesu, gdy profilowanie było aktywne.

 Zgłoszona wartość obejmuje strony rezydentne z segmentów pamięci współużytkowanej, do których odwołuje się proces. Udostępnione biblioteki DLL, do których odwołania do procesu są uwzględniane w segmentach pamięci współużytkowanej, które są zliczane. Wartość zestawu roboczego procesu może być wyższa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu segmentów pamięci współużytkowanej.

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej, z jakiej aktywnie korzysta proces. Ma również wpływ na ilość pamięci fizycznej (lub pamięci RAM) dostępne do uruchomienia aplikacji i rywalizacji dla tej pamięci fizycznej z innych uruchomionych procesów. Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [Zestaw roboczy](/windows/win32/memory/working-set) w dokumentacji zarządzania pamięcią systemu Windows w msdn.

## <a name="how-to-use-rule-data"></a>Jak korzystać z danych reguł
 Reguła zbiera te dane pomiarowe z funkcji monitorowania wydajności systemu Windows i zgłasza go tylko w celu uzyskania informacji. Użyj go do porównania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach testowych.

 Kliknij dwukrotnie wiadomość w oknie Lista błędów, aby przejść do [widoku znaczników](../profiling/marks-view.md) danych profilowania. Znajdź kolumny **liczników Proces\Zestaw roboczy** i **Pamięć\Strony/s.** Następnie znajdź maksymalną wartość **zestawu roboczego Process\i** porównaj ją z wartością **Pamięć\Strony/s.** Często maksymalna wartość zestawu roboczego jest skojarzona z interwałem, w którym zmniejsza się aktywność we/wy stronicowania, zwłaszcza jeśli komputer jest ograniczony pamięcią.

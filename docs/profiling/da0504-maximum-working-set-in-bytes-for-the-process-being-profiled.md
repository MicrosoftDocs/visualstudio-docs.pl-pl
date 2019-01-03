---
title: 'DA0504: Maksymalny zestaw roboczy w bajtach dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cd19d720331bbd16b02c545384260305295d588
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921880"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maksymalny zestaw roboczy w bajtach dla procesu poddawanego profilowaniu

|||  
|-|-|  
|Identyfikator reguły|DA0504|  
|Kategoria|Zarządzanie zasobami|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Te dane zostały zebrane wyłącznie w celach informacyjnych. Licznik zestawu roboczego procesu mierzy fizyczne użycie pamięci przez profilowany proces. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych.|  
|Typ reguły|Informacje|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty maksymalną ilość pamięci fizycznej w bajtach, aktualnie używane w procesie. Proces Zestaw roboczy reprezentuje stron z przestrzeni adresowej procesu, które obecnie znajdują się w pamięci fizycznej. Ta zasada raporty maksymalną wartość zestaw roboczy procesu podczas profilowania jest aktywny.  

 Wartość zgłaszaną zawiera rezydentnego strony z segmentów pamięci współużytkowanej, których proces ma odwołania. Współdzielone Dlll przetwarzania odwołania są objęte segmentów pamięci współużytkowanej, które są uwzględniane. Wartość procesu, rozmiar zestawu roboczego mogą być większe niż ilość pamięci wirtualnej, która ze względu na segmenty udostępnionej pamięci przydzielonej przez proces.  

 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej aktywnie używanej przez proces. Również jest zależna od ilości pamięci fizycznej (lub pamięci RAM) dostępna do uruchamiania aplikacji i rywalizacji o tej pamięci fizycznej z innych uruchomionych procesów. Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [rozmiar zestawu roboczego](http://go.microsoft.com/fwlink/?LinkId=177830) w dokumentacji MSDN zarządzanie pamięcią Windows.  

## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Reguła zbiera te dane pomiaru z funkcji monitorowania wydajności, Windows i zgłasza go wyłącznie w celach informacyjnych. Użyj go, aby porównać wydajność różnych wersji lub kompilacjach programu lub zrozumieć wydajność aplikacji w ramach testu w różnych scenariuszach.  

 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **Ustaw Process\Working** i **Pamięć\Strony/s** licznik kolumn. Następnie znajdź wartość maksymalna **Ustaw Process\Working** i porównać go do **Pamięć\Strony/s** wartość. Często maksimum zestawu roboczego jest skojarzony z interwał, w którym znajduje się pogorszyła aktywności We/Wy stronicowania, zwłaszcza, jeśli komputer jest ograniczone do pamięci.
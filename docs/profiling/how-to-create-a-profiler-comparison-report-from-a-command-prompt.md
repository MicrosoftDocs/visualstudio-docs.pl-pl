---
title: 'Instrukcje: Tworzenie raportu porównania Profiler w wierszu polecenia z | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11a3850073068cf280901a6948565329e83f4629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973958"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Instrukcje: Tworzenie raportu porównania profilera z wiersza polecenia
Możesz wygenerować [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools raport, który porównuje dane dotyczące wydajności dwóch danych profilowania (. *Vsp* lub. *vsps*) plików. Ten raport prezentuje różnic, największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego. Wartości w raporcie przedstawiają zmian lub zmiany z linią bazową pierwszego pliku, który określisz. Tę deltę jest obliczana przez określenie różnica między stara wartość, czyli wartość punktu odniesienia, a wartość wyniku z analizy nowych. Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.

 Aby wyświetlić listę identyfikatorów kategorii porównania i pola, wpisz następujące polecenie w wierszu:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Aby utworzyć raport porównawczy, należy użyć następującej składni:

 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [ **/** `Options`]

 Można dodać opcji z poniższej tabeli, aby **VSPerfReport/diff** wiersza polecenia.

|Opcja|Opis|
|------------|-----------------|
|**DiffThreshold:** [*wartość*]|Różnica należy pominąć, jeśli jest poniżej tej wartości procentowej wartości progu. Ponadto nowe dane przy użyciu wartości znajdujących się poniżej tego progu nie będą wyświetlane.|
|**DiffTable:** *TableName*|Ta tabela służy do porównywania plików. Domyślnie jest używany w tabeli funkcji. Określ identyfikator, który znajduje się w **VSPerfReport/querydifftables zwraca**.|
|**DiffColumn:** *NazwaKolumny*|Ta kolumna służy do porównywania wartości. Domyślnie kolumna % próbek wyłącznych jest używana. Określ identyfikator, który znajduje się w **VSPerfReport/querydifftables zwraca**.|
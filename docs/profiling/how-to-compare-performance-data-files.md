---
title: 'Instrukcje: Porównywanie plików danych dotyczących wydajności | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101512cb15bca022e5e3b473c84bd433a7269e15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973906"
---
# <a name="how-to-compare-performance-data-files"></a>Instrukcje: Porównywanie plików danych dotyczących wydajności
Możesz porównać wyniki dwóch plików danych profilera różnych (. *Vsp* lub. *vsps*), tworząc porównania ("Diff"), raportu lub wyświetlić. Porównanie przedstawiono różnice największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego.

 Raport Diff przedstawia widok tabeli danych. W tabeli przedstawiono, różnicowej lub zmiana z linii bazowej. To jest obliczana przez określenie różnicy starej wartości, wartość punktu odniesienia i wartość wyniku z nowego analizy.

 Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.

 Próg można ustawić do zmniejszenia szumu i odfiltrować wszystkie dane w widoku tabeli wiersze, które nie uległy zmianie o określoną wartość.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok pliku porównania dla projektu w Eksploratorze wydajności

1. W **Eksplorator wydajności**w obszarze **raporty**, wybierz opcję. *Vsp* lub. *vsps* plik raportu, który chcesz użyć jako wartości linii bazowej do porównania.

2. Wybierz opcję. *vsp* lub. *vsps* pliki, które chcesz porównać raportów.

3. Kliknij prawym przyciskiem myszy jeden z wybranych plików, a następnie kliknij przycisk **raporty porównaj**.

### <a name="to-compare-values"></a>Do porównywania wartości

1. Wybierz **raport porównawczy** karta w oknie widoku raportu.

2. W **tabeli** listy rozwijanej wybierz funkcję lub moduły do porównania.

3. W **kolumny** listy rozwijanej wybierz wartość, którą chcesz porównać.

4. (opcjonalnie) Wpisz wartość dla **próg**.

5. Kliknij przycisk **zastosować**.

### <a name="to-compare-report-files"></a>Porównywanie plików raportów

1. Na **analizy** menu, wybierz opcję **Porównaj wydajność raportów**.

2. W **wybierz pliki analizy porównanie** okien, przeglądania i wybierz **plik punktu odniesienia** pliku analizy (. *Vsp* lub. *vsps*) i **plik do porównania** (. *Vsp* lub. *vsps*).

3. Kliknij przycisk **OK**.
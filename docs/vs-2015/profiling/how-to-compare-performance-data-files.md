---
title: 'Porady: porównywanie plików danych dotyczących wydajności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf80c86f233a40ba0d65d239ae1668d575a66bb2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752618"
---
# <a name="how-to-compare-performance-data-files"></a>Porady: porównywanie plików danych dotyczących wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz porównać wyniki dwa pliki danych różnych profiler (.vsp lub .vsps), tworząc raport porównawczy ("Diff") lub widoku. Porównanie przedstawiono różnice największe Regresje wydajności i ulepszeń, które wystąpiły w jednej sesji profilowania do innego.  
  
 Raport Diff przedstawia widok tabeli danych. W tabeli przedstawiono, różnicowej lub zmiana z linii bazowej. To jest obliczana przez określenie różnicy starej wartości, wartość punktu odniesienia i wartość wyniku z nowego analizy.  
  
 Porównywanie danych profilera może bazować na funkcje w kodzie, moduły w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Próg można ustawić do zmniejszenia szumu i odfiltrować wszystkie dane w widoku tabeli wiersze, które nie uległy zmianie o określoną wartość.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok pliku porównania dla projektu w Eksploratorze wydajności  
  
1.  W **Eksplorator wydajności**w obszarze **raporty**, wybierz plik .vsp lub .vsps raport, który chcesz użyć jako wartości linii bazowej do porównania.  
  
2.  Wybierz pliki .vsp lub .vsps raportów, które chcesz porównać.  
  
3.  Kliknij prawym przyciskiem myszy jeden z wybranych plików, a następnie kliknij przycisk **raporty porównaj**.  
  
### <a name="to-compare-values"></a>Do porównywania wartości  
  
1.  Wybierz **raport porównawczy** karta w oknie widoku raportu.  
  
2.  W **tabeli** listy rozwijanej wybierz funkcję lub moduły do porównania.  
  
3.  W **kolumny** listy rozwijanej wybierz wartość, którą chcesz porównać.  
  
4.  (opcjonalnie) Wpisz wartość dla **próg**.  
  
5.  Kliknij przycisk **zastosować**.  
  
### <a name="to-compare-report-files"></a>Porównywanie plików raportów  
  
1.  Na **analizy** menu, wybierz opcję **Porównaj wydajność raportów**.  
  
2.  W **wybierz pliki analizy porównanie** okien, przeglądania i wybierz **plik punktu odniesienia** pliku analizy (.vsp lub .vsps) i **plik do porównania** (.vsp lub .vsps).  
  
3.  Kliknij przycisk **OK**.




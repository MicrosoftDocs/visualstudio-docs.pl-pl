---
title: Zapisywanie i eksportowanie wydajności danych dotyczących narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 22dd181a991c4c2c006335df955ba27dd4d27ce6
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54756414"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Zapisywanie i eksportowanie wydajności danych dotyczących narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak zapisywanie i eksportowanie plików danych dotyczących wydajności.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Jak: Zapisywanie plików danych dotyczących wydajności jako pliki przeanalizowany raport  
 Możesz zapisać filtrowane lub niefiltrowane widoki profilowania pliki danych (Vsp) jako pliki przeanalizowany raport (.vsps). Plik raportu analizy mogą być wyświetlane w oknie Widok raportu i jest znacznie mniejszy niż oryginalny plik Vsp. Jednak nie można zastosować filtr do danych pliku .vsps. Można utworzyć plik przeanalizowany raport z poziomu Eksploratora wydajności bez konieczności otwierania pliku w zintegrowanym środowisku programistycznym (IDE), lub możesz otworzyć i filtrowanie plików Vsp i następnie zapisać wyniki.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać raport analizy wydajności z poziomu Eksploratora wydajności  
  
1.  W obszarze **raporty**, kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz analizować, a następnie kliknij przycisk **Zapisz przeanalizowany**.  
  
2.  W **zapisać dane przeanalizowane** okna dialogowego pole, określ katalog, a następnie wpisz nazwę pliku.  
  
3.  Kliknij przycisk **Zapisz.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać raport analizy wydajności z okna widoku raportu  
  
1.  Otwórz plik profilowania (.vsp) danych w oknie Widok raportu.  
  
2.  (Opcjonalnie) Zastosowanie filtru do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **Zapisz przeanalizowany** na pasku narzędzi okna widoku raportu.  
  
4.  W **zapisać dane przeanalizowane** okna dialogowego pole, określ katalog, a następnie wpisz nazwę pliku.  
  
5.  Kliknij przycisk **Zapisz.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Instrukcje: Narzędzi profilowania eksportowanie raportów. XML lub. Plik CSV  
 Możesz wyeksportować jeden lub więcej widoków raportu z pliku .vsp lub .vsps pliku danych profilowania jako wartość rozdzielany przecinkami lub plik XML. Można filtrować dane w oknie Widok raportu, możesz wyeksportować lub możesz wyeksportować raport widoki całego pliku danych z **Eksplorator wydajności** okna.  
  
> [!NOTE]
>  Można również skopiuj i Wklej wybrane wiersze z okna widoku raportu jako wartości rozdzielane tabulatorami.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Aby eksportować raporty dotyczące wydajności w oknie Eksploratora wydajności  
  
1.  W **Eksplorator wydajności**, wybierz raport, kliknij prawym przyciskiem myszy i wybierz pozycję **wyeksportować**.  
  
     **Eksportowanie raportu** pojawi się okno dialogowe.  
  
2.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
3.  W obszarze **prefiks raportu**, określ prefiks, którego chcesz dodać do nazwy raportu.  
  
4.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
5.  W obszarze **format raportu wyeksportowanych**, wybierz (rozdzielany przecinkami) (*.csv) lub danych XML (\*.xml).  
  
6.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do pliku o nazwie \<prefiksu > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Raporty można eksportować wydajności z okna widoku raportu  
  
1.  Otwórz plik Vsp w oknie Widok raportu.  
  
2.  (Opcjonalnie) Zastosowanie filtru do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **Eksportowanie raportu** na pasku narzędzi okna widoku raportu.  
  
4.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
5.  W obszarze **prefiks raportu**, określ prefiks, którego chcesz dodać do nazwy raportu.  
  
6.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
7.  W obszarze **format raportu wyeksportowanych**, wybierz (rozdzielany przecinkami) (*.csv) lub danych XML (\*.xml).  
  
8.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do pliku o nazwie \<prefiksu > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Analizowanie wydajności danych dotyczących narzędzi](../profiling/analyzing-performance-tools-data.md)   
 [Porównywanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

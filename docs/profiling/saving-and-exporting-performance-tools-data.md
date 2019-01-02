---
title: Zapisywanie i eksportowanie wydajności danych dotyczących narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bb2020ff396eef3dd9dad4c0ed2e2fd015e0fd6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838375"
---
# <a name="save-and-export-performance-tools-data"></a>Zapisywanie i eksportowanie danych dotyczących narzędzi wydajności
W tym artykule opisano, jak zapisywanie i eksportowanie plików danych dotyczących wydajności.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Instrukcje: Zapisywanie plików danych wydajności jako pliki przeanalizowany raport  
 Możesz zapisać filtrowane lub niefiltrowane widoki danych profilowania (. *Vsp*) plików, ile przeanalizowane raportu (. *vsps*) plików. Plik przeanalizowany raport można wyświetlić w oknie Widok raportu i jest znacznie mniejszy niż oryginalny. *vsp* pliku. Jednak nie można zastosować filtr do danych. *vsps* pliku. Można utworzyć plik przeanalizowany raport z poziomu Eksploratora wydajności bez konieczności otwierania pliku w zintegrowanym środowisku programistycznym (IDE) lub możesz otworzyć i filtrowania. *vsp* pliku, a następnie zapisz wyniki.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać raport analizy wydajności z poziomu Eksploratora wydajności  
  
1.  W obszarze **raporty**, kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz analizować, a następnie kliknij przycisk **Zapisz przeanalizowany**.  
  
2.  W **zapisać dane przeanalizowane** okna dialogowego pole, określ katalog, a następnie wpisz nazwę pliku.  
  
3.  Kliknij przycisk **Zapisz.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać raport analizy wydajności z okna widoku raportu  
  
1.  Otwieranie danych profilowania (. *Vsp*) pliku w oknie Widok raportu.  
  
2.  (Opcjonalnie) Zastosowanie filtru do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **Zapisz przeanalizowany** na pasku narzędzi okna widoku raportu.  
  
4.  W **zapisać dane przeanalizowane** okna dialogowego pole, określ katalog, a następnie wpisz nazwę pliku.  
  
5.  Kliknij przycisk **Zapisz.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Instrukcje: Eksportowanie raportów narzędzi profilowania do pliku XML lub CSV  
 Możesz wyeksportować jeden lub więcej widoków raportu z. *vsp* pliku lub. *vsps* profilowania plik danych jako rozdzielany przecinkami lub plik XML. Można filtrować dane w oknie Widok raportu, możesz wyeksportować lub możesz wyeksportować raport widoki całego pliku danych z **Eksplorator wydajności** okna.  
  
> [!NOTE]
>  Można również skopiuj i Wklej wybrane wiersze z okna widoku raportu jako wartości rozdzielane tabulatorami.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Aby eksportować raporty dotyczące wydajności w oknie Eksploratora wydajności  
  
1.  W **Eksplorator wydajności**, wybierz raport, kliknij prawym przyciskiem myszy i wybierz pozycję **wyeksportować**.  
  
     **Eksportowanie raportu** pojawi się okno dialogowe.  
  
2.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
3.  W obszarze **prefiks raportu**, określ prefiks, którego chcesz dodać do nazwy raportu.  
  
4.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
5.  W obszarze **format raportu wyeksportowanych**, wybierz (rozdzielany przecinkami) (\*CSV\), lub danych XML (\*.xml\).  
  
6.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do pliku o nazwie \<prefiksu > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Raporty można eksportować wydajności z okna widoku raportu  
  
1.  Otwórz. *vsp* pliku w oknie Widok raportu.  
  
2.  (Opcjonalnie) Zastosowanie filtru do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **Eksportowanie raportu** na pasku narzędzi okna widoku raportu.  
  
4.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
5.  W obszarze **prefiks raportu**, określ prefiks, którego chcesz dodać do nazwy raportu.  
  
6.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
7.  W obszarze **format raportu wyeksportowanych**, wybierz (rozdzielany przecinkami) (\*CSV), lub danych XML (\*.xml).  
  
8.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do pliku o nazwie \<prefiksu > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
## <a name="see-also"></a>Zobacz także  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Analizowanie danych dotyczących narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)   
 [Porównywanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

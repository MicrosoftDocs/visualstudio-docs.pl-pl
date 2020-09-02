---
title: Zapisywanie i eksportowanie danych narzędzi wydajności | Microsoft Docs
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
ms.openlocfilehash: 3be6d5d732e5cbb2050c68ac8c7db722c3f709f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795238"
---
# <a name="saving-and-exporting-performance-tools-data"></a>Zapisywanie i eksportowanie danych dotyczących narzędzi do oceny wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób zapisywania i eksportowania plików danych dotyczących wydajności.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a><a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Instrukcje: zapisywanie plików danych wydajności jako przeanalizowanych plików raportów  
 Można zapisać filtrowane lub niefiltrowanych widoków plików danych profilowania (. vsp) jako plików raportów przeanalizowanych (vsps). Analizowany plik raportu może być wyświetlany w oknie widok raportu i jest znacznie mniejszy niż oryginalny plik. vsp. Nie można jednak zastosować filtru do danych pliku. vsps. Można utworzyć przeanalizowany plik raportu z Eksplorator wydajności bez otwierania pliku w zintegrowanym środowisku programistycznym (IDE) lub można otworzyć i filtrować plik. vsp, a następnie zapisać wyniki.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać raport z przeanalizowanej wydajności z Eksplorator wydajności  
  
1. W obszarze **raporty**kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz analizować, a następnie kliknij pozycję **Zapisz przeanalizowane**.  
  
2. W oknie dialogowym **Zapisz przeanalizowane dane** określ katalog, a następnie wpisz nazwę pliku.  
  
3. Kliknij przycisk **Zapisz.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać raport z przeanalizowanej wydajności z okna widok raportu  
  
1. Otwórz plik profilowania danych (. vsp) w oknie widok raportu.  
  
2. Obowiązkowe Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).  
  
3. Kliknij przycisk **Zapisz przeanalizowane** na pasku narzędzi okna widok raportu.  
  
4. W oknie dialogowym **Zapisz przeanalizowane dane** określ katalog, a następnie wpisz nazwę pliku.  
  
5. Kliknij przycisk **Zapisz.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Instrukcje: Eksportowanie raportów narzędzia profilowania do programu. XML lub. Plik CSV  
 Jeden lub więcej widoków raportów można wyeksportować z pliku. vsp lub pliku danych profilowania. vsps jako plik rozdzielony przecinkami lub XML. Dane można filtrować w oknie widok raportu przed jego wyeksportowaniem lub można eksportować widoki raportów całego pliku danych z okna **Eksplorator wydajności** .  
  
> [!NOTE]
> Możesz również kopiować i wklejać zaznaczone wiersze z okna widok raportu jako wartości rozdzielane tabulatorami.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Aby wyeksportować raporty dotyczące wydajności z okna Eksplorator wydajności  
  
1. W **Eksplorator wydajności**wybierz raport, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Eksportuj**.  
  
     Zostanie wyświetlone okno dialogowe **Eksportuj raport** .  
  
2. Wybierz widoki raportów, które chcesz wyeksportować.  
  
3. W obszarze **Zgłoś prefiks z**Określ prefiks, który ma zostać dodany do nazwy raportu.  
  
4. W obszarze **wyeksportowana Lokalizacja raportu**określ katalog.  
  
5. W obszarze **Format wyeksportowanego raportu**wybierz pozycję (rozdzielany przecinkami) (*. csv) lub dane XML ( \* XML).  
  
6. Kliknij polecenie **Eksportuj**.  
  
     Każdy widok raportu jest zapisywany w osobnym pliku o nazwie \<prefix> _ \<report view name> .\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Aby wyeksportować raporty dotyczące wydajności z okna widok raportu  
  
1. Otwórz plik VSP w oknie widok raportu.  
  
2. Obowiązkowe Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).  
  
3. Kliknij przycisk **Eksportuj raport** na pasku narzędzi okna widok raportu.  
  
4. Wybierz widoki raportów, które chcesz wyeksportować.  
  
5. W obszarze **Zgłoś prefiks z**Określ prefiks, który ma zostać dodany do nazwy raportu.  
  
6. W obszarze **wyeksportowana Lokalizacja raportu**określ katalog.  
  
7. W obszarze **Format wyeksportowanego raportu**wybierz pozycję (rozdzielany przecinkami) (*. csv) lub dane XML ( \* XML).  
  
8. Kliknij polecenie **Eksportuj**.  
  
     Każdy widok raportu jest zapisywany w osobnym pliku o nazwie \<prefix> _ \<report view name> .\<csv&#124;xml>  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)   
 [Porównywanie plików danych wydajności](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

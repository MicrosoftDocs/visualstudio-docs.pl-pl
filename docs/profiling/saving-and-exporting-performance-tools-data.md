---
title: Zapisywanie i eksportowanie danych narzędzi wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 729dc2e28446420dd2590e132b7ec8a5444fcb9c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773902"
---
# <a name="save-and-export-performance-tools-data"></a>Zapisywanie i eksportowanie danych dotyczących narzędzi wydajności
W tym artykule opisano sposób zapisywania i eksportowania plików danych o wydajności.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Jak: Zapisywanie plików danych o wydajności jako analizowanych plików raportu
 Można zapisywać filtrowane lub niefiltrowane widoki danych profilowania (.* vsp)* plików jako analizowany raport (.* vsps).* Analizowany plik raportu można wyświetlić w oknie widoku Raport i jest znacznie mniejszy niż oryginalny . *vsp.* Nie można jednak zastosować filtru do danych pliku . *vsps.* Analizowany plik raportu można utworzyć z Eksploratora wydajności bez otwierania pliku w zintegrowanym środowisku programistycznym (IDE) lub otworzyć i odfiltrować plik . *vsp,* a następnie zapisać wyniki.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać analizowany raport o wydajności z Eksploratora wydajności

1. W **obszarze Raporty**kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz przeanalizować, a następnie kliknij polecenie Zapisz **analizowane**.

2. W oknie dialogowym **Zapisywanie analizowanych danych** określ katalog, a następnie wpisz nazwę pliku.

3. Kliknij **pozycję Zapisz.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać analizowany raport wydajności z okna widoku raport

1. Otwórz dane profilowania (.* vsp*) w oknie widoku Raport.

2. (Opcjonalnie) Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).

3. Kliknij **pozycję Zapisz analizowane** na pasku narzędzi okna widoku raportu.

4. W oknie dialogowym **Zapisywanie analizowanych danych** określ katalog, a następnie wpisz nazwę pliku.

5. Kliknij **pozycję Zapisz.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Jak: Eksportowanie raportów narzędzi profilowania do pliku xml lub csv
 Można wyeksportować jeden lub więcej widoków raportu z pliku . *vsp* lub plik . *vsps* profilowania pliku danych jako przecinka rozdzielone lub pliku XML. Przed wyeksportowaniem można filtrować dane w oknie Widoku raportu lub eksportować widoki raportu całego pliku danych z okna **Eksploratora wydajności.**

> [!NOTE]
> Można również kopiować i wklejać zaznaczone wiersze z okna widoku Raport jako wartości oddzielone tabulatorami.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Aby wyeksportować raporty o wydajności z okna Eksploratora wydajności

1. W **Eksploratorze wydajności**zaznacz raport, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Eksportuj**.

     Zostanie wyświetlone okno dialogowe **Raport eksportu.**

2. Wybierz widoki raportu, które chcesz wyeksportować.

3. W **obszarze Raport prefiksu z**określ prefiks, który chcesz dodać do nazwy raportu.

4. W obszarze **Wyeksportowana lokalizacja raportu**określ katalog.

5. W obszarze **Wyeksportowany format raportu**wybierz\*(rozdzielony przecinek) ( .csv\)lub XML Data (\*.xml\).

6. Kliknij polecenie **Eksportuj**.

     Każdy widok raportu jest zapisywany w \<osobnym pliku\<o nazwie prefiks>_ nazwę widoku raportu>. \<> csv&#124;xml

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Aby wyeksportować raporty wydajności z okna widoku raport

1. Otwórz plik . *vsp* w oknie widoku raport.

2. (Opcjonalnie) Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).

3. Kliknij **pozycję Raport eksportu** na pasku narzędzi okna widoku raportu.

4. Wybierz widoki raportu, które chcesz wyeksportować.

5. W **obszarze Raport prefiksu z**określ prefiks, który chcesz dodać do nazwy raportu.

6. W obszarze **Wyeksportowana lokalizacja raportu**określ katalog.

7. W obszarze **Wyeksportowany format raportu**wybierz\*(rozdzielone przecinkami) ( csv) lub XML Data (\*.xml).

8. Kliknij polecenie **Eksportuj**.

     Każdy widok raportu jest zapisywany w \<osobnym pliku\<o nazwie prefiks>_ nazwę widoku raportu>. \<> csv&#124;xml

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [Porównywanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

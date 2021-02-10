---
title: Zapisywanie i eksportowanie danych narzędzi wydajności | Microsoft Docs
description: Dowiedz się, jak zapisywać filtrowane lub niefiltrowane widoki plików danych profilowania (. vsp) jako pliki raportów przeanalizowanych (vsps).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fa43d324f23958c9dc9b72447527ecd035e99c53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950107"
---
# <a name="save-and-export-performance-tools-data"></a>Zapisywanie i eksportowanie danych dotyczących narzędzi wydajności
W tym artykule opisano sposób zapisywania i eksportowania plików danych dotyczących wydajności.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Instrukcje: zapisywanie plików danych wydajności jako przeanalizowanych plików raportów
 Możesz zapisywać filtrowane lub niefiltrowane widoki danych profilowania (.*VSP*) pliki zgodnie z przeanalizowanym raportem (.*vsps*). Analizowany plik raportu może być wyświetlany w oknie widok raportu i jest znacznie mniejszy niż oryginał. plik *VSP* . Nie można jednak zastosować filtru do danych. plik *vsps* . Można utworzyć przeanalizowany plik raportu z Eksplorator wydajności bez otwierania pliku w zintegrowanym środowisku programistycznym (IDE) lub można otworzyć i odfiltrować. plik *VSP* , a następnie Zapisz wyniki.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać raport z przeanalizowanej wydajności z Eksplorator wydajności

1. W obszarze **raporty** kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz analizować, a następnie kliknij pozycję **Zapisz przeanalizowane**.

2. W oknie dialogowym **Zapisz przeanalizowane dane** określ katalog, a następnie wpisz nazwę pliku.

3. Kliknij przycisk **Zapisz.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać raport z przeanalizowanej wydajności z okna widok raportu

1. Otwórz dane profilowania (.*VSP*) w oknie widok raportu.

2. Obowiązkowe Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).

3. Kliknij przycisk **Zapisz przeanalizowane** na pasku narzędzi okna widok raportu.

4. W oknie dialogowym **Zapisz przeanalizowane dane** określ katalog, a następnie wpisz nazwę pliku.

5. Kliknij przycisk **Zapisz.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Instrukcje: Eksportowanie raportów narzędzi profilowania do pliku XML lub CSV
 Możesz wyeksportować jeden lub więcej widoków raportu z. plik *VSP* lub. *vsps* plik danych profilowania jako rozdzielany przecinkami lub plik XML. Dane można filtrować w oknie widok raportu przed jego wyeksportowaniem lub można eksportować widoki raportów całego pliku danych z okna **Eksplorator wydajności** .

> [!NOTE]
> Możesz również kopiować i wklejać zaznaczone wiersze z okna widok raportu jako wartości rozdzielane tabulatorami.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Aby wyeksportować raporty dotyczące wydajności z okna Eksplorator wydajności

1. W **Eksplorator wydajności** wybierz raport, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Eksportuj**.

     Zostanie wyświetlone okno dialogowe **Eksportuj raport** .

2. Wybierz widoki raportów, które chcesz wyeksportować.

3. W obszarze **Zgłoś prefiks z** Określ prefiks, który ma zostać dodany do nazwy raportu.

4. W obszarze **wyeksportowana Lokalizacja raportu** określ katalog.

5. W **wyeksportowanym formacie raportu** wybierz (rozdzielany przecinkami) ( \* . csv \) lub XML danych ( \* . xml) \) .

6. Kliknij polecenie **Eksportuj**.

     Każdy widok raportu jest zapisywany w osobnym pliku o nazwie \<prefix> _ \<report view name> .\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Aby wyeksportować raporty dotyczące wydajności z okna widok raportu

1. Otwórz okno. plik *VSP* w oknie widok raportu.

2. Obowiązkowe Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [Filtr widoku raportu wydajności](../profiling/performance-report-view-filter.md).

3. Kliknij przycisk **Eksportuj raport** na pasku narzędzi okna widok raportu.

4. Wybierz widoki raportów, które chcesz wyeksportować.

5. W obszarze **Zgłoś prefiks z** Określ prefiks, który ma zostać dodany do nazwy raportu.

6. W obszarze **wyeksportowana Lokalizacja raportu** określ katalog.

7. W obszarze **wyeksportowany format raportu** wybierz pozycję (rozdzielany przecinkami) ( \* CSV) lub dane XML ( \* XML).

8. Kliknij polecenie **Eksportuj**.

     Każdy widok raportu jest zapisywany w osobnym pliku o nazwie \<prefix> _ \<report view name> .\<csv&#124;xml>

## <a name="see-also"></a>Zobacz też
- [Eksplorator wydajności](../profiling/performance-explorer.md)
- [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)
- [Porównywanie plików danych dotyczących wydajności](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)

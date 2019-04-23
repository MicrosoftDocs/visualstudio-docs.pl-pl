---
title: Filtrowanie widoków raportów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2f06778de19c16df9d6e43108ecf4daba539c06
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084391"
---
# <a name="filter-report-views"></a>Filtrowanie widoków raportu
Filtry można zastosować do pliku danych, aby ograniczyć dane profilowania, który jest wyświetlany w widokach raport dotyczący wydajności i wyeksportowane pliki raportu profilowania. Można ograniczyć raport, aby dane między wartości sygnatur czasowych i umożliwia ograniczenie danych do określonych procesów i wątków. Można zapisać w pliku filtrów i utworzenie filtru na inny plik danych profilowania, importując zapisany filtr.

 Można również ograniczyć raportu do segmentu czasu za pomocą graficznego osi czasu w widoku Podsumowanie. Zobacz [jak: Filtrowanie widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Aby wykluczyć systemu i kod innych firm z raportu, zobacz [jak: Filtrowanie widoków raportu narzędzi profilowania w celu wyświetlania kodu w ramach funkcji Tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedury

#### <a name="to-create-a-profiler-report-filter"></a>Aby utworzyć filtr raportów profilera

1. Jeśli nie zostanie wyświetlone okno Filtr widoku raportów wydajności, kliknij przycisk **Pokaż filtr** na pasku narzędzi w widoku raportu wydajności.

     Filtr widoku raportów wydajności znajduje się tabela. Każdy wiersz w tabeli reprezentuje klauzuli filtru. Możesz dodać dowolną liczbę klauzul do filtru.

2. Dla każdej klauzuli, który chcesz dodać do filtru wybierz lub wprowadź wartości w następujących polach wiersza.

    |Pole|Opis|
    |-----------|-----------------|
    |**I/lub**|Wybierz **i** Jeśli tę klauzulę i dalej klauzula musi mieć wartość true do Dopasuj wynik. Wybierz **lub** , jeśli ta klauzula lub klauzuli dalej może być wartość true, aby dopasować wynik.|
    |**Pole**|Wybierz pole raportu do użycia w klauzuli filtru z wyświetlonej listy pól danych.|
    |**Operator**|Wybierz operator, który określa relację, która ma w klauzuli między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większa niż lub równe|
    |**Wartość**|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Aby utworzyć filtr raportów profilera w widoku raportu znaczniki

1. Wybierz **znaczniki** z **bieżący widok** listy na pasku narzędzi w widoku raportu wydajności.

    Zostanie wyświetlony raport profiler znaczników.

2. Wybierz ETW lub próbkowania, nawet, którą chcesz użyć jako punktu wyjścia raportu.

3. Naciśnij i przytrzymaj klawisz CTRL i kliknij zdarzenie, które chcesz użyć jako punktu końcowego raportu.

4. Kliknij prawym przyciskiem myszy, a następnie kliknij jedną z następujących opcji:

   - **Dodaj filtr znaczników** tworzy klauzul filtru, korzystających z kolumny Oznacz jako pole filtru.

   - **Dodaj filtr sygnatury czasowe** tworzy klauzul filtru, korzystających z jako pole filtru w kolumnie sygnatura czasowa w milisekundach.

     Dwie opcje filtrowania bieżącego pliku danych, w tym samym początkowego i punktu końcowego. Jedną z opcji może być lepiej, jeśli eksportujesz filtru do użycia w innych raportach.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Aby załadować istniejący filtr z pliku

1. Kliknij na pasku narzędzi widoku raportu wydajności **filtru importu**.

     **Załaduj filtr** zostanie wyświetlone okno dialogowe.

2. Określ lokalizację i nazwę pliku filtru (.vspf) można załadować.

#### <a name="to-execute-a-filter"></a>Wykonywanie filtru

- Kliknij na pasku narzędzi widoku raportu wydajności **wykonaj filtr**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Aby zatrzymać filtr, który trwa zbyt długo, można wykonać

- Kliknij na pasku narzędzi widoku raportu wydajności **zatrzymać filtru**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Aby usunąć filtr w widoku raportu

1. Usuń wiersze klauzul filtr widoku raportów wydajności.

2. Kliknij na pasku narzędzi widoku raportu wydajności **wykonaj filtr**.

#### <a name="to-save-a-filter-to-a-file"></a>Aby zapisać filtr do pliku

1. Kliknij na pasku narzędzi widoku raportu wydajności **Eksportuj filtr**.

     **Zapisywanie filtru** zostanie wyświetlone okno dialogowe.

2. Określ lokalizację i nazwę pliku filtru (.vspf) można zapisać.

## <a name="see-also"></a>Zobacz także
- [Dostosowywanie widoków raportów narzędzi do oceny wydajności](../profiling/customizing-performance-tools-report-views.md)
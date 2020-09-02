---
title: Filtrowanie widoków raportów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: acdfe8f96d30ad881d8c9c0f0a9ff48c3353afee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779249"
---
# <a name="filter-report-views"></a>Filtruj widoki raportów
Można zastosować filtry do profilowania plików danych, aby ograniczyć dane profilowania, które są wyświetlane w widokach raportu wydajności i eksportowane do plików raportów. Można ograniczyć raport do danych między wartościami sygnatur czasowych, a dane można ograniczyć do określonych procesów i wątków. Filtry można zapisać do pliku, a następnie utworzyć filtr dla innego pliku danych profilowania, importując zapisany filtr.

 Możesz również ograniczyć raport do segmentu czasu przy użyciu graficznej osi czasu w widoku podsumowania. Zobacz [jak: filtrowanie widoków raportu na podstawie podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Aby wykluczyć system i kod innej firmy z raportu, zobacz [How to: Filter narzędzia profilowania widoki raportów do wyświetlenia tylko mój kod](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedury

#### <a name="to-create-a-profiler-report-filter"></a>Aby utworzyć filtr raportu profilera

1. Jeśli okno filtru wydajności widok raportu nie jest wyświetlane, kliknij przycisk **Pokaż filtr** na pasku narzędzi Widok raportu wydajności.

     Filtr widoku raportu wydajności jest tabelą. Każdy wiersz tabeli reprezentuje klauzulę filtru. Możesz dodać dowolną liczbę klauzul do filtru.

2. Dla każdej klauzuli, która ma zostać dodana do filtru, wybierz lub wprowadź wartości w następujących polach wiersza.

    |Pole|Opis|
    |-----------|-----------------|
    |**I/lub**|Wybierz **i** czy klauzula i klauzula Next muszą mieć obie wartości prawda, aby dopasować wynik. Wybierz **lub** , jeśli ta klauzula lub Następna klauzula może mieć wartość true, aby dopasować wynik.|
    |**Pole**|Wybierz pole raportu, które ma być używane w klauzuli Filter z wyświetlonej listy pól danych.|
    |**Operator**|Wybierz operator, który określa relację, która ma być używana w klauzuli między polem a wartością.<br /><br /> = Równa się<br /><br /> <>  nie równa się<br /><br /> < mniejsze niż<br /><br /> > większe niż<br /><br /> <= mniejsze niż lub równe<br /><br /> >= większe niż lub równe|
    |**Wartość**|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola wyświetlają dostępne wartości dla pola.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Aby utworzyć filtr raportu profilera z widoku raportu znaczników

1. Wybierz pozycję **znaczniki** z listy **bieżący widok** na pasku narzędzi Widok raportu wydajności.

    Zostanie wyświetlony raport profilera znaczników.

2. Wybierz pozycję ETW lub próbkowanie, nawet jeśli chcesz użyć jako punktu początkowego raportu.

3. Naciśnij i przytrzymaj klawisz CTRL, a następnie kliknij zdarzenie, którego chcesz użyć jako punktu końcowego raportu.

4. Kliknij prawym przyciskiem myszy, a następnie kliknij jedną z następujących opcji:

   - **Dodaj filtr dla znaczników** tworzy klauzule filtru, które używają kolumny Oznacz jako pola filtru.

   - **Dodaj filtr dla sygnatur czasowych** tworzy klauzule filtru, które używają sygnatury czasowej w kolumnie w milisekundach jako pola filtru.

     Dwie opcje filtrują bieżący plik danych w tym samym punkcie początkowym i końcowym. Każda opcja może być lepsza w przypadku eksportowania filtru do użycia w innych raportach.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Aby załadować istniejący filtr z pliku

1. Na pasku narzędzi Widok raportu wydajności kliknij przycisk **Importuj filtr**.

     Zostanie wyświetlone okno dialogowe **ładowanie filtru** .

2. Określ lokalizację i nazwę pliku filtru (. vspf) do załadowania.

#### <a name="to-execute-a-filter"></a>Aby wykonać filtr

- Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Wykonaj filtr**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Aby zatrzymać filtr, który trwa zbyt długo

- Na pasku narzędzi Widok raportu wydajności kliknij przycisk **Zatrzymaj filtr**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Aby usunąć filtr w widoku raportu

1. Usuń wiersze klauzul w filtr widoku raportu wydajności.

2. Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Wykonaj filtr**.

#### <a name="to-save-a-filter-to-a-file"></a>Aby zapisać filtr do pliku

1. Na pasku narzędzi Widok raportu wydajności kliknij przycisk **Eksportuj filtr**.

     Zostanie wyświetlone okno dialogowe **Zapisywanie filtru** .

2. Określ lokalizację i nazwę pliku filtru (vspf), który ma zostać zapisany.

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie widoków raportów narzędzi do oceny wydajności](../profiling/customizing-performance-tools-report-views.md)

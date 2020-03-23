---
title: Filtrowanie widoków raportu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779249"
---
# <a name="filter-report-views"></a>Filtruj widoki raportu
Filtry można zastosować do plików danych profilowania, aby ograniczyć dane profilowania wyświetlane w widokach raportu wydajności i eksportowane do plików raportów. Można ograniczyć raport do danych między wartościami sygnatury czasowej i można ograniczyć dane do określonych procesów i wątków. Filtry można zapisać w pliku, a następnie utworzyć filtr na innym pliku danych profilowania, importując zapisany filtr.

 Raport można również ograniczyć do segmentu czasu, korzystając z graficznej osi czasu w widoku podsumowania. Zobacz [Jak: Filtruj widoki raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

 Aby wykluczyć kod systemowy i kod innych firm z raportu, zobacz [Jak: Filtrowanie widoków raportów narzędzi profilowania w celu wyświetlenia tylko mojego kodu](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)

## <a name="procedures"></a>Procedury

#### <a name="to-create-a-profiler-report-filter"></a>Aby utworzyć filtr raportu profilera

1. Jeśli okno Filtr widoku raportu wydajności nie jest wyświetlane, kliknij pozycję **Pokaż filtr** na pasku narzędzi Widok raportu wydajności.

     Filtr widoku raportu wydajności jest tabelą. Każdy wiersz tabeli reprezentuje klauzulę filtru. Do filtru można dodać dowolną liczbę klauzul.

2. Dla każdej klauzuli, którą chcesz dodać do filtru, zaznacz lub wprowadź wartości w następujących polach wiersza.

    |Pole|Opis|
    |-----------|-----------------|
    |**Lub**|Wybierz **i** jeśli ta klauzula i następna klauzula musi być true, aby dopasować wynik. Wybierz **lub** jeśli ta klauzula lub następna klauzula może być spełniony, aby dopasować wynik.|
    |**Pole**|Wybierz pole raportu, które ma być używane w klauzuli filtru, z wyświetlona lista pól danych.|
    |**Operator**|Wybierz operatora, który określa relację, która ma w klauzuli między polem a wartością.<br /><br /> = Równa się<br /><br /> <>  nie równa się<br /><br /> < mniej niż<br /><br /> > większa niż<br /><br /> <= Mniej niż lub Równo<br /><br /> >= większa lub równa|
    |**Wartość**|Wybierz lub wprowadź wartość, która ma być wyszukane. Niektóre pola wyświetlają listę dostępnych wartości pola.|

#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Aby utworzyć filtr raportu profilera z widoku Raport znaczników

1. Wybierz **znaczniki** z listy **Widok bieżący** na pasku narzędzi Widok raportu wydajności.

    Zostanie wyświetlony raport profilera znaczników.

2. Wybierz ETW lub próbkowanie nawet, które chcesz użyć jako punkt wyjścia raportu.

3. Naciśnij i przytrzymaj klawisz CTRL i kliknij zdarzenie, które ma być używane jako punkt końcowy raportu.

4. Kliknij prawym przyciskiem myszy, a następnie kliknij jedną z następujących opcji:

   - **Dodaj filtr na znacznikach** tworzy klauzule filtru, które używają kolumny Oznacz jako pola filtru.

   - **Dodaj filtr na znacznikach czasu** tworzy klauzule filtru, które używają kolumny Sygnatura czasowa w milisekundach jako pola filtru.

     Dwie opcje filtrują bieżący plik danych w tym samym punkcie początkowym i końcowym. Każda z tych opcji może być lepsza, jeśli eksportujesz filtr do użycia w innych raportach.

#### <a name="to-load-an-existing-filter-from-a-file"></a>Aby załadować istniejący filtr z pliku

1. Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Filtr importu**.

     Zostanie wyświetlone okno dialogowe **Filtr obciążenia.**

2. Określ lokalizację i nazwę pliku filtru (.vspf), który ma być załadowany.

#### <a name="to-execute-a-filter"></a>Aby wykonać filtr

- Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Wykonaj filtr**.

#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Aby zatrzymać filtr, który trwa zbyt długo, aby wykonać

- Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Zatrzymaj filtr**.

#### <a name="to-remove-a-filter-on-a-report-view"></a>Aby usunąć filtr w widoku raportu

1. Usuń wiersze klauzul w filtrze widoku raportu wydajności.

2. Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Wykonaj filtr**.

#### <a name="to-save-a-filter-to-a-file"></a>Aby zapisać filtr w pliku

1. Na pasku narzędzi Widok raportu wydajności kliknij pozycję **Filtr eksportu**.

     Zostanie wyświetlone okno dialogowe **Zapisz filtr.**

2. Określ lokalizację i nazwę pliku filtru (vspf) do zapisania.

## <a name="see-also"></a>Zobacz też
- [Dostosowywanie widoków raportów narzędzi do oceny wydajności](../profiling/customizing-performance-tools-report-views.md)

---
title: Analizowanie użycia pamięci dla obiektów .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898470"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analizowanie użycia pamięci za pomocą narzędzia do alokacji obiektów platformy .NET

Możesz sprawdzić, ile pamięci używanej przez aplikację i jakie ścieżki kodu przydzielają najwięcej pamięci za pomocą narzędzia alokacji obiektów platformy .NET.

Po uruchomieniu narzędzia można zobaczyć ścieżki wykonywania funkcji, w których obiekty są przyłączone, aby można było śledzić z powrotem do poziomu głównego drzewa wywołań, który zajmuje najwięcej ilości pamięci.

## <a name="setup"></a>Konfiguracja

1. Otwórz Profiler wydajności (**ALT + F2)** w programie Visual Studio.
2.  Zaznacz pole wyboru **śledzenie alokacji obiektów platformy .NET** .

![Centrum diag](../profiling/media/diaghub.png "Centrum diag")

> [!NOTE]
> Projekt startowy jest domyślnie wybrany jako **docelowy analiz** , ale można go zmienić na uruchomiony proces, pliki wykonywalne, uruchomione aplikacje i zainstalowane aplikacje, otwierając menu rozwijane **Zmień docelowy** , a następnie wybierając z dostępnych opcji.

   Narzędzie alokacji obiektów platformy .NET aktualnie nie obsługuje plików wykonywalnych za pośrednictwem menu rozwijanego. Musisz przejść przez system projektu exe, aby użyć narzędzia. Aby to zrobić, Zamknij bieżące rozwiązanie (**plik** -> **zamknąć rozwiązanie**), a następnie naciśnij pozycję **plik** -> **otworzyć projekt lub rozwiązanie** — > Wybierz plik. exe.

![Cel analizy](../profiling/media/analysistarget.png "Cel analizy")

3. Kliknij przycisk **Uruchom** , aby uruchomić narzędzie.

![Zatrzymaj zbieranie](../profiling/media/stopcollection.png "Zatrzymaj zbieranie")

4. Po uruchomieniu narzędzia Przejdź przez żądany scenariusz w aplikacji, a następnie naciśnij przycisk **Zatrzymaj zbieranie** lub Zamknij aplikację, aby wyświetlić dane.
5. Kliknij kartę **alokacja** i zobacz obraz podobny do przedstawionego poniżej.

![Dział](../profiling/media/allocation.png "Alokacja")

Gratulacje! Teraz można analizować alokację pamięci obiektów.

## <a name="understand-your-data"></a>Zrozumienie danych

### <a name="collection"></a>Kolekcja

![Kolekcja](../profiling/media/collection.png "Kolekcja")

Widok kolekcji pozwala sprawdzić, ile obiektów zostało zebranych podczas wyrzucania elementów bezużytecznych i ile z nich zostało zachowane. Ten widok udostępnia również kilka wykresów kołowych do wizualizacji zebranych i nieprzemieszczonych obiektów według typu.

- **Zebrana** kolumna pokazuje liczbę obiektów zebranych przez moduł zbierający elementy bezużyteczne.
- Kolumna **Przeżyjed** pokazuje liczbę obiektów, które przeżyły po uruchomieniu modułu wyrzucania elementów bezużytecznych.

### <a name="allocation"></a>Alokacja

![Alokacja rozszerzona](../profiling/media/allocationexpanded.png "Alokacja rozszerzona")

Widok alokacja umożliwia wyświetlenie lokalizacji obiektów, które są przydzielane do pamięci, i ilości pamięci przydzielanej przez te obiekty.

- Kolumna **name** jest listą różnych klas i struktur, które zajmują pamięć. Każdy element w kolumnie jest węzłem, który można rozszerzyć, jeśli istnieją elementy należące do tej kategorii. (Tylko widok**alokacji** )
- Kolumna **całkowita (alokacje)** przedstawia liczbę obiektów w ramach określonego typu alokacji, które zajmują pamięć. (**Alokacja**, **drzewo wywołań**i widok **funkcji** )
- Kolumna **własne (alokacje)** pokazuje liczbę obiektów w ramach pojedynczego elementu, który zajmuje pamięć. (**Alokacja**, **drzewo wywołań**i widok **funkcji** )
- Wszystkie trzy z tych kolumn są sortowane. W przypadku kolumny **name** elementy są sortowane alfabetycznie (do przodu lub do tyłu). W przypadku **łącznego** i **samodzielnego (przydziałów)** można sortować liczbowe (w coraz większym stopniu lub malejąco).
- Kolumny **łączny rozmiar (w bajtach)** i **własne rozmiary (bajty)** nie są domyślnie włączone. Aby je włączyć, kliknij prawym przyciskiem myszy **nazwę**, **całkowitą** lub samodzielną **(alokacje)** kolumny, a następnie kliknij pozycję **łączny rozmiar** i opcje **samodzielnego rozmiaru** , aby dodać je do wykresu. Dwie kolumny są podobne do **sum (alokacji)** i **samodzielnych (alokacji)** , z wyjątkiem tego, że zamiast wyświetlania liczby obiektów, które zajmują pamięć, pokazują łączną ilość pamięci w bajtach, jaką te obiekty zajmują. [Tylko Widok alokacji]

### <a name="call-tree"></a>Drzewo wywołań

![Drzewo wywołań](../profiling/media/calltree.png "Drzewo wywołań")

Widok **drzewa wywołań** pozwala zobaczyć ścieżki wykonywania funkcji, które zawierają obiekty przydzielające dużą ilość pamięci.

- Kolumna **nazwa funkcji** zawiera proces lub nazwę funkcji zawierającej obiekty przydzielające pamięć na podstawie poziomu przeglądanego węzła.
- Kolumny **łączne** i samodzielne **(alokacje)** zawierają te same informacje, co widok **alokacji** .
- Kolumna **Nazwa modułu** zawiera moduł, który zawiera funkcję lub proces wywołujący.

![Ścieżka gorąca](../profiling/media/hotpath.png "Ścieżka gorąca")

- Przycisk **Rozwiń ścieżkę gorącą** wyróżnia ścieżki wykonywania funkcji, która zawiera wiele obiektów przydzielających pamięć. Algorytm jest uruchamiany w wybranym przez użytkownika węźle zainteresowania i wyróżnia ścieżkę większości przydziałów, a użytkownik w trakcie badania.
- Przycisk **Pokaż ścieżkę gorącą** włącza lub wyłącza ikony płomienia wskazujących, który węzeł jest częścią **ścieżki aktywnej**.

### <a name="functions"></a>Funkcje

![Funkcje](../profiling/media/functions.png "Funkcje")

Widok **funkcji** zawiera procesy, moduły i funkcje, które są przydzielane pamięci.

- Kolumna **name** zawiera procesy jako węzły najwyższego poziomu. Poniżej procesów są moduły, a w obszarze moduły są funkcjami.
- Kolumny **łączne** i samodzielne **(alokacje)** zawierają te same informacje, co widok **alokacji** .

Widok **Alokacje**, **drzewo wywołań**i **funkcje** wszystkie zawierają opcje **Pokaż tylko mój kod**, **Pokaż kod natywny**i **wyszukiwania** :

![Pasek filtru](../profiling/media/filterbar.png "Pasek filtru")

- **Pokaż tylko mój kod** zwija systemy, struktury i inny kod niebędący użytkownikiem oraz ramki **[kod zewnętrzny]** , aby można było skupić się na kodzie użytkownika. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu użytkownika przy użyciu tylko mój kod](../debugger/just-my-code.md).
- **Pokaż kod natywny** pokazuje kod natywny w elemencie docelowym analizy, w tym kod niebędący użytkownikiem, jeśli został wybrany.
- **Pole filtr** umożliwia filtrowanie w dół kolumny **Nazwa** lub **nazwa funkcji** na podstawie parametru, który jest udostępniany. Po prostu wpisz w polu, a tabela powinna filtrować w dół, aby wyświetlić tylko typy, które zawierają podany ciąg.

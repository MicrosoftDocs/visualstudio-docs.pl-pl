---
title: Analizowanie użycia pamięci dla obiektów .NET | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898470"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analizowanie użycia pamięci za pomocą narzędzia Alokacja obiektów .NET

Możesz zobaczyć, ile pamięci używa aplikacja i jakie ścieżki kodu przydzielić najwięcej pamięci za pomocą narzędzia .NET alokacji obiektów.

Po uruchomieniu narzędzia, można zobaczyć ścieżki wykonywania funkcji, gdzie obiekty są przydzielane, dzięki czemu można prześledzić z powrotem do katalogu głównego drzewa wywołań, który zajmuje najwięcej pamięci.

## <a name="setup"></a>Konfiguracja

1. Otwórz program Profileer wydajności **(Alt + F2)** w programie Visual Studio.
2.  Zaznacz pole wyboru **Śledzenie alokacji obiektów .NET.**

![Piasta Diag](../profiling/media/diaghub.png "Piasta Diag")

> [!NOTE]
> Projekt startowy jest domyślnie wybierany jako **obiekt docelowy analizy,** ale można go zmienić na uruchomiony proces, pliki wykonywalne, uruchomione aplikacje i zainstalowane aplikacje, otwierając menu rozwijane **Zmień miejsce docelowe,** a następnie wybierając z dostępnych opcji.

   Narzędzie .NET Object Allocation nie obsługuje obecnie plików wykonywalnych za pośrednictwem menu rozwijanego. Aby skorzystać z narzędzia, musisz przejść przez system projektu exe. Aby to zrobić, zamknij bieżące rozwiązanie **(Rozwiązanie zamknięcia****pliku),** -> a następnie naciśnij **pozycję Otwórz plik** -> **projektu lub rozwiązania** - > wybierz plik .exe.

![Cel analizy](../profiling/media/analysistarget.png "Cel analizy")

3. Kliknij przycisk **Start,** aby uruchomić narzędzie.

![Zatrzymaj kolekcję](../profiling/media/stopcollection.png "Zatrzymaj kolekcję")

4. Po uruchomieniu narzędzia przejdź przez żądany scenariusz w aplikacji, a następnie naciśnij **przycisk Zatrzymaj zbieranie** lub zamknij aplikację, aby wyświetlić dane.
5. Kliknij kartę **Alokacja,** a zobaczysz obraz podobny do pokazanego poniżej.

![Alokacja](../profiling/media/allocation.png "Alokacja")

Gratulacje! Teraz można analizować alokację pamięci obiektów.

## <a name="understand-your-data"></a>Poznaj swoje dane

### <a name="collection"></a>Collection

![Kolekcja](../profiling/media/collection.png "Collection")

Widok kolekcji pozwala zobaczyć, ile obiektów zostały zebrane podczas wyrzucania elementów bezużytecznych i ile zostały zachowane. Ten widok zawiera również kilka wykresów kołowych do wizualizacji zebranych i zachowanych obiektów według typu.

- **Collected** Kolumna pokazuje liczbę obiektów, które moduł zbierający elementy bezużyteczne zebrane.
- **Survived** Kolumna pokazuje liczbę obiektów, które przetrwały po odśmiecania elementów bezużytecznych został uruchomiony.

### <a name="allocation"></a>Alokacja

![Alokacja rozszerzona](../profiling/media/allocationexpanded.png "Alokacja rozszerzona")

Widok alokacji umożliwia wyświetlenie lokalizacji obiektów, które przydzielają pamięć i ile pamięci te obiekty są przydzielane.

- **Name** kolumna jest lista różnych klas i struktur, które zajmują pamięci. Każdy element w kolumnie jest węzłem, który można rozwinąć, jeśli istnieją elementy w tej kategorii zajmujące pamięć. (Tylko widok**alokacji)**
- **Kolumna Całkowita (alokacje)** pokazuje liczbę obiektów w ramach określonego typu alokacji, które zajmują pamięć. **(Alokacja,** **Drzewo wywołań**i Widok **funkcji)**
- **Self (Alokacje)** Kolumna pokazuje liczbę obiektów w obrębie pojedynczego elementu, który zajmuje pamięć. **(Alokacja,** **Drzewo wywołań**i Widok **funkcji)**
- Wszystkie trzy z tych kolumn można sortować. W przypadku kolumny **Nazwa** elementy są sortowane alfabetycznie (do przodu lub do tyłu). W przypadku **sumy** i **jaźni (alokacje)** można sortować numerycznie (coraz częściej lub malejąco).
- Kolumny **Całkowity rozmiar (bajty)** i **Rozmiar własny (bajty)** domyślnie nie są włączone. Aby je włączyć, kliknij prawym przyciskiem myszy kolumny **Nazwa**, **Suma** lub **Jaźń (Alokacje),** a następnie kliknij polecenie **Całkowity rozmiar** i **Rozmiar własny,** aby dodać je do wykresu. Dwie kolumny są podobne do **Sum (Alokacje)** i **Self (Alokacje),** z tą różnicą, że zamiast pokazywać liczbę obiektów zajmujących pamięć, pokazują całkowitą ilość pamięci w bajtach, które te obiekty zajmują. [Tylko widok alokacji]

### <a name="call-tree"></a>Drzewo połączeń

![Drzewo połączeń](../profiling/media/calltree.png "Drzewo połączeń")

Widok **drzewa wywołań** umożliwia wyświetlenie ścieżek wykonywania funkcji, które zawierają obiekty przydzielające dużo pamięci.

- **Kolumna Nazwa funkcji** zawiera proces lub nazwę funkcji zawierającej obiekty przydzielające pamięć na podstawie poziomu sprawdzanego węzła.
- Kolumny **Suma** i **Jaźń (Alokacje)** mają te same informacje co widok **Alokacja.**
- Kolumna **Nazwa modułu** zawiera moduł, który zawiera funkcję lub proces, który wywołuje.

![Gorąca ścieżka](../profiling/media/hotpath.png "Gorąca ścieżka")

- Przycisk **Rozwiń ścieżkę gorącą** wyróżnia ścieżkę wykonywania funkcji, która zawiera wiele obiektów, które przydzielają pamięć. Algorytm rozpoczyna się od wybranego przez użytkownika węzła zainteresowania i wyróżnia ścieżkę większości alokacji, prowadząc użytkownika w ich badaniu.
- Przycisk **Pokaż gorącą ścieżkę** włącza lub wyłącza ikony płomienia wskazujące, który węzeł jest częścią **ścieżki gorącej**.

### <a name="functions"></a>Funkcje

![Funkcje](../profiling/media/functions.png "Funkcje")

Widok **Funkcje** pokazuje procesy, moduły i funkcje, które przydzielają pamięć.

- **Kolumna Nazwa** pokazuje procesy jako węzły najwyższego poziomu. Pod procesami są moduły, a w modułach są funkcje.
- Kolumny **Suma** i **Jaźń (Alokacje)** mają te same informacje co widok **Alokacja.**

Wszystkie widoki **Alokacje,** **Drzewo wywołań**i **Funkcje** zawierają opcje **Pokaż tylko mój kod,** Pokaż kod **macierzysty**i **Wyszukaj:**

![Pasek filtra](../profiling/media/filterbar.png "Pasek filtra")

- **Pokaż tylko mój kod** zwija systemy, struktury i inny kod niebędący użytkownikiem i do ramek **[Kod zewnętrzny],** dzięki czemu kod użytkownika może być skoncentrowany na. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu użytkownika za pomocą tylko mój kod](../debugger/just-my-code.md).
- **Pokaż kod macierzysty** pokazuje kod macierzysty w ramach obiektu docelowego analizy, w tym kod niebędący użytkownikiem, jeśli jest zaznaczony.
- **Pole Filtr** umożliwia filtrowanie kolumny **Nazwa** lub **Nazwa funkcji** na podstawie podawania parametru. Wystarczy wpisać w polu, a tabela powinna filtrować w dół, aby wyświetlić tylko typy, które zawierają dostarczony ciąg.

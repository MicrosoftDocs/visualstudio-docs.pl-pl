---
title: Analizowanie użycia pamięci dla obiektów .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 563531b6dfbf59e33b63dcb4561612d86cd39acc
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970235"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analizowanie użycia pamięci za pomocą narzędzia alokacji obiektów platformy .NET

Możesz sprawdzić ilość pamięci używanej przez aplikację i informacje o ścieżce kodu przydzielające najwięcej pamięci za pomocą narzędzia alokacji obiektów platformy .NET.

Po uruchomieniu narzędzia można zobaczyć ścieżki wykonywania funkcji, w których są przyliczane obiekty. Następnie można śledzić z powrotem do poziomu głównego drzewa wywołań, który zajmuje najwięcej pamięci.

## <a name="setup"></a>Konfigurowanie

1. Wybierz **kombinację klawiszy Alt + F2** , aby otworzyć Profiler wydajności w programie Visual Studio.

1. Zaznacz pole wyboru **śledzenie alokacji obiektów platformy .NET** .

   ![Wybrane narzędzie do śledzenia alokacji obiektów dotnet](../profiling/media/dotnetalloctoolselected.png "Wybrane narzędzie do śledzenia alokacji obiektów dotnet")

1. Wybierz przycisk **Start** , aby uruchomić narzędzie.

1. Po uruchomieniu narzędzia Przejdź do scenariusza, który chcesz profilować w aplikacji. Następnie wybierz pozycję **Zatrzymaj zbieranie** lub Zamknij aplikację, aby zobaczyć swoje dane.

   ![Okno pokazujące Zatrzymaj zbieranie](../profiling/media/stopcollectionlighttheme.png "Okno pokazujące Zatrzymaj zbieranie")

1. Wybierz kartę **alokacja** . Zostanie wyświetlona zawartość okna podobna do poniższego zrzutu ekranu.

   ![Karta alokacja](../profiling/media/allocationview.png "Karta alokacja")

Teraz można analizować alokację pamięci obiektów.

Podczas zbierania Narzędzie śledzenia może spowolnić profilowaną aplikację. Jeśli wydajność narzędzia śledzenia lub aplikacji jest powolna i jeśli nie musisz śledzić każdego obiektu, możesz dostosować częstotliwość próbkowania. Aby to zrobić, wybierz symbol koła zębatego obok narzędzia śledzenia na stronie podsumowania profilera.

![Ustawienia dla narzędzia do alokacji dotnet](../profiling/media/dotnetallocsettings.png "Ustawienia dla narzędzia do alokacji dotnet")

Dostosuj częstotliwość próbkowania do pożądanej szybkości. Ta zmiana ułatwia przyspieszenie wydajności aplikacji podczas zbierania i analizowania danych.

![Skorygowana częstotliwość próbkowania](../profiling/media/adjustedsamplingratedotnetalloctool.png "Skorygowana częstotliwość próbkowania")

Aby uzyskać więcej informacji na temat zwiększania wydajności narzędzia, zobacz [Optymalizacja ustawień profilera](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Zrozumienie danych

![Wykres dla narzędzia do alokacji dotnet](../profiling/media/graphdotnetalloc.png "Wykres dla narzędzia do alokacji dotnet")

W poprzednim widoku graficznym na górnym wykresie przedstawiono liczbę aktywnych obiektów w aplikacji. Wykres Delta dolnego **obiektu** przedstawia wartość procentową zmiany obiektów aplikacji. Czerwone słupki oznaczają, gdy wystąpiło wyrzucanie elementów bezużytecznych.

![Filtrowany wykres czasu alokacji dotnet](../profiling/media/graphdotnetalloctimefiltered.png "Filtrowany wykres czasu alokacji dotnet")

Można filtrować dane tabelaryczne w celu wyświetlenia działania tylko dla określonego zakresu czasu. Możesz również powiększyć lub pomniejszyć wykres.

### <a name="allocation"></a>Alokacja

![Widok alokacja rozwinięty](../profiling/media/allocationexpandedlight.png "Widok alokacja rozwinięty")

Widok **alokacja** przedstawia lokalizację obiektów, które przydzielają pamięć i ilość pamięci przydzielanej przez te obiekty.

- Kolumna **Type** jest listą klas i struktur, które zajmują pamięć. Kliknij dwukrotnie typ, aby wyświetlić jego śledzenie jako odwrócone drzewo wywołań. W widoku **alokacji** można zobaczyć elementy należące do wybranej kategorii, które zajmują pamięć.

- Kolumna **Alokacje** zawiera liczbę obiektów, które zajmują pamięć w ramach określonego typu alokacji lub funkcji. Ta kolumna pojawia się tylko w widokach **alokacja**, **drzewo wywołań** i **funkcje** .

- Kolumny **bajtów** i **średni rozmiar (w bajtach)** nie są wyświetlane domyślnie. Aby je wyświetlić, kliknij prawym przyciskiem myszy kolumnę **Typ** lub **Alokacje** , a następnie wybierz opcje **bajty** i **średni rozmiar (bajty)** , aby dodać je do wykresu. 

   Dwie kolumny są podobne do **sum (alokacji)** i **samodzielnych (alokacji)**, z tą różnicą, że pokazują ilość zajętej pamięci zamiast liczby obiektów zużywających pamięć. Te kolumny są wyświetlane tylko w widoku **alokacja** .

- Kolumna **Nazwa modułu** zawiera moduł, który zawiera funkcję lub proces wywołujący.

Wszystkie te kolumny są sortowane. W przypadku kolumn **typu** i **nazwy modułu** można sortować elementy alfabetycznie w kolejności rosnącej lub malejącej. W przypadku **alokacji**, **bajtów** i **średniego rozmiaru (w bajtach)** można sortować elementy przez zwiększenie lub zmniejszenie wartości liczbowej.

#### <a name="symbols"></a>Symbole

Następujące symbole są wyświetlane w kartach **alokacja**, **drzewo wywołań** i **funkcje** :

- ![Symbol typu wartości](../profiling/media/valuetypeicon.png "Symbol typu wartości") — typ wartości, na przykład liczba całkowita.

- ![Symbol kolekcji wartości typu](../profiling/media/valuetypecollectionicon.png "Symbol kolekcji wartości typu") — Kolekcja wartości typu, taka jak tablica liczb całkowitych

- ![Symbol typu odwołania](../profiling/media/referencetypeicon.png "Symbol typu odwołania") — typ referencyjny, taki jak ciąg

- ![Symbol kolekcji typu odwołania](../profiling/media/referencetypecollectionicon.png "Symbol kolekcji typu odwołania") — Kolekcja typu odwołania, taka jak tablica ciągów

### <a name="call-tree"></a>Drzewo wywołań

![Widok drzewa wywołań](../profiling/media/calltreelight.png "Widok drzewa wywołań")

Widok **drzewa wywołań** przedstawia ścieżki wykonywania funkcji, które zawierają obiekty przydzielenia dużo pamięci.

- Kolumna **nazwa funkcji** zawiera proces lub nazwę funkcji zawierającej obiekty, które przydzielą pamięć. Ekran jest oparty na poziomie przeglądanego węzła.
- Kolumny **Suma (alokacja)** i **całkowity rozmiar (w bajtach)** zawierają liczbę przydzielonych obiektów i ilość pamięci używanej przez funkcję oraz wszystkie inne funkcje, które wywołuje.
- Kolumny **własne (alokacje)** i **własne rozmiary (bajty)** zawierają liczbę przydzielonych obiektów i ilość pamięci używanej przez pojedynczą wybraną funkcję lub typ alokacji.
- Kolumna **średni rozmiar (w bajtach)** zawiera te same informacje, które są wyświetlane w widoku **Alokacje** .
- Kolumna **Nazwa modułu** zawiera moduł, który zawiera funkcję lub proces wywołujący.

   ![Rozszerzona ścieżka gorąca](../profiling/media/hotpathlight.png "Rozszerzona ścieżka gorąca")

- Przycisk **Rozwiń ścieżkę gorącą** powoduje wyróżnienie ścieżki wykonywania funkcji, która zawiera wiele obiektów przydzielających pamięć. Algorytm jest uruchamiany w węźle, który wybierzesz i podświetla ścieżkę najbardziej przydziałów.
- Przycisk **Pokaż ścieżkę gorącą** pokazuje lub ukrywa symbole płomienia wskazujące, które węzły są częścią ścieżki aktywnej.

### <a name="functions"></a>Funkcje

![Widok funkcji](../profiling/media/functionslight.png "Widok funkcji")

Widok **funkcji** zawiera procesy, moduły i funkcje, które są przydzielane pamięci.

- Kolumna **name** zawiera procesy jako węzły najwyższego poziomu. Procesy poniżej są modułami, a poniżej moduły są funkcjami.
- Te kolumny zawierają te same informacje, co w widokach drzewa **alokacji** i **wywołań** :

  - **Suma (przydziały)**
  - **Własne (alokacje)**
  - **Łączny rozmiar (w bajtach)**
  - **Własny rozmiar (w bajtach)**
  - **Średni rozmiar (w bajtach)**

### <a name="collection"></a>Kolekcja

![Widok kolekcji](../profiling/media/collectionlight.png "Widok kolekcji")

Widok **kolekcji** pokazuje, ile obiektów zostało zebranych lub zachowanych podczas wyrzucania elementów bezużytecznych. Ten widok przedstawia także wykresy kołowe do wizualizacji zebranych i nieprzestawionych obiektów według typu.

- **Zebrana** kolumna pokazuje liczbę obiektów zebranych przez moduł zbierający elementy bezużyteczne.
- Kolumna **Przeżyjed** pokazuje liczbę obiektów, które przeżyły po uruchomieniu modułu wyrzucania elementów bezużytecznych.

### <a name="filtering-tools"></a>Narzędzia filtrowania

Widok **Alokacje**, **drzewo wywołań** i **funkcje** wszystkie zawierają opcje **Pokaż tylko mój kod** i **Pokaż kod natywny** oraz pole filtru.

- **Pokaż tylko mój kod** zwija systemy, struktury i inny kod niebędący użytkownikiem do ramek **[kod zewnętrzny]** , dzięki czemu możesz skupić się na tylko kodzie. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu użytkownika przy użyciu tylko mój kod](../debugger/just-my-code.md).
- **Pokaż kod natywny** pokazuje kod natywny w elemencie docelowym analizy i może zawierać kod niebędący użytkownikiem.
- Za pomocą pola filtru można filtrować w dół kolumnę **Nazwa** lub **nazwa funkcji** na podstawie podanych wartości. W polu Wprowadź wartość ciągu. W tabeli są wyświetlane tylko typy zawierające ten ciąg.

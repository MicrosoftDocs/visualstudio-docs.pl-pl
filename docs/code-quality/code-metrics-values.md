---
title: Oblicz metryki kodu
ms.date: 11/02/2018
description: Dowiedz się więcej na temat złożoności cyklomatyczna, sprzęgania klas i innych metryk kodu programu Visual Studio. Zobacz, jak metryki mogą śledzić postęp opracowywania i identyfikować zagrożenia.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.codemetrics.toolwindow
dev_langs:
- CSharp
- VB
- FSharp
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5e7ee628f5a48f573afed9753f4fad17f85e33a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348648"
---
# <a name="code-metrics-values"></a>Wartości metryk kodu

Zwiększona złożoność nowoczesnych aplikacji oprogramowania również zwiększa trudność, aby kod był niezawodny i konserwowany. Metryki kodu są zestawem miar oprogramowania, które zapewniają deweloperom lepszy wgląd w kod, który opracowuje. Dzięki wykorzystaniu metryk kodu deweloperzy mogą zrozumieć, które typy i/lub metody powinny być odwiedzane lub dokładniej przetestowane. Zespoły programistyczne mogą identyfikować potencjalne zagrożenia, zrozumieć bieżący stan projektu i śledzić postęp podczas opracowywania oprogramowania.

Deweloperzy mogą używać programu Visual Studio do generowania danych metryk kodu, które mierzą złożoność i łatwość utrzymania kodu zarządzanego. Dane metryk kodu mogą być generowane dla całego rozwiązania lub pojedynczego projektu.

Aby uzyskać informacje o sposobach generowania danych metryk kodu w programie Visual Studio, zobacz [How to: Generate Code Metric Data](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Pomiary oprogramowania

Na poniższej liście przedstawiono wyniki metryki kodu, które program Visual Studio oblicza:

- **Indeks utrzymania** — oblicza wartość indeksu z przedziału od 0 do 100, która reprezentuje względną łatwość utrzymywania kodu. Wysoka wartość to lepsza łatwość utrzymania. Klasyfikacje kodowane kolorami mogą szybko identyfikować problemy w kodzie. Zielona Ocena wynosi od 20 do 100 i wskazuje, że kod ma dobrą łatwość utrzymania. Żółta Klasyfikacja ma wartość z zakresu od 10 do 19 i wskazuje, że kod jest umiarkowanie konserwowany. Czerwona Ocena jest klasyfikacją od 0 do 9 i wskazuje na niską łatwość utrzymania. Aby uzyskać więcej informacji, zobacz wpis w blogu [zakres i znaczenie indeksu łatwość utrzymania](/archive/blogs/codeanalysis/maintainability-index-range-and-meaning) .

- **Złożoność cyklomatyczna** — mierzy strukturalną złożoność kodu. Jest on tworzony przez obliczenie liczby różnych ścieżek kodu w przepływie programu. Program, który ma złożony przepływ sterowania, wymaga więcej testów do osiągnięcia dobrego pokrycia kodu i jest mniej utrzymany. Aby uzyskać więcej informacji, zobacz [wpis Wikipedia dotyczący złożoności cyklomatyczna](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Głębokość dziedziczenia** — wskazuje liczbę różnych klas, które dziedziczą od siebie nawzajem, z powrotem do klasy bazowej. Głębokość dziedziczenia jest podobna do sprzęgu klasy w przypadku, gdy zmiana klasy bazowej może mieć wpływ na wszystkie klasy dziedziczone. Im wyższy numer, tym lepiej dziedziczą i wyższy potencjał dla modyfikacji klasy podstawowej, aby spowodować powstanie istotnej zmiany. Aby uzyskać głębokość dziedziczenia, niska wartość jest dobra, a wysoka wartość jest zła.

- **Sprzęganie klas** — mierzy sprzężenie do unikatowych klas za pomocą parametrów, zmiennych lokalnych, typów zwracanych, wywołań metod, wystąpień ogólnych lub szablonów, klas bazowych, implementacji interfejsu, pól zdefiniowanych w typach zewnętrznych i dekoracji atrybutu. Dobre projektowanie oprogramowania oznacza, że typy i metody powinny mieć wysoką spójność i niskie sprzężenie. Duże sprzężenie wskazuje, że projekt jest trudno używany i konserwowany ze względu na wiele współzależności z innymi typami. Aby uzyskać więcej informacji, zobacz wpis na blogu dotyczący [sprzęgania klas](/archive/blogs/zainnab/code-metrics-class-coupling) .

::: moniker range=">=vs-2019"

- **Wiersze kodu źródłowego** — wskazuje dokładną liczbę wierszy kodu źródłowego, które znajdują się w pliku źródłowym, w tym puste wiersze. Ta Metryka jest dostępna w programie Visual Studio 2019 w wersji 16,4 i Microsoft. CodeAnalysis. Metrics (2.9.5).

- **Wiersze kodu wykonywalnego** — wskazuje przybliżoną liczbę wierszy lub operacji kodu wykonywalnego. Jest to liczba operacji w kodzie wykonywalnym. Ta Metryka jest dostępna w programie Visual Studio 2019 w wersji 16,4 i Microsoft. CodeAnalysis. Metrics (2.9.5). Wartość jest zwykle blisko zbliżonej do poprzedniej metryki, **wierszy kodu** , która jest metryką opartą na instrukcji MSIL używaną w trybie starszym.
::: moniker-end
::: moniker range="vs-2017"

- **Wiersze kodu** — wskazuje przybliżoną liczbę wierszy w kodzie. Liczba jest oparta na kodzie IL i dlatego nie jest dokładną liczbą wierszy w pliku kodu źródłowego. Duża liczba może wskazywać, że typ lub metoda próbuje wykonać zbyt dużo pracy i należy ją podzielić. Może również wskazywać, że typ lub metoda może być trudno zachować.

   > [!NOTE]
   > [Wersja wiersza polecenia](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) narzędzia metryki kodu zlicza rzeczywiste wiersze kodu, ponieważ analizuje kod źródłowy zamiast Il.
::: moniker-end

## <a name="anonymous-methods"></a>Metody anonimowe

*Metoda anonimowa* to tylko Metoda, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametru delegata. Metryki kodu są wynikiem metody anonimowej zadeklarowanej w elemencie członkowskim, takiej jak metoda lub akcesor, są skojarzone z elementem członkowskim, który deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

## <a name="generated-code"></a>Wygenerowany kod

Niektóre narzędzia i kompilatory oprogramowania generują kod, który jest dodawany do projektu i deweloper projektu nie widzi lub nie powinien zmieniać się. Przede wszystkim metryki kodu ignorują wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk odzwierciedlają elementy, które Projektant może zobaczyć i zmienić.

Kod wygenerowany dla Windows Forms nie jest ignorowany, ponieważ jest to kod, który deweloper może zobaczyć i zmienić.

## <a name="next-steps"></a>Następne kroki

- [Instrukcje: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
- [Korzystanie z okna wyników metryk kodu](../code-quality/working-with-code-metrics-data.md)
---
title: Oblicz metryki kodu
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886412"
---
# <a name="code-metrics-values"></a>Wartości metryk kodów

Wzrostu złożoności nowoczesnych aplikacji, zwiększa także trudności niezawodne i łatwy w obsłudze, dzięki czemu kod. Metryki kodu to zestaw miar oprogramowania, które dostarczają deweloperowi lepszy wgląd w kod rozwija. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny być przekształcił lub bardziej dokładnie przetestowana. Zespoły deweloperów można zidentyfikować potencjalne zagrożenia, zrozumienie bieżącego stanu projektu i śledzenia postępu podczas tworzenia oprogramowania.

Deweloperzy mogą używać programu Visual Studio do generowania danych metryk kodu, które mierzą złożoności i łatwości konserwacji kodu zarządzanego. Mogą być generowane danych metryki kodu dla całego rozwiązania lub pojedynczego projektu.

Aby dowiedzieć się, jak Generowanie danych metryk kodu w programie Visual Studio, zobacz [porady: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Pomiarów oprogramowania

Na poniższej liście przedstawiono kod wyników metryk, które oblicza programu Visual Studio:

- **Indeks łatwości utrzymania** — oblicza wartość indeksu od 0 do 100, która reprezentuje względną łatwość utrzymania kodu. Wysoka wartość oznacza lepsze łatwość konserwacji. Klasyfikacje oznaczone kolorem umożliwia szybką identyfikację aktywnych problemów w kodzie. Ocena zielony od 20 do 100 i wskazuje, że kod ma dużą łatwość utrzymania. Żółty ocena jest od 10 do 19 i wskazuje, że kod jest umiarkowanie łatwego w utrzymaniu. Ocena czerwony jest ma klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania. Aby uzyskać więcej informacji, zobacz wpis w blogu [zakres i znaczenie indeksu łatwość utrzymania](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) .

- **Złożoność Cyklomatyczna** -mierzy strukturalnych złożoności kodu. Zostanie utworzony, obliczając liczbę różne ścieżki przepływu programu. Program, który ma złożony przepływ sterowania, wymaga więcej testów do osiągnięcia dobrego pokrycia kodu i jest mniej utrzymany. Aby uzyskać więcej informacji, zobacz [wpis Wikipedia dotyczący złożoności cyklomatyczna](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Głębokość dziedziczenia** — wskazuje liczbę różnych klas, które dziedziczą od siebie nawzajem, z powrotem do klasy bazowej. Głębokość dziedziczenia jest podobna do sprzęgu klasy w przypadku, gdy zmiana klasy bazowej może mieć wpływ na wszystkie klasy dziedziczone. Im wyższy numer, tym lepiej dziedziczą i wyższy potencjał dla modyfikacji klasy podstawowej, aby spowodować powstanie istotnej zmiany. Aby uzyskać głębokość dziedziczenia, niska wartość jest dobra, a wysoka wartość jest zła.

- **Klasa sprzężenia** -mierzy sprzężenia unikatowy klasy za pomocą parametrów, zmienne lokalne, zwracanych typów, wywołania metody, wystąpień generyczny lub szablonu, klas bazowych, implementacji interfejsu, pól zdefiniowanych dla typów zewnętrznych i Atrybut dekoracji. Projektowania oprogramowania dobre nakazują, typów i metod powinni mieć wysoką spójność i mało sprzężenia. Sprzężenie wysoki wskazuje projekt, który jest trudny do ponownego użycia i utrzymywać ze względu na jej wielu współzależności na inne typy. Aby uzyskać więcej informacji, zobacz wpis na blogu dotyczący [sprzęgania klas](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Wiersze kodu źródłowego** — wskazuje dokładną liczbę wierszy kodu źródłowego, które znajdują się w pliku źródłowym, w tym puste wiersze. Ta Metryka jest dostępna w programie Visual Studio 2019 w wersji 16,4 i Microsoft. CodeAnalysis. metics (2.9.5).

- **Wiersze kodu wykonywalnego** — wskazuje przybliżoną liczbę wierszy lub operacji kodu wykonywalnego. Jest to liczba operacji w kodzie wykonywalnym. Ta Metryka jest dostępna w programie Visual Studio 2019 w wersji 16,4 i Microsoft. CodeAnalysis. metics (2.9.5). Wartość jest zwykle blisko zbliżonej do poprzedniej metryki, **wierszy kodu**, która jest metryką opartą na instrukcji MSIL używaną w trybie starszym.
::: moniker-end
::: moniker range="vs-2017"

- **Wiersze kodu** — Wskazuje przybliżoną liczbę wierszy w kodzie. Liczba zależy od kodu IL i dlatego nie dokładną liczbę wierszy w pliku kodu źródłowego. Duża liczba może wskazywać, że typ lub metoda próbuje wykonać zbyt dużo pracy i należy ją podzielić. Może również wskazywać, że typ lub metoda może być trudne do utrzymania.

   > [!NOTE]
   > [Wersji wiersza polecenia](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) kodu narzędzie metryki liczby rzeczywiste wiersze kodu, ponieważ analizuje ona kodu źródłowego, zamiast IL.
::: moniker-end

## <a name="anonymous-methods"></a>Metody anonimowe

*Metody anonimowej* jest po prostu metody, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametr delegata. Metryki kodu są wynikiem metody anonimowej zadeklarowanej w elemencie członkowskim, takiej jak metoda lub akcesor, są skojarzone z elementem członkowskim, który deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

## <a name="generated-code"></a>Wygenerowany kod

Niektóre kompilatory i narzędzia generowania kodu, który został dodany do projektu i projektanta projektu, nie zobaczą albo nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk, aby odzwierciedlić, co deweloper może wyświetlić i zmienić.

Kod generowany dla formularzy Windows Forms nie jest ignorowana, ponieważ jest kod, który deweloper może wyświetlić i zmienić.

## <a name="next-steps"></a>Następne kroki

- [Porady: generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
- [Korzystanie z okna wyników metryk kodów](../code-quality/working-with-code-metrics-data.md)

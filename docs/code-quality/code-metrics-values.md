---
title: Oblicz metryki kodu
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 960c2b546abe3554a5912efde9bd09bb5b2189b7
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835959"
---
# <a name="code-metrics-values"></a>Wartości metryk kodów

Wzrostu złożoności nowoczesnych aplikacji, zwiększa także trudności niezawodne i łatwy w obsłudze, dzięki czemu kod. Metryki kodu to zestaw miar oprogramowania, które dostarczają deweloperowi lepszy wgląd w kod rozwija. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny być przekształcił lub bardziej dokładnie przetestowana. Zespoły deweloperów można zidentyfikować potencjalne zagrożenia, zrozumienie bieżącego stanu projektu i śledzenia postępu podczas tworzenia oprogramowania.

Deweloperzy mogą używać programu Visual Studio do generowania danych metryk kodu, które mierzą złożoności i łatwości konserwacji kodu zarządzanego. Mogą być generowane danych metryki kodu dla całego rozwiązania lub pojedynczego projektu.

Aby dowiedzieć się, jak Generowanie danych metryk kodu w programie Visual Studio, zobacz [jak: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Pomiarów oprogramowania

Na poniższej liście przedstawiono kod wyników metryk, które oblicza programu Visual Studio:

- **Indeks łatwości utrzymania** — oblicza wartość indeksu od 0 do 100, która reprezentuje względną łatwość utrzymania kodu. Wysoka wartość oznacza lepsze łatwość konserwacji. Klasyfikacje oznaczone kolorem umożliwia szybką identyfikację aktywnych problemów w kodzie. Ocena zielony od 20 do 100 i wskazuje, że kod ma dużą łatwość utrzymania. Żółty ocena jest od 10 do 19 i wskazuje, że kod jest umiarkowanie łatwego w utrzymaniu. Ocena czerwony jest ma klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania. Aby uzyskać więcej informacji, zobacz [zakres indeks łatwości utrzymania i znaczenie](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) wpis w blogu.

- **Złożoność Cyklomatyczna** -mierzy strukturalnych złożoności kodu. Zostanie utworzony, obliczając liczbę różne ścieżki przepływu programu. Program, który zawiera przepływ sterowania złożonych wymaga więcej testów do osiągnięcia pokrycia kodu dobre i jest mniej łatwego w utrzymaniu. Aby uzyskać więcej informacji, zobacz [Wikipedia wpis dla złożoność cyklomatyczna](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Głębokość dziedziczenia** — wskazuje liczbę różnych klas dziedziczących od siebie nawzajem, aż do klasy bazowej. Głębokość dziedziczenia jest podobny do klasy sprzężenia, w tym zmiany w klasie bazowej może mieć wpływ na dowolne klasy dziedziczone. Im większa tej liczby, bardziej dziedziczenia i wyższa potencjalnych modyfikacje klasy bazowej spowodować podziału zmianie. Głębokość dziedziczenia niską wartość jest prawidłowy, i o wysokiej wartości jest nieodpowiedni.

- **Klasa sprzężenia** -mierzy sprzężenia unikatowy klasy za pomocą parametrów, zmienne lokalne, zwracanych typów, wywołania metody, wystąpień generyczny lub szablonu, klas bazowych, implementacji interfejsu, pól zdefiniowanych dla typów zewnętrznych i Atrybut dekoracji. Projektowania oprogramowania dobre nakazują, typów i metod powinni mieć wysoką spójność i mało sprzężenia. Sprzężenie wysoki wskazuje projekt, który jest trudny do ponownego użycia i utrzymywać ze względu na jej wielu współzależności na inne typy. Aby uzyskać więcej informacji, zobacz [sprzężenia klas](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) wpis w blogu.

- **Wiersze kodu** — Wskazuje przybliżoną liczbę wierszy w kodzie. Liczba zależy od kodu IL i dlatego nie dokładną liczbę wierszy w pliku kodu źródłowego. Wysoka liczba może wskazywać, że typ lub metoda próbuje wykonać dużo pracy i można podzielić. Może również wskazywać, że typ lub metoda może być trudne do utrzymania.

   > [!NOTE]
   > [Wersji wiersza polecenia](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) kodu narzędzie metryki liczby rzeczywiste wiersze kodu, ponieważ analizuje ona kodu źródłowego, zamiast IL.

## <a name="anonymous-methods"></a>Metody anonimowe

*Metody anonimowej* jest po prostu metody, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametr delegata. Metryki kodu w wyniku metody anonimowej, który jest zadeklarowany wewnątrz elementu członkowskiego, takie jak metody lub metody dostępu są skojarzone z elementem członkowskim, który deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

## <a name="generated-code"></a>Wygenerowany kod

Niektóre kompilatory i narzędzia generowania kodu, który został dodany do projektu i projektanta projektu, nie zobaczą albo nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk, aby odzwierciedlić, co deweloper może wyświetlić i zmienić.

Kod generowany dla formularzy Windows Forms nie jest ignorowana, ponieważ jest kod, który deweloper może wyświetlić i zmienić.

## <a name="next-steps"></a>Następne kroki

- [Instrukcje: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
- [Korzystanie z okna wyników metryk kodów](../code-quality/working-with-code-metrics-data.md)

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
ms.openlocfilehash: f989e5ec028f3a296585c54eb17b54f4da7c1cf0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809318"
---
# <a name="code-metrics-values"></a>Wartości metryk kodów

Wzrostu złożoności nowoczesnych aplikacji, zwiększa także trudności niezawodne i łatwy w obsłudze, dzięki czemu kod. Metryki kodu to zestaw miar oprogramowania, które dostarczają deweloperowi lepszy wgląd w kod rozwija. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny być przekształcił lub bardziej dokładnie przetestowana. Zespoły deweloperów można zidentyfikować potencjalne zagrożenia, zrozumienie bieżącego stanu projektu i śledzenia postępu podczas tworzenia oprogramowania.

Deweloperzy mogą używać programu Visual Studio do generowania danych metryk kodu, które mierzą złożoności i łatwości konserwacji kodu zarządzanego. Mogą być generowane danych metryki kodu dla całego rozwiązania lub pojedynczego projektu.

Aby dowiedzieć się, jak Generowanie danych metryk kodu w programie Visual Studio, zobacz [jak: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Pomiarów oprogramowania

Na poniższej liście przedstawiono kod wyników metryk, które oblicza programu Visual Studio:

- **Indeks łatwości utrzymania** — oblicza wartość indeksu od 0 do 100, która reprezentuje względną łatwość utrzymania kodu. Wysoka wartość oznacza lepsze łatwość konserwacji. Klasyfikacje oznaczone kolorem umożliwia szybką identyfikację aktywnych problemów w kodzie. Ocena zielony od 20 do 100 i wskazuje, że kod ma dużą łatwość utrzymania. Żółty ocena jest od 10 do 19 i wskazuje, że kod jest umiarkowanie łatwego w utrzymaniu. Ocena czerwony jest ma klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania.

- **Złożoność Cyklomatyczna** -mierzy strukturalnych złożoności kodu. Zostanie utworzony, obliczając liczbę różne ścieżki przepływu programu. Program, który zawiera przepływ sterowania złożonych będzie wymagać więcej testów do osiągnięcia pokrycia kodu dobre i będzie mniej łatwego w utrzymaniu.

- **Głębokość dziedziczenia** — wskazuje liczbę definicji klasy, które rozszerzenia w katalogu głównym hierarchii klas. Głębiej hierarchii coraz trudniejszy do zrozumienia, gdzie są zdefiniowane określonej metody i pola może być lub / i zmieniony.

- **Klasa sprzężenia** -mierzy sprzężenia unikatowy klasy za pomocą parametrów, zmienne lokalne, zwracanych typów, wywołania metody, wystąpień generyczny lub szablonu, klas bazowych, implementacji interfejsu, pól zdefiniowanych dla typów zewnętrznych i Atrybut dekoracji. Projektowania oprogramowania dobre nakazują, typów i metod powinni mieć wysoką spójność i mało sprzężenia. Sprzężenie wysoki wskazuje projekt, który jest trudny do ponownego użycia i utrzymywać ze względu na jej wielu współzależności na inne typy.

- **Wiersze kodu** — Wskazuje przybliżoną liczbę wierszy w kodzie. Liczba zależy od kodu IL i dlatego nie dokładną liczbę wierszy w pliku kodu źródłowego. Bardzo wysoka liczba może wskazywać typ lub metoda próbuje wykonać dużo pracy i powinien być podziału. Może również wskazywać, że typ lub metoda może być trudne do utrzymania.

   > [!NOTE]
   > [Wersji wiersza polecenia](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) kodu narzędzie metryki liczby rzeczywiste wiersze kodu, ponieważ analizuje ona kodu źródłowego, zamiast IL.

## <a name="anonymous-methods"></a>Metody anonimowe

*Metody anonimowej* jest po prostu metody, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametr delegata. Wyniki metryk dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, na przykład metodę lub metodę dostępu, są skojarzone z elementu członkowskiego, która deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

Aby uzyskać więcej informacji na temat sposobu metryki kodu traktuje metod anonimowych, zobacz [metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Wygenerowany kod

Niektóre kompilatory i narzędzia generowania kodu, który został dodany do projektu i projektanta projektu, nie zobaczą albo nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk, aby odzwierciedlić, co deweloper może wyświetlić i zmienić.

Kod generowany dla formularzy Windows Forms nie jest ignorowana, ponieważ jest kod, który deweloper może wyświetlić i zmienić.

## <a name="next-steps"></a>Następne kroki

- [Instrukcje: Generowanie danych metryk kodu](../code-quality/how-to-generate-code-metrics-data.md)
- [Korzystanie z okna wyników metryk kodów](../code-quality/working-with-code-metrics-data.md)
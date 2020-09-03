---
title: Wartości metryk kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667720"
---
# <a name="code-metrics-values"></a>Wartości metryk kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metryki kodu są zestawem miar oprogramowania, które zapewniają deweloperom lepszy wgląd w kod, który opracowuje. Dzięki wykorzystaniu metryk kodu deweloperzy mogą zrozumieć, które typy i/lub metody powinny być odwiedzane lub dokładniej przetestowane. Zespoły programistyczne mogą identyfikować potencjalne zagrożenia, zrozumieć bieżący stan projektu i śledzić postęp podczas opracowywania oprogramowania.

## <a name="software-measurements"></a>Pomiary oprogramowania
 Na poniższej liście przedstawiono wyniki metryk kodu, które [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oblicza:

- **Indeks utrzymania** — oblicza wartość indeksu z przedziału od 0 do 100, która reprezentuje względną łatwość utrzymywania kodu. Wysoka wartość to lepsza łatwość utrzymania. Klasyfikacje kodowane kolorami mogą szybko identyfikować problemy w kodzie. Zielona Ocena wynosi od 20 do 100 i wskazuje, że kod ma dobrą łatwość utrzymania. Żółta Klasyfikacja ma wartość z zakresu od 10 do 19 i wskazuje, że kod jest umiarkowanie konserwowany. Czerwona Ocena jest klasyfikacją od 0 do 9 i wskazuje na niską łatwość utrzymania.

- **Złożoność cyklomatyczna** — mierzy strukturalną złożoność kodu. Jest on tworzony przez obliczenie liczby różnych ścieżek kodu w przepływie programu. Program, który ma złożony przepływ sterowania, będzie wymagał większej liczby testów w celu osiągnięcia dobrego pokrycia kodu i będzie mniej utrzymany.

    > [!NOTE]
    > W niektórych przypadkach Obliczanie złożoności cyklomatyczna dla metody [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] różni się od wcześniejszych wersji. Aby uzyskać więcej informacji, zobacz sekcję "zmiany w sekcji obliczenia złożoności kodu w programie Visual Studio 2010" dotyczące [rozwiązywania problemów z metrykami kodu](../code-quality/troubleshooting-code-metrics-issues.md).

- **Głębokość dziedziczenia** — wskazuje liczbę definicji klas, które zwiększają się do katalogu głównego hierarchii klas. Dokładniejsze hierarchia jest trudniejsza do zrozumienia, gdzie poszczególne metody i pola są zdefiniowane lub/i ponownie definiowane.

- **Sprzęganie klas** — mierzy sprzężenie do unikatowych klas za pomocą parametrów, zmiennych lokalnych, typów zwracanych, wywołań metod, wystąpień ogólnych lub szablonów, klas bazowych, implementacji interfejsu, pól zdefiniowanych w typach zewnętrznych i dekoracji atrybutu. Dobre projektowanie oprogramowania oznacza, że typy i metody powinny mieć wysoką spójność i niskie sprzężenie. Duże sprzężenie wskazuje, że projekt jest trudno używany i konserwowany ze względu na wiele współzależności z innymi typami.

- **Wiersze kodu** — wskazuje przybliżoną liczbę wierszy w kodzie. Liczba jest oparta na kodzie IL i dlatego nie jest dokładną liczbą wierszy w pliku kodu źródłowego. Bardzo duża liczba może wskazywać, że typ lub metoda próbuje wykonać zbyt dużo pracy i należy ją podzielić. Może również wskazywać, że typ lub metoda może być trudno zachować.

## <a name="anonymous-methods"></a>Metody anonimowe
 *Metoda anonimowa* to tylko Metoda, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametru delegata. Wyniki metryk dla anonimowej metody zadeklarowanej w elemencie członkowskim, takie jak metoda lub akcesor, są skojarzone z elementem członkowskim, który deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

 Aby uzyskać więcej informacji o sposobie traktowania metod anonimowych przez metryki kodu, zobacz [anonimowe metody i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Wygenerowany kod
 Niektóre narzędzia i kompilatory oprogramowania generują kod, który jest dodawany do projektu i deweloper projektu nie widzi lub nie powinien zmieniać się. Przede wszystkim metryki kodu ignorują wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk odzwierciedlają elementy, które Projektant może zobaczyć i zmienić.

 Kod wygenerowany dla formularzy systemu Windows nie jest ignorowany, ponieważ jest to kod, który deweloper może zobaczyć i zmienić.

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

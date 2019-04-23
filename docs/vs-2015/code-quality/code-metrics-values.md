---
title: Wartości metryk kodu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d5e3669ddaf9d8073038f0fa0c01c7e5a19a209d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60049566"
---
# <a name="code-metrics-values"></a>Wartości metryk kodów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metryki kodu to zestaw miar oprogramowania, które dostarczają deweloperowi lepszy wgląd w kod rozwija. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny być przekształcił lub bardziej dokładnie przetestowana. Zespoły deweloperów można zidentyfikować potencjalne zagrożenia, zrozumienie bieżącego stanu projektu i śledzenia postępu podczas tworzenia oprogramowania.  
  
## <a name="software-measurements"></a>Pomiarów oprogramowania  
 Na poniższej liście przedstawiono wyników metryk kodów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oblicza:  
  
- **Indeks łatwości utrzymania** — oblicza wartość indeksu od 0 do 100, która reprezentuje względną łatwość utrzymania kodu. Wysoka wartość oznacza lepsze łatwość konserwacji. Klasyfikacje oznaczone kolorem umożliwia szybką identyfikację aktywnych problemów w kodzie. Ocena zielony od 20 do 100 i wskazuje, że kod ma dużą łatwość utrzymania. Żółty ocena jest od 10 do 19 i wskazuje, że kod jest umiarkowanie łatwego w utrzymaniu. Ocena czerwony jest ma klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania.  
  
- **Złożoność Cyklomatyczna** — mierzy strukturalnych złożoności kodu. Zostanie utworzony, obliczając liczbę różne ścieżki przepływu programu. Program, który zawiera przepływ sterowania złożonych będzie wymagać więcej testów do osiągnięcia pokrycia kodu dobre i będzie mniej łatwego w utrzymaniu.  
  
    > [!NOTE]
    >  W niektórych przypadkach obliczenia złożoność cyklomatyczna metody w [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] różni się od wcześniejszych wersji. Aby uzyskać więcej informacji, zobacz "Zmiany w Visual Studio 2010 złożoność obliczeń sekcję kodu" z [Rozwiązywanie problemów metryki kodu](../code-quality/troubleshooting-code-metrics-issues.md).  
  
- **Głębokość dziedziczenia** — wskazuje liczbę definicji klasy, które rozszerzenia w katalogu głównym hierarchii klas. Głębiej hierarchii coraz trudniejszy do zrozumienia, gdzie są zdefiniowane określonej metody i pola może być lub / i zmieniony.  
  
- **Klasa sprzężenia** — mierzy sprzężenia unikatowy klasy za pomocą parametrów, zmienne lokalne, zwracanych typów, wywołania metody, wystąpień generyczny lub szablonu, klas bazowych, implementacji interfejsu, pól zdefiniowanych dla typów zewnętrznych i Atrybut dekoracji. Projektowania oprogramowania dobre nakazują, typów i metod powinni mieć wysoką spójność i mało sprzężenia. Sprzężenie wysoki wskazuje projekt, który jest trudny do ponownego użycia i utrzymywać ze względu na jej wielu współzależności na inne typy.  
  
- **Wiersze kodu** — Wskazuje przybliżoną liczbę wierszy w kodzie. Liczba zależy od kodu IL i dlatego nie dokładną liczbę wierszy w pliku kodu źródłowego. Bardzo wysoka liczba może wskazywać typ lub metoda próbuje wykonać dużo pracy i powinien być podziału. Może również wskazywać, że typ lub metoda może być trudne do utrzymania.  
  
## <a name="anonymous-methods"></a>Metody anonimowe  
 *Metody anonimowej* jest po prostu metody, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametr delegata. Wyniki metryk dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, na przykład metodę lub metodę dostępu, są skojarzone z elementu członkowskiego, która deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.  
  
 Aby uzyskać więcej informacji na temat sposobu metryki kodu traktuje metod anonimowych, zobacz [metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Niektóre kompilatory i narzędzia generowania kodu, który został dodany do projektu i projektanta projektu, nie zobaczą albo nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk, aby odzwierciedlić, co deweloper może wyświetlić i zmienić.  
  
 Kod generowany dla formularzy Windows forms nie jest ignorowana, ponieważ jest kod, który deweloper może wyświetlić i zmienić.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

---
title: Co&#39;s nowego w dziedzinie projektowania
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c68db12f8ecea523327250fec1f600639a2f267
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408361"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Co nowego w projektowaniu w programie Visual Studio w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Ta wersja programu Visual Studio obejmuje następujące ulepszenia ułatwiające lepsze zrozumienie i projektowania kodu.

 **Mapy kodu i wykresy zależności**

 W programie Visual Studio Enterprise Jeśli chcesz poznać konkretne zależności w kodzie, utwórz ich wizualizację przez utworzenie map kodów. Następnie można przejść te relacje za pomocą mapy wyświetlanej obok kodu. Mapy kodu może również ułatwić śledzenie bieżącego miejsca w kodzie podczas pracy nad nim lub debugowania, dzięki czemu przeczytasz mniej kodu podczas Dowiedz się więcej na temat projektu kodu.

 W ostatecznej wersji (RTM) wprowadziliśmy menu skrótów dla elementów kodu i linki znacznie łatwiejsze do użycia przez zgrupowanie poleceń w sekcje dotyczące wybierania, edycji, Zarządzanie grupami i zmieniania układu zawartości grupy. Zwróć uwagę, że projekty testu są wyświetlane przy użyciu innego stylu z innych projektów i zaktualizowane bardziej odpowiednie ikony elementów w mapie.

 ![Pokaż zaznaczone elementy na nowej mapie kodu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Inne ulepszenia obejmują:

- **Udoskonalone diagramy górne**. Dla średnich lub dużych rozwiązań programu Visual Studio można teraz używać uproszczonego menu architektura, można uzyskać kod bardziej przydatne mapy rozwiązania. Zestawy rozwiązania są grupowane według folderów rozwiązania, dzięki czemu można zobaczyć je w kontekście i wykorzystać nakład pracy, umieszczoną w tworzenie struktury rozwiązania. Natychmiast zauważysz projektu i odwołania do zestawu, a następnie zostaną wyświetlone typy linków. Dodatkowo zestawy zewnętrzne w stosunku do rozwiązania są pogrupowane w bardziej zwarty sposób.

- **Projekty testowe mają różne style i można je filtrować**. Teraz możesz łatwiej i szybciej zidentyfikować projekty testowe na mapie, ponieważ mają odrębny styl. One może je także odfiltrować, dzięki czemu możesz skupić się na działającym kodzie aplikacji.

- **Uproszczone zewnętrzne linki zależności**. Linki zależności nie przedstawiają już dziedziczenia z System.Object, System.ValueType, System.Enum i System.Delegate, co ułatwia dostrzeżenie zewnętrznych zależności na mapie kodu.

- **"Przechodzenie do szczegółów w łączach zależności" obejmuje filtry**. Otrzymujesz przydatny, przejrzysty diagram, który umożliwia poznanie elementów składowych linku zależności. Diagram jest mniej "zatłoczony" i uwzględnia zostało wybrane opcje filtrowania linków.

- **Elementy kodu są dodawane do mapy kodu z ich kontekstami**. Ponieważ teraz diagramy są wyświetlane razem ze swoimi kontekstami (aż do poziomu zestawu i folderu rozwiązania, które można odfiltrować w razie potrzeby), uzyskujesz bardziej użyteczne diagramy podczas przeciągania i upuszczania elementów kodu z Eksploratora rozwiązań, widoku klas i przeglądarki obiektów; lub podczas zaznaczania elementów w Eksploratorze rozwiązań i wybierając polecenie Pokaż na mapie kodu.

- Szybsze **pobieranie map kodu**. Operacja przeciągnięcia i upuszczenia daje natychmiastowy efekt, a linki między węzłami są tworzone dużo szybciej i bez wpływania na kolejne operacje użytkownika, takie jak rozwinięcie węzła lub zażądanie kolejnych węzłów. Po utworzeniu map kodu bez kompilowania rozwiązania, wszystkie przypadki brzegowe — takie jak brak skompilowanych zestawów — są obecnie przetwarzane.

- **Pomiń ponowne kompilowanie rozwiązania.** Zapewnia lepszą wydajność, podczas tworzenia i edytowania diagramów.

- **Filtrowanie węzłów i grup elementów kodu**. Możesz szybko zwiększyć przejrzystość map, pokazując lub ukrywając elementy kodu według ich kategorii, a także grupować elementy kodu według folderów rozwiązania, zestawów, przestrzeni nazw, folderów projektu i typów.

- **Odfiltruj relacje, aby ułatwić odczytywanie diagramów**. Filtrowanie linku dotyczy teraz także linków między grupami, co sprawia, że praca z oknem filtru jest płynniejsza niż w poprzednich wersjach.

- **Utwórz diagramy na podstawie widok klasy i Przeglądarka obiektów**. Przeciągnij i upuść pliki oraz zestawy na nową lub istniejącą mapę w oknach widoku klas i przeglądarki obiektów.

  Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

  **Inne zmiany dotyczące projektowania i modelowania w tej wersji:**

- **Diagramy warstwowe**. Aktualizuj te diagramy za pomocą widoku klas i przeglądarki obiektów. Aby spełnić wymagania dotyczące projektowania oprogramowania, należy użyć diagramów warstw do opisania oczekiwanych zależności oprogramowania. Utrzymuj spójność kodu z tego projektu możliwości znalezienia kodu niespełniającego tych ograniczeń i weryfikowaniu przyszłego kodu względem tej linii bazowej.

- **Diagramy UML**. Użytkownik nie można już tworzyć diagramów klas UML i diagramy sekwencji z kodu. Ale wciąż można jednak tworzyć te diagramy z użyciem nowych elementów UML.

- **Eksplorator architektury**. Do tworzenia diagramów nie jest już służy Eksploratora architektury. Ale nadal można korzystać z Eksploratora rozwiązań.

## <a name="VersionSupport"></a>Obsługa wersji dla architektury i narzędzi modelowania

Program Visual Studio 2015 jest dostępna w wielu wersjach. Nie wszystkie te zapewniają obsługę architekturę i narzędzia do modelowania. W poniższej tabeli przedstawiono Dostępność poszczególnych narzędzi.

|**Funkcja**|**Przedsiębiorstwo**|**Profesjonalist**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kodu**|Yes|Obsługuje tylko odczytywanie i filtrowanie map kodu, dodając nowe węzły ogólnego i tworzenie nowy Graf skierowany z zaznaczenia.|-|-|
|**Diagramy klas UML**|Yes|-|-|-|
|**Diagramy sekwencji UML**|Yes|-|-|-|
|**Diagramy przypadków użycia UML**|Yes|-|-|-|
|**Diagramy aktywności UML**|Yes|-|-|-|
|**Diagramy składników UML**|Yes|-|-|-|
|**Diagramy warstw**|Yes|-|-|-|
|**Wykresy ukierunkowane** (diagramy dgml)|Yes|Yes|-|-|
|**Klonowanie kodu**|Yes|-|-|-|
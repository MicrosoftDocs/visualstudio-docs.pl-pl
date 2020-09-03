---
title: Jakie&#39;s nowe dla projektu
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315333"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Co nowego w projektowaniu w programie Visual Studio w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
W tej wersji programu Visual Studio wprowadzono następujące ulepszenia, które ułatwiają lepsze zrozumienie i projektowanie kodu.

 **Mapy kodu i wykresy zależności**

 W Visual Studio Enterprise, gdy chcesz zrozumieć konkretne zależności w kodzie, wizualizuj je przez tworzenie map kodu. Następnie można przejść do tych relacji przy użyciu mapy, która pojawia się obok kodu. Mapy kodu mogą również pomóc w śledzeniu miejsca w kodzie podczas pracy lub debugowania kodu, dzięki czemu można czytać mniej kodu, a dowiedzieć się więcej o projekcie kodu.

 W wersji ostatecznej (RTM) wprowadziliśmy menu skrótów dla elementów kodu i linków znacznie łatwiejszych do użycia przez grupowanie poleceń w sekcje związane z zaznaczaniem, edytowaniem i zarządzaniem grupami oraz zmiana układu zawartości grupy. Zwróć również uwagę, że projekty testowe są wyświetlane w innym stylu niż inne projekty i że zaktualizowaliśmy ikony dla elementów na mapie, aby uzyskać bardziej odpowiednie wersje.

 ![Pokaż zaznaczone elementy na nowej mapie kodu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Inne ulepszenia obejmują:

- **Udoskonalone diagramy górne**. W przypadku średnich i dużych rozwiązań programu Visual Studio możesz teraz użyć uproszczonego menu architektura, aby uzyskać bardziej przydatne mapy kodu dla rozwiązania. Zestawy rozwiązań są pogrupowane według folderów rozwiązania, dzięki czemu można je zobaczyć w kontekście i wykorzystać nakład pracy, który został umieszczony w tworzeniu struktury rozwiązania. Natychmiast zobaczysz odwołania projektu i zestawu, a następnie pojawią się typy łączy. Ponadto zestawy zewnętrzne są pogrupowane w bardziej zwarty sposób.

- **Projekty testowe mają różne style i można je filtrować**. Teraz można łatwiej i szybko identyfikować projekty testowe na mapie, ponieważ różnią się one stylami. Można je również odfiltrować, aby skoncentrować się na kodzie roboczym aplikacji.

- **Uproszczone zewnętrzne linki zależności**. Linki zależności nie przedstawiają już dziedziczenia z elementów System. Object, system. ValueType, system. Enum i system. Delegate, co ułatwia przeglądanie zewnętrznych zależności na mapie kodu.

- **"Przechodzenie do szczegółów w łączach zależności" obejmuje filtry**. Uzyskujesz przydatny, przejrzysty diagram podczas jego rozszerzania, aby zrozumieć wkłady do linku zależności. Diagram jest mniej czytelny i uwzględnia wybrane opcje filtrowania linków.

- **Elementy kodu są dodawane do mapy kodu z ich kontekstami**. Ponieważ diagramy są teraz wyświetlane wraz z ich kontekstami (do zestawu i folderu rozwiązania, które można odfiltrować w razie potrzeby), są dostępne bardziej użyteczne diagramy podczas przeciągania i upuszczania elementów kodu z Eksplorator rozwiązań, Widok klasy, Przeglądarka obiektów; lub po wybraniu elementów w Eksplorator rozwiązań i wybraniu pozycji Pokaż na mapie kodu.

- Szybsze **pobieranie map kodu**. Operacje przeciągania i upuszczania dają bezpośredni wynik, a linki między węzłami są tworzone znacznie szybciej, bez wywierania wpływu na kolejne operacje inicjowane przez użytkownika, takie jak rozszerzanie węzła lub żądanie większej liczby węzłów. Po utworzeniu map kodu bez kompilowania rozwiązania wszystkie przypadki narożne — takie jak zestawy nie są kompilowane — są teraz przetwarzane.

- **Pomiń ponowne kompilowanie rozwiązania.** Zapewnia lepszą wydajność podczas tworzenia i edytowania diagramów.

- **Filtrowanie węzłów i grup elementów kodu**. Mapy można szybko odkodować, pokazując lub ukrywając elementy kodu na podstawie ich kategorii, a także Grupując elementy kodu według folderów rozwiązania, zestawów, przestrzeni nazw, folderów projektu i typów.

- **Odfiltruj relacje, aby ułatwić odczytywanie diagramów**. Filtrowanie linków teraz dotyczy również linków między grupami, dzięki czemu praca z oknem filtru jest mniej niepożądane niż w poprzednich wersjach.

- **Utwórz diagramy na podstawie widok klasy i Przeglądarka obiektów**. Przeciągnij i upuść pliki i zestawy do nowej lub istniejącej mapy z Widok klasy i Przeglądarka obiektów Windows.

  Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

  **Inne zmiany dotyczące projektowania i modelowania w tej wersji:**

- **Diagramy warstwowe**. Zaktualizuj te diagramy przy użyciu Widok klasy i Przeglądarka obiektów. Aby spełnić wymagania dotyczące projektu oprogramowania, należy użyć diagramów warstw do opisania żądanych zależności oprogramowania. Zachowaj spójność kodu z tym projektem, wyszukując kod, który nie spełnia tych ograniczeń, i sprawdzając przyszły kod w tym punkcie odniesienia.

- **Diagramy UML**. Nie można już tworzyć diagramów klas UML i diagramów sekwencyjnych na podstawie kodu. Jednak nadal można tworzyć te diagramy za pomocą nowych elementów UML.

- **Eksplorator architektury**. Nie można już korzystać z Eksploratora architektury do tworzenia diagramów. Można jednak nadal używać Eksplorator rozwiązań.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a> Obsługa wersji dla architektury i narzędzi modelowania

Program Visual Studio 2015 jest dostępny w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Przedsiębiorstwo**|**Professional Edition**|**Społeczność**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kodu**|Tak|Obsługuje tylko odczytywanie i filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego ukierunkowanego wykresu na podstawie zaznaczenia.|-|-|
|**Diagramy klas UML**|Tak|-|-|-|
|**Diagramy sekwencji UML**|Tak|-|-|-|
|**Diagramy przypadków użycia UML**|Tak|-|-|-|
|**Diagramy aktywności UML**|Tak|-|-|-|
|**Diagramy składników UML**|Tak|-|-|-|
|**Diagramy warstw**|Tak|-|-|-|
|**Wykresy ukierunkowane** (diagramy dgml)|Tak|Tak|-|-|
|**Klonowanie kodu**|Tak|-|-|-|
---
title: Co&#39;nowego w projektowaniu
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302372"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Co nowego w projekcie w programie Visual Studio w programie Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Ta wersja programu Visual Studio zawiera następujące ulepszenia, które ułatwią lepsze zrozumienie i zaprojektowanie kodu.

 **Mapy kodu i wykresy zależności**

 W programie Visual Studio Enterprise, jeśli chcesz zrozumieć określone zależności w kodzie, wizualizuj je, tworząc mapy kodu. Następnie można nawigować po tych relacjach za pomocą mapy, która pojawia się obok kodu. Mapy kodu może również pomóc śledzić swoje miejsce w kodzie podczas pracy lub debugowania kodu, dzięki czemu będziesz czytać mniej kodu, podczas gdy dowiesz się więcej o projekcie kodu.

 W ostatecznej wersji (RTM) znacznie ułatwiliśmy korzystanie z menu skrótów dla elementów kodu i łączy, grupując polecenia w sekcje związane z wybieraniem, edytowaniem, zarządzaniem grupami i zmienianiem układu zawartości grupy. Należy również zauważyć, że projekty testowe są wyświetlane w innym stylu niż inne projekty i że zaktualizowaliśmy ikony elementów na mapie do bardziej odpowiednich wersji.

 ![Pokazywale wybranych elementów na nowej mapie kodu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNowamapa")

 Inne ulepszenia obejmują:

- **Ulepszone diagramy odgórne**. W przypadku średnich i dużych rozwiązań programu Visual Studio można teraz użyć uproszczonego menu architektury, aby uzyskać bardziej przydatne mapy kodu dla rozwiązania. Zestawy rozwiązania są pogrupowane według folderów rozwiązania, dzięki czemu można je zobaczyć w kontekście i wykorzystać wysiłek, który został wprowadzony w strukturyzację rozwiązania. Natychmiast zobaczysz odwołania do projektu i zestawu, a następnie pojawią się typy łączy. Ponadto zestawy zewnętrzne do rozwiązania są pogrupowane w bardziej kompaktowy sposób.

- **Projekty testowe są inaczej stylizowane i mogą być filtrowane**. Teraz można łatwiej i szybciej identyfikować projekty testowe na mapie, ponieważ są one inaczej stylizowane. Można je również odfiltrować, dzięki czemu można skupić się na kodzie roboczym aplikacji.

- **Uproszczone łącza zależności zewnętrznych**. Łącza zależności nie reprezentują już dziedziczenia z system.Object, System.ValueType, System.Enum i System.Delegate, co ułatwia wyświetlanie zależności zewnętrznych na mapie kodu.

- **"Przechodzenie do łączy zależności" uwzględnia filtry**. Otrzymasz przydatny, przejrzysty diagram podczas rozwijania go, aby zrozumieć wkład do łącza zależności. Diagram jest mniej zaśmiecony i uwzględnia wybrane opcje filtrowania łączy.

- **Elementy kodu są dodawane do mapy kodu z ich kontekstem**. Ponieważ diagramy są teraz wyświetlane z ich kontekstem (do folderu zestawu i rozwiązania, który można odfiltrować w razie potrzeby), można uzyskać bardziej przydatne diagramy podczas przeciągania i upuszczania elementów kodu z Eksploratora rozwiązań, widoku klasy, przeglądarki obiektów; lub podczas wybierania elementów w Eksploratorze rozwiązań i wybierania opcji Pokaż na mapie kodu.

- **Szybciej pobierz reaktywne mapy kodu**. Operacje przeciągania i upuszczania dają natychmiastowy wynik, a łącza między węzłami są tworzone znacznie szybciej, bez wpływu na kolejne operacje inicjowane przez użytkownika, takie jak rozwijanie węzła lub żądanie większej liczby węzłów. Podczas tworzenia map kodu bez tworzenia rozwiązania wszystkie przypadki narożne — na przykład gdy zestawy nie są budowane — są teraz przetwarzane.

- **Pomiń przebudowę rozwiązania.** Zapewnia lepszą wydajność podczas tworzenia i edytowania diagramów.

- **Filtruj węzły i grupy elementów kodu**. Można szybko uporządkować mapy, wyświetlając lub ukrywając elementy kodu na podstawie ich kategorii, a także grupując elementy kodu według folderów rozwiązania, zestawów, obszarów nazw, folderów projektu i typów.

- **Filtruj relacje, aby ułatwić czytanie diagramów**. Filtrowanie łączy ma teraz zastosowanie również do łączy między grupami, co sprawia, że praca z oknem filtru jest mniej inwazyjna niż w poprzednich wersjach.

- **Tworzenie diagramów z widoku klasy i przeglądarki obiektów**. Przeciągnij i upuść pliki i złożenia do nowej lub istniejącej mapy z okien widok klasy i przeglądarka obiektów.

  Zobacz [Zależności mapowe między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

  **Inne zmiany w projekcie i modelowaniu w tej wersji:**

- **Diagramy warstwowe**. Zaktualizuj te diagramy przy użyciu widoku klasy i przeglądarki obiektów. Aby spełnić wymagania dotyczące projektowania oprogramowania, użyj diagramów warstw, aby opisać żądane zależności dla oprogramowania. Zachowaj kod zgodny z tym projektem, znajdując kod, który nie spełnia tych ograniczeń, i sprawdzając poprawność przyszłego kodu za pomocą tej linii bazowej.

- **diagramy UML**. Diagramy klas UML i diagramy sekwencji nie można już tworzyć na podstawie kodu. Ale nadal tworzyć te diagramy przy użyciu nowych elementów UML.

- **Eksplorator architektury**. Nie można już używać Eksploratora architektury do tworzenia diagramów. Ale nadal można korzystać z Eksploratora rozwiązań.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a>Obsługa edycji dla architektury i narzędzi do modelowania

Visual Studio 2015 jest dostępny w kilku wersjach. Nie wszystkie z nich zapewniają obsługę architektury i narzędzi modelowania. W poniższej tabeli przedstawiono dostępność każdego narzędzia.

|**Funkcja**|**Przedsiębiorstwo**|**Professional Edition**|**Społeczność**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kodu**|Tak|Obsługuje tylko odczytywanie i filtrowanie map kodu, dodawanie nowych węzłów ogólnych i tworzenie nowego wykresu kierowanego z zaznaczenia.|-|-|
|**Diagramy klas UML**|Tak|-|-|-|
|**Diagramy sekwencji UML**|Tak|-|-|-|
|**Diagramy przypadków użycia UML**|Tak|-|-|-|
|**Diagramy aktywności UML**|Tak|-|-|-|
|**Diagramy składników UML**|Tak|-|-|-|
|**Diagramy warstw**|Tak|-|-|-|
|**Wykresy skierowane (diagramy** DGML)|Tak|Tak|-|-|
|**Klon kodu**|Tak|-|-|-|
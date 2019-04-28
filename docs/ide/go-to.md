---
title: Przejdź do pliku, przejdź do symbolu, przejdź do wiersza
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588bc57dc2cda1030e9e1b8d1f989b2cc2d31662
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62550064"
---
# <a name="find-code-using-go-to-commands"></a>Znajdowanie kodu za pomocą poleceń Przejdź do

Visual Studio **przejdź do** poleceń wyszukiwania ukierunkowanych swój kod, aby ułatwić szybkie znajdowanie określonych elementów. Możesz przejść do określonego wiersza, typów, symboli, plików i elementów członkowskich z prostego, jednolitego interfejsu.

## <a name="how-to-use-it"></a>Jak z niej korzystać

Dane wejściowe | Funkcja
------------ | ---
**Keyboard** | Naciśnij klawisz **Ctrl**+**T** lub **Ctrl**+**,**
**Myszy** | Wybierz **Edytuj** > **przejdź do** > **przejdź do wszystkich**

Niewielki przedział jest wyświetlany w prawym górnym rogu edytora kodu.

![Przejdź do wszystkich okien](media/go-to-all.png)

Podczas wpisywania w polu tekstowym, wyniki są wyświetlane na liście rozwijanej poniżej pola tekstowego. Aby przejść do elementu, wybierz go na liście.

![Nawiguj do okna](../ide/media/vside_navigatetowindow.png)

Możesz też wprowadzić znak zapytania (**?**) Aby uzyskać dodatkową pomoc.

![Przejdź do wszystkich pomocy](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrowane wyszukiwania

Określony element jest domyślnie wyszukiwane we wszystkich elementach rozwiązań. Jednak można ograniczyć wyszukiwanie kodu, tak aby elementy określonych typów, prefacing wyszukiwane terminy z niektórych znaków. Filtr wyszukiwania można szybko zmienić, wybierając przyciski na **przejdź do** paska narzędzi okna dialogowego pole. Przyciski, Zmień filtry typów, które są po lewej stronie i przyciski, zmień zakres wyszukiwania, które są po prawej stronie.

![Przejdź do elementów członkowskich](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtruj do określonego typu elementu kodu

Aby zawęzić kryteria wyszukiwania dla określonego typu elementu kodu, możesz określić prefiks w polu wyszukiwania lub wybierz jednego z pięciu ikony filtru:

Prefiks | Ikona | Skrót | Opis
:-: | - | - | -
:| ![Ikona wiersza](media/gotoall-line-icon.png) | **Ctrl**+**G** | Przejdź do określonego numeru wiersza
f| ![Ikona pliki](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | Przejdź do określonego pliku
r| ![Ikona ostatnie pliki](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | Przejdź do pliku określonego, ostatnio odwiedzonych
t| ![Ikony typów](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | Przejdź do określonego typu
m| ![Ikona elementów członkowskich](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | Przejdź do określonego elementu członkowskiego
\#| ![Ikony symboli](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | Przejdź do określonego symbolu

### <a name="filter-to-a-specific-location"></a>Filtruj do określonej lokalizacji

Aby zawęzić kryteria wyszukiwania do określonej lokalizacji, wybierz jedną z ikon dwóch dokumentów:

Ikona | Opis
---- | ---
![Bieżący dokument](media/gotoall_currentdocument.png) | Wyszukiwanie tylko bieżący dokument
![Zewnętrzne dokumenty](media/gotoall_external.png) | Wyszukiwanie dokumentów zewnętrznych, oprócz tych znajdujących się w projekt/rozwiązanie

## <a name="camel-casing"></a>Camelcase

Jeśli używasz [camelcase](https://en.wikipedia.org/wiki/Camel_case) w kodzie, można znaleźć elementy kodu szybciej, wprowadzając tylko wielkimi literami nazwa elementu kodu. Na przykład, jeśli kod ma typ o nazwie `CredentialViewModel`, można zawęzić wyszukiwanie, wybierając **typu** filtru (**t**), a następnie wprowadzenie tylko wielkimi literami nazwę (`CVM`) w Przejdź do okna dialogowego pole. Ta funkcja może być przydatne, jeśli kod ma długich nazwach.

![Przejdź do okna — Wyszukiwanie za pomocą literami](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ustawienia

Wybierając ikonę koła zębatego ![Ikona koła zębatego](media/gotoall_gear.png) Pozwala zmienić sposób działania tej funkcji:

Ustawienie | Opis
------- | ---
Użyj karty podglądu | Natychmiast wyświetlić wybranego elementu w karcie podglądu środowiska IDE
Pokaż szczegóły | Wyświetl w oknie projektu, plików, wiersza i podsumowanie informacji z komentarzy dokumentacji
Wyśrodkuj okno | Przenieś to okno w środkowej górnej edytora kodu, zamiast prawym górnym rogu

## <a name="see-also"></a>Zobacz także

- [Przechodzenie do kodu](../ide/navigating-code.md)
- [Przejdź do wiersza, okno dialogowe](../ide/reference/go-to-line.md)
- [Polecenia Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
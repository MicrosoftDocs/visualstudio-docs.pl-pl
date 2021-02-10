---
title: Przejdź do pliku, przejdź do symbolu, przejdź do wiersza
description: Dowiedz się więcej na temat poleceń w programie Visual Studio i sposobach ich używania do wykonywania ukierunkowanych wyszukiwań w kodzie.
ms.custom: SEO-VS-2020
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 257db632c095027d9fa4be667a30e809ecb2fff4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946621"
---
# <a name="find-code-using-go-to-commands"></a>Znajdowanie kodu za pomocą poleceń Przejdź do

Program Visual Studio **Przejdź do poleceń umożliwia** skoncentrowane wyszukiwanie kodu, aby pomóc w szybkim wyszukiwaniu określonych elementów. Możesz przejść do określonego wiersza, typu, symbolu, pliku i składowej z prostego, jednolitego interfejsu.

## <a name="how-to-use-it"></a>Sposób użycia

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Naciśnij **klawisze CTRL** + **T** lub **Ctrl** + **,**
**Mysz** | Wybierz pozycję **Edytuj**  >  **Przejdź do** opcji  >  **Przejdź do wszystkiego**

Małe okno jest wyświetlane w prawym górnym rogu edytora kodu.

![Przejdź do okna wszystkie](media/go-to-all.png)

Podczas wpisywania w polu tekstowym wyniki pojawiają się na liście rozwijanej poniżej pola tekstowego. Aby przejść do elementu, wybierz go z listy.

![Przejdź do okna](../ide/media/vside_navigatetowindow.png)

Możesz również wprowadzić znak zapytania (**?**), aby uzyskać dodatkową pomoc.

![Przejdź do całej pomocy](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Wyszukiwania filtrowane

Domyślnie określony element jest wyszukiwany we wszystkich elementach rozwiązania. Można jednak ograniczyć wyszukiwanie kodu do określonych typów elementów, umieszczając je na podstawie określonych znaków. Możesz również szybko zmienić filtr wyszukiwania, wybierając przyciski na pasku narzędzi okna dialogowego **Przejdź do** . Przyciski, które zmieniają filtry typów, znajdują się po lewej stronie, a przyciski, które zmieniają zakres wyszukiwania, znajdują się po prawej stronie.

![Przejdź do elementów członkowskich](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrowanie do określonego typu elementu kodu

Aby zawęzić wyszukiwanie do określonego typu elementu kodu, można określić prefiks w polu wyszukiwania lub wybrać jedną z pięciu ikon filtru:

Prefiks | Ikona | Skrót | Opis
:-: | - | - | -
:| ![Ikona linii](media/gotoall-line-icon.png) | **Ctrl** + **G** | Przejdź do określonego numeru wiersza
f| ![Ikona plików](media/gotoall-files-icon.png) | **Ctrl** + **1**, **Ctrl** + **F** | Przejdź do określonego pliku
r| ![Ikona ostatnich plików](media/gotoall-recent-files-icon.png) | **Ctrl** + **1**, **Ctrl** + **R** | Przejdź do określonego, ostatnio odwiedzonego pliku
t| ![Ikona typów](media/gotoall-types-icon.png) | **Ctrl** + **1**, **Ctrl** + **T** | Przejdź do określonego typu
m| ![Ikona członków](media/gotoall-members-icon.png) | **Ctrl** + **1**, **Ctrl** + **M** | Przejdź do określonego elementu członkowskiego
\#| ![Ikona symboli](media/gotoall-symbols-icon.png) | **Ctrl** + **1**, **Ctrl** + **S** | Przejdź do podanego symbolu

### <a name="filter-to-a-specific-location"></a>Filtrowanie do określonej lokalizacji

Aby zawęzić wyszukiwanie do określonej lokalizacji, wybierz jedną z dwóch ikon dokumentu:

Ikona | Opis
---- | ---
![Bieżący dokument](media/gotoall_currentdocument.png) | Wyszukaj tylko bieżący dokument
![Dokumenty zewnętrzne](media/gotoall_external.png) | Przeszukaj zewnętrzne dokumenty poza tymi znajdującymi się w projekcie/rozwiązaniu

## <a name="camel-casing"></a>Notacji CamelCase

Jeśli używasz [notacji CamelCase wielkości liter](https://en.wikipedia.org/wiki/Camel_case) w kodzie, możesz znaleźć elementy kodu szybciej, wprowadzając tylko wielkie litery nazwy elementu kodu. Na przykład jeśli kod ma typ o nazwie, możesz `CredentialViewModel` zawęzić wyszukiwanie, wybierając filtr **typu** (**t**), a następnie wprowadzając tylko wielkie litery nazwy ( `CVM` ) w oknie dialogowym przejdź do. Ta funkcja może być przydatna, jeśli kod ma długie nazwy.

![Przejdź do okna — wyszukiwanie przy użyciu wersalików](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ustawienia

Wybieranie ikony koła zębatego ![Ikona koła zębatego](media/gotoall_gear.png) umożliwia zmianę sposobu działania tej funkcji:

Ustawienie | Opis
------- | ---
Użyj karty podglądu | Wyświetl wybrany element natychmiast na karcie podglądu IDE
Pokaż szczegóły | Wyświetl informacje o projekcie, pliku, wierszu i podsumowaniu z komentarzy do dokumentacji w oknie
Wyśrodkuj okno | Przenieś to okno do najwyższego środka edytora kodu zamiast w prawym górnym rogu

## <a name="see-also"></a>Zobacz też

- [Nawiguj po kodzie](../ide/navigating-code.md)
- [Idź do linii — Okno dialogowe](../ide/reference/go-to-line.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)

---
title: Przejdź do pliku, przejdź do symbolu, przejdź do wiersza
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb39f1d395e48351aeacb587556224b0f86aac3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593788"
---
# <a name="find-code-using-go-to-commands"></a>Znajdowanie kodu za pomocą poleceń Przejdź do

Polecenia Przejdź **do** programu Visual Studio wykonują skoncentrowane wyszukiwanie kodu, aby szybko znaleźć określone elementy. Możesz przejść do określonego wiersza, typu, symbolu, pliku i elementu członkowskiego z prostego, ujednoliconego interfejsu.

## <a name="how-to-use-it"></a>Korzystanie

Dane wejściowe | Funkcja
------------ | ---
**Klawiatura** | Naciśnij **klawisze Ctrl**+**T** lub **Ctrl**+**,**
**Mysz** | Wybierz **pozycję Edytuj** > **przejdź do** > **opcji Przejdź do wszystkich**

W prawym górnym rogu edytora kodu jest wyświetlane małe okno.

![Przejdź do wszystkich okna](media/go-to-all.png)

Podczas wpisywalnego pola tekstowego wyniki są wyświetlane na liście rozwijanej pod polem tekstowym. Aby przejść do elementu, wybierz go na liście.

![Nawiguj do okna](../ide/media/vside_navigatetowindow.png)

Możesz również wprowadzić znak zapytania (**?**), aby uzyskać dodatkową pomoc.

![Przejdź do wszystkich pomocy](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Wyszukiwarki filtrowane

Domyślnie określony element jest wyszukiwany we wszystkich elementach rozwiązania. Można jednak ograniczyć wyszukiwanie kodu do określonych typów elementów, prefacing wyszukiwanych terminów z określonymi znakami. Filtr wyszukiwania można również szybko zmienić, wybierając przyciski na pasku narzędzi okna dialogowego **Przejdź do.** Przyciski, które zmieniają filtry typu znajdują się po lewej stronie, a przyciski, które zmieniają zakres wyszukiwania, znajdują się po prawej stronie.

![Przejdź do członków](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrowanie do określonego typu elementu kodu

Aby zawęzić wyszukiwanie do określonego typu elementu kodu, można określić prefiks w polu wyszukiwania lub wybrać jedną z pięciu ikon filtru:

Prefiks | Ikona | Skrót | Opis
:-: | - | - | -
:| ![Ikona linii](media/gotoall-line-icon.png) | **Ctrl**+**G** | Przejdź do określonego numeru wiersza
k| ![Ikona Pliki](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | Przejdź do określonego pliku
r| ![Ikona ostatnich plików](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | Przejdź do określonego, ostatnio odsuwu pliku
t| ![Ikona Typy](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | Przejdź do określonego typu
m| ![Ikona członkowie](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | Przejdź do określonego elementu członkowskiego
\#| ![Ikona Symbole](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | Przejdź do określonego symbolu

### <a name="filter-to-a-specific-location"></a>Filtrowanie do określonej lokalizacji

Aby zawęzić wyszukiwanie do określonej lokalizacji, wybierz jedną z dwóch ikon dokumentu:

Ikona | Opis
---- | ---
![Bieżący dokument](media/gotoall_currentdocument.png) | Wyszukiwanie tylko bieżącego dokumentu
![Dokumenty zewnętrzne](media/gotoall_external.png) | Wyszukiwanie dokumentów zewnętrznych oprócz dokumentów znajdujących się w projekcie/rozwiązaniu

## <a name="camel-casing"></a>Obudowa wielbłąda

Jeśli używasz [camel obudowy](https://en.wikipedia.org/wiki/Camel_case) w kodzie, można znaleźć elementy kodu szybciej, wprowadzając tylko wielkie litery nazwy elementu kodu. Na przykład, jeśli kod ma `CredentialViewModel`typ o nazwie , można zawęzić wyszukiwanie, wybierając filtr **Typ** (`CVM`**t**), a następnie wprowadzając tylko wielkie litery nazwy ( ) w oknie dialogowym Przejdź do. Ta funkcja może być przydatna, jeśli kod ma długie nazwy.

![Nawiguj do okna - wyszukiwanie za pomocą wielkich liter](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ustawienia

Wybór ikony koła zębatego ![Ikona koła zębatego](media/gotoall_gear.png) pozwala zmienić sposób działania tej funkcji:

Ustawienie | Opis
------- | ---
Użyj karty podglądu | Natychmiast wyświetly zaznaczony element na karcie podglądu IDE
Pokaż szczegóły | Wyświetlanie informacji o projekcie, pliku, wierszu i podsumowaniu z komentarzy dokumentacji w oknie
Okno środkowe | Przenieś to okno do górnego środka edytora kodu, a nie w prawym górnym rogu

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie](../ide/navigating-code.md)
- [Idź do linii — Okno dialogowe](../ide/reference/go-to-line.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)

---
title: Projekty języka R
description: Jak utworzyć projekty w Menedżerze R w programie Visual Studio, w tym właściwości, polecenia projektu i szablony.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 42cdc6e964d23b5aafdfe225c04d5d35b151cc08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936408"
---
# <a name="create-r-projects-in-visual-studio"></a>Tworzenie projektów języka R w programie Visual Studio

Projekt R (plik *. RXPROJ* ) identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem. Zawiera również informacje o kompilacji dla każdego pliku, utrzymuje informacje do integracji z systemami kontroli źródła i pomaga organizować aplikację w składnikach logicznych. Informacje dotyczące obszaru roboczego, takie jak lista zainstalowanych pakietów, są jednak obsługiwane oddzielnie w obszarze roboczym.

Projekty są zawsze zarządzane w ramach *rozwiązania* programu Visual Studio, które może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Zobacz [Używanie wielu typów projektów w programie Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Tworzenie nowego projektu R

1. Otwórz program Visual Studio.
1. Wybierz pozycję **plik > nowy > projekt** (**Ctrl** + **SHIFT** + **N**)
1. Wybierz pozycję "projekt r" z sekcji **Szablony**  >  **R**, Nadaj projektowi nazwę i lokalizację, a następnie wybierz **przycisk OK**:

    ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w program VS2017)](media/getting-started-01-new-project.png)

To polecenie tworzy projekt z pustym *skryptem. Plik języka R* jest otwarty w edytorze. Należy również zauważyć, że w **Eksplorator rozwiązań** istnieją dwa inne pliki w projekcie:

![Zawartość projektu języka R utworzonego na podstawie szablonu](media/projects-template-results.png)

*. Rhistory* rejestruje wszelkie polecenia wprowadzane do okna [R Interactive](interactive-repl-for-r-in-visual-studio.md) . Możesz otworzyć dedykowane okno **historii przy użyciu**  >  polecenia **Windows History systemu Microsoft**  >   . To okno ma przycisk paska narzędzi i elementy menu kontekstowego, aby wyczyścić zawartość historii.

Plik *rproject. rproj* przechowuje niektóre ustawienia projektu specyficzne dla języka R, które nie są zarządzane w inny sposób przez program Visual Studio:

| Właściwość | Domyślne | Opis |
| --- | --- | --- |
| Wersja | 1.0 | Wersja R Tools for Visual Studio użyta do utworzenia projektu. |
| RestoreWorkspace | Domyślne | Automatycznie Ładuj poprzednie zmienne obszaru roboczego z `.RData` pliku w katalogu projektu. |
| SaveWorkspace | Domyślne | Zapisz bieżące zmienne obszaru roboczego do `.RData` pliku w katalogu projektu podczas zamykania projektu. |
| AlwaysSaveHistory | Domyślne | Zapisz bieżącą historię okna interaktywnego do `.RHistory` pliku w katalogu projektu podczas zamykania projektu. |
| EnableCodeIndexing | Tak | Określa, czy uruchomić zadanie indeksowania w tle w celu przyspieszenia wyszukiwania kodu. |
| UseSpacesForTab | Tak | Określa, czy należy wstawiać spacje (tak) czy znak tabulacji (nie) po naciśnięciu klawisza **Tab** w edytorze. |
| NumSpacesForTab | 2 | Liczba spacji do wstawienia, jeśli UseSpacesForTab ma wartość tak. |
| Encoding | UTF-8 | Domyślne kodowanie `.R` plików. |
| RnwWeave | Sweave | Pakiet, który ma być używany podczas natkania pliku RNW. |
| Pian | pdfLaTeX | Biblioteka do użycia podczas konwertowania RMarkdown do formatu PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Konwertowanie folderu plików na projekt języka R

Jeśli masz istniejący folder programu *. Pliki języka R* , które mają być zarządzane w projekcie, wykonaj następujące czynności:

1. Utwórz nowy projekt w programie Visual Studio, jak w poprzedniej sekcji.
1. Skopiuj pliki do folderu projektu.
1. W programie Visual Studio Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj**  >  **istniejący element** i przejdź do plików, które chcesz dodać. Te pliki pojawiają się w drzewie projektu po wybraniu przycisku **OK**.
1. Aby zorganizować kod w podfolderach, kliknij prawym przyciskiem myszy projekt, najpierw wybierz opcję **Dodaj**  >  **Nowy folder** , a następnie skopiuj pliki do tego folderu i Dodaj te istniejące elementy w kroku 3.

## <a name="project-properties"></a>Właściwości projektu

Aby otworzyć strony właściwości projektu, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** lub wybierz element menu **Właściwości > projektu (nazwa projektu)** . Otwarte okno wyświetla właściwości projektu:

| Tab | Właściwość | Opis |
| --- | --- | --- |
| Uruchom | Plik startowy | Nazwa pliku, który jest uruchamiany za pomocą polecenia **źródłowego pliku startowego** , **F5**,   >  **debugowanie rozpoczęcia** debugowania lub Rozpocznij **debugowanie**  >  **bez debugowania**. Kliknij prawym przyciskiem myszy plik w projekcie i wybierz polecenie **Ustaw jako startowy skrypt R** również ustawia go jako plik startowy. |
| | Resetuj R Interactive przy uruchomieniu | Czyści wszystkie zmienne z obszaru roboczego okna interaktywnego podczas uruchamiania projektu. To gwarantuje, że nie ma żadnej końcowej zawartości obszaru roboczego z poprzedniej. |
| | Ścieżka projektu zdalnego | Ścieżka do zdalnego obszaru roboczego. |
| | Transferowanie plików przy uruchomieniu | Wskazuje, czy pliki projektu, zgodnie z filtrem w **plikach do przeniesienia**, mają zostać skopiowane do zdalnego obszaru roboczego przy każdym uruchomieniu. |
| | Pliki do przesłania | Nazwy plików i symbole wieloznaczne wskazujące określone pliki do skopiowania do zdalnego obszaru roboczego, jeśli wybrano **pliki transferu w uruchomieniu** . |
| Ustawienia | (Plik Settings. R) | Ustawienia projektu języka R pochodzą z *ustawień. R* lub **. Settings. R* pliki, które znajdują się wewnątrz projektu. Jeśli nie ma pliku ustawień, możesz dodać zmienne, zapisać stronę i domyślny plik *Ustawienia. R* . Możesz również **dodać plik ustawień** do projektu za pomocą  >  polecenia menu **Dodaj nowy element** . <br/> Ustawienia są przechowywane jako kod języka R, a plik może być źródłem przed uruchomieniem innych modułów, co oznacza wstępne wypełnianie środowiska ze wstępnie zdefiniowanymi ustawieniami. |

## <a name="r-specific-project-commands"></a>Polecenia projektu specyficznego dla języka R

Projekty programu Visual Studio obsługują wiele ogólnych poleceń za pomocą menu dostępnego po kliknięciu prawym przyciskiem myszy i menu **projektu** . Aby uzyskać szczegółowe informacje na temat tych ogólnych funkcji, zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Należy jednak pamiętać, że R Tools for Visual Studio (RTVS) dodaje wiele własnych poleceń do menu po kliknięciu prawym przyciskiem myszy dla projektu R, a także plików i folderów w ramach projektu.

| Polecenie | Opis |
| --- | --- |
| Ustaw tutaj katalog roboczy | Ustawia katalog roboczy okna R Interactive do folderu projektu, który może być również używany w dowolnym podfolderze w projekcie. |
| Otwórz folder zawierający | Otwiera Eksploratora Windows w lokalizacji wybranego pliku. |
| Dodaj skrypt języka R | Tworzy i otwiera nowy *. Plik R* o nazwie domyślnej. Możesz również użyć polecenia **Dodaj**  >  **nowy element** , aby utworzyć *. Pliki języka R* oraz inne typy plików. Zobacz [Szablony elementów specyficznych dla języka R](#r-specific-item-templates). |
| Dodaj R Markdown | Tworzy i otwiera nowy dokument *. RMD* o nazwie domyślnej. Możesz również użyć polecenia **Dodaj**  >  **nowy element** , aby utworzyć pliki *RMD* oraz liczbę innych typów plików. Zobacz [Szablony elementów specyficznych dla języka R](#r-specific-item-templates).  |
| Publikuj procedury składowane | Uruchamia proces publikowania wszelkich procedur składowanych zawartych w skryptach języka R. Zobacz [pracy z SQL Server procedurami składowanymi](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Szablony elementów specyficznych dla języka R

RTVS zawiera wiele szablonów dla określonych typów plików. Aby uzyskać dostęp do szablonów, kliknij prawym przyciskiem myszy projekt R i wybierz polecenie **Dodaj**  >  **nowy element**, wybierając pozycję **projekt**  >  **Dodaj nowy element** lub używając **pliku**  >  **Nowy**  >  **plik** i wybierając kartę **R** . Najlepszym sposobem eksplorowania szablonu jest utworzenie nowego projektu i wstawienie plików każdego typu.

> [!Note]
> W   >  poleceniach Dodaj **nowy element** są również wyświetlane ogólne typy plików, które nie są wymienione w tabeli. plik o  >  **nowym**  >  **pliku** te typy są zawarte zamiast na karcie **Ogólne** .

| Typ pliku | Opis |
| --- | --- |
| Skrypt języka R | Plik tekstowy zawierający te same polecenia, które można wprowadzić w wierszu polecenia języka R. |
| Znaczniki R Markdown | Plik zawierający dokument [R MARKDOWN](rmarkdown-with-r-in-visual-studio.md) . |
| Ustawienia języka R | Plik, który zawiera ustawienia aplikacji języka R. |
| Dokumentacja języka R | Ogólny plik dokumentacji języka R zawierający tylko pola Nazwa, alias i tytuł. |
| Dokumentacja języka R (funkcja) | Plik dokumentacji języka R zawierający wiele pól z komentarzami opisującymi funkcję. |
| Dokumentacja języka R (DataSet) | Plik dokumentacji języka R zawierający wiele pól z komentarzami do opisywania zestawu danych. |
| Zapytanie SQL | Pusty plik *. SQL* . Zobacz [Work with SQL Server i R](integrating-sql-server-with-r.md). |
| Procedura składowana w języku R | Plik R z podrzędnym zapytaniem SQL i podrzędnym plikiem szablonu procedury składowanej. Zobacz [Work with SQL Server i R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Używanie wielu typów projektów w programie Visual Studio

Rozwiązania programu Visual Studio zapewniają wygodne miejsce do gromadzenia powiązanych projektów i zarządzania nimi w jednym miejscu logicznym. Rozwiązania ułatwiają organizację kodu i ułatwiają współpracę w zespołach.

W poniższym przykładzie rozwiązanie zawiera projekt języka R z modelem utworzonym przy użyciu języka R i Azure Machine Learning, projekt języka Python/scikit-uczenie, projekt C++ zawierający moduły do intensywnej pracy obliczeniowej, projekt SQL do zarządzania danymi oraz projekt Python/butelkowy dla witryny sieci Web, która publikuje wynik:

![Program Visual Studio Eksplorator rozwiązań pokazujący wiele powiązanych projektów w rozwiązaniu](media/projects-polyglot.png)

Projekt wyróżniony pogrubioną jest projektem "Start" dla rozwiązania; Aby to zmienić, kliknij prawym przyciskiem myszy inny projekt i wybierz polecenie **Ustaw jako projekt startowy**.

> [!Note]
> Obecnie nie ma żadnej jawnej integracji języka R z językiem C# (w przypadku platformy Python, w której znajduje się kod w języku [C++](../python/working-with-c-cpp-python-in-visual-studio.md)).  Dostępne są jednak biblioteki, które udostępniają mosty języka C# i C++ dla języka R.

Aby uzyskać więcej informacji na temat ogólnego zarządzania projektami i rozwiązaniami, zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

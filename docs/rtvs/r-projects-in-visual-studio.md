---
title: Projekty języka R
description: Jak utworzyć Menedżera projekty języka R w programie Visual Studio, w tym jej właściwości, polecenia projektów i szablonów.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: a24f887b5e8d12a757098eb94768ad110a5cb727
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669215"
---
# <a name="create-r-projects-in-visual-studio"></a>Tworzenie projektów języka R w programie Visual Studio

Projekt R ( *.rxproj* pliku) identyfikuje źródła i plikami zawartości skojarzonymi z projektem. Także zawiera informacje o kompilacji dla każdego pliku, przechowuje informacje w celu integracji z systemów kontroli źródła i pomaga organizować aplikację w logiczne składniki. Obszar roboczy informacje dotyczące na przykład listy zainstalowanych pakietów, jednak jest obsługiwana oddzielnie w obszar roboczy.

Projekty są zawsze zarządzane w ramach programu Visual Studio *rozwiązania*, która może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Zobacz [Użyj wiele typów projektów w programie Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Tworzenie nowego projektu języka R

1. Otwórz program Visual Studio.
1. Wybierz **Plik > Nowy > Projekt** (**Ctrl**+**Shift**+**N**)
1. Wybierz pozycję "Projekt R" w obszarze **szablony** > **R**, należy nadać projektowi nazwę i lokalizację i wybierz **OK**:

    ![Okno dialogowe Nowy projekt dla języka R w programie Visual Studio (RTVS w programie VS2017)](media/getting-started-01-new-project.png)

To polecenie tworzy projekt z pustym *skryptu. R* plik jest otwarty w edytorze. Zwróć uwagę, również w **Eksploratora rozwiązań** istnieją dwa inne pliki w projekcie:

![Zawartość projektu języka R utworzone na podstawie szablonu](media/projects-template-results.png)

*. Rhistory* rejestruje niezależnie od polecenia, możesz wprowadzić do [interaktywne R](interactive-repl-for-r-in-visual-studio.md) okna. Możesz otworzyć okno Historia dedykowanych z **R Tools** > **Windows** > **historii** polecenia. To okno ma narzędzi przycisk kontekstu elementy menu i wyczyścić zawartość historii.

*Rproject.rproj* pliku zachowuje niektóre ustawienia projektu specyficzne dla języka R, które w przeciwnym razie nie są zarządzane przez program Visual Studio:

| Właściwość | Domyślne | Opis |
| --- | --- | --- |
| Wersja | 1.0 | Wersja R Tools for Visual Studio używane do tworzenia projektu. |
| RestoreWorkspace | Domyślny | Automatyczne ładowanie poprzedniej zmienne obszaru roboczego z `.RData` pliku w katalogu projektu. |
| SaveWorkspace | Domyślny | Zapisz bieżący obszar roboczy zmienne `.RData` pliku w katalogu projektu podczas zamykania projektu. |
| AlwaysSaveHistory | Domyślny | Zapisz bieżące okno interaktywne historii `.RHistory` pliku w katalogu projektu podczas zamykania projektu. |
| EnableCodeIndexing | Tak | Określa, czy do uruchomienia zadania indeksowania w tle mogą przyspieszyć wyszukiwania kodu. |
| UseSpacesForTab | Tak | Określa, czy wstawiać miejsca do magazynowania (tak) lub znak tabulacji (Brak) gdy **kartę** zostanie naciśnięty klawisz w edytorze. |
| NumSpacesForTab | 2 | Liczba miejsc do magazynowania, jeżeli UseSpacesForTab to Yes. |
| Kodowanie | UTF-8 | Domyślne kodowanie `.R` plików. |
| RnwWeave | Sweave | Pakiet do użycia podczas tkania pliku Rnw. |
| LaTeX | pdfLaTeX | Biblioteki do użycia podczas konwertowania RMarkdwon do formatu PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Konwertowanie folder z plikami do projektu języka R

Jeśli masz istniejące foldery *. R* pliki, które mają być zarządzane w projekcie, wykonaj następujące czynności:

1. Utwórz nowy projekt w programie Visual Studio, tak jak w poprzedniej sekcji.
1. Skopiuj pliki do folderu projektu.
1. W Eksploratorze rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj** > **istniejący element**, a następnie przejdź do plików, które chcesz dodać. Te pliki są wyświetlane w drzewie Twojego projektu po wybraniu **OK**.
1. Aby zorganizować kodu w podfolderach, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj** > **nowy Folder** po pierwsze, następnie skopiuj pliki do tego folderu i dodać tych istniejących elementów w kroku 3.

## <a name="project-properties"></a>Właściwości projektu

Aby otworzyć na stronach właściwości projektu, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**, lub wybierz **projektu > właściwości (nazwa projektu)** menu element. W otwartym oknie Wyświetla właściwości projektu:

| Tab | Właściwość | Opis |
| --- | --- | --- |
| Uruchom | Plik startowy | Nazwa pliku, który jest uruchamiany z **źródłowy plik startowy** polecenia **F5**, **debugowania** > **Rozpocznij debugowanie**, lub  **Debugowanie** > **Uruchom bez debugowania**. Kliknij prawym przyciskiem myszy plik w projekcie i wybierając polecenie **ustawiony jako skrypt uruchamiania R** także ustawia go jako plik startowy. |
| | Resetuj R interakcyjne przy uruchomieniu | Czyści wszystkie zmienne z obszaru roboczego w oknie interaktywnym podczas uruchamiania projektu. Gwarancje tak tą operacją nie jest zawartość nie końcowej obszaru roboczego z poprzednich przebiegów. |
| | Ścieżka projektu zdalnego | Ścieżka do zdalnego obszaru roboczego. |
| | Transfer plików przy uruchomieniu | Wskazuje, czy projekt pliki podlegają filtru **plików do transferu**, mają zostać skopiowane do zdalnego obszaru roboczego z poszczególnymi uruchomieniami. |
| | Transfer plików | Nazwy plików i symboli wieloznacznych, wskazując określone pliki do skopiowania do zdalnego obszaru roboczego, jeśli **transferu plików przy uruchomieniu** jest zaznaczone. |
| Ustawienia | (Plik Settings.R) | Ustawienia projektu języka R pochodzą *Settings.R* lub **. Settings.R* pliki, które znajdują się w projekcie. Jeśli nie ma żadnego pliku ustawień, można dodać zmienne zapisywania strony i domyślnym *Settings.R* zostanie utworzony plik. Plik ustawień można również dodać do projektu przy użyciu **pliku** > **Dodaj nowy element** polecenia menu. <br/> Ustawienia są przechowywane jako kod języka R, a plik może być źródło przed uruchomieniem innych modułów, w związku z tym wstępne wypełnianie środowiska ze wstępnie zdefiniowanymi ustawieniami. |

## <a name="r-specific-project-commands"></a>Polecenia projektu specyficznego dla języka R

Projektów programu Visual Studio obsługuje szereg ogólne poleceń w menu kliknij prawym przyciskiem myszy i **projektu** menu. Aby uzyskać szczegółowe informacje dotyczące tych ogólnych możliwości, zobacz [rozwiązań i projektów w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md). Należy pamiętać, jednak czy R Tools for Visual Studio (RTVS) dodaje swoje własne polecenia do menu kontekstowe dla projektu języka R, a także pliki i foldery w projekcie.

| Polecenie | Opis |
| --- | --- |
| Ustaw katalog roboczy, w tym miejscu | Określa katalog roboczy okno interaktywne R do folderu projektu, który pozwala także na dowolnego podfolderu w ramach projektu. |
| Otwórz Folder zawierający | Zostanie otwarty Eksplorator Windows w lokalizacji wybranego pliku. |
| Dodaj skrypt języka R | Tworzy i otwiera nową *. R* plik o nazwie domyślnej. Można również użyć **Dodaj** > **nowy element** polecenie, aby utworzyć *. R* plików, a także wiele innych typów plików. Zobacz [szablonów elementów specyficznych dla języka R](#r-specific-item-templates). |
| Dodaj znaczniki R Markdown | Tworzy i otwiera nowe *.rmd* dokumentu o domyślnej nazwie. Można również użyć **Dodaj** > **nowy element** polecenie, aby utworzyć *.rmd* plików, a także wiele innych typów plików. Zobacz [szablonów elementów specyficznych dla języka R](#r-specific-item-templates).  |
| Publikuj procedury składowane | Uruchamia proces publikowania żadnych procedur składowanych zawarte w skryptów języka R. Zobacz [pracy za pomocą procedur składowanych serwera SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Szablony elementów specyficznych dla języka R

RTVS zawiera wiele szablonów dla określonych typów plików. Możesz uzyskać dostęp do szablonów, klikając prawym przyciskiem myszy projekt R i wybierając **Dodaj** > **nowy element**, wybierając **projektu**  >   **Dodaj nowy element**, lub za pomocą **pliku** > **New** > **pliku** i wybierając polecenie **R** kartę. Najlepszym sposobem, aby zapoznać się z szablonem jest utworzenie nowego projektu i wstawiania plików każdego typu.

> [!Note]
> **Dodaj** > **nowy element** polecenia również wyświetlić typy ogólne plików, które nie są wymienione w tabeli; **pliku** > **New**   >  **Pliku** te typy są zawarte w zamian na **ogólne** kartę.

| Typ pliku | Opis |
| --- | --- |
| Skrypt języka R | Plik tekstowy zawierający te same polecenia, które mogą być wprowadzane w wierszu polecenia języka R. |
| Znaczniki R Markdown | Plik zawierający [R Markdown](rmarkdown-with-r-in-visual-studio.md) dokumentu. |
| Ustawienia języka R | Plik, który zawiera ustawienia aplikacji R. |
| Dokumentace R | Ogólny plik dokumentacji języka R zawierający tylko nazwę aliasu i pola tytułu. |
| Dokumentace R (funkce) | Dokumentacja języka R plik zawierający wiele pól z komentarzami do opisywania funkcji. |
| Dokumentace R (zestaw danych) | Dokumentacja języka R plik zawierający wiele pól z komentarzami do opisywania zestawu danych. |
| SQL Query | I puste *.sql* pliku. Zobacz [pracy z programu SQL Server i R](integrating-sql-server-with-r.md). |
| Procedura składowana przy użyciu języka R | Plik języka R z podrzędnych zapytanie SQL i podrzędne przechowywane procedury pliku szablonu. Zobacz [pracy z programu SQL Server i R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Używanie wielu typów projektu w programie Visual Studio

Rozwiązania programu Visual Studio zapewnia wygodne miejsce do zbierania i Zarządzaj powiązanymi projektami w jednym miejscu logiczne. Rozwiązania pomaga w zapewnieniu kodu uporządkowane i usprawnia współpracę w obrębie zespołów.

W poniższym przykładzie rozwiązanie zawiera projekt R dzięki modelowi utworzone przy użyciu języka R i Azure Machine Learning, projektu języka Python/scikit-learn, projektu C++, zawierające modułów na potrzeby intensywnie korzystających z pracy obliczeniowej, projekt SQL do zarządzania danymi i języka Python/Bottle projekt witryny sieci web, która publikuje wyniki:

![Visual Studio Eksplorator rozwiązań wielu powiązanych projektów w rozwiązaniu](media/projects-polyglot.png)

Projekt wyróżnioną pogrubienie jest projektem "Uruchamianie" dla rozwiązania; Aby je zmienić, kliknij prawym przyciskiem myszy inny projekt, a następnie wybierz **Ustaw jako projekt startowy**.

> [!Note]
> Obecnie nie ma żadnych jawnych R, aby C#integracji języka /C++ (ponieważ ma dla języka Python, zobacz [Tworzenie rozszerzenia C++ dla języka Python](../python/working-with-c-cpp-python-in-visual-studio.md)).  Istnieją jednak dostępne biblioteki, które zapewniają C# i mostków C++ dla języka R.

Aby uzyskać więcej informacji na temat zarządzania projektami i rozwiązaniami ogólnie rzecz biorąc, zobacz [rozwiązań i projektów w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

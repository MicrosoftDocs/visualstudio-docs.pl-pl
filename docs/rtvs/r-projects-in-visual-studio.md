---
title: Projekty języka R
description: Jak utworzyć projekt menedżera R w programie Visual Studio, w tym właściwości, polecenia projektu i szablony.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302694"
---
# <a name="create-r-projects-in-visual-studio"></a>Tworzenie projektów języka R w programie Visual Studio

Projekt R (plik *rxproj)* identyfikuje wszystkie pliki źródłowe i zawartości skojarzone z projektem. Zawiera również informacje kompilacji dla każdego pliku, przechowuje informacje do integracji z systemami kontroli źródła i pomaga zorganizować aplikację w składniki logiczne. Informacje związane z obszarem roboczym, takie jak lista zainstalowanych pakietów, są jednak przechowywane oddzielnie w samym obszarze roboczym.

Projekty są zawsze zarządzane w ramach *rozwiązania*visual studio , które mogą zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie nawzajem. Zobacz [Używanie wielu typów projektów w programie Visual Studio](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Tworzenie nowego projektu R

1. Otwórz program Visual Studio.
1. Wybierz **polecenie > nowy projekt >** **(Ctrl**+**Shift**+**N**)
1. Wybierz "Projekt R" w obszarze **Szablony** > **R**, nadaj projektowi nazwę i lokalizację, a następnie wybierz **przycisk OK:**

    ![Nowe okno dialogowe projektu dla języka R w programie Visual Studio (RTVS w programie VS2017)](media/getting-started-01-new-project.png)

To polecenie tworzy projekt z pustym *skryptem. R* plik otwarty w edytorze. Zwróć uwagę również w **Eksploratorze rozwiązań** istnieją dwa inne pliki w projekcie:

![Zawartość projektu R utworzonego na podstawie szablonu](media/projects-template-results.png)

W *. Rhistory* rejestruje niezależnie od poleceń wprowadzonych w oknie [R Interactive.](interactive-repl-for-r-in-visual-studio.md) Dedykowane okno historii można otworzyć za pomocą**polecenia** Historia**systemu Windows** >  **narzędzi** > R. To okno zawiera przycisk paska narzędzi i elementy menu kontekstowego, aby wyczyścić zawartość historii.

Plik *rproject.rproj* zachowuje pewne ustawienia projektu specyficzne dla języka R, które w przeciwnym razie nie są zarządzane przez program Visual Studio:

| Właściwość | Domyślne | Opis |
| --- | --- | --- |
| Wersja | 1.0 | Wersja narzędzia języka R dla programu Visual Studio używane do tworzenia projektu. |
| Obszar przywracania | Domyślne | Automatycznie ładuj poprzednie zmienne `.RData` obszaru roboczego z pliku w katalogu projektu. |
| Obszar pracy save | Domyślne | Podczas zamykania projektu zapisywanie bieżących zmiennych obszaru roboczego `.RData` w pliku w katalogu projektu. |
| ZawszeSaveHistory | Domyślne | Zapisz bieżącą historię `.RHistory` interakcyjnego okna w pliku w katalogu projektu podczas zamykania projektu. |
| Włącz funkcję Kodowanie | Tak | Określa, czy ma być uruchamiane zadanie indeksowania w tle, aby przyspieszyć wyszukiwanie kodu. |
| Przy użyciu przestrzenifortab | Tak | Określa, czy spacje mają być wstawiane (Tak) czy znak Tab (Nie) po naciśnięciu **klawisza Tab** w edytorze. |
| NumSpacesForTab | 2 | Liczba spacji do wstawienia, jeśli usespacesfortab jest Tak. |
| Kodowanie | UTF-8 | Domyślne kodowanie `.R` plików. |
| RnwWeave ( RnwWeave ) | Sweave (Sweave) | Pakiet do użycia podczas tkania pliku Rnw. |
| Lateks | pdfLaTeX | Biblioteka do użycia podczas konwertowania RMarkdown na plik PDF. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Konwertowanie folderu plików na projekt R

Jeśli masz istniejący folder *. Pliki R,* którymi chcesz zarządzać w projekcie, wykonaj następujące czynności:

1. Utwórz nowy projekt w programie Visual Studio, tak jak w poprzedniej sekcji.
1. Skopiuj pliki do folderu projektu.
1. W Eksploratorze rozwiązań programu Visual Studio kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Dodaj** > **istniejący element**i przejdź do plików, które chcesz dodać. Te pliki pojawiają się w drzewie projektu po wybraniu **przycisku OK**.
1. Aby uporządkować kod w podfolderach, kliknij prawym przyciskiem myszy projekt, wybierz najpierw **pozycję Dodaj** > **nowy folder,** a następnie skopiuj pliki do tego folderu i dodaj te istniejące elementy w kroku 3.

## <a name="project-properties"></a>Właściwości projektu

Aby otworzyć strony właściwości projektu, kliknij projekt prawym przyciskiem myszy w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**lub wybierz element menu **Właściwości > projektu (nazwa projektu).** W oknie, które się otwiera, są wyświetlane właściwości projektu:

| Tab | Właściwość | Opis |
| --- | --- | --- |
| Run | Plik startowy | Nazwa pliku uruchamianego za pomocą polecenia **Plik startowy Źródła,** **F5**, **Debugowanie** > **start debugowania**lub **Debugowanie** > **Start bez debugowania**. Kliknięcie prawym przyciskiem myszy pliku w projekcie i **wybranie opcji Ustaw jako skrypt R startowego** powoduje również ustawienie go jako pliku startowego. |
| | Resetuj program R Interactive w trybie uruchamiania | Czyści wszystkie zmienne z obszaru roboczego okna interaktywnego podczas uruchamiania projektu. W ten sposób gwarantuje, że nie ma pozostałości zawartości obszaru roboczego z pervious działa. |
| | Zdalna ścieżka projektu | Ścieżka do zdalnego obszaru roboczego. |
| | Przesyłanie plików w biegu | Wskazuje, czy pliki projektu, podlegające filtrowi w **plikach do przesłania,** mają być kopiowane do zdalnego obszaru roboczego przy każdym uruchomieniu. |
| | Pliki do przesłania | Nazwy plików i symbole wieloznaczne wskazujące określone pliki do skopiowania do zdalnego obszaru roboczego, jeśli wybrano **przesyłanie plików w środowisku.** |
| Ustawienia | (Plik Settings.R) | R ustawienia projektu pochodzą z *Settings.R* lub **. Settings.R* plików, które znajdują się wewnątrz projektu. Jeśli nie ma pliku ustawień, można dodać zmienne, zapisać stronę i utworzyć domyślny plik *Settings.R.* Plik ustawień można również dodać do projektu za pomocą polecenia menu Dodaj nowy **element.** > **Add New Item** <br/> Ustawienia są przechowywane jako kod R, a plik może być pozyskiwany przed uruchomieniem innych modułów, co wstępnie wypełnia środowisko ze wstępnie zdefiniowanymi ustawieniami. |

## <a name="r-specific-project-commands"></a>Polecenia projektu specyficzne dla R

Projekty programu Visual Studio obsługują szereg poleceń ogólnych za pośrednictwem menu po kliknięciu prawym przyciskiem myszy i menu **Projekt.** Aby uzyskać szczegółowe informacje na temat tych ogólnych możliwości, zobacz [Rozwiązania i projekty w programie Visual Studio.](../ide/solutions-and-projects-in-visual-studio.md) Należy jednak pamiętać, że R Tools for Visual Studio (RTVS) dodaje szereg własnych poleceń do menu po kliknięciu prawym przyciskiem myszy dla projektu języka R, a także pliki i foldery w projekcie.

| Polecenie | Opis |
| --- | --- |
| Ustaw katalog roboczy tutaj | Ustawia katalog roboczy okna R Interactive na folder projektu, który może być również używany w dowolnym podfolderze w projekcie. |
| Otwórz folder zawierający | Otwiera Eksploratora Windows w lokalizacji wybranego pliku. |
| Dodaj skrypt R | Tworzy i otwiera nowy *plik . R* o nazwie domyślnej. Do utworzenia polecenia Dodaj nowy element można również użyć polecenia **Dodaj** > **nowy element** *. R,* a także wiele innych typów plików. Zobacz [Szablony elementów specyficznych dla R](#r-specific-item-templates). |
| Dodaj R Markdown | Tworzy i otwiera nowy dokument *rmd* o domyślnej nazwie. Za pomocą polecenia **Dodaj** > **nowy element** można również utworzyć pliki *rmd,* a także wiele innych typów plików. Zobacz [Szablony elementów specyficznych dla R](#r-specific-item-templates).  |
| Publikowanie procedur przechowywanych | Rozpoczyna proces publikowania wszelkich procedur przechowywanych zawartych w skryptach języka R. Zobacz [Praca z procedurami przechowywanymi programu SQL Server](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>Szablony elementów specyficznych dla R

RTVS zawiera szereg szablonów dla określonych typów plików. Dostęp do szablonów można uzyskać, klikając prawym przyciskiem myszy projekt R i wybierając pozycję **Dodaj** > **nowy element,** wybierając pozycję **Project** > **Add New Item**lub używając **pliku** > **nowy** > **plik** i wybierając kartę **R.** Najlepszym sposobem eksplorowania szablonu jest utworzenie nowego projektu i wstawienie plików każdego typu.

> [!Note]
> Polecenia **Dodaj** > **nowy element** wyświetlają również ogólne typy plików, których nie ma w tabeli; z **plikiem** > **nowy** > **plik** te typy są zawarte zamiast na karcie **Ogólne.**

| Typ pliku | Opis |
| --- | --- |
| Skrypt języka R | Plik tekstowy zawierający te same polecenia, które można wprowadzić w wierszu polecenia R. |
| Znaczniki R Markdown | Plik zawierający dokument [R Markdown.](rmarkdown-with-r-in-visual-studio.md) |
| Ustawienia R | Plik zawierający ustawienia aplikacji R. |
| Dokumentacja R | Ogólny plik dokumentacji R zawierający tylko nazwy, alias i pola tytułu. |
| Dokumentacja R (funkcja) | Plik dokumentacji R zawierający wiele pól z komentarzami opisującymi funkcję. |
| Dokumentacja R (zestaw danych) | Plik dokumentacji R zawierający wiele pól z komentarzami do opisywania zestawu danych. |
| Kwerenda SQL | Pusty plik *.sql.* Zobacz [Praca z programem SQL Server i R](integrating-sql-server-with-r.md). |
| Procedura składowana z R | Plik języka R z podrzędnym plikiem szablonu sql query i podrzędnym plikiem szablonu procedury składowanej. Zobacz [Praca z programem SQL Server i R](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Używanie wielu typów projektów w programie Visual Studio

Rozwiązania programu Visual Studio zapewniają wygodne miejsce do zbierania powiązanych projektów i zarządzania nimi w jednym logicznym miejscu. Rozwiązania pomagają utrzymać porządek w kodzie i ułatwiają współpracę w zespołach.

W poniższym przykładzie rozwiązanie zawiera projekt języka R z modelem zbudowanym przy użyciu usługi R i Azure Machine Learning, projekt Python/scikit-learn, projekt C++ zawierający moduły intensywnej pracy obliczeniowej, projekt SQL do zarządzania danymi oraz projekt Python/Bottle dla witryny sieci web, która publikuje wynik:

![Eksplorator rozwiązań programu Visual Studio przedstawiający wiele powiązanych projektów w rozwiązaniu](media/projects-polyglot.png)

Projekt wyróżniony pogrubioną twarzą jest projektem "startupowym" dla rozwiązania; aby go zmienić, kliknij prawym przyciskiem myszy inny projekt i wybierz pozycję **Ustaw jako projekt startowy**.

> [!Note]
> Obecnie nie ma żadnych jawnych r do języka C#/C++ integracji w miejscu (jak istnieje w pythonie, zobacz [Tworzenie rozszerzenia C++ dla Języka Python).](../python/working-with-c-cpp-python-in-visual-studio.md)  Istnieją jednak biblioteki dostępne, które zapewniają C# i C++ mosty dla języka R.

Aby uzyskać więcej informacji na temat zarządzania projektami i rozwiązaniami w ogóle, zobacz [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

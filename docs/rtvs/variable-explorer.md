---
title: Narzędzie Variable Explorer dla języka R
description: Narzędzie Variable Explorer w programie Visual Studio zawiera wszystkie zmienne w danym zakresie w bieżącej sesji języka R:.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d5058931e5568b7a84016e599faced9ae614e80d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000262"
---
# <a name="variable-explorer"></a>Eksplorator zmiennych

**Narzędzie Variable Explorer** oknie otwierane przy użyciu **R Tools** > **Windows** > **narzędzie Variable Explorer** (lub **Ctrl**+**8** jeśli używano **R Tools** > **ustawienia do nauki o danych**), zawiera wszystkie zmienne w danym zakresie w bieżącej sesji języka R:. Na przykład, jeśli otworzysz **narzędzie Variable Explorer** i wprowadź następujące wiersze w [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**Narzędzie Variable Explorer** zostanie wyświetlone okno w następujący sposób:

![Okno Eksplorator zmiennych w programie Visual Studio](media/variable-explorer-window.png)

W przypadku bardziej złożonych ramki danych języka R, zdefiniowane w sesji można przejść do danych. Na przykład po uruchomieniu `cars <- mtcars` możesz przejść za pomocą zestawu danych, rozwijając poszczególnych węzłów w **narzędzie Variable Explorer**:

![Rozwinięty widok Eksplorator zmiennych](media/variable-explorer-expanded-results.png)

Aby usunąć zmienne, kliknij prawym przyciskiem myszy i wybierz **Usuń**, lub wybrać zmienną i naciśnij klawisz **Usuń** klucza.

Możesz również wyszukać obserwacji w ramce danych przy użyciu Wyszukiwanie przyrostowe. Po pierwsze rozwiń węzły w ramce danych, który chcesz wyszukać, a następnie wprowadź terminy wyszukiwania w polu wyszukiwania.

## <a name="details-table-view"></a>Widok szczegółów (tabela)

Ponieważ dane są często tabelarycznych, dowolny typ złożony danych, można wyświetlić jako osobnej tabeli, wybierając ikonę lupy, lub kliknij prawym przyciskiem myszy i wybierając **Pokaż szczegóły**.

![Widok Eksploratora zmiennych w tabeli](media/variable-explorer-table-view.png)

Kliknięcie nagłówka kolumny sortuje je według kolumny (Przełączanie pomiędzy rosnącej na malejącą lub odwrotnie). Przytrzymanie **Shift** i klikając dodatkowe kolumny dodaje te kolumny do także sortowania. Kliknięcie kolumny bez **Shift** zwraca pojedynczą kolumnę sortowania.

Sekwencja, w którym możesz kliknąć nagłówki kolumn określa kolejność, w którym jest wykonywane sortowanie. Na przykład **Shift**+**kliknij** **cyl** kolumny, a następnie **Shift**+**kliknij** **mpg** kolumny dwa razy, aby posortować listę dla cylindrów rosnącej na malejącą lub odwrotnie milach na galon:

![Widok tabeli Sortowanie według dwóch kolumn danych.](media/variable-explorer-table-view-sorting.png)

Ponieważ **narzędzie Variable Explorer** i widoki tabel znajdują się w oddzielnych okna programu Visual Studio, można rozmieścić je jednak side-by-side pracy, takich jak. Zobacz [dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) ogólne instrukcje.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otwórz w programie Excel (lub inne aplikacje obsługujące CSV)

Do dalszych manipulacji i analizy jest często przydatne do wyeksportowania zmienne sesji do pliku CSV. Eksportowanie jest przeprowadzane za pomocą mała ikona programu Excel (![ikonę eksportowania programu Excel](media/variable-explorer-excel-icon.png)) obok każdego węzła w **narzędzie Variable Explorer**, lub kliknij element prawym przyciskiem myszy i wybierając **Otwórz w aplikacji CSV**. Wybierając ikonę zapisuje dane do pliku CSV w *%userprofile%\Documents\RTVS_CSV_Exports* folder, a następnie uruchamia pliku i otwiera go w dowolnych aplikacji jest skojarzona z *CSV*rozszerzenia.

## <a name="scopes"></a>Zakresy

Domyślnie **narzędzie Variable Explorer** otwiera się w zakresie globalnym. Aby przełączyć się zasięg pakietu, należy wybrać pakiet z listy rozwijanej w górnej części okna.

![Eksplorator zmiennych zakresu pakietu](media/variable-explorer-package-scopes.png)

Możesz również przełączyć się do zakresu funkcji, po zatrzymaniu w punkcie przerwania w debugerze (należy pamiętać, że **narzędzie Variable Explorer** nie powoduje automatycznego przełączenia do zakresu funkcji kodu debugowany):

![Narzędzie Variable Explorer przedstawiający ramki danych podczas debugowania](media/variable-explorer-as-locals-window.png)

**Narzędzie Variable Explorer** automatycznie zmiany funkcji zakresu, jak krok po kroku przez kod w debugerze, takich jak Pokazywanie zmiennych lokalnych w funkcji.

## <a name="import-data-into-variable-explorer"></a>Importowanie danych do Eksplorator zmiennych

Dwa polecenia w **narzędzie Variable Explorer** narzędzi, które są również dostępne za pośrednictwem **R Tools** > **danych** menu zewnętrznych CSV zestawy danych importowania do usługi języka R Sesja:  **Importowanie zestawu danych do sesji języka R na adres URL sieci Web** i **zaimportować zestaw danych do sesji języka R z pliku tekstowego**.

Po zidentyfikowaniu pliku CSV można zaimportować Visual Studio Wyświetla **Importowanie zestawu danych** okna dialogowego, w którym masz opcje do kontrolowania, jak ten plik danych jest analizowany (oznacza to, co to jest separator pola i sposób obsługi ofert). Można także wyświetlić podgląd ramki zaimportowanych danych i oryginalny plik danych:

![Okno dialogowe importowania zestawu danych](media/variable-explorer-import-dataset-dialog.png)

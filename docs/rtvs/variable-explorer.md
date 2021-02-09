---
title: Eksplorator zmiennych dla języka R
description: Eksplorator zmiennych w programie Visual Studio Wyświetla wszystkie zmienne w danym zakresie w bieżącej sesji języka R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: f69e5b61e80d3a00522307dd7481f74418407d99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851806"
---
# <a name="variable-explorer"></a>Eksplorator zmiennych

Okno **Eksplorator zmiennych** , otwarte przy użyciu **narzędzi r Tools**  >  **Windows**  >  **Eksplorator zmiennych** (lub **Ctrl** + **8** , jeśli użyto **narzędzi r Tools**  >  **nauka o danych — ustawienia**), pokazuje wszystkie zmienne w danym zakresie w bieżącej sesji języka r. Na przykład, jeśli otworzysz **Eksplorator zmiennych** i wprowadzisz następujące wiersze w [oknie interaktywnym](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Okno **Eksplorator zmiennych** zostanie wyświetlone w następujący sposób:

![Okno Eksploratora zmiennych w programie Visual Studio](media/variable-explorer-window.png)

Jeśli w sesji zdefiniowano bardziej złożoną ramkę danych języka R, możesz przejść do danych. Na przykład po uruchomieniu można `cars <- mtcars` nawigować przez zestaw danych, rozszerzając różne węzły w **Eksplorator zmiennych**:

![Rozwinięty widok Eksplorator zmiennych](media/variable-explorer-expanded-results.png)

Aby usunąć zmienne, kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń** lub wybierz zmienną i naciśnij klawisz **delete** .

Możesz również wyszukać obserwację w ramce danych przy użyciu wyszukiwania przyrostowego. Najpierw rozwiń węzły w ramce danych, którą chcesz wyszukać, a następnie wprowadź terminy wyszukiwania w polu wyszukiwania.

## <a name="details-table-view"></a>Widok szczegółów (tabela)

Ponieważ dane są często tabelaryczne, można wyświetlić dowolny złożony typ danych jako osobną tabelę, wybierając ikonę lupy lub klikając prawym przyciskiem myszy i wybierając pozycję **Pokaż szczegóły**.

![Widok tabeli Eksplorator zmiennych](media/variable-explorer-table-view.png)

Kliknięcie nagłówka kolumny sortuje dane według kolumny (zmienne między rosnącą i malejącą). Wciśnięcie **klawisza Shift** i kliknięcie pozycji dodatkowe kolumny spowoduje również dodanie tych kolumn do sortowania. Kliknięcie kolumny bez **przesunięcia** do sortowania pojedynczej kolumny.

Sekwencja, w której klikasz nagłówki kolumn określa kolejność wykonywania sortowania. Na przykład naciśnij **klawisz Shift** + , a następnie **kliknij kolumnę** **CYL** , a następnie  + **kliknij dwukrotnie przycisk** " **MPG** ", aby posortować listę dla rosnących cylindrów oraz malejące mile na galon:

![Widok tabeli sortowania danych według dwóch kolumn.](media/variable-explorer-table-view-sorting.png)

Ponieważ **Eksplorator zmiennych** i widoki tabel znajdują się w osobnych oknach programu Visual Studio, można je rozmieścić w taki sam sposób, jak w przypadku pracy obok siebie. Ogólne instrukcje można znaleźć [w temacie Dostosowywanie układów okien w programie Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) .

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otwórz w programie Excel (lub innej aplikacji obsługującej CSV)

Aby zapewnić dalsze manipulowanie i analizę, często warto wyeksportować zmienne sesji do woluminu CSV. Eksportowanie odbywa się z małą ikoną programu Excel ( ![ ikona eksportu programu Excel ](media/variable-explorer-excel-icon.png) ) obok każdego węzła w **Eksplorator zmiennych** lub klikając prawym przyciskiem myszy element i wybierając polecenie **Otwórz w aplikacji CSV**. Wybranie ikony spowoduje zapisanie danych w nowym pliku CSV w folderze *%userprofile%\documents\ RTVS_CSV_Exports* , a następnie uruchomienie tego pliku, otwierając go w dowolnej aplikacji skojarzonej z rozszerzeniem *CSV* .

## <a name="scopes"></a>Zakresy

Domyślnie **Eksplorator zmiennych** otwiera zakres globalny. Możesz przełączyć się do zakresu pakietu, wybierając pakiet z listy rozwijanej w górnej części okna.

![Eksplorator zmiennych pokazujący zakres pakietu](media/variable-explorer-package-scopes.png)

Możesz również przełączyć się do zakresu funkcji po zatrzymaniu w punkcie przerwania w debugerze (należy zauważyć, że **Eksplorator zmiennych** nie przełączy się automatycznie z zakresem funkcji debugowanego kodu):

![Eksplorator zmiennych wyświetlania ramki danych podczas debugowania](media/variable-explorer-as-locals-window.png)

**Eksplorator zmiennych** automatycznie zmienia zakres funkcji podczas przechodzenia przez kod w debugerze, takich jak wyświetlanie zmiennych lokalnych w funkcji.

## <a name="import-data-into-variable-explorer"></a>Importuj dane do Eksplorator zmiennych

Dwa polecenia na pasku narzędzi **Eksplorator zmiennych** , które są również dostępne za pośrednictwem menu dane **Narzędzia R Tools**  >   , Importuj zewnętrzne zestawy danych CSV do sesji języka r: **Importuj zestaw danych do sesji języka r z internetowego adresu URL** i **Importuj zestaw danych do sesji języka r z pliku tekstowego**.

Po zidentyfikowaniu pliku CSV, który ma zostać zaimportowany, program Visual Studio wyświetli okno dialogowe **Importowanie zestawu danych** , w którym można kontrolować sposób analizowania tego pliku danych (czyli to, co to jest separator pola i jak obsługiwać cudzysłowy). Możesz również wyświetlić podgląd zaimportowanej ramki danych i oryginalnego pliku danych:

![Okno dialogowe Importowanie zestawu danych](media/variable-explorer-import-dataset-dialog.png)

---
title: Eksplorator zmiennych dla R
description: Eksplorator zmiennych w programie Visual Studio pokazuje wszystkie zmienne w danym zakresie w bieżącej sesji języka R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809873"
---
# <a name="variable-explorer"></a>Eksplorator zmiennych

Okno **Eksplorator zmiennych,** otwarte przy użyciu **R Tools** > **Eksplorator** > **zmiennych windows** (lub **Ctrl**+**8,** jeśli używano ustawień nauki**danych**R **Tools),** > pokazuje wszystkie zmienne w danym zakresie w bieżącej sesji języka R. Na przykład, jeśli otworzysz **Eksplorator zmiennych** i wprowadzisz następujące wiersze w [oknie interaktywnym:](interactive-repl-for-r-in-visual-studio.md)

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Następnie okno **Eksplorator zmiennych** jest wyświetlane w następujący sposób:

![Okno Eksploratora zmiennych w programie Visual Studio](media/variable-explorer-window.png)

Jeśli w sesji zdefiniowano bardziej złożoną ramkę danych R, możesz przejść do danych. Na przykład po `cars <- mtcars` uruchomieniu można poruszać się po zestawie danych, rozwijając różne węzły w **Eksploratorze zmiennych:**

![Rozszerzony widok Eksploratora zmiennych](media/variable-explorer-expanded-results.png)

Aby usunąć zmienne, kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń**lub zaznacz ją i naciśnij klawisz **Delete.**

Można również wyszukać obserwację w ramce danych za pomocą wyszukiwania przyrostowego. Najpierw rozwiń węzły w ramce danych, którą chcesz przeszukać, a następnie wprowadź wyszukiwane terminy w polu wyszukiwania.

## <a name="details-table-view"></a>Widok szczegóły (tabela)

Ponieważ dane są często tabelaryczne, można wyświetlić dowolny złożony typ danych jako osobną tabelę, wybierając ikonę lupy lub klikając prawym przyciskiem myszy i wybierając polecenie **Pokaż szczegóły**.

![Widok tabeli Eksploratora zmiennych](media/variable-explorer-table-view.png)

Kliknięcie nagłówka kolumny sortuje dane według kolumny (na przemian rosnąco i malejąco). Przytrzymanie **klawisza Shift** i kliknięcie dodatkowych kolumn powoduje dodanie tych kolumn do sortowania. Kliknięcie kolumny bez **zmiany** powoduje powrót do sortowania pojedynczych kolumn.

Kolejność klikania nagłówków kolumn określa kolejność wykonywania sortowania. Na przykład **shift**+**kliknij** kolumnę **cyl,** a następnie **shift**+**kliknij** dwukrotnie kolumnę **mpg,** aby posortować listę rosnących cylindrów i malejących mil na galon:

![Widok tabeli sortowania danych według dwóch kolumn.](media/variable-explorer-table-view-sorting.png)

Ponieważ **Eksplorator zmiennych** i widoki tabel znajdują się w oddzielnych oknach programu Visual Studio, można je rozmieścić w trybie rzeczywistym do pracy obok siebie. Zobacz [Dostosowywanie układów okien w programie Visual Studio,](../ide/customizing-window-layouts-in-visual-studio.md) aby uzyskać ogólne instrukcje.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Otwórz w programie Excel (lub innej aplikacji obsługującej csv)

Do dalszej manipulacji i analizy często warto eksportować zmienne sesji do pliku CSV. Eksportowanie odbywa się za pomocą![małej](media/variable-explorer-excel-icon.png)ikony programu Excel (ikona eksportu programu Excel) obok każdego węzła w **Eksploratorze zmiennych**lub przez kliknięcie prawym przyciskiem myszy elementu i wybranie opcji **Otwórz w aplikacji CSV**. Wybranie ikony powoduje zapisanie danych w nowym pliku CSV w folderze *%userprofile%\Documents\RTVS_CSV_Exports,* a następnie uruchomienie tego pliku, który otwiera go w dowolnej aplikacji skojarzonej z rozszerzeniem *csv.*

## <a name="scopes"></a>Zakresy

Domyślnie **Eksplorator zmiennych** otwiera zakres globalny. Można przełączyć się do zakresu pakietu, wybierając pakiet z listy rozwijanej w górnej części okna.

![Eksplorator zmiennych przedstawiający zakres pakietu](media/variable-explorer-package-scopes.png)

Można również przełączyć się do zakresu funkcji po zatrzymaniu w punkcie przerwania w debugerze (należy pamiętać, że **Eksplorator zmiennych** nie przełącza się automatycznie do zakresu funkcji kodu, który jest debugowany):

![Eksplorator zmiennych przedstawiający ramkę danych podczas debugowania](media/variable-explorer-as-locals-window.png)

**Eksplorator zmiennych** automatycznie zmienia zakres funkcji podczas przechodzenia przez kod w debugerze, na przykład pokazując zmienne lokalne w funkcji.

## <a name="import-data-into-variable-explorer"></a>Importowanie danych do Eksploratora zmiennych

Dwa polecenia na pasku narzędzi **Eksploratora zmiennych,** które są również dostępne za pośrednictwem menu > **Dane** **narzędzi R,** importują zewnętrzne zestawy danych CSV do sesji R: **Importuj zestaw danych do sesji R z adresu URL sieci Web** i **Importuj zestaw danych do sesji R z pliku tekstowego**.

Po zidentyfikowaniu pliku CSV do zaimportowania program Visual Studio wyświetla okno dialogowe **Importuj zestaw danych,** w którym dostępne są opcje kontrolowania sposobu analizowania tego pliku danych (czyli separatora pól i sposobu obsługi cudzysłowów). Można również wyświetlić podgląd importowanej ramki danych i oryginalnego pliku danych:

![Okno dialogowe Importowanie zestawu danych](media/variable-explorer-import-dataset-dialog.png)

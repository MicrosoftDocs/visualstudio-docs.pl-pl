---
title: Opcje narzędzi języka R
description: Informacje dotyczące opcji w programie Visual Studio dla języka R i skojarzonych funkcji.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ed2ee29fb7a0a832dd3076cbd47a7f9cd1414d96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939477"
---
# <a name="r-tools-for-visual-studio-options"></a>Opcje R Tools for Visual Studio

Ustawienia są dostępne za pomocą menu Opcje **Narzędzia r Tools**  >   lub **narzędzi**  >  **Opcje** i przewijanie do **narzędzi języka r**:

  ![Okno dialogowe opcji dla narzędzi R Tools](media/options-dialog.png)

Opcje i ustawienia specyficzne dla języka R są dostępne przy użyciu poniższych metod. Należy zaznaczyć pole wyboru **Pokaż wszystkie ustawienia** w dolnej części okna dialogowego **Opcje** dla wszystkich tych sekcji do wyświetlenia.

- Opcje formatowania kodu (zobacz [Opcje edytora](editing-r-code-in-visual-studio.md#editor-options): **Narzędzia**  >  **Opcje** menu, a następnie wybierz **Edytor tekstu**  >  **R**  >  
- Opcje Linter (zobacz [Zaznaczanie błędów](linting-r-code.md)): **Narzędzia**  >  menu **Opcje** , a następnie wybierz **Edytor tekstu**  >  **R**  >  **lint**
- Zaawansowane opcje edytora ([opisane w tym artykule](#text-editor--r--advanced-options)): **Narzędzia**  >  menu **Opcje** , a następnie wybierz **Edytor tekstu**  >  **R**  >  **Advanced**
- Opcje behawioralne ([opisane w tym artykule](#r-tools--advanced-options)): **Narzędzia r Tools**  >  menu **Opcje** lub **Narzędzia**  >  , a następnie przewiń do **Narzędzia R Tools**.

Polecenie **R Tools**  >  **nauka o danych — ustawienia** ma także wpływ na wiele różnych ustawień w programie Visual Studio. To polecenie zostało opisane w następnej sekcji.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Narzędzia R > Nauka o danych — ustawienia

Element menu **> narzędzia R Tools nauka o danych — ustawienia** KONFIGURUJE środowisko IDE programu Visual Studio z układem zoptymalizowanym pod kątem potrzeb analityków danych. W przypadku tej opcji program otwiera okna [interakcyjne](interactive-repl-for-r-in-visual-studio.md), [Eksplorator zmiennych](variable-explorer.md)i [obszary robocze](r-workspaces-in-visual-studio.md) :

![Układ okna analityków danych w programie Visual Studio](media/installation-data-scientist-layout-result.png)

Aby później wrócić do innych ustawień programu Visual Studio, należy najpierw użyć   >  polecenia **Importuj i Eksportuj ustawienia** , wybierz opcję **Eksportuj wybrane ustawienia środowiska** i podaj nazwę pliku. Aby przywrócić te ustawienia, użyj tego samego polecenia i wybierz opcję **Importuj wybrane ustawienia środowiska**. Możesz również użyć tych samych poleceń, jeśli zmienisz układ Analityka danych i chcesz wrócić do niego później, zamiast używać polecenia **nauka o danych — ustawienia** .

## <a name="text-editor--r--advanced-options"></a>Edytor tekstu > opcji R > Advanced

Opcje te kontrolują zachowanie formatowania, IntelliSense, konspekt, wcięcia i sprawdzanie składni dla języka R.

![Okno dialogowe Opcje zaawansowane opcje edytora tekstu R](media/options-dialog-advanced-text-editor.png)

Każda opcja jest ustawiona na wartość włączone lub wyłączone w celu sterowania zachowaniem. Aby uzyskać szczegółowe informacje na temat tego, co ma wpływ na poszczególne opcje, zobacz okienko pomocy u dołu okna dialogowego. Pamiętaj, że możesz przeciągnąć górną część tego okienka pomocy, aby okienko było większe.

![Rozwinięte okienko pomocy w oknie dialogowym Opcje zaawansowane edytora tekstu w języku R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Narzędzia R > opcje zaawansowane

Polecenie menu Opcje **narzędzi r Tools**  >   otwiera okno dialogowe **Opcje** do opcji r:

  ![Okno dialogowe opcji dla narzędzi R Tools](media/options-dialog.png)

W poniższych sekcjach opisano różne opcje dostępne na tej stronie.

### <a name="debugging"></a>Debugowanie

Te opcje kontrolują sposób obsługi wartości w [Eksplorator zmiennych](variable-explorer.md) i w oknach debugera, takich jak Watch i lokalne (zobacz [Debugowanie kodu R](debugging-r-in-visual-studio.md)).

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Oceń aktywne powiązania | `True` | Gdy `True` , zapewnia, że zawsze będzie wyświetlana najbardziej aktualna wartość podczas inspekcji zmiennych i właściwości. Ryzyko polega na tym, że Ocena wyrażeń może spowodować efekty uboczne, w zależności od tego, jak zostały zaimplementowane. |
| Pokaż zmienne z prefiksami z kropką | `False` | Określa, czy są wyświetlane zmienne poprzedzone prefiksem `.` . |

### <a name="grid-view"></a>Widok siatki

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Obliczanie dynamiczne | `False` | Domyślnie `View(<expression>)` Funkcja tworzy migawkę danych jako ramkę danych, która może zużywać znaczną ilość pamięci z dużymi zestawami danych. Ustawienie tej opcji `True` oznacza, że wyrażenie jest oceniane, gdy siatka zostanie odświeżona w celu pobrania tylko tych danych, które są wyświetlane. Jeśli jednak wyrażenie zmieni również zmiany danych, które mogą być nieodpowiednie dla wyrażeń PIP dplyr. |

### <a name="help"></a>Pomoc

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka sieci Web F1 | `Internal` | Kontroluje sposób wyświetlania pomocy podczas wyszukiwania terminu przy użyciu **klawisza Ctrl** + **F1**. W przypadku ustawienia opcji `Internal` Pomoc jest renderowana w oknie narzędzia w programie Visual Studio. W przypadku ustawienia opcji `External` Pomoc pojawia się w domyślnej przeglądarce sieci Web. |
| Ciąg wyszukiwanie w sieci Web F1 | `R site:stackoverflow.com` | Kontroluje, jak terminy wyszukiwania są przesyłane do aparatu wyszukiwania po naciśnięciu klawisza **Ctrl** + **F1** w okresie w edytorze. Domyślnie ciąg to `R site:stackoverflow.com` , który jest dołączany `R` do wyszukiwanego terminu. `site:stackoverflow.com`Jest to dyrektywa aparatu wyszukiwania, która informuje go o zakresie wyszukiwania do stron w `stackoverflow.com` domenie. |
| Przeglądarka Pomoc dla języka R | `Automatic` | Kontroluje sposób wyświetlania pomocy podczas wyszukiwania dokumentacji języka R przy użyciu **klawisza F1**, **?** lub **?**. Po ustawieniu na `Automatic` , help renderuje w odpowiednim oknie. Na przykład Pomoc HTML pojawia się w oknie narzędzia programu Visual Studio, a pliki PDF pojawiają się w domyślnym programie PDF. W przypadku ustawienia opcji `External` Pomoc jest renderowana w domyślnej przeglądarce sieci Web. |

### <a name="history"></a>Historia

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zawsze Zapisuj historię | `True` | Kontroluje, czy RTVS zapisuje historię poleceń do *. RHistory* plik w katalogu roboczym za każdym razem, gdy projekt jest zamknięty. Zapisywanie historii jest wykonywane nawet wtedy, gdy projekt nie zostanie zapisany przed zakończeniem pracy. |
| Resetuj filtr wyszukiwania | `True` | Określa, czy okno historii może odfiltrować historię poleceń, aby wyświetlić tylko te polecenia, które są zgodne z terminem filtru w oknie dialogowym Historia poleceń w języku R. To ustawienie określa, czy należy zresetować filtr wyszukiwania historii za każdym razem, gdy zostanie uruchomione nowe polecenie lub przejdziesz do nowego projektu, który wyzwala obciążenie innego *. Plik RHistory* . Ustawienie domyślne `True` minimalizuje czas nieoczekiwany podczas uruchamiania polecenia z zestawem filtrów i zastanawiasz się, dlaczego uruchomione polecenie nie było widoczne w historii. |
| Użyj wyboru wielowierszowego | `True` | Określa, czy można wybrać wielowierszową instrukcję w historii przy użyciu jednego kliknięcia. Włącza również nawigację w górę i w dół w oknach interaktywnych przez instrukcje zamiast wierszy. |

### <a name="html"></a>HTML

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka stron HTML | `External` | Określa miejsce, w którym `ggvis` jest renderowana zawartość, taka jak wykres lub `shiny` aplikacja. `Internal` Wyświetla dane wyjściowe HTML w oknie narzędzia w programie Visual Studio; `External` wyświetla dane wyjściowe HTML w domyślnej przeglądarce. |

### <a name="logging"></a>Rejestrowanie

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zdarzenia dziennika | `Normal` | Steruje szczegółowością rejestrowania używanego na potrzeby diagnostyki RTVS. Domyślne ustawienie `Normal` tworzenia pliku dziennika w `TEMP` katalogu. Gdy jest ustawiona na `Traffic` , RTVS rejestruje wszystkie polecenia i odpowiedzi w sesji. Te pliki dziennika nigdy nie opuszczają maszyny, ale mogą być przydatne do diagnozowania problemów w RTVS. |

### <a name="markdown"></a>Znaczniki języka Markdown

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka promocji — wersja zapoznawcza | `External` | Określa, gdzie jest wyświetlane dane wyjściowe HTML RMarkdown. `Internal` pokazuje dokument HTML RMarkdown w oknie narzędzia w programie Visual Studio; `External` wyświetla HTML RMarkdown przy użyciu domyślnej przeglądarki. |

### <a name="r-engine"></a>Aparat języka R

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Strona kodowa | `(OS Default)` | Ustawia stronę kodową (ustawienia regionalne) dla języka R. Domyślnie używa on podstawowych ustawień regionalnych systemu operacyjnego. |
| CRAN dublowanie | `(Use .Rprofile)` | Ustawia domyślne dublowanie CRAN dla instalacji pakietów. Domyślne ustawienie `Use .Rprofile` uwzględnia ustawienia dublowania Cran w *. Plik RProfile* . |

### <a name="workspace"></a>Workspace

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Załaduj obszar roboczy podczas otwierania projektu | `No` | Ustawienie umożliwiające `Yes` ładowanie danych sesji z programu *. RData* plik w środowisku globalnym, gdy projekt jest otwarty. |
| Monituj o zapisanie obszaru roboczego przy resetowaniu | `Yes` | Ustawienie, aby `No` wyłączyć monitowanie o zapisanie obszaru roboczego po kliknięciu przycisku Resetuj w oknie interaktywnym. |
| Zapisz obszar roboczy po zamknięciu projektu | `No` | Ustawienie umożliwiające `Yes` zapisanie środowiska globalnego w programie *. Plik RData* , gdy projekt jest zamknięty. |
| Pokaż okno dialogowe potwierdzenia przed przełączeniem obszarów roboczych | `Yes` | Ustawienie umożliwiające `No` wyłączenie monitowania użytkownika o potwierdzenie podczas przełączania różnych obszarów roboczych. Zobacz [przełączanie między obszarami roboczymi](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Pokaż wskaźnik obciążenia maszyny | `False` | Kontroluje widoczność wskaźnika obciążenia procesora/pamięci/sieci na pasku stanu. Ponieważ wskaźnik wiąże się z ruchem sieciowym, warto to zrobić `False` w zdalnych scenariuszach taryfowych. Zmiana tej opcji wymaga ponownego uruchomienia programu Visual Studio. |

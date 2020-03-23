---
title: Opcje narzędzi R
description: Odwołanie do opcji w programie Visual Studio dla języka języka języka R i skojarzonych funkcji.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302708"
---
# <a name="r-tools-for-visual-studio-options"></a>Opcje narzędzia języka R dla programu Visual Studio

Dostęp do ustawień można uzyskać za pomocą menu**Opcje** **narzędzi** > R lub za pomocą**opcji** **narzędzi** > i przewijania do **R Tools:**

  ![Okno dialogowe Opcje dla narzędzi R](media/options-dialog.png)

Opcje i ustawienia specyficzne dla języka R są dostępne przy użyciu poniższych metod. Aby wszystkie te sekcje były wyświetlane, należy **zaznaczyć** pole Pokaż wszystkie ustawienia u dołu okna dialogowego **Opcje.**

- Opcje formatowania kodu (zobacz [Opcje edytora](editing-r-code-in-visual-studio.md#editor-options): Menu**Opcje** **narzędzi,** > a następnie wybierz pozycję **Edytor** > tekstu**R** > **Formatowanie**
- Opcje linter (patrz [Linting](linting-r-code.md)): Menu**Opcje** **narzędzi,** > a następnie wybierz pozycję **Edytor** > tekstu**R** > **Lint**
- Zaawansowane opcje edytora[(opisane w tym artykule):](#text-editor--r--advanced-options)Menu**Opcje** **narzędzi,** > a następnie wybierz edytor **tekstu** > **R** > **Zaawansowane**
- Opcje behawioralne ([opisane w tym artykule):](#r-tools--advanced-options)Menu**Opcje** **narzędzi** > R lub**Opcje** **narzędzi** > , a następnie przewiń do **pozycji R Tools**.

Polecenie**Ustawienia nauki o danych** **R Tools** > wpływa również na szereg różnych ustawień w programie Visual Studio. To polecenie jest opisane w następnej sekcji.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R Narzędzia > ustawienia do nauki o danych

Element menu **R Tools > Data Science Settings** konfiguruje IDE programu Visual Studio z układem zoptymalizowanym pod kątem potrzeb analityków danych. W szczególności ta opcja otwiera [interaktywne,](interactive-repl-for-r-in-visual-studio.md) [Eksplorator zmiennych](variable-explorer.md)i [obszary robocze:](r-workspaces-in-visual-studio.md)

![Układ okna naukowiec danych w programie Visual Studio](media/installation-data-scientist-layout-result.png)

Aby później powrócić do innych ustawień programu Visual Studio, najpierw użyj polecenia **Narzędzia** > **Importuj i Eksportuj ustawienia,** wybierz pozycję **Eksportuj wybrane ustawienia środowiska**i określ nazwę pliku. Aby przywrócić te ustawienia, użyj tego samego polecenia i wybierz **pozycję Importuj wybrane ustawienia środowiska**. Można również użyć tych samych poleceń, jeśli zmienisz układ analityka danych i chcesz wrócić do niego później, zamiast bezpośrednio przy użyciu polecenia **Ustawienia nauki o danych.**

## <a name="text-editor--r--advanced-options"></a>Edytor tekstu > opcje zaawansowane > R

Te opcje kontrolują zachowanie formatowania, IntelliSense, tworzenia nakreślenia, wcięcie i sprawdzanie składni dla R.

![Okno dialogowe Opcje dla zaawansowanych opcji edytora tekstu R](media/options-dialog-advanced-text-editor.png)

Każda opcja jest ustawiona na włączanie lub wyłączanie, aby kontrolować dane zachowanie. Szczegółowe informacje na temat wpływu każdej opcji można znaleźć w okienku pomocy u dołu okna dialogowego. Pamiętaj, że możesz przeciągnąć górną część okienka pomocy w górę, aby pomnożyć okienko.

![Rozwinięte okienko pomocy w oknie dialogowym zaawansowanych opcji edytora tekstu R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R Narzędzia > opcje zaawansowane

Polecenie menu**Opcje** **narzędzi** > R otwiera okno dialogowe **Opcje** dla opcji R:

  ![Okno dialogowe Opcje dla narzędzi R](media/options-dialog.png)

W poniższych sekcjach opisano różne opcje dostępne na tej stronie.

### <a name="debugging"></a>Debugging

Te opcje określają sposób obsługi wartości w [Eksploratorze zmiennych](variable-explorer.md) i w oknach debugera, takich jak Czujka i Zmienne lokalne (zobacz [kod debugowania R).](debugging-r-in-visual-studio.md)

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Oceń aktywne powiązania | `True` | When `True`, zapewnia, że zawsze widzisz najbardziej aktualną wartość podczas sprawdzania zmiennych i właściwości. Ryzyko polega na tym, że ocena wyrażeń może powodować skutki uboczne, w zależności od tego, jak zostały zaimplementowane. |
| Pokaż zmienne z kropkami | `False` | Określa, czy wyświetlane `.` są zmienne poprzedzone. |

### <a name="grid-view"></a>Widok siatki

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Ocena dynamiczna | `False` | Domyślnie `View(<expression>)` funkcja wykonuje migawkę danych jako ramki danych, która może zużywać znaczną ilość pamięci z dużymi zestawami danych. Ustawienie tej `True` opcji oznacza, że wyrażenie jest oceniane, gdy siatka jest odświeżana w celu pobrania tylko tych danych, które są wyświetlane. Jeśli jednak wyrażenie zmieni dane również się zmienią, co może być nieodpowiednie dla wyrażeń pip dplyr. |

### <a name="help"></a>Pomoc

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka internetowa F1 | `Internal` | Określa sposób wyświetlania pomocy podczas wyszukiwania terminu przy użyciu **klawisza Ctrl**+**F1**. Po ustawieniu `Internal`, pomoc jest renderowana w oknie narzędzia w programie Visual Studio. Po ustawieniu `External`na , pomoc pojawia się w domyślnej przeglądarce internetowej. |
| Ciąg wyszukiwania w sieci Web F1 | `R site:stackoverflow.com` | Steruje tym, jak wyszukiwane terminy są przekazywane do wyszukiwarki po naciśnięciu **klawisza Ctrl**+**F1** na termin w edytorze. Domyślnie ciąg `R site:stackoverflow.com`jest , który `R` dołącza do wyszukiwago terminu. Jest `site:stackoverflow.com` to dyrektywa do wyszukiwarki, która informuje go `stackoverflow.com` do zakresu wyszukiwania do stron w domenie. |
| R Przeglądarka pomocy | `Automatic` | Określa sposób wyświetlania pomocy podczas przeszukiwania dokumentacji języka R przy użyciu **F1**, **?**, lub **??**. Po ustawieniu , `Automatic`pomoc renderuje w odpowiednim oknie. Na przykład pomoc HTML pojawia się w oknie narzędzia programu Visual Studio, podczas gdy pliki PDF są wyświetlane w domyślnym programie PDF. Po ustawieniu `External`, pomoc jest renderowana w domyślnej przeglądarce internetowej. |

### <a name="history"></a>Historia

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zawsze zapisuj historię | `True` | Określa, czy RTVS zapisuje historię poleceń w *pliku . RHistory* w katalogu roboczym, gdy projekt jest zamknięty. Zapisanie historii odbywa się nawet wtedy, gdy projekt nie zostanie zapisane przed jego zakończeniem. |
| Resetowanie filtru wyszukiwania | `True` | Określa, czy okno Historia może filtrować historię poleceń, aby wyświetlić tylko polecenia, które są zgodne z terminem filtru w oknie dialogowym Historia R. To ustawienie określa, czy należy zresetować filtr wyszukiwania historii przy każdym uruchomieniu nowego polecenia, czy przełączyć się na nowy projekt, co powoduje obciążenie innego *. RHistoria.* Domyślne ustawienie `True` minimalizuje zaskoczenie po uruchomieniu polecenia z zestawem filtrów i zastanawiasz się, dlaczego polecenie, które właśnie uruchomiono, nie pojawiło się w historii. |
| Użyj wyboru wielowierszowego | `True` | Określa, czy za pomocą jednego kliknięcia można wybrać instrukcję wielowierszową w historii. Umożliwia również nawigację w górę /w dół w interaktywnym systemie Windows za pomocą instrukcji, a nie linii. |

### <a name="html"></a>HTML

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka stron HTML | `External` | Określa, gdzie jest `ggvis` renderowana zawartość, taka jak wykres lub `shiny` aplikacja. `Internal`pokazuje dane wyjściowe HTML w oknie narzędzia w programie Visual Studio; `External` wyświetla dane wyjściowe HTML w domyślnej przeglądarce. |

### <a name="logging"></a>Rejestrowanie

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Rejestrowanie zdarzeń | `Normal` | Steruje szczegółowością rejestrowania używanego do diagnostyki RTVS. Domyślne ustawienie `Normal` tworzy plik dziennika `TEMP` w katalogu. Po ustawieniu na `Traffic`, RTVS rejestruje wszystkie polecenia i odpowiedzi w sesji. Te pliki dziennika nigdy nie opuszczają komputera, ale mogą być pomocne w diagnozowaniu problemów w RTVS. |

### <a name="markdown"></a>Markdown

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka podglądu Markdown | `External` | Określa, gdzie jest wyświetlany wynik HTML RMarkdown. `Internal`pokazuje dokument HTML RMarkdown w oknie narzędzia w programie Visual Studio; `External` wyświetla RMarkdown HTML przy użyciu domyślnej przeglądarki. |

### <a name="r-engine"></a>Silnik R

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Strona kodowa | `(OS Default)` | Ustawia stronę kodową (ustawienia regionalne) dla R. Domyślnie używa podstawowych ustawień regionalnych systemu operacyjnego. |
| Lusterko CRAN | `(Use .Rprofile)` | Ustawia domyślne dublowanie CRAN dla instalacji pakietów. Domyślne ustawienie `Use .Rprofile` uwzględnia ustawienia lustra CRAN w pliku *. R Plik profilu.* |

### <a name="workspace"></a>Workspace

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Ładowanie obszaru roboczego po otwarciu projektu | `No` | Ustawienie `Yes` umożliwiające ładowanie danych sesji z pliku *. RData* w środowisku globalnym po otwarciu projektu. |
| Monitowanie o zapisanie obszaru roboczego przy resetowaniu | `Yes` | Ustawienie `No` wyłącza monitowanie o zapisanie obszaru roboczego po kliknięciu przycisku Reset w oknie interaktywnym. |
| Zapisywanie obszaru roboczego po zamknięciu projektu | `No` | Ustawienie `Yes` umożliwiające zapisywanie środowiska globalnego w pliku *. RData* po zamknięciu projektu. |
| Pokaż okno dialogowe potwierdzenia przed przełączeniem obszarów roboczych | `Yes` | Ustawienie, `No` aby wyłączyć monitowanie użytkownika o potwierdzenie podczas przełączania się między różnymi obszarami roboczymi. Zobacz [Przełączanie między obszarami roboczymi](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Pokaż wskaźnik obciążenia maszyny | `False` | Steruje widocznością wskaźnika obciążenia procesora/pamięci/sieci na pasku stanu. Ponieważ wskaźnik powoduje ruch sieciowy, warto zachować `False` to w zdalnych scenariuszach taryfowych. Zmiana tej opcji wymaga ponownego uruchomienia programu Visual Studio. |

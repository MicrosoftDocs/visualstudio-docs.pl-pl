---
title: Opcje narzędzia języka R
description: Odwołanie do opcji w programie Visual Studio dla języka R i skojarzone funkcji.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 2d48f59be1bb8e41e5cb587a6c5defcfb6e3227f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900564"
---
# <a name="r-tools-for-visual-studio-options"></a>Narzędzia języka R dla programu Visual Studio, opcje

Ustawienia są dostępne za pośrednictwem **R Tools** > **opcje** menu lub za pomocą **narzędzia** > **opcje** i przewijając do **R Tools**:

  ![Okno dialogowe Opcje dla narzędzia języka R](media/options-dialog.png)

Opcje i ustawienia specyficzne dla języka R są dostępne przy użyciu poniższych metod. Musisz wybrać **Pokaż wszystkie ustawienia** u dołu **opcje** wszystkie te sekcje się pojawić okno dialogowe.

- Opcje formatowania kodu (zobacz [opcji edytora](editing-r-code-in-visual-studio.md#editor-options): **Narzędzia** > **opcje** menu, następnie wybierz pozycję **edytora tekstów** > **R** > **formatowania**
- Opcje linter (zobacz [Zaznaczanie błędów](linting-r-code.md)): **Narzędzia** > **opcje** menu, następnie wybierz pozycję **edytora tekstów** > **R** > **Lint**
- Zaawansowane opcje edytora ([opisanych w tym artykule](#text-editor--r--advanced-options)): **Narzędzia** > **opcje** menu, następnie wybierz pozycję **edytora tekstów** > **R** > **zaawansowane**
- Opcje zachowania ([opisanych w tym artykule](#r-tools--advanced-options)): **Narzędzia języka R** > **opcje** menu lub **narzędzia** > **opcje**, następnie przewiń listę do **R Tools**.

**R Tools** > **ustawienia do nauki o danych** polecenie ma również wpływ na wiele różnych ustawień w programie Visual Studio ogólną. To polecenie jest opisane w następnej sekcji.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Narzędzia języka R > Ustawienia do nauki o danych

**R Tools > Ustawienia do nauki o danych** elementu menu powoduje skonfigurowanie środowiska IDE programu Visual Studio za pomocą układu, który jest zoptymalizowany pod kątem potrzeb naukowców pracujących. W szczególności, ta opcja umożliwia otwarcie [Interactive](interactive-repl-for-r-in-visual-studio.md), [narzędzie Variable Explorer](variable-explorer.md), i [obszary robocze](r-workspaces-in-visual-studio.md) systemu windows:

![Układ okna naukowego przetwarzania danych w programie Visual Studio](media/installation-data-scientist-layout-result.png)

Aby później przywrócić pozostałe ustawienia programu Visual Studio, należy najpierw użyć **narzędzia** > **Import i eksport ustawień** polecenia select **Eksportuj wybrane ustawienia środowiska**, a następnie określ nazwę pliku. Aby przywrócić te ustawienia, użyj tego samego polecenia, a następnie wybierz pozycję **Importuj ustawienia wybranego środowiska**. Również można użyć tych samych poleceń, jeśli zmienisz układ naukowego przetwarzania danych, a chcesz do niej powrócić w późniejszym czasie na zamiast używania **ustawienia do nauki o danych** polecenia bezpośrednio.

## <a name="text-editor--r--advanced-options"></a>Edytor tekstu > R > Opcje zaawansowane

Te opcje umożliwiają kontrolowanie zachowania formatowania, funkcji IntelliSense, tworzenie konspektu, wcięcia i składnia sprawdzania pod kątem języka R.

![Okno dialogowe Opcje dla opcji edytora zaawansowanego tekstu R](media/options-dialog-advanced-text-editor.png)

Każda opcja jest równa lub wyłącz do sterowania zachowaniem w danym. Szczegółowe informacje dotyczące wpływa na każdej opcji Przyjrzyj się okienku pomocy w dolnej części okna dialogowego. Należy pamiętać, że można przeciągnąć górnej części okienka Pomocy do okienka większych upewnij.

![Rozwinięte okienko pomocy w oknie dialogowym Zaawansowane opcje edytora tekstowego języka R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Narzędzia języka R > Opcje zaawansowane

**R Tools** > **opcje** polecenie menu otwiera **opcje** okno dialogowe Opcje języka R:

  ![Okno dialogowe Opcje dla narzędzia języka R](media/options-dialog.png)

Poniżej opisano różne opcje dostępne na tej stronie.

### <a name="debugging"></a>Debugowanie

Te opcje umożliwiają kontrolowanie sposobu obsługi wartości w [narzędzie Variable Explorer](variable-explorer.md) i w oknach debugera, takie jak wyrażenie kontrolne i lokalne (zobacz [kod R debugowania](debugging-r-in-visual-studio.md)).

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Oceń aktywne powiązania | `True` | Gdy `True`, zapewnia zawsze wyświetlić najbardziej aktualne wartości podczas sprawdzania zmiennych i właściwości. Ryzyko jest tego obliczenia, które wyrażeń może spowodować, że efekty uboczne, w zależności od tego, jak zostały zaimplementowane. |
| Wyświetlanie zmiennych poprzedzone kropką | `False` | Określa, czy zmienne prefiksem `.` są wyświetlane. |

### <a name="grid-view"></a>Widok siatki

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Obliczanie dynamiczne | `False` | Domyślnie `View(<expression>)` funkcja tworzy migawkę danych jako ramkę danych, która może zużywać znaczną pamięć z dużymi zestawami danych. Ustawienie tej opcji na `True` oznacza, że wyrażenie jest oceniane podczas odświeżania siatki w celu pobrania tylko tych danych, która jest wyświetlana. Jednak jeśli zmiany wyrażeń również zmieniają się dane, które może być nieodpowiedni dla dplyr pip wyrażeń. |

### <a name="help"></a>Pomoc

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarki sieci Web F1 | `Internal` | Określa, jak uzyskać pomoc jest wyświetlane, gdy wyszukiwany termin, w którym używana jest **Ctrl**+**F1**. Po ustawieniu `Internal`, pomoc jest renderowany w oknie narzędzi w programie Visual Studio. Po ustawieniu `External`, Pomoc pojawia się w domyślnej przeglądarce internetowej. |
| F1 Ciąg wyszukiwania w sieci Web | `R site:stackoverflow.com` | Określa, jak wyszukiwane terminy są przekazywane do aparat wyszukiwania, po naciśnięciu klawisza **Ctrl**+**F1** dla terminu w edytorze. Domyślnie ten ciąg jest `R site:stackoverflow.com`, która dołącza `R` do wyszukiwanego terminu. `site:stackoverflow.com` Jest dyrektywą do wyszukiwarki, który nakazuje, aby zawęzić zakres wyszukiwania do stron w `stackoverflow.com` domeny. |
| Przeglądarka Pomocy języka R | `Automatic` | Określa, jak uzyskać pomoc jest wyświetlane, gdy w przypadku wyszukiwania przy użyciu dokumentacji języka R **F1**, **?**, lub **?** . Po ustawieniu `Automatic`, Pomoc powoduje wyświetlenie odpowiedniego okna. Na przykład pomocy HTML pojawia się w obrębie okna narzędzi programu Visual Studio, pliki PDF znajdują się w domyślnym programie PDF. Po ustawieniu `External`, pomoc jest wyświetlana w domyślnej przeglądarce internetowej. |

### <a name="history"></a>Historia

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zawsze zapisuj historii | `True` | Określa, czy RTVS zapisuje historii poleceń do *. RHistory* pliku w katalogu roboczym, gdy projekt jest zamknięty. Zapisywanie historii odbywa się nawet wtedy, gdy nie można zapisać projekt, przed zakończeniem pracy. |
| Zresetuj filtr wyszukiwania | `True` | Określa, czy okno Historia można filtrować historii poleceń, aby pokazać tylko polecenia, które podciąg dopasowywania termin z filtru w oknie dialogowym historie R. To ustawienie określa, czy chcesz zresetować filtr wyszukiwania historii zawsze wtedy, gdy nowe polecenie lub przełącz się do nowego projektu, co powoduje wyzwolenie obciążenia innego *. RHistory* pliku. Domyślne ustawienie `True` minimalizuje Zaskoczenie, gdy należy uruchomić polecenie z zestaw filtrów więc trzeba sprawdzić, dlaczego polecenie uruchomienia tylko widoczne nie w historii. |
| Używanie opcji wyboru z wielowierszowym | `True` | Określa, czy oświadczenie wielowierszowego pola można wybrać w historii za pomocą jednego kliknięcia. Umożliwia także strzałkę nawigacji po kodzie w Windows interakcyjnego w górę/w dół instrukcji zamiast wierszy. |

### <a name="html"></a>HTML

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarki strony HTML | `External` | Określa, gdzie zawartości, takie jak `ggvis` wykres, lub `shiny` aplikacji jest renderowany. `Internal` przedstawia dane wyjściowe HTML w obrębie okna narzędzi w programie Visual Studio; `External` wyświetla dane wyjściowe HTML w domyślnej przeglądarce. |

### <a name="logging"></a>Rejestrowanie

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Dziennik zdarzeń | `Normal` | Określa poziom szczegółowości rejestrowania umożliwiający RTVS diagnostyki. Domyślne ustawienie `Normal` tworzy plik dziennika w swojej `TEMP` katalogu. Po ustawieniu `Traffic`, RTVS rejestruje wszystkie polecenia i odpowiedzi w sesji. Te pliki dziennika nigdy nie należy pozostawić komputer, ale mogą być przydatne do diagnozowania problemów w RTVS. |

### <a name="markdown"></a>Markdown

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka Podgląd języka markdown | `External` | Określa, w którym będą wyświetlane dane wyjściowe RMarkdown HTML. `Internal` Pokazuje dokumentu RMarkdown HTML, w ramach okna narzędzi w programie Visual Studio; `External` Wyświetla HTML RMarkdown za pomocą domyślnej przeglądarki. |

### <a name="r-engine"></a>Aparat języka R

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Strona kodowa | `(OS Default)` | Ustawia stronę kodową (ustawienia regionalne) dla języka R. Domyślnie używa podstawowych ustawień regionalnych systemu operacyjnego. |
| Dublowanie CRAN | `(Use .Rprofile)` | Ustawia dublowanie CRAN domyślny, w ramach instalacji pakietów. Domyślne ustawienie `Use .Rprofile` uwzględnia ustawienia CRAN dublowane w swojej *. RProfile* pliku. |

### <a name="workspace"></a>Obszar roboczy

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Załaduj obszar roboczy, po otwarciu projektu | `No` | Ustawienie `Yes` umożliwia ładowanie danych sesji z *. Dane_rekordu* plików w środowisku globalnym, po otwarciu projektu. |
| Monit o zapisanie obszar roboczy w przypadku zresetowania | `Yes` | Ustawienie `No` wyłącza monitowania o zapisywanie obszaru roboczego, po kliknięciu przycisku resetowania w oknie interaktywnym. |
| Zapisywanie obszaru roboczego po zamknięciu projektu | `No` | Ustawienie `Yes` umożliwia zapisywanie w środowisku globalnym, aby *. Dane_rekordu* plików, gdy projekt jest zamknięty. |
| Pokaż okno dialogowe potwierdzenia przed przełączeniem obszarów roboczych | `Yes` | Ustawienie `No` Wyłącza monitowanie użytkownika o potwierdzenie podczas przełączania między różnych obszarów roboczych. Zobacz [przełączać się między obszarami roboczymi](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Pokaż wskaźnik obciążenia maszyny | `False` | Określa widoczność wskaźnika obciążenia procesora CPU i pamięci/sieci na pasku stanu. Ponieważ wskaźnik ponosi ruchu sieciowego, warto zachować `False` w scenariuszach mierzonego zdalnego. Zmiana ta opcja wymaga, uruchom ponownie program Visual Studio. |

---
title: Edytowanie kodu języka R
description: Visual Studio zawiera dostosowane środowisko edytowania dla języka R, zachowując wszystkie funkcje i możliwości, aby korzystać z rozszerzeń.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868020"
---
# <a name="edit-r-code-in-visual-studio"></a>Edytowanie kodu języka R w programie Visual Studio

Narzędzia R Tools for Visual Studio (RTVS) dostosowanie programu Visual Studio, edytowanie specjalnie dla języka R przy zachowaniu wszystkich funkcji i możliwości, aby korzystać z rozszerzeń. (Na przykład, jeśli wolisz VIM klawiszy, można zainstalować bezpłatne [rozszerzenia VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z witryny Marketplace programu Visual Studio.)

Oprócz funkcji w tym artykule, zobacz też [IntelliSense](r-intellisense.md), [Zaznaczanie błędów](linting-r-code.md), [fragmenty kodu](code-snippets-for-r.md), i [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Wyróżnianie składni

Oprócz kolorowania różnych części kodu, takich jak ciągi, komentarze i słów kluczowych, RTVS wyróżnia i umożliwia łącza w komentarzach:

![Kolorowania kodu języka R](media/editing-syntax-colors.png)

Aby dostosować, czcionki i kolory określone wyróżnienia, zaznacz **narzędzia** > **opcje** polecenia, przejdź do folderu **środowiska**  >  **Czcionki i kolory**, następnie zmień ustawienia dla elementów związanych z języka R w **wyświetlania elementów** pola:

![Czcionki i kolory dla kodu języka R](media/editing-syntax-colors-options.png)

Program Visual Studio również podkreśla błędy składniowe w edytorze:

![Błąd składniowy wyróżniania w kodzie języka R](media/editing-syntax-error.png)

Aby zmienić to zachowanie, zobacz **zaawansowane** > **sprawdzanie składni** w obszarze [opcji edytora](#editor-options).

## <a name="edit-and-organize-code"></a>Edytuj i organizowania kodu

Podczas pisania kodu RTVS zapewnia automatyczne uzupełnianie, zgodnie z opisem na [IntelliSense](r-intellisense.md) strony. Wykonuje też, automatycznego formatowania, takie jak uzupełnianie nawiasów klamrowych i nawiasy:

![Animacja formatowanie wbudowanych](media/editing-inline-formatting.gif)

Podczas wpisywania wywołań funkcji, które mają wiele parametrów, często ma być wiersz w górę parametry, aby poprawić czytelność kodu. RTVS pamięta wcięcie zestawu parametrów i automatycznie stosuje ten wcięć dla kolejnych wierszy:

![Animacja Automatyczne wcięcie](media/editing-auto-indentation.gif)

Aby zmienić to zachowanie, zobacz [opcji edytora](#editor-options) dla **karty** grupy.

Zwijane regiony kodu umożliwiają tymczasowo ukryć części kodu w edytorze. Program Visual Studio tworzy różnych regionów dla Ciebie automatycznie, jak w przypadku wielowierszowe instrukcje, chyba że **zaawansowane** > **konspekt** > **zwijanie kodu**  opcja jest ustawiona na wyłączone.

Utworzyć odpowiedni kod regionu własny, Otocz z komentarzami, które kończą się `---`. Mała +/-kontrolek z lewej strony kodu pozwala następnie rozwijanie i zwijanie regionów:

![Tworzenie region zwijany z komentarzami](media/editing-collapsible-regions.gif)

Domyślnie program Visual Studio Wstawia spacje, po naciśnięciu klawisza **kartę** klucza. Można ponownie zmienić to zachowanie, zgodnie z opisem na [karty Opcje, Edytor tekstu](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Nawigowanie po kodzie

Nawigowanie po kodzie umożliwia szybki dostęp do kodu źródłowego programu R i jego bibliotek. Te funkcje na bieżąco przepływ pracy, niż musieć go ręcznie wyszukiwanie w kodzie.

**Przejdź do definicji** szybko skacze do definicji funkcji lub pojawia się wbudowany mini edytor, którego można odczytać kodu źródłowego funkcji biblioteki. Po prostu kliknij prawym przyciskiem myszy funkcję, zainteresowań, a następnie wybierz pozycję **przejdź do definicji**, albo umieść kursor w funkcji i naciśnij klawisz **F12**.

To polecenie otwiera nowe okno edytora zawierające kod źródłowy dla funkcji. Wygodnie kursora na początku definicji funkcji.

**Zobacz definicję**, wywoływana w menu kliknij prawym przyciskiem myszy lub **Alt**+**F12**, wstawia region tylko do odczytu, którą można przewijać zawierające kod źródłowy funkcji poniżej Wywołanie funkcji:

![Animacja dla definicji wglądu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Wyślij kod do okna interaktywnego

Wielu programistów chce pisanie kodu w edytorze, a następnie wyślij kod do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) do natychmiastowego testowania (znany także jako odczytu — ocena-Print-Loop lub REPL). Naciśnięcie klawisza **Ctrl**+**Enter** języka R w edytorze bieżący wiersz kodu do okna interaktywnego, a następnie umieszcza kursor w następnym wierszu. Za pomocą **Ctrl**+**Enter**, następnie można skutecznie przejść przez kod w edytorze.

Możesz również wybrać kod i naciśnij klawisz **Ctrl**+**Enter** do zastosowania tej całego wyboru. Alternatywnie, kliknij prawym przyciskiem myszy zaznaczenie i wybierz **Execute w Interactive**.

## <a name="format-code"></a>Formatowanie kodu

Automatyczne formatowanie w programie Visual Studio przechowuje kod, który pisania, a także kod, który możesz wkleić do edytora, sformatowane według stawki ustalonej przez preferencje. Można także dokonać wyboru, kliknij prawym przyciskiem myszy, a następnie wybierz **Formatuj zaznaczenie** (**Ctrl**+**K**,**F**) do zastosowania tych Preferencje. Na przykład, gdyby definicja funkcji wszystko w jednym wierszu:

```R
f<-function  (a){  return(a + 1) }
```

Stosuje formatowanie czyści ją jako:

```R
f <- function(a) { return(a + 1) }
```

Aby ponownie formatować całego pliku z kodem, wybierz **Edytuj** > **zaawansowane** > **Formatuj dokument** (**Ctrl** + **E**,**D**).

Automatyczne formatowanie jest oddzielnym operacji, która może być cofnięte. Na przykład, jeśli Wklej kod w edytorze i formatowanie ma zastosowanie, wybranie opcji **Edytuj** > **Cofnij** lub naciskając **Ctrl** + **Z** raz odwraca formatowanie; drugi **Cofnij** odwraca wklejania, sam.

Opcje formatowania (w tym wyłączenie opcji formatowania) są ustawiane za pomocą **narzędzia** > **opcje** na **edytora tekstów**  >  **R** > **zaawansowane** kartę. Możesz przejść bezpośrednio do tej strony, przy użyciu **R Tools** > **opcji edytora** polecenia lub przez kliknięcie prawym przyciskiem myszy w edytorze i wybraniu **Opcjeformatowania**. Zobacz [opcji edytora](#editor-options) sekcji, aby uzyskać szczegółowe informacje.

## <a name="inserting-roxygen-comments"></a>Wstawianie komentarzy Roxygen

RTVS zapewnia skrót do generowania [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) komentarze, przy użyciu nazwy parametrów funkcji. Po prostu wpisz `###` w pustym wierszu powyżej definicji funkcji:

![Animacja Wstawianie komentarza Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opcje edytora

Opcji edytora specyficznych są ustawiane za pomocą **narzędzia** > **opcje** polecenia, przechodząc do **edytora tekstów** > **R**, lub użyj polecenia skrót **R Tools** > **opcji edytora**.

Opcje na **ogólne**, **paski przewijania**, i **karty** karty nie są specyficzne dla języka R, ale są raczej ogólne ustawienia programu Visual Studio, dostępne dla wszystkich języków, ale zastosowane na Podstawa dla języka. Aby uzyskać szczegółowe informacje zobacz następujące artykuły:

- [Opcje, Edytor tekstów, Wszystkie języki](../ide/reference/options-text-editor-all-languages.md)
- [Śledzić możesz kodu przez dostosowania paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Karty Opcje, Edytor tekstu](../ide/reference/options-text-editor-all-languages-tabs.md)

Opcje na **R** > **zaawansowane** karty są specyficzne dla RTVS:

| Grupa | Opcja | Domyślny | Opis |
| --- | --- | --- | --- |
| Formatowanie | Formatowanie automatyczne | On | Formatuje kodu podczas wpisywania. Nie ma wpływu na **Formatuj zaznaczenie** lub **Formatuj dokument** poleceń. |
| | Rozwinięty nawiasów klamrowych | Off | Umieszcza otwartą {w nowym wierszu. |
| | Formatuj przy wklejeniu | On | Stosuje formatowanie przy wklejaniu. |
| | Format zakresu} | On | Zakres formatów po wpisaniu zamykającego}. |
| | Odstęp po przecinku | On | Umieszcza odstęp po przecinkach. |
| | Odstęp po — słowo kluczowe | On | Umieszcza spację po słów kluczowych, takich jak `if`, `while`, i `repeat`. |
| | Odstęp przed { | On | Umieszcza spacji przed i otwierania {. |
| | Miejsca do magazynowania kolem znaku = | On | Umieszcza spacje wokół znaku równości. |
| IntelliSense | Zatwierdzenie w klawisza Enter | Off | Zatwierdzenia automatyczne uzupełnianie zaznaczenia podczas **Enter** naciśnięciu. |
| | Zatwierdź klucza miejsca | Off | Zatwierdzenia automatyczne uzupełnianie zaznaczenia podczas **miejsca** naciśnięciu.|
| | Listy uzupełniania w pierwszym znakiem | On | Zawiera listy uzupełniania w pierwszym typy znaków. Gdy wyłączone, zostanie wyświetlona lista uzupełniania z **Edytuj** > **IntelliSense** > **List Members** (**Ctrl** + **"J"**). |
| | Listy uzupełniania w **kartę** klucza | Off | Wywołuje listy uzupełniania, wpisując jeden lub więcej znaków, a następnie naciskając klawisz **kartę**. |
| | Dopasowanie częściowe typy nazwy argumentu | Off | Podczas wpisywania nazwy argumentów w wywołaniu funkcji, pomocy dotyczącej sygnatur zawiera opis argumentu, który najlepiej odpowiada. |
| Okno interaktywne | Kontrola syntaxe v Konzole R | Off | Stosuje składni sprawdzania w oknie interaktywnym. Sprawdzanie składni mogą nie działać poprawnie w instrukcjach wiele wierszy. |
| Tworzenie konspektu | Zwijanie kodu | On | Automatycznie tworzy zwijane regiony dla zagadnień, takich jak wielowierszowe instrukcje. |
| Sprawdzanie składni | Pokaż błędy składniowe | On | Umożliwia automatyczne sprawdzanie kodu składni. |

---
title: Edytuj kod R
description: Visual Studio zapewnia dostosowane środowisko edycji dla języka R przy zachowaniu wszystkich funkcji i możliwość korzystania z rozszerzeń.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302715"
---
# <a name="edit-r-code-in-visual-studio"></a>Edytowanie kodu języka R w programie Visual Studio

R Tools for Visual Studio (RTVS) dostosowuje środowisko edycji programu Visual Studio specjalnie dla języka R, zachowując wszystkie funkcje i możliwość używania rozszerzeń. (Na przykład, jeśli wolisz powiązania kluczy VIM, możesz zainstalować bezpłatne [rozszerzenie VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z portalu Visual Studio Marketplace.

Oprócz funkcji w tym artykule, zobacz także [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [fragmenty kodu](code-snippets-for-r.md)i [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Wyróżnianie składni

Oprócz kolorowania różnych części kodu, takich jak ciągi, komentarze i słowa kluczowe, RTVS również podkreśla i włącza łącza w komentarzach:

![Kolorowanki składni dla kodu R](media/editing-syntax-colors.png)

Aby dostosować czcionki i niektóre kolory wyróżnienia, wybierz polecenie**Opcje** **narzędzi,** > przejdź do**pozycji Czcionki i kolory** **środowiska,** > a następnie zmień ustawienia elementów związanych z R w polu **Elementy wyświetlane:**

![Czcionki i opcje kolorów dla kodu R](media/editing-syntax-colors-options.png)

Program Visual Studio podkreśla również błędy składni w edytorze:

![Wyróżnianie błędu składni w kodzie R](media/editing-syntax-error.png)

Aby zmienić to zachowanie, zobacz ustawienie**sprawdzania składni** **zaawansowanej** > w obszarze [Opcje edytora](#editor-options).

## <a name="edit-and-organize-code"></a>Edytowanie i organizowanie kodu

Podczas wpisywać kod RTVS zapewnia automatyczne uzupełnianie zgodnie z opisem na stronie [IntelliSense.](r-intellisense.md) Wykonuje również automatyczne formatowanie, takie jak uzupełnianie nawiasów klamrowych i nawiasów:

![Animacja formatowania wbudowanego](media/editing-inline-formatting.gif)

Podczas wpisywania wywołań funkcji, które mają wiele parametrów, często chcesz wyrównać parametry, aby kod był łatwiejszy do odczytania. RTVS zapamiętuje wcięcie ustawione dla parametrów i automatycznie stosuje to wcięcie dla kolejnych wierszy:

![Animacja automatycznego wcięci](media/editing-auto-indentation.gif)

Aby zmienić to zachowanie, zobacz [opcje edytora](#editor-options) dla grupy **Karty.**

Zwijane regiony kodu umożliwiają tymczasowe ukrywanie części kodu w edytorze. Visual Studio tworzy różne regiony dla Ciebie automatycznie, jak dla instrukcji wielowierszowych, chyba że **opcja zaawansowanego** > kodu**posypka** > **jest** ustawiona na Wyłączone.

Aby utworzyć własny region, otoczyć żądany kod `---`komentarzami, które kończą się na pliku . Małe +/- formanty po lewej stronie kodu pozwala następnie rozwinąć i zwinąć regiony:

![Tworzenie zwijanego regionu z komentarzami](media/editing-collapsible-regions.gif)

Domyślnie program Visual Studio wstawia spacje po naciśnięciu **klawisza Tab.** Możesz ponownie zmienić to zachowanie zgodnie z opisem w [opcjach, Edytorze tekstu, kartach](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Nawigacja po kodzie

Nawigacja kodu zapewnia szybki dostęp do kodu źródłowego programu R i jego bibliotek. Te funkcje utrzymują cię w przepływie pracy, a nie konieczności ręcznego przeszukiwania kodu.

**Przejdź do definicji** szybko przeskakuje do definicji funkcji lub wyskakuje wbudowany mini-edytor do odczytu kodu źródłowego funkcji biblioteki. Wystarczy kliknąć prawym przyciskiem myszy interesującą funkcję i wybrać **opcję Przejdź do definicji**lub umieścić kursor w funkcji i nacisnąć **klawisz F12**.

To polecenie otwiera nowe okno edytora zawierające kod źródłowy funkcji. Kursor jest wygodnie umieszczony na początku definicji funkcji.

**Peek Definition**, wywoływane z menu po kliknięciu prawym przyciskiem myszy lub **Alt**+**F12**, wstawia tylko do odczytu, przewijany region zawierający kod źródłowy funkcji poniżej wywołania funkcji:

![Animacja do definicji wglądu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Wyślij kod do okna interaktywnego

Wielu deweloperów lubi pisać kod w edytorze, a następnie wysłać ten kod do [interaktywnego okna](interactive-repl-for-r-in-visual-studio.md) do natychmiastowego testowania (znany również jako Read-Evaluate-Print-Loop lub REPL). Naciśnięcie **klawisza Ctrl**+**Enter** w edytorze R powoduje wysłanie bieżącego wiersza kodu do okna interaktywnego, a następnie umieszcza kursor w następnym wierszu. Z **Ctrl**+**Enter**, a następnie, można skutecznie krok przez kod z edytora.

Można również wybrać kod i nacisnąć klawisz **Ctrl**+**Enter,** aby zastosować całe zaznaczenie. Alternatywnie kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **Wykonaj w trybie interaktywnym**.

## <a name="format-code"></a>Formatowanie kodu

Automatyczne formatowanie programu Visual Studio zachowuje kod, który piszesz, a także kod wklejony do edytora, sformatowany zgodnie z preferencjami. Można również dokonać wyboru, kliknąć prawym przyciskiem myszy i wybrać **opcję Zaznaczenie formatu** **(Ctrl**+**K**,**F),** aby zastosować te preferencje. Na przykład, jeśli definicja funkcji jest zdefiniowana w jednym wierszu:

```R
f<-function  (a){  return(a + 1) }
```

Zastosowanie formatowania czyści go do:

```R
f <- function(a) { return(a + 1) }
```

Aby sformatować cały plik kodu, wybierz **pozycję Edytuj** > **dokument formatu** **zaawansowanego** > **(Ctrl**+**E**,**D**).

Automatyczne formatowanie jest oddzielną operacją, którą można cofnąć. Na przykład, jeśli wklejasz kod do edytora i formatujesz go, zaznaczenie **opcji Edytuj** > **cofnij** lub naciśnięcie **klawisza Ctrl**+**Z** po odwróceniu formatowania; drugie **cofanie** odwraca samą wklej.

Opcje formatowania (w tym wyłączenie formatowania) są ustawiane za pomocą**opcji** **narzędzia** > na karcie**Zaawansowane** **edytor** > tekstu**R.** >  Możesz przejść bezpośrednio do tej strony za pomocą polecenia**Opcje Edytora** **narzędzi** > R lub klikając prawym przyciskiem myszy w edytorze i wybierając opcję **Formatowanie**. Szczegółowe informacje można znaleźć w sekcji [opcji edytora.](#editor-options)

## <a name="inserting-roxygen-comments"></a>Wstawianie komentarzy Roxygen

RTVS zapewnia skrót do generowania komentarzy [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) przy użyciu nazw parametrów funkcji. Wystarczy `###` wpisać w pustym wierszu powyżej definicji funkcji:

![Animacja wstawiania komentarza Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opcje edytora

Opcje specyficzne dla edytora są ustawiane za pomocą polecenia **Opcje narzędzi,** > **Options** przechodzenia do **edytora** > tekstu**R**lub polecenia skrótu **R Opcje** > **edytora**narzędzi .

Opcje na kartach **Ogólne,** **Przewijanie**i **Karty** nie są specyficzne dla języka R, ale są raczej ogólne ustawienia programu Visual Studio dostępne dla wszystkich języków, ale stosowane w poszczególnych językach. Aby uzyskać szczegółowe informacje, zobacz następujące artykuły:

- [Opcje, edytor tekstu, wszystkie języki](../ide/reference/options-text-editor-all-languages.md)
- [Śledzenie kodu przez dostosowywanie paska przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opcje, Edytor tekstu, Karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Opcje na **R** > **karcie** Zaawansowane R są specyficzne dla RTVS:

| Grupa | Opcja | Domyślne | Opis |
| --- | --- | --- | --- |
| Formatowanie | Automatyczne formatowanie | Włączone | Formatuje kod podczas pisania. Nie ma wpływu na polecenia **Zaznaczanie formatu** **ani Formatowanie dokumentu.** |
| | Rozszerzone nawiasy klamrowe | Wyłączone | Umieszcza otwarte { w nowym wierszu. |
| | Format przy wklejać | Włączone | Stosuje formatowanie przy wklejanie. |
| | Zakres formatu na } | Włączone | Formatuje zakres po wpisaniu zamknięcia }. |
| | Miejsce po przecince | Włączone | Umieszcza spację po przecinkach. |
| | Spacja po słowie kluczowym | Włączone | Umieszcza miejsce po słowach kluczowych, takich jak `if`, `while`i `repeat`. |
| | Miejsce przed { | Włączone | Umieszcza miejsce przed otwarciem i otwarciem {. |
| | Przestrzenie wokół = | Włączone | Umieszcza przestrzenie wokół znaku równości. |
| IntelliSense | Zaajmy przy klawiszu Enter | Wyłączone | Zatwierdza wybór automatycznego uzupełniania po **naciśnięciu klawisza Enter.** |
| | Zatwierdzę klucz przestrzeni | Wyłączone | Zatwierdza wybór automatycznego uzupełniania po **naciśnięciu miejsca.**|
| | Lista uzupełnień pierwszego znaku | Włączone | Pokazuje listę uzupełnień dla pierwszych typów znaków. Po wyłączeniu wyświetlana jest lista uzupełnień z **poleceniem Edytuj** > **elementy członkowskie listy** **IntelliSense** > **(Ctrl**+**J).** |
| | Lista uzupełnień w kluczu **tabulatora** | Wyłączone | Wywołuje listę uzupełnień, wpisując jeden lub więcej znaków i naciskając **klawisz Tab**. |
| | Dopasuj nazwy argumentów typów częściowo | Wyłączone | WHen wpisując nazwy argumentów w wywołaniu funkcji, pomoc podpisu pokazuje opis argumentu, który jest najlepszym dopasowaniem. |
| Okno interaktywne | Sprawdzanie składni w konsoli R | Wyłączone | Stosuje sprawdzanie składni w oknie Interaktywna. Sprawdzanie składni może nie działać poprawnie z instrukcjami wielowierszowymi. |
| Tworzenie konspektu | Tworzenie nakreślenia kodu | Włączone | Automatycznie tworzy obszary zwijane dla obszarów, takich jak instrukcje wielowierszowe. |
| Sprawdzanie składni | Pokaż błędy składniowe | Włączone | Umożliwia automatyczne sprawdzanie składni kodu. |

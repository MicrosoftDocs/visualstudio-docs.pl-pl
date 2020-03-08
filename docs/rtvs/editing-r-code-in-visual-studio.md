---
title: Edytuj kod języka R
description: Program Visual Studio zapewnia dostosowane środowisko do edycji dla języka R, zachowując jednocześnie wszystkie funkcje i możliwość korzystania z rozszerzeń.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409648"
---
# <a name="edit-r-code-in-visual-studio"></a>Edytuj kod języka R w programie Visual Studio

R Tools for Visual Studio (RTVS) — ślady środowiska edycji programu Visual Studio przeznaczonego wyłącznie dla języka R, zachowując wszystkie funkcje i możliwość korzystania z rozszerzeń. (Na przykład jeśli wolisz używać powiązań klucza VIM, możesz zainstalować [rozszerzenie Free VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) z poziomu Visual Studio Marketplace.)

Oprócz funkcji opisanych w tym artykule, zobacz również sekcję [IntelliSense](r-intellisense.md), [Zaznaczanie błędów](linting-r-code.md), [fragmenty kodu](code-snippets-for-r.md)i [R MARKDOWN](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Wyróżnianie składni

Oprócz kolorowania różnych części kodu, takich jak ciągi, komentarze i słowa kluczowe, RTVS również wyróżnia i włącza linki w komentarzach:

![Kolorowanie składni dla kodu języka R](media/editing-syntax-colors.png)

Aby dostosować czcionki i niektóre kolory wyróżnienia, wybierz polecenie **narzędzia** > **Opcje** , przejdź do **środowiska** > **czcionki i kolory**, a następnie zmień ustawienia dla elementów związanych z językiem R w polu **Wyświetl elementy** :

![Czcionki i opcje koloru dla kodu języka R](media/editing-syntax-colors-options.png)

Program Visual Studio również podkreśla błędy składni w edytorze:

![Wyróżnianie błędu składniowy w kodzie R](media/editing-syntax-error.png)

Aby zmienić to zachowanie, zapoznaj się z ustawieniem **Sprawdzanie składni** > **zaawansowanych** w obszarze [Opcje edytora](#editor-options).

## <a name="edit-and-organize-code"></a>Edytuj i Organizuj kod

Podczas wpisywania kodu RTVS zapewnia Autouzupełnianie zgodnie z opisem na stronie [IntelliSense](r-intellisense.md) . Jest to również automatyczne formatowanie, takie jak uzupełnianie nawiasów klamrowych i nawiasów:

![Animacja formatowania wbudowanego](media/editing-inline-formatting.gif)

Podczas wpisywania wywołań do funkcji, które mają wiele parametrów, często chcesz wierszować parametry, aby ułatwić odczytywanie kodu. RTVS zapamiętuje wcięcie ustawione dla parametrów i automatycznie stosuje to wcięcie dla kolejnych wierszy:

![Animacja automatycznego wcięcia](media/editing-auto-indentation.gif)

Aby zmienić to zachowanie, zobacz [Opcje edytora](#editor-options) dla grupy **kart** .

Zwijane regiony kodu umożliwiają tymczasowe ukrycie części kodu w edytorze. Program Visual Studio automatycznie tworzy różne regiony, podobnie jak w przypadku instrukcji wielowierszowych, chyba że **Zaawansowana** > **Konspekt** > opcja tworzenia **konspektu kodu** jest wyłączona.

Aby utworzyć region własny, należy ująć odpowiedni kod z komentarzami kończącymi się `---`. Małe kontrolki +/-po lewej stronie kodu pozwalają następnie rozwijać i zwijać regiony:

![Tworzenie regionu zwijanego z komentarzami](media/editing-collapsible-regions.gif)

Domyślnie program Visual Studio Wstawia spacje po naciśnięciu klawisza **Tab** . Możesz ponownie zmienić to zachowanie zgodnie z opisem w temacie [Opcje, Edytor tekstu, karty](../ide/reference/options-text-editor-all-languages.md).

## <a name="code-navigation"></a>Nawigacja po kodzie

Nawigacja po kodzie umożliwia szybki dostęp do kodu źródłowego programu R i jego bibliotek. Dzięki tym funkcjom przepływ pracy nie trzeba ręcznie przeszukiwać kodu.

**Przejdź do definicji** , szybko przeskoczy do definicji funkcji lub wyskakujący wbudowany edytor miniinstalacji, aby odczytać kod źródłowy funkcji biblioteki. Po prostu kliknij prawym przyciskiem myszy funkcję zainteresowania i wybierz pozycję **Przejdź do definicji**lub umieść kursor w funkcji i naciśnij klawisz **F12**.

To polecenie powoduje otwarcie nowego okna edytora zawierającego kod źródłowy dla tej funkcji. Kursor jest wygodnie umieszczony na początku definicji funkcji.

Przechodzenie do **definicji**, wywoływane z menu po kliknięciu prawym przyciskiem myszy lub **Alt**+**F12**, wstawia region przewijalny tylko do odczytu zawierający kod źródłowy funkcji poniżej wywołania funkcji:

![Animacja dla definicji wglądu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Wyślij kod do okna interaktywnego

Wielu deweloperów lubi napisać kod w edytorze, a następnie wysłać ten kod do [okna interaktywnego](interactive-repl-for-r-in-visual-studio.md) do natychmiastowego testowania (nazywanego również pętlą Read-Test-Print-Loop lub REPL). Naciśnięcie klawisza **Ctrl**+**Enter** w edytorze języka R powoduje wysłanie bieżącego wiersza kodu do okna interaktywnego, a następnie umieszczenie kursora w następnym wierszu. Po **naciśnięciu klawisza Ctrl**+**Enter**można efektywnie krokowo przełączać kod z edytora.

Możesz również wybrać opcję kod i nacisnąć klawisz **Ctrl**+**Enter** , aby zastosować cały wybór. Alternatywnie kliknij prawym przyciskiem myszy zaznaczenie i wybierz polecenie **wykonaj w trybie interaktywnym**.

## <a name="format-code"></a>Formatowanie kodu

Automatyczne formatowanie programu Visual Studio zachowuje zapisany kod, a także kod, który można wkleić do edytora, sformatowany zgodnie z preferencjami. Możesz również dokonać wyboru, kliknąć prawym przyciskiem myszy i wybrać opcję **Formatuj zaznaczenie** (**Ctrl**+**K**,**F**), aby zastosować te Preferencje. Na przykład jeśli w pojedynczym wierszu zdefiniowano definicję funkcji:

```R
f<-function  (a){  return(a + 1) }
```

Zastosowanie formatowania czyści to:

```R
f <- function(a) { return(a + 1) }
```

Aby ponownie sformatować cały plik kodu, wybierz opcję **edytuj** > **Advanced** > **Format dokumentu** (**Ctrl**+**E**,**D**).

Automatyczne formatowanie jest oddzielną operacją, którą można cofnąć. Na przykład, Jeśli wkleisz kod w edytorze i formatowanie zostanie zastosowane, zaznacz opcję **edytuj** > **Cofnij** lub naciśnij klawisz **Ctrl**+**Z** , aby zmienić formatowanie. Druga **cofnięcie** powoduje odwrócenie samego wklejenia.

Opcje formatowania (w tym wyłączenie formatowania) są ustawiane za pomocą **opcji** **Narzędzia** > w **edytorze tekstu** > karcie **R** > **Zaawansowane** . Możesz przejść bezpośrednio do tej strony za pomocą **Narzędzia R Tools** > **Editor Options** lub klikając prawym przyciskiem myszy w edytorze i wybierając **Opcje formatowania**. Szczegóły można znaleźć w sekcji [Opcje edytora](#editor-options) .

## <a name="inserting-roxygen-comments"></a>Wstawianie komentarzy Roxygen

RTVS udostępnia skrót do generowania komentarzy [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) przy użyciu nazw parametrów funkcji. Po prostu wpisz `###` w pustym wierszu powyżej definicji funkcji:

![Animacja wstawiania komentarza Roxygen](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Opcje edytora

Opcje specyficzne dla edytora są ustawiane za pomocą poleceń **narzędzia** > **Opcje** , nawigowanie do **edytora tekstu** > **R**lub przy użyciu polecenia skrótu **Narzędzia R Tools** > **opcji edytora**.

Opcje na kartach **Ogólne**, **paski przewijania**i **karty** nie są specyficzne dla języka R, ale zamiast ogólnych ustawień programu Visual Studio są dostępne dla wszystkich języków, ale są stosowane w przypadku poszczególnych języków. Aby uzyskać szczegółowe informacje, zobacz następujące artykuły:

- [Opcje, Edytor tekstów, Wszystkie języki](../ide/reference/options-text-editor-all-languages.md)
- [Śledź kod, dostosowując pasek przewijania](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Opcje, Edytor tekstu, karty](../ide/reference/options-text-editor-all-languages-tabs.md)

Opcje na karcie **Zaawansowane** w systemie **R** > są specyficzne dla RTVS:

| Grupa | Opcja | Domyślne | Opis |
| --- | --- | --- | --- |
| Formatowanie | Automatyczne formatowanie | Włączone | Formatuje kod w trakcie pisania. Nie ma wpływu na **wybór formatu** ani **Formatowanie poleceń dokumentu** . |
| | Rozwinięte nawiasy klamrowe | Wyłączone | Umieszcza otwarty {w nowym wierszu. |
| | Formatuj przy wklejaniu | Włączone | Stosuje formatowanie podczas wklejania. |
| | Zakres formatu na} | Włączone | Formatuje zakres po wpisaniu zamykającego}. |
| | Odstęp po przecinku | Włączone | Umieszcza spację po przecinkach. |
| | Spacja po słowie kluczowym | Włączone | Umieszcza spację po słowach kluczowych, takich jak `if`, `while`i `repeat`. |
| | Spacja przed { | Włączone | Umieszcza miejsce przed i otwierając {. |
| | Odstępy wokół = | Włączone | Umieszcza spacje wokół znaku równości. |
| IntelliSense | Zatwierdź przy klawiszu ENTER | Wyłączone | Zatwierdza wybór autouzupełniania po naciśnięciu **klawisza ENTER** . |
| | Zatwierdź przy kluczu spacji | Wyłączone | Zatwierdza wybór autouzupełniania po naciśnięciu **klawisza** .|
| | Lista uzupełniania pierwszego znaku | Włączone | Pokazuje listę uzupełniania dla pierwszych typów znaków. Gdy jest wyłączone, zostanie wyświetlona lista uzupełniania z przyciskami **edytuj** > **IntelliSense** > **listy członków** (**Ctrl**+**J**). |
| | Lista uzupełniania na klawisz **karty** | Wyłączone | Wywołuje listę uzupełniania, wpisując jeden lub więcej znaków i naciskając klawisz **Tab**. |
| | Dopasuj nazwy argumentów częściowo typów | Wyłączone | W przypadku wpisywania nazw argumentów w wywołaniu funkcji Pomoc dotycząca podpisu zawiera opis najlepszego dopasowania argumentu. |
| Okno interaktywne | Sprawdzanie składni w konsoli języka R | Wyłączone | Stosuje sprawdzanie składni w oknie interaktywnym. Sprawdzanie składni może nie funkcjonować poprawnie z użyciem instrukcji wielowierszowych. |
| Tworzenie konspektu | Konspekt kodu | Włączone | Program automatycznie tworzy zwijane regiony dla obszarów, takich jak instrukcje wielowierszowe. |
| Sprawdzanie składni | Pokaż błędy składni | Włączone | Włącza automatyczne sprawdzanie składni kodu. |

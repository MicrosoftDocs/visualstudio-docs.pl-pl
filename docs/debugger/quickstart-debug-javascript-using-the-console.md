---
title: Debugowanie kodu JavaScript przy użyciu konsoli programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- JavaScript
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e56350c2fd0583d3fef4e77e559a4df1fd894663
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348109"
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Debugowanie kodu JavaScript przy użyciu konsoli programu Visual Studio

Można użyć okna konsoli języka JavaScript do korzystania z i debugowania aplikacji platformy UWP utworzonych przy użyciu języka JavaScript. Te funkcje są obsługiwane w przypadku aplikacji i aplikacji platformy UWP utworzonych przy użyciu Visual Studio Tools Apache Cordova. Aby uzyskać informacje dotyczące poleceń konsoli, zobacz [JavaScript konsoli poleceń](../debugger/javascript-console-commands.md?view=vs-2017).

Okno konsoli JavaScript umożliwia:

- Wysyłanie obiektów, wartości i komunikatów z aplikacji do okna konsoli.

- Wyświetlaj i Modyfikuj wartości zmiennych lokalnych i globalnych w uruchomionej aplikacji.

- Wyświetl wizualizacje obiektów.

- Uruchom kod JavaScript, który jest wykonywany w bieżącym kontekście skryptu.

- Wyświetlaj błędy i wyjątki języka JavaScript, a także wyjątki Document Object Model (DOM) i środowisko wykonawcze systemu Windows.

- Wykonaj inne zadania, takie jak czyszczenie ekranu. Aby uzyskać pełną listę poleceń, zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md?view=vs-2017) .

> [!TIP]
> Jeśli okno konsoli JavaScript jest zamknięte, wybierz polecenie **Debuguj** >  **Windows**  >  **konsolę JavaScript** systemu Windows, aby je ponownie otworzyć. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.

Korzystając z okna konsoli JavaScript, można korzystać z aplikacji bez zatrzymywania i ponownego uruchamiania debugera. Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md). Aby uzyskać informacje o innych funkcjach debugowania języka JavaScript, takich jak używanie DOM Explorer i ustawień punktów przerwania, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) oraz [debugowanie aplikacji w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md).

## <a name="debug-by-using-the-javascript-console-window"></a><a name="InteractiveConsole"></a>Debugowanie przy użyciu okna konsoli JavaScript
Poniższe kroki tworzą `FlipView` aplikację i pokazują, jak interaktywnie debugować błąd kodowania JavaScript.

> [!NOTE]
> Przykładowa aplikacja jest aplikacją platformy UWP. Jednak funkcje konsoli opisane tutaj dotyczą również aplikacji utworzonych przy użyciu Visual Studio Tools Apache Cordova.

#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Aby debugować kod JavaScript w aplikacji FlipView

1. Utwórz nowe rozwiązanie w programie Visual Studio, wybierając pozycję **plik**  >  **Nowy projekt**.

2. Wybierz **język JavaScript**  >  **systemu Windows uniwersalny**, a następnie wybierz pozycję **aplikacja WinJS**.

3. Wpisz nazwę projektu, na przykład `FlipViewApp` , i wybierz **przycisk OK** , aby utworzyć aplikację.

4. W elemencie BODY index.html Zastąp istniejący kod HTML tym kodem:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. Otwórz domyślny. CSS i Dodaj arkusz CSS dla `#fView` selektora:

    ```css
    #fView {
        background-color:#0094ff;
        height: 500px;
        margin: 25px;
    }
    ```

6. Otwórz default.js i Zastąp kod następującym kodem JavaScript:

    ```javascript
    (function () {
        "use strict";

        var app = WinJS.Application;
        var activation = Windows.ApplicationModel.Activation;

        var myData = [];
        for (var x = 0; x < 4; x++) {
            myData[x] = { flipImg: "/images/logo.png" }
        };

        var pages = new WinJS.Binding.List(myData, { proxy: true });

        app.onactivated = function (args) {
            if (args.detail.kind === activation.ActivationKind.launch) {
                if (args.detail.previousExecutionState !==
                activation.ApplicationExecutionState.terminated) {
                    // TODO: . . .
                } else {
                    // TODO: . . .
                }
                args.setPromise(WinJS.UI.processAll());

                updateImages();
            }
        };

        function updateImages() {

            pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });

        };

        app.oncheckpoint = function (args) {
        };

        app.start();

        var publicMembers = {
            items: pages
        };

        WinJS.Namespace.define("Data", publicMembers);

    })();
    ```

7. Jeśli element docelowy debugowania nie jest jeszcze wybrany, wybierz opcję **komputer lokalny** z listy rozwijanej obok przycisku **urządzenia** na pasku narzędzi **debugowania** :

    ![Wybierz listę obiektów docelowych debugowania](../debugger/media/js_select_target.png "JS_Select_Target")

8. Naciśnij klawisz F5, aby uruchomić debuger.

    Aplikacja jest uruchamiana, ale brakuje obrazów. Błędy APPHOST w oknie konsoli JavaScript wskazują, że brakuje obrazów.

9. Po `FlipView` uruchomieniu aplikacji wpisz `Data.items` w wierszu polecenia okna konsoli (obok symbolu ">>") i naciśnij klawisz ENTER.

    Wizualizator dla `items` obiektu pojawia się w oknie konsoli. Oznacza to, że `items` obiekt skonkretyzowany i jest dostępny w bieżącym kontekście skryptu. W oknie konsoli możesz kliknąć węzeł obiektu, aby wyświetlić wartości właściwości (lub użyć klawiszy strzałek). Jeśli klikniesz przycisk w dół w `items._data` obiekcie, jak widać na poniższej ilustracji, oznacza to, że odwołania do źródła obrazu są nieprawidłowe, zgodnie z oczekiwaniami. Obrazy domyślne (logo.png) nadal znajdują się w obiekcie i brakuje obrazów przeplatanych o oczekiwanych obrazach.

    ![Okno konsoli JavaScript](../debugger/media/js_console_window.png "JS_Console_Window")

    Należy również zauważyć, że w obiekcie istnieje dużo więcej elementów `items._data` niż oczekiwano.

10. W wierszu polecenia wpisz `Data.items.push` i naciśnij klawisz ENTER. Okno konsoli zawiera wizualizator dla `push` funkcji, która jest zaimplementowana w [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] pliku projektu. W tej aplikacji używamy `push` do dodawania poprawnych elementów. Za pomocą funkcji IntelliSense dowiesz się, że należy użyć, `setAt` Aby zastąpić domyślne obrazy.

11. Aby rozwiązać ten problem interaktywnie bez zatrzymywania sesji debugowania, Otwórz default.js i wybierz ten kod z `updateImages` funkcji:

    ```javascript
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

     Skopiuj i wklej ten kod do monitu wejścia konsoli JavaScript.

    > [!TIP]
    > Po wklejeniu wielu wierszy kodu do monitu wejścia konsoli JavaScript, monit wejściowy konsoli automatycznie przełącza się do trybu wielowierszowego. Aby włączyć i wyłączyć tryb wielowierszowy, możesz nacisnąć klawisze Ctrl + Alt + M. Aby uruchomić skrypt w trybie wielowierszowym, naciśnij klawisze CTRL + ENTER lub wybierz symbol strzałki w prawym dolnym rogu okna. Aby uzyskać więcej informacji, zobacz [tryb Single-line i tryb wielowierszowy w oknie konsoli JavaScript](#SinglelineMultilineMode).

12. Popraw `push` wywołania funkcji w wierszu polecenia, zastępując polecenie `pages.push` `Data.items.setAt` . Poprawiony kod powinien wyglądać następująco:

    ```javascript
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

    > [!TIP]
    > Jeśli chcesz użyć `pages` obiektu zamiast `Data.items` , należy ustawić punkt przerwania w kodzie, aby zachować `pages` obiekt w zakresie.

13. Wybierz zielony symbol strzałki, aby uruchomić skrypt.

14. Naciśnij kombinację klawiszy Ctrl + Alt + M, aby przełączyć monit wejściowy konsoli do trybu jednowierszowego, a następnie wybierz pozycję **Wyczyść dane wejściowe** (czerwony znak "X"), aby usunąć kod z monitu wejściowego.

15. Wpisz `Data.items.length = 3` w wierszu polecenia, a następnie naciśnij klawisz ENTER. Spowoduje to usunięcie nadmiarowych elementów z danych.

16. Sprawdź aplikację ponownie i zobaczysz, że poprawne obrazy znajdują się na odpowiednich `FlipView` stronach.

17. W DOM Explorer można zobaczyć zaktualizowany element DIV i można przejść do poddrzewa, aby znaleźć oczekiwane elementy IMG.

18. Zatrzymaj debugowanie, wybierając **Debuguj**  >  **Zatrzymaj debugowanie** lub naciskając klawisze Shift + F5, a następnie Popraw kod źródłowy.

    Aby zapoznać się z kompletną stroną default.html zawierającą poprawiony przykładowy kod, zobacz [Debugowanie kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md).

## <a name="interactive-debugging-and-break-mode"></a><a name="InteractiveDebuggingBreakMode"></a>Interaktywny tryb debugowania i przerwania
Możesz użyć punktów przerwania i przejść do kodu podczas korzystania z narzędzi debugowania JavaScript, takich jak okno konsoli JavaScript. Gdy program uruchomiony w debugerze napotyka punkt przerwania, debuger tymczasowo zawiesza wykonywanie programu. Gdy wykonywanie jest zawieszone, program przełącza z trybu uruchamiania do trybu przerwania. W dowolnym momencie można wznowić wykonywanie.

Gdy program jest w trybie przerwania, można użyć okna konsoli JavaScript do uruchomienia skryptów i poleceń, które są prawidłowe w bieżącym kontekście wykonywania skryptu. W tej procedurze zostanie użyta stała wersja `FlipView` aplikacji, która została wcześniej utworzona w celu zademonstrowania użycia trybu przerwania.

#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Aby ustawić punkt przerwania i debugować aplikację

1. W pliku default.html `FlipView` aplikacji, która została wcześniej utworzona, otwórz menu skrótów dla `updateImages()` funkcji, a następnie wybierz **punkt**przerwania  >  **Wstaw punkt przerwania**.

2. Wybierz pozycję **komputer lokalny** na liście rozwijanej obok przycisku **Rozpocznij debugowanie** na pasku narzędzi **debugowania** .

3. Wybierz **Debuguj**  >  **Rozpocznij debugowanie**lub naciśnij klawisz F5.

    Aplikacja przechodzi do trybu przerwania, gdy wykonanie osiągnie `updateImages()` funkcję, a bieżący wiersz wykonania programu jest wyróżniony kolorem żółtym.

    ![Używanie trybu przerwania z konsolą JavaScript](../debugger/media/js_breakmode.png "JS_BreakMode")

    Można zmienić wartości zmiennych, aby natychmiast wpłynąć na stan programu bez kończenia bieżącej sesji debugowania.

4. Wpisz `updateImages` w wierszu polecenia i naciśnij klawisz ENTER. Wizualizator dla funkcji pojawia się w oknie konsoli.

5. Wybierz funkcję w oknie konsoli, aby wyświetlić implementację funkcji.

    Poniższa ilustracja przedstawia okno konsoli w tym momencie.

    ![Okno konsoli JavaScript przedstawiające wizualizator](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")

6. Skopiuj jeden wiersz funkcji z okna dane wyjściowe do monitu wejściowego i zmień wartość indeksu na 3:

    ```javascript
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    ```

7. Naciśnij klawisz ENTER, aby uruchomić wiersz kodu.

    Jeśli chcesz krokowo przejść przez wiersz kodu, naciśnij klawisz F11 lub naciśnij klawisz F5, aby kontynuować wykonywanie programu.

8. Naciśnij klawisz F5, aby kontynuować wykonywanie programu. `FlipView`Zostanie wyświetlona aplikacja, a teraz wszystkie cztery strony pokazują jeden z obrazów innych niż domyślne.

    Aby przełączyć się z powrotem do programu Visual Studio, naciśnij klawisz F12 lub Alt + Tab.

## <a name="single-line-mode-and-multiline-mode-in-the-javascript-console-window"></a><a name="SinglelineMultilineMode"></a>Tryb jednowierszowy i tryb wielowierszowy w oknie konsoli JavaScript
Monit wejściowy okna konsoli JavaScript obsługuje tryb Single-line i tryb wielowierszowy. Interaktywna procedura debugowania w tym temacie zawiera przykład użycia obu trybów. Możesz nacisnąć klawisze Ctrl + Alt + M, aby przełączać się między trybami.

Tryb jednowierszowy zawiera historię danych wejściowych. Możesz nawigować przez historię danych wejściowych za pomocą klawiszy Strzałka w górę i Strzałka w dół. Tryb jednowierszowy czyści monit wejściowy podczas uruchamiania skryptów. Aby uruchomić skrypt w trybie jednowierszowym, naciśnij klawisz ENTER.

Tryb wielowierszowy nie czyści monitu wejściowego podczas uruchamiania skryptów. Po przełączeniu do trybu single-line z trybu wielowierszowego można wyczyścić linię wejściową, naciskając pozycję **Wyczyść dane wejściowe** (czerwony znak "X"). Aby uruchomić skrypt w trybie wielowierszowym, naciśnij klawisze CTRL + ENTER lub wybierz symbol strzałki w prawym dolnym rogu okna.

## <a name="switching-the-script-execution-context"></a><a name="Switching"></a>Przełączanie kontekstu wykonywania skryptu
Okno konsoli JavaScript umożliwia korzystanie z jednego kontekstu wykonywania, który reprezentuje pojedyncze wystąpienie hosta platformy sieci Web (WWAHost.exe) w danym momencie. W niektórych scenariuszach aplikacja może uruchamiać inne wystąpienie hosta, na przykład w przypadku używania `iframe` , kontraktu udostępniania, internetowego procesu roboczego lub `WebView` kontrolki. Jeśli uruchomione jest inne wystąpienie hosta, można wybrać inny kontekst wykonywania podczas uruchamiania aplikacji, wybierając kontekst wykonywania na liście **Target** .

Na poniższej ilustracji przedstawiono listę docelową w oknie konsoli JavaScript.

![Wybór elementu docelowego w oknie konsoli JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

Możesz również przełączyć kontekst wykonywania za pomocą `cd` polecenia, ale musisz znać nazwę innego kontekstu wykonywania i używane odwołanie musi znajdować się w zakresie. Lista **obiektów docelowych** zapewnia lepszy dostęp do innych kontekstów wykonywania.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md?view=vs-2017)
- [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md?view=vs-2017)
- [Debugowanie przykładowego kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
- [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)
- [Pomoc techniczna i ułatwienia dostępu](https://visualstudio.microsoft.com/vs/support/)

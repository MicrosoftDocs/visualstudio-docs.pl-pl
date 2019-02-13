---
title: Debugowanie kodu JavaScript przy użyciu konsoli | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 9d1056e65e769710a1092142104e87eaead37521
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227577"
---
# <a name="debug-javascript-using-the-console-in-visual-studio"></a>Debugowanie kodu JavaScript przy użyciu konsoli w programie Visual Studio

Okno konsoli JavaScript w interakcję i debugowanie aplikacji platformy UWP skompilowane przy użyciu języka JavaScript. Te funkcje są obsługiwane dla aplikacji platformy uniwersalnej systemu Windows i aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova. Aby uzyskać informacje o poleceniu konsoli, zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).

Okna konsoli języka JavaScript umożliwia:

- Wysyłanie obiektów, wartości i komunikaty z aplikacji w oknie konsoli.

- Wyświetlanie i modyfikowanie wartości zmiennych lokalnych i globalnych w działającej aplikacji.

- Wizualizatory obiekt widoku.

- Uruchom kod JavaScript, który jest wykonywany w ramach bieżącego kontekstu skryptu.

- Wyświetl błędy języka JavaScript i wyjątków, oprócz wyjątków modelu DOM (Document Object) i środowiska wykonawczego Windows.

- Wykonywanie innych zadań, takich jak wyczyścić ekran. Zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md) pełną listę poleceń.

> [!TIP]
> Jeśli okno konsoli JavaScript jest zamknięta, wybierz **debugowania**> **Windows** > **konsoli JavaScript** otworzyć go ponownie. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.

Korzystanie z okna konsoli języka JavaScript, możesz porozmawiać z aplikacji bez zatrzymywania i ponownego uruchamiania debugera. Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md). Aby uzyskać informacje na temat innych debugowanie funkcji, takich jak za pomocą narzędzia DOM Explorer oraz ustawiania punktów przerwania, JavaScript, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) i [debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps).

## <a name="InteractiveConsole"></a> Debugowanie przy użyciu okna konsoli języka JavaScript
Poniższe kroki umożliwiają utworzenie `FlipView` aplikacji i pokazują, jak interaktywnie debugowanie kodu JavaScript, błąd kodowania.

> [!NOTE]
> Przykładowa aplikacja w tym miejscu jest aplikacją platformy uniwersalnej systemu Windows. Jednak funkcje konsoli opisane w tym miejscu dotyczą również aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova.

#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Aby debugować kod JavaScript w aplikacji FlipView

1. Utwórz nowe rozwiązanie w programie Visual Studio, wybierając **pliku** > **nowy projekt**.

2. Wybierz **JavaScript** > **Windows Universal**, a następnie wybierz **aplikacja WinJS**.

3. Wpisz nazwę dla projektu, takie jak `FlipViewApp`i wybierz polecenie **OK** do tworzenia aplikacji.

4. W elemencie BODY index.html Zastąp istniejący kod HTML przy użyciu tego kodu:

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

5. Otwórz default.css i Dodaj CSS dla `#fView` selektor:

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

7. Jeśli docelowy debugowania nie została jeszcze wybrana, wybierz opcję **komputera lokalnego** z listy rozwijanej obok pozycji listy **urządzenia** znajdujący się na **debugowania** narzędzi:

    ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")

8. Naciśnij klawisz F5, aby uruchomić debuger.

    Brak uruchomienia aplikacji, ale obrazy. APPHOST błędy w oknie konsoli JavaScript wskazują, czy Brak obrazów.

9. Za pomocą `FlipView` aplikacji, typ `Data.items` w konsoli wiersza okna dane wejściowe (obok pozycji ">>" symbol) i naciśnij klawisz Enter.

    Wizualizator dla `items` obiekt, który jest wyświetlany w oknie konsoli. Oznacza to, że `items` obiekt uruchomiony i jest dostępny w bieżącym kontekście skryptu. W oknie konsoli możesz kliknąć przez węzły obiektu, aby wyświetlić wartości właściwości (lub użyj klawiszy strzałek). Jeśli klikniesz w dół do `items._data` obiektu, jak widać na ilustracji, można znaleźć jego odwołania do źródła obrazu są niepoprawne, zgodnie z oczekiwaniami. Domyślne obrazy (logo.png) są nadal znajdują się w obiekcie, a istnieją brakujących obrazów oraz oczekiwanego obrazów.

    ![Okno konsoli JavaScript](../debugger/media/js_console_window.png "JS_Console_Window")

    Należy również zauważyć, że istnieje wiele elementów, które znajdują się w `items._data` obiektu niż można by oczekiwać.

10. W wierszu polecenia wpisz `Data.items.push` i naciśnij klawisz Enter. W oknie konsoli wyświetlane są Wizualizator dla `push` funkcji, która jest zaimplementowana w [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] pliku projektu. W tej aplikacji, używamy `push` dodać odpowiednie elementy. Z badania nieco za pomocą funkcji IntelliSense, dowiesz się, że firma Microsoft używa `setAt` zastąpić domyślne obrazy.

11. Aby rozwiązać ten problem, interaktywnie bez zatrzymywania sesji debugowania, otwórz default.js i wybierz ten kod z `updateImages` funkcji:

    ```javascript
    pages.push(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    pages.push(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    pages.push(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

     Skopiuj i wklej ten kod w wierszu polecenia konsoli JavaScript danych wejściowych.

    > [!TIP]
    > Podczas wklejania wiele wierszy kodu w konsoli JavaScript danych wejściowych wiersza, wiersz danych wejściowych konsoli automatycznie wykona przełączenie do trybu wielowierszowego. Można nacisnąć klawisze Ctrl + Alt + M, aby włączyć tryb wielowierszowy włączać i wyłączać. Aby uruchomić skrypt w trybu wielowierszowego, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałki w prawym dolnym rogu okna. Aby uzyskać więcej informacji, zobacz [trybu jednowierszowego i trybu wielowierszowego w oknie konsoli JavaScript](#SinglelineMultilineMode).

12. Popraw `push` funkcja wywołuje w wierszu polecenia, zastępując `pages.push` z `Data.items.setAt`. Poprawiony kod powinien wyglądać następująco:

    ```javascript
    Data.items.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    Data.items.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
    Data.items.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    ```

    > [!TIP]
    > Jeśli chcesz używać `pages` zamiast obiektu `Data.items`, należy ustawić punkt przerwania w kodzie, aby zachować `pages` obiekt w zakresie.

13. Wybierz symbol zieloną strzałkę, aby uruchomić skrypt.

14. Naciśnij klawisze Ctrl + Alt + M, Przełącz wiersz danych wejściowych konsoli do trybu jednowierszowego, a następnie wybierz polecenie **Wyczyść dane wejściowe** (kolor czerwony "symbol X") można usunąć kod w wierszu danych wejściowych.

15. Typ `Data.items.length = 3` w wierszu, a następnie naciśnij klawisz Enter. Spowoduje to usunięcie nadmiarowe elementy danych.

16. Sprawdź aplikację ponownie, a zobaczysz, czy poprawny obrazów na poprawny `FlipView` stron.

17. W Eksploratorze DOM możesz zobaczyć zaktualizowane element DIV, i możesz przejść do poddrzewo, aby znaleźć oczekiwanego elementy IMG.

18. Zatrzymaj debugowanie wybierając **debugowania** > **Zatrzymaj debugowanie** lub przez naciśnięcie klawisza Shift + F5, a następnie Rozwiąż kodu źródłowego.

    Aby zawierającą pełną default.html strony poprawione przykładowego kodu, zobacz [debugowanie HTML, CSS i JavaScript przykładowy kod](../debugger/debug-html-css-and-javascript-sample-code.md).

## <a name="InteractiveDebuggingBreakMode"></a> Tryb interaktywny debugowania i podziału
Możesz użyć punktów przerwania i wejdź do kodu, podczas korzystania z narzędzi, takich jak okno konsoli JavaScript debugowanie kodu JavaScript. Gdy program, który jest uruchomiony w debugerze napotka punkt przerwania, debuger tymczasowo wstrzymuje wykonywanie programu. Gdy wykonanie programu jest zawieszone, program zmienia się z wykonywania tryb na tryb przerwania. Można wznowić wykonywania w dowolnym momencie.

Gdy program jest w trybie przerwania, można użyć okna konsoli JavaScript na uruchamianie skryptów i poleceń, które są prawidłowe w bieżącym kontekście wykonania skryptu. W tej procedurze użyjesz stały wersję `FlipView` aplikacji utworzony wcześniej, aby zademonstrować użycie trybu przerwania.

#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Aby ustawić punkt przerwania i debugować aplikację

1. W pliku default.html `FlipView` aplikację, która wcześniej utworzona, otwórz menu skrótów dla `updateImages()` funkcji, a następnie wybierz **punktu przerwania** > **Wstaw punkt przerwania**.

2. Wybierz **komputera lokalnego** listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** znajdujący się na **debugowania** paska narzędzi.

3. Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij klawisz F5.

    Aplikacja przejdzie do trybu podziału gdy wykonywanie osiągnie `updateImages()` funkcji i bieżący wiersz wykonania programu zostanie wyróżniona na żółto.

    ![Za pomocą konsoli języka JavaScript przy użyciu trybu przerwania](../debugger/media/js_breakmode.png "JS_BreakMode")

    Można zmienić wartości zmiennych, które bezpośrednio wpływają na stan programu bez przerywania bieżącą sesję debugowania.

4. Typ `updateImages` wiersza i naciśnij klawisz Enter. Wizualizator dla funkcji pojawia się w oknie konsoli.

5. Wybierz funkcję w oknie konsoli, aby pokazać implementacja funkcji.

    Poniższa ilustracja przedstawia okno konsoli w tym momencie.

    ![Okno konsoli JavaScript przedstawiający wizualizatora](../debugger/media/js_console_function_visualizer.png "JS_Console_Function_Visualizer")

6. Skopiuj jeden wiersz w funkcji z okna danych wyjściowych do danych wejściowych wiersza polecenia i zmień wartość indeksu na 3:

    ```javascript
    pages.setAt(3, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
    ```

7. Naciśnij klawisz Enter, aby uruchomić wiersz kodu.

    Jeśli chcesz śledzić wykonywanie kodu wiersz po wierszu, naciśnij klawisz F11 lub naciśnij klawisz F5, aby kontynuować wykonywanie programów.

8. Naciśnij klawisz F5, aby kontynuować wykonywanie programów. `FlipView` Pojawia się w aplikacji, a wszystkie cztery strony pokazują teraz jeden z obrazów innych niż domyślne.

    Aby przełączyć się do programu Visual Studio, naciśnij klawisz F12 lub Alt + Tab.

## <a name="SinglelineMultilineMode"></a> Tryb jednowierszowy i trybu wielowierszowego w oknie konsoli JavaScript
Monit wejściowy dla okna konsoli języka JavaScript obsługuje tryb jednowierszowy i trybu wielowierszowego. Interaktywne procedury debugowania, w tym temacie zawiera przykład użycia obu trybów. Można nacisnąć klawisze Ctrl + Alt + M, aby przełączać się między trybami.

Tryb jednowierszowy zawiera Historia wejściowego. Możesz przejść w historii danych wejściowych za pomocą klawiszy Strzałka w górę i Strzałka w dół. Tryb jednowierszowy czyści wiersz danych wejściowych podczas wykonywania skryptów. Aby uruchomić skrypt w tryb jednowierszowy, naciśnij klawisz Enter.

Tryb wielowierszowy czyść wiersz danych wejściowych podczas uruchamiania skryptów. Po przełączeniu do trybu jednowierszowego z trybu wielowierszowego, możesz wyczyścić wejścia liniowego, naciskając klawisz **Wyczyść dane wejściowe** (czerwony "symbol X"). Aby uruchomić skrypt w trybu wielowierszowego, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałki w prawym dolnym rogu okna.

## <a name="Switching"></a> Przełączanie kontekstu wykonywania skryptu
Okna konsoli języka JavaScript pozwala na interakcję z kontekstem pojedyncze wykonanie, który reprezentuje pojedyncze wystąpienie hosta platformy sieci web (WWAHost.exe), w danym momencie. W niektórych scenariuszach aplikacji może uruchomić kolejne wystąpienie hosta, na przykład przy użyciu `iframe`, kontrakt udziału, internetowy proces roboczy lub `WebView` kontroli. Jeśli działa inne wystąpienie hosta, można wybrać kontekstu wykonywania różnych podczas uruchamiania aplikacji, wybierając w kontekście wykonywania **docelowej** listy.

Poniższa ilustracja przedstawia listy docelowej w oknie konsoli JavaScript.

![Docelowa wybierane w oknie konsoli JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

Można również przełączyć kontekst wykonywania za pomocą `cd` polecenie, ale musisz znać nazwę kontekstu wykonywania i odwołania, możesz użyć musi się mieścić w zakresie. **Docelowej** listy zapewnia lepszy dostęp do innych kontekstach wykonywania.

## <a name="see-also"></a>Zobacz też
[Debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)  
[Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)  
[Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)  
[Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)  
[Debugowanie przykładowego kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)  
[Szybki start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)  
[Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)  
[Pomoc techniczna i dostępność](https://visualstudio.microsoft.com/vs/support/)

---
title: 'Szybki Start: Debugowanie kodu JavaScript przy użyciu konsoli | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.JavaScriptConsole
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript Console
- JavaScript debugging
- debugging, JavaScript
ms.assetid: ea7adb71-52b6-4a5a-9346-98ca94b06bd7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61f36594b4158c95621ec240fd7a883accd259a8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802606"
---
# <a name="quickstart-debug-javascript-using-the-console"></a>Szybki start: Debugowanie kodu JavaScript przy użyciu konsoli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Okno konsoli JavaScript w interakcję i debugować aplikacje Store utworzone przy użyciu języka JavaScript. Te funkcje są obsługiwane w przypadku [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji Windows Phone Store apps i aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova. Aby uzyskać informacje o poleceniu konsoli, zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
 Okna konsoli języka JavaScript umożliwia:  
  
- Wysyłanie obiektów, wartości i komunikaty z aplikacji w oknie konsoli.  
  
- Wyświetlanie i modyfikowanie wartości zmiennych lokalnych i globalnych w działającej aplikacji.  
  
- Wizualizatory obiekt widoku.  
  
- Uruchom kod JavaScript, który jest wykonywany w ramach bieżącego kontekstu skryptu.  
  
- Wyświetl błędy języka JavaScript i wyjątków, oprócz wyjątków modelu DOM (Document Object) i środowiska wykonawczego Windows.  
  
- Wykonywanie innych zadań, takich jak wyczyścić ekran. Zobacz [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md) pełną listę poleceń.  
  
  W tym temacie:  
  
- [Debugowanie przy użyciu okna konsoli języka JavaScript](#InteractiveConsole)  
  
- [Tryb interaktywny debugowania i podziału](#InteractiveDebuggingBreakMode)  
  
- [Tryb jednowierszowy i trybu wielowierszowego w oknie konsoli JavaScript](#SinglelineMultilineMode)  
  
- [Przełączanie kontekstu wykonywania skryptu](#Switching)  
  
> [!TIP]
>  Jeśli okno konsoli JavaScript jest zamknięta, wybierz **debugowania**>**Windows** > **konsoli JavaScript** otworzyć go ponownie. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.  
  
 Korzystanie z okna konsoli języka JavaScript, możesz porozmawiać z aplikacji bez zatrzymywania i ponownego uruchamiania debugera. Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md). Aby uzyskać informacje na temat innych debugowanie funkcji, takich jak za pomocą narzędzia DOM Explorer oraz ustawiania punktów przerwania, JavaScript, zobacz [Szybki Start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) i [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
##  <a name="InteractiveConsole"></a> Debugowanie przy użyciu okna konsoli języka JavaScript  
 Poniższe kroki umożliwiają utworzenie `FlipView` aplikacji i pokazują, jak interaktywnie debugowanie kodu JavaScript, błąd kodowania.  
  
> [!CAUTION]
>  Przykładowa aplikacja w tym miejscu jest aplikacji Windows Store. Jednak funkcje konsoli opisane w tym miejscu dotyczą również aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova.  
  
#### <a name="to-debug-javascript-code-in-the-flipview-app"></a>Aby debugować kod JavaScript w aplikacji FlipView  
  
1.  Utwórz nowe rozwiązanie w programie Visual Studio, wybierając **pliku** > **nowy projekt**.  
  
2.  Wybierz **JavaScript** > **Store Apps**, wybierają **aplikacje Windows** lub **aplikacji Windows Phone**, a następnie wybierz polecenie  **Pusta aplikacja**.  
  
3.  Wpisz nazwę dla projektu, takie jak `FlipViewApp`i wybierz polecenie **OK** do tworzenia aplikacji.  
  
4.  W elemencie BODY default.html Zastąp istniejący kod HTML przy użyciu tego kodu:  
  
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
  
5.  Otwórz default.css i Dodaj CSS dla `#fView` selektor:  
  
    ```css  
    #fView {  
        background-color:#0094ff;  
        height: 500px;  
        margin: 25px;  
    }  
    ```  
  
6.  Otwórz default.js i Zastąp kod następującym kodem JavaScript:  
  
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
  
            pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
            pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
            pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
  
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
  
7.  Jeśli docelowy debugowania nie została jeszcze wybrana, wybierz opcję **symulator** lub dla Windows Phone **Emulator 8.1 WVGA 4 cala 512MB** z listy rozwijanej obok pozycji listy **urządzenia** znajdujący się na **debugowania** narzędzi:  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8.  Naciśnij klawisz F5, aby uruchomić debuger.  
  
     Brak uruchomienia aplikacji, ale obrazy. APPHOST błędy w oknie konsoli JavaScript wskazują, czy Brak obrazów.  
  
9. Za pomocą `FlipView` aplikacji uruchomionej w symulatorze lub w emulatorze telefonu, typ `Data.items` w konsoli wiersza okna dane wejściowe (obok pozycji ">>" symbol) i naciśnij klawisz Enter.  
  
     Wizualizator dla `items` obiekt, który jest wyświetlany w oknie konsoli. Oznacza to, że `items` obiekt uruchomiony i jest dostępny w bieżącym kontekście skryptu. W oknie konsoli możesz kliknąć przez węzły obiektu, aby wyświetlić wartości właściwości (lub użyj klawiszy strzałek). Jeśli klikniesz w dół do `items._data` obiektu, jak widać na ilustracji, można znaleźć jego odwołania do źródła obrazu są niepoprawne, zgodnie z oczekiwaniami. Domyślne obrazy (logo.png) są nadal znajdują się w obiekcie, a istnieją brakujących obrazów oraz oczekiwanego obrazów.  
  
     ![Okno konsoli JavaScript](../debugger/media/js-console-window.png "JS_Console_Window")  
  
     Należy również zauważyć, że istnieje wiele elementów, które znajdują się w `items._data` obiektu niż można by oczekiwać.  
  
10. W wierszu polecenia wpisz `Data.items.push` i naciśnij klawisz Enter. W oknie konsoli wyświetlane są Wizualizator dla `push` funkcji, która jest zaimplementowana w [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] pliku projektu. W tej aplikacji, używamy `push` dodać odpowiednie elementy. Z badania nieco za pomocą funkcji IntelliSense, dowiesz się, że firma Microsoft używa `setAt` zastąpić domyślne obrazy.  
  
11. Aby rozwiązać ten problem, interaktywnie bez zatrzymywania sesji debugowania, otwórz default.js i wybierz ten kod z `updateImages` funkcji:  
  
    ```javascript  
    pages.push(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    pages.push(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    pages.push(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
     Skopiuj i wklej ten kod w wierszu polecenia konsoli JavaScript danych wejściowych.  
  
    > [!TIP]
    >  Podczas wklejania wiele wierszy kodu w konsoli JavaScript danych wejściowych wiersza, wiersz danych wejściowych konsoli automatycznie wykona przełączenie do trybu wielowierszowego. Można nacisnąć klawisze Ctrl + Alt + M, aby włączyć tryb wielowierszowy włączać i wyłączać. Aby uruchomić skrypt w trybu wielowierszowego, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałki w prawym dolnym rogu okna. Aby uzyskać więcej informacji, zobacz [trybu jednowierszowego i trybu wielowierszowego w oknie konsoli JavaScript](#SinglelineMultilineMode).  
  
12. Popraw `push` funkcja wywołuje w wierszu polecenia, zastępując `pages.push` z `Data.items.setAt`. Poprawiony kod powinien wyglądać następująco:  
  
    ```javascript  
    Data.items.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
    Data.items.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
    Data.items.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
    > [!TIP]
    >  Jeśli chcesz używać `pages` zamiast obiektu `Data.items`, należy ustawić punkt przerwania w kodzie, aby zachować `pages` obiekt w zakresie.  
  
13. Wybierz symbol zieloną strzałkę, aby uruchomić skrypt.  
  
14. Naciśnij klawisze Ctrl + Alt + M, Przełącz wiersz danych wejściowych konsoli do trybu jednowierszowego, a następnie wybierz polecenie **Wyczyść dane wejściowe** (kolor czerwony "symbol X") można usunąć kod w wierszu danych wejściowych.  
  
15. Typ `Data.items.length = 3` w wierszu, a następnie naciśnij klawisz Enter. Spowoduje to usunięcie nadmiarowe elementy danych.  
  
16. Ponownie sprawdzić symulatorze lub w emulatorze telefonu, a zobaczysz, czy poprawny obrazów na poprawny `FlipView` stron.  
  
17. W Eksploratorze DOM możesz zobaczyć zaktualizowane element DIV, i możesz przejść do poddrzewo, aby znaleźć oczekiwanego elementy IMG.  
  
18. Zatrzymaj debugowanie wybierając **debugowania** > **Zatrzymaj debugowanie** lub przez naciśnięcie klawisza Shift + F5, a następnie Rozwiąż kodu źródłowego.  
  
     Aby zawierającą pełną default.html strony poprawione przykładowego kodu, zobacz [debugowanie HTML, CSS i JavaScript przykładowy kod](../debugger/debug-html-css-and-javascript-sample-code.md).  
  
##  <a name="InteractiveDebuggingBreakMode"></a> Tryb interaktywny debugowania i podziału  
 Możesz użyć punktów przerwania i wejdź do kodu, podczas korzystania z narzędzi, takich jak okno konsoli JavaScript debugowanie kodu JavaScript. Gdy program, który jest uruchomiony w debugerze napotka punkt przerwania, debuger tymczasowo wstrzymuje wykonywanie programu. Gdy wykonanie programu jest zawieszone, program zmienia się z wykonywania tryb na tryb przerwania. Można wznowić wykonywania w dowolnym momencie.  
  
 Gdy program jest w trybie przerwania, można użyć okna konsoli JavaScript na uruchamianie skryptów i poleceń, które są prawidłowe w bieżącym kontekście wykonania skryptu. W tej procedurze użyjesz stały wersję `FlipView` aplikacji utworzony wcześniej, aby zademonstrować użycie trybu przerwania.  
  
#### <a name="to-set-a-breakpoint-and-debug-the-app"></a>Aby ustawić punkt przerwania i debugować aplikację  
  
1.  W pliku default.html `FlipView` aplikację, która wcześniej utworzona, otwórz menu skrótów dla `updateImages()` funkcji, a następnie wybierz **punktu przerwania** > **Wstaw punkt przerwania**.  
  
2.  Wybierz **komputera lokalnego** lub **Emulator 8.1 WVGA 4 cala 512MB** listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** znajdujący się na **debugowania** pasek narzędzi.  
  
3.  Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij klawisz F5.  
  
     Aplikacja przejdzie do trybu podziału gdy wykonywanie osiągnie `updateImages()` funkcji i bieżący wiersz wykonania programu zostanie wyróżniona na żółto.  
  
     ![Za pomocą konsoli języka JavaScript przy użyciu trybu przerwania](../debugger/media/js-breakmode.png "JS_BreakMode")  
  
     Można zmienić wartości zmiennych, które bezpośrednio wpływają na stan programu bez przerywania bieżącą sesję debugowania.  
  
4.  Typ `updateImages` wiersza i naciśnij klawisz Enter. Wizualizator dla funkcji pojawia się w oknie konsoli.  
  
5.  Wybierz funkcję w oknie konsoli, aby pokazać implementacja funkcji.  
  
     Poniższa ilustracja przedstawia okno konsoli w tym momencie.  
  
     ![Okno konsoli JavaScript przedstawiający wizualizatora](../debugger/media/js-console-function-visualizer.png "JS_Console_Function_Visualizer")  
  
6.  Skopiuj jeden wiersz w funkcji z okna danych wyjściowych do danych wejściowych wiersza polecenia i zmień wartość indeksu na 3:  
  
    ```javascript  
    pages.setAt(3, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    ```  
  
7.  Naciśnij klawisz Enter, aby uruchomić wiersz kodu.  
  
     Jeśli chcesz śledzić wykonywanie kodu wiersz po wierszu, naciśnij klawisz F11 lub naciśnij klawisz F5, aby kontynuować wykonywanie programów.  
  
8.  Naciśnij klawisz F5, aby kontynuować wykonywanie programów. `FlipView` Pojawia się w aplikacji, a wszystkie cztery strony pokazują teraz jeden z obrazów innych niż domyślne.  
  
     Aby przełączyć się do programu Visual Studio, naciśnij klawisz F12 lub Alt + Tab.  
  
##  <a name="SinglelineMultilineMode"></a> Tryb jednowierszowy i trybu wielowierszowego w oknie konsoli JavaScript  
 Monit wejściowy dla okna konsoli języka JavaScript obsługuje tryb jednowierszowy i trybu wielowierszowego. Interaktywne procedury debugowania, w tym temacie zawiera przykład użycia obu trybów. Można nacisnąć klawisze Ctrl + Alt + M, aby przełączać się między trybami.  
  
 Tryb jednowierszowy zawiera Historia wejściowego. Możesz przejść w historii danych wejściowych za pomocą klawiszy Strzałka w górę i Strzałka w dół. Tryb jednowierszowy czyści wiersz danych wejściowych podczas wykonywania skryptów. Aby uruchomić skrypt w tryb jednowierszowy, naciśnij klawisz Enter.  
  
 Tryb wielowierszowy czyść wiersz danych wejściowych podczas uruchamiania skryptów. Po przełączeniu do trybu jednowierszowego z trybu wielowierszowego, możesz wyczyścić wejścia liniowego, naciskając klawisz **Wyczyść dane wejściowe** (czerwony "symbol X"). Aby uruchomić skrypt w trybu wielowierszowego, naciśnij klawisze Ctrl + Enter lub wybierz symbol strzałki w prawym dolnym rogu okna.  
  
##  <a name="Switching"></a> Przełączanie kontekstu wykonywania skryptu  
 Okna konsoli języka JavaScript pozwala na interakcję z kontekstem pojedyncze wykonanie, który reprezentuje pojedyncze wystąpienie hosta platformy sieci web (WWAHost.exe), w danym momencie. W niektórych scenariuszach aplikacji może uruchomić kolejne wystąpienie hosta, na przykład przy użyciu `iframe`, kontrakt udziału, internetowy proces roboczy lub `WebView` kontroli. Jeśli działa inne wystąpienie hosta, można wybrać kontekstu wykonywania różnych podczas uruchamiania aplikacji, wybierając w kontekście wykonywania **docelowej** listy.  
  
 Poniższa ilustracja przedstawia listy docelowej w oknie konsoli JavaScript.  
  
 ![Docelowa wybierane w oknie konsoli JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
 Można również przełączyć kontekst wykonywania za pomocą `cd` polecenie, ale musisz znać nazwę kontekstu wykonywania i odwołania, możesz użyć musi się mieścić w zakresie. **Docelowej** listy zapewnia lepszy dostęp do innych kontekstach wykonywania.  
  
##  <a name="BrowserSupport"></a> Przeglądarki i pomoc techniczna platformy  
 Okno konsoli JavaScript jest obsługiwane na następujących platformach:  
  
-   [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] i Windows Phone Store aplikacji przy użyciu języków JavaScript i HTML  
  
-   Internet Explorer 11, systemem [!INCLUDE[win81](../includes/win81-md.md)]  
  
-   Uruchomione programie Internet Explorer 10 [!INCLUDE[win8](../includes/win8-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)   
 [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Debugowanie przykładowego kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Szybki Start: Debugowanie HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)   
 [Pomoc techniczna i dostępność](http://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)




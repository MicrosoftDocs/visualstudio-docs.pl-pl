---
title: Debugowanie kodu HTML i CSS w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.date: 07/17/2018
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- JavaScript
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [UWP apps]
- DOM Explorer [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3bb136367d08fa430080cb26290fff9aa4e15d13
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526259"
---
# <a name="debug-html-and-css-in-uwp-apps-in-visual-studio"></a>Debugowanie kodu HTML i CSS w aplikacjach platformy UWP w programie Visual Studio

Dla aplikacji JavaScript programu Visual Studio zapewnia kompleksowe środowisko debugowania, który zawiera funkcje, które są znane deweloperom korzystającym z programu Internet Explorer i Visual Studio. Te funkcje są obsługiwane dla aplikacji platformy uniwersalnej systemu Windows i aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova.

Przy użyciu interaktywnych modelu debugowania, dostarczone przez narzędzia inspekcji modelu DOM, można wyświetlać i modyfikować wygenerowanego kodu HTML i CSS. Można to zrobić bez zatrzymywania i ponownego uruchamiania debugera.

Aby uzyskać informacje na temat innych debugowanie funkcji, takich jak korzystanie z okna konsoli języka JavaScript i ustawiania punktów przerwania, JavaScript, zobacz [Szybki Start: Debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps).

## <a name="InspectingDOM"></a> Sprawdzanie modelu DOM na żywo
Narzędzia DOM Explorer Pokazuje widok renderowanej strony i narzędzia DOM Explorer można użyć, aby zmienić wartości i natychmiast wyświetlić wyniki. Dzięki temu można testować zmiany bez zatrzymywania i ponownego uruchamiania debugera. Kod źródłowy w projekcie nie zmienia się podczas interakcji z strony za pomocą tej metody, dlatego podczas korekt odpowiedni kod możesz znaleźć, wprowadź zmiany do kodu źródłowego.

> [!TIP]
> Aby uniknąć zatrzymywania i ponownego uruchamiania debugera, po wprowadzeniu zmian do kodu źródłowego, możesz odświeżyć aplikację za pomocą **aplikacji Windows Odśwież** przycisk na pasku narzędzi debugowania (lub naciskając klawisz F4). Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).

Możesz użyć narzędzia DOM Explorer, aby:

- Przejdź poddrzewo elementu modelu DOM i sprawdzić wygenerowanego kodu HTML, CSS i JavaScript.

- Dynamicznie Edycja atrybutów i style CSS renderowany elementów i natychmiast wyświetlić wyniki.

- Sprawdzanie, jak zostały zastosowane style CSS do elementów strony i śledzenia reguł, które zostały zastosowane.

  Podczas debugowania aplikacji, często jest konieczne do wybrania elementów w modelu DOM Explorer. Po wybraniu elementu, wartości, które są wyświetlane na kartach po prawej stronie Eksploratora DOM automatycznie aktualizowana w celu odzwierciedlenia wybranego elementu w programie DOM Explorer. Oto karty: **Style**, **obliczane**, **układ**. Aplikacje platformy uniwersalnej systemu Windows obsługują także **zdarzenia** i **zmiany** karty. Aby uzyskać więcej informacji na temat wybierania elementów, zobacz [wybierania elementów](#SelectingElements).

> [!TIP]
> Jeśli nastąpi zamknięcie okna narzędzia DOM Explorer, wybierz **debugowania**>**Windows** > **narzędzia DOM Explorer** otworzyć go ponownie. Okno jest wyświetlane tylko podczas sesji debugowania skryptu.

W poniższej procedurze omówimy proces interaktywnie debugowanie aplikacji przy użyciu narzędzia DOM Explorer. Utworzymy aplikację, która używa `FlipView` sterowania, a następnie ją debugować. Ta aplikacja zawiera kilka błędów.

> [!WARNING]
> Następujące Przykładowa aplikacja jest aplikacją platformy uniwersalnej systemu Windows. Te same funkcje są obsługiwane w przypadku Cordova, ale aplikacja będzie inna.

#### <a name="to-debug-by-inspecting-the-live-dom"></a>Aby debugować, sprawdzając modelu DOM na żywo

1. Utwórz nowe rozwiązanie w programie Visual Studio, wybierając **pliku** > **nowy projekt**.

2. Wybierz **JavaScript** > **Windows Universal**, a następnie wybierz **aplikacja WinJS**.

3. Wpisz nazwę dla projektu, takie jak `FlipViewApp`i wybierz polecenie **OK** do tworzenia aplikacji.

4. W elemencie BODY index.html Dodaj następujący kod:

    ```html
    <div id="flipTemplate" data-win-control="WinJS.Binding.Template"
            style="display:none">
        <div class="fixedItem" >
            <img src="#" data-win-bind="src: flipImg" />
        </div>
    </div>
    <div id="fView" style="width:100px;height:100px"
        data-win-control="WinJS.UI.FlipView" data-win-options="{
        itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
    </div>
    ```

5. Otwórz default.css i dodaj następujące arkusze CSS:

    ```css
    #fView {
        background-color:#0094ff;
        height: 100%;
        width: 100%;
        margin: 25%;
    }
    ```

6. Zastąp kod w pliku default.js przy użyciu tego kodu:

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

            pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
            pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
            pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
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

    Poniższa ilustracja pokazuje, co chcemy zobaczyć, jeśli możemy uruchomić tę aplikację. Aby uzyskać aplikację w ten stan firma Microsoft będzie jednak ustalenie liczby błędów.

    ![Aplikacja FlipView przedstawiający oczekiwanych wyników](../debugger/media/js_dom_appfixed.png "JS_DOM_AppFixed")

7. Wybierz **komputera lokalnego** z listy rozwijanej obok pozycji listy **Rozpocznij debugowanie** znajdujący się na **debugowania** narzędzi:

    ![Wybierz opcję debugowania listy docelowej](../debugger/media/js_select_target.png "JS_Select_Target")

8. Wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.

    Spowoduje to uruchomienie aplikacji, ale będzie widoczny przede wszystkim pusty ekran, ponieważ stylu ma kilka błędów. Pierwszy `FlipView` obraz jest wyświetlany w mały kwadrat w pobliżu środka ekranu.

9. Przejdź do programu Visual Studio i wybierz **narzędzia DOM Explorer** kartę.

    > [!TIP]
    > Można nacisnąć klawisze Alt + Tab lub F12, aby przełączać się między Visual Studio i uruchomionej aplikacji.

10. W oknie narzędzia DOM Explorer, wybierz element DIV sekcji, która ma identyfikator równy `"fView"`. Użyj klawiszy strzałek, aby wyświetlić i wybrać poprawny element DIV. (Klawisz strzałki w prawo służy do wyświetlania elementy podrzędne.)

    ![DOM Explorer](../debugger/media/js_dom_explorer.png "JS_DOM_Explorer")

    > [!TIP]
    > DIV element można wybrać w lewym dolnym rogu okna konsoli języka JavaScript, wpisując `select(fView)` na >> danych wejściowych wiersza, a następnie naciśnij klawisz Enter.

    Wartości, które są wyświetlane na kartach po prawej stronie okna Eksploratora DOM automatycznie aktualizowana w celu odzwierciedlenia bieżącego elementu w programie DOM Explorer.

11. Wybierz **obliczane** kartę po prawej stronie.

    Ta karta przedstawia wartości obliczanej lub ostateczna, dla każdej właściwości wybranego elementu DOM w LICZBIE.

12. Otwórz reguły CSS wysokość. Zwróć uwagę, że jest zestawie style wbudowane do 100px, który pojawia się niespójna z wartością wysokość 100%, ustaw dla `#fView` selektora CSS. Przekreślonego tekstu dla `#fView` selektor wskazuje stylu śródwierszowego jest pierwszeństwo przed tego stylu.

    Poniższa ilustracja przedstawia **obliczane** kartę.

    ![Karta obliczane Eksploratora DOM](../debugger/media/js_dom_explorer_computed.png "JS_DOM_Explorer_Computed")

13. W głównym oknie narzędzia DOM Explorer, kliknij dwukrotnie style wbudowane do wysokości i szerokości `fView` DIV element. Teraz możesz edytować wartości w tym miejscu. W tym scenariuszu chcemy całkowicie usunąć.

14. W oknie głównym kliknij dwukrotnie `width: 100px;height: 100px;`, naciśnij klawisz **Usuń** klucza, a następnie naciśnij klawisz **Enter**. Po naciśnięciu klawisza Enter nowe wartości są natychmiast odzwierciedlane w aplikacji, mimo że nie zostały zatrzymane sesji debugowania.

    > [!IMPORTANT]
    > Jak można zaktualizować atrybutów w oknie Eksploratora modelu DOM, ale też aktualizować wartości, które pojawiają się na **style**, **obliczane**, i **układ** karty. Aby uzyskać więcej informacji, zobacz [stylów CSS debugowania przy użyciu narzędzia DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md) i [układu debugowania za pomocą narzędzia DOM Explorer](../debugger/debug-layout-using-dom-explorer.md).

15. Przełącz się do aplikacji, wybierając go lub za pomocą klawiszy Alt + Tab.

    Teraz `FlipView` kontroli jest większy niż rozmiar ekranu symulatora modułu lub w emulatorze telefonu. Nie jest zamierzone wynik. Aby zbadać, przełącz się do programu Visual Studio.

16. W Eksploratorze DOM wybierz **obliczane** karcie ponownie, a następnie otwórz reguła wysokości. FView element nadal znajduje się wartość 100%, zgodnie z oczekiwaniami z CSS, ale obliczona wartość jest równa wysokość ekranu aplikacji (na przykład 800 piks 667.67px lub inną wartość), który jest nie chcemy dla tej aplikacji. Aby zbadać w następnych krokach usuwamy wysokość i szerokość dla `fView` DIV element.

17. W **style** karcie, usuń zaznaczenie pola wyboru właściwości wysokości i szerokości `#fView` selektora CSS.

    **Obliczane** karta zawiera teraz wysokość 400 piks. Informacje wskazują, że ta wartość pochodzi z selektora właściwości flipview .exe, określone w interfejsu użytkownika — dark.css, czyli pliku CSS platformy.

18. Przejdź z powrotem do aplikacji.

    Elementy zostały ulepszone. Dostępna jest jednak nadal jeden problem więcej, aby rozwiązać problem: marginesy są zbyt duże.

19. Aby zbadać, przełącz się do programu Visual Studio, a następnie wybierz **układ** kartę, aby przyjrzeć się modelu pudełkowego elementu.

    W **układ** kartę, zostaną wyświetlone następujące czynności:

    - 255px (przesunięcie) i 255px (margines) lub podobne wartości, w zależności od rozdzielczości urządzenia.

      Na poniższej ilustracji pokazano sposób, w jaki **układ** wygląda kartę, jeśli używasz emulatora 100px przesunięcie i marginesu).

      ![Karta Układ Eksploratora DOM](../debugger/media/js_dom_explorer_layout.png "JS_DOM_Explorer_Layout")

      To prawdopodobnie nie prawo. **Obliczane** karta zawiera również te same wartości marginesów.

20. Wybierz **style** kartę, a następnie zlokalizuj `#fView` selektora CSS. W tym miejscu zobaczysz wartość 25% na **margines** właściwości.

21. Wybierz 25% i zmienić ją na 25px, a następnie naciśnij klawisz Enter.

22. Również w **style** kartę, wybrać regułę wysokość selektora właściwości flipview .exe Zmień 400 piks na 500 px i naciśnij klawisz Enter.

23. Przejdź z powrotem do aplikacji i sprawdź, czy położenie elementów znajduje się poprawna. Aby wprowadzić poprawki do źródła i odświeżać aplikację bez zatrzymywania i ponownego uruchamiania debugera, zobacz poniższą procedurę.

#### <a name="to-refresh-your-app-while-debugging"></a>Aby odświeżyć aplikację podczas debugowania

1. Gdy aplikacja jest nadal uruchomione, przełącz się do programu Visual Studio.

2. Otwórz plik default.html i zmodyfikować kod źródłowy, zmieniając wysokości i szerokości `"fView"` elementu DIV na 100%.

3. Wybierz **aplikacji Windows Odśwież** znajdujący się na pasku narzędzi debugowania (lub naciśnij klawisz F4). Przycisk wygląda następująco: ![Odśwież aplikację Windows](../debugger/media/js_refresh.png "JS_Refresh").

    Ponowne załadowanie strony aplikacji, a następnie przywraca symulator lub w emulatorze telefonu pierwszego planu.

    Aby uzyskać więcej informacji na temat funkcji odświeżania, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).

## <a name="SelectingElements"></a> Zaznaczanie elementów
Podczas debugowania aplikacji, możesz wybrać elementy modelu DOM na trzy sposoby:

- Klikając elementy bezpośrednio w oknie Eksploratora modelu DOM (lub za pomocą klawiszy strzałek).

- Za pomocą **zaznacz Element** przycisku (Ctrl + B).

- Za pomocą `select` polecenia, które jest jednym z [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).

  Korzystając z okna narzędzia DOM Explorer wybierz elementy, a wskaźnik myszy na elemencie, odpowiadający mu element jest wyróżniony w działającej aplikacji. Możesz kliknąć element w Eksploratorze DOM, aby go zaznaczyć, lub można użyć klawiszy strzałek, aby zaznaczyć, a następnie wybierz elementy. Można również wybrać elementy w Eksploratorze DOM, za pomocą **elementu wybierz** przycisku. Poniższa ilustracja przedstawia **zaznacz Element** przycisku.

  ![Wybierz przycisk Element w Eksploratorze DOM](../debugger/media/js_dom_select_element_button.png "JS_DOM_Select_Element_Button")

  Po kliknięciu **elementu wybierz** (lub naciśnij klawisze Ctrl + B), spowoduje to zmianę trybu zaznaczania, aby wybrać element w Eksploratorze DOM, klikając go w uruchomionej aplikacji. Powrót do trybu normalnego wyboru zmiany trybu po jednym kliknięciem. Po kliknięciu **elementu wybierz**, aplikacja przejdzie do pierwszego planu i kursor zmienia się na odzwierciedlają nowy tryb wyboru. Po kliknięciu elementu Schemat, narzędzia DOM Explorer zwraca na pierwszy plan określonego wybranego elementu.

  Przed wybraniem **zaznacz Element**, można określić, czy do wyróżnienia elementów w uruchomionej aplikacji, przełączając **wyświetlania strony sieci web najważniejsze** przycisku. Poniższa ilustracja przedstawia tego przycisku. Najważniejsze funkcje są domyślnie wyświetlane.

  ![Wyświetlanie strony sieci web wyróżnia przycisk](../debugger/media/js_dom_display_highlights_button.png "JS_DOM_Display_Highlights_Button")

  W przypadku zaznacz elementy wyróżniono elementy, które kursor w symulatorze. Kolory dla elementy wyróżnione zgodny z modelem pola, który pojawia się w **układ** karta Narzędzia DOM Explorer.

> [!NOTE]
> Wyróżnianie elementów, umieszczając kursor myszy nad nimi jest tylko częściowo obsługiwane w Emulator Windows Phone.

## <a name="see-also"></a>Zobacz też
- [Debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
- [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)
- [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)
- [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)
- [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)
- [Debugowanie przykładowego kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)
- [Pomoc techniczna i dostępność](https://msdn.microsoft.com/library/tzbxw1af(VS.120).aspx)

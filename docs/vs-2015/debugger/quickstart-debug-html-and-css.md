---
title: 'Szybki Start: Debugowanie kodu HTML i CSS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.WebClient.DomExplorer
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, CSS
- debugging, HTML
- debugging, JavaScript [Windows Store apps]
- DOM Explorer [Windows Store apps]
ms.assetid: 6d156cff-36c6-425a-acf8-e1f02d4f7869
caps.latest.revision: 104
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: be85bd5c09d59df576d66cef6cf2d4e7e34876ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687653"
---
# <a name="quickstart-debug-html-and-css"></a>Szybki start: debugowanie kodu HTML i CSS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 W przypadku aplikacji JavaScript program Visual Studio oferuje kompleksowe środowisko debugowania, które obejmuje funkcje, które są znane dla deweloperów Internet Explorer i Visual Studio. Te funkcje są obsługiwane dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, Windows Phone sklepu i aplikacji utworzonych przy użyciu Visual Studio Tools dla Apache Cordova  
  
 Korzystając z interaktywnego modelu debugowania dostarczonego przez narzędzia do inspekcji DOM, można wyświetlać i modyfikować renderowane kod HTML i CSS. Wszystkie te czynności można wykonać bez zatrzymywania i ponownego uruchamiania debugera.  
  
 W tym temacie:  
  
- [Sprawdzanie aktywnego modelu DOM](#InspectingDOM)  
  
- [Wybieranie elementów](#SelectingElements)  
  
  Aby uzyskać dodatkowe informacje na temat korzystania z DOM Explorer, zobacz następujące tematy:  
  
- [Debugowanie stylów CSS przy użyciu eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)  
  
- [Debugowanie układu przy użyciu eksploratora modelu DOM](../debugger/debug-layout-using-dom-explorer.md)  
  
- [Podgląd odbiorników zdarzeń DOM](../debugger/view-dom-event-listeners.md)  
  
- [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)  
  
- [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)  
  
  Aby uzyskać informacje o innych funkcjach debugowania JavaScript, takich jak korzystanie z okna konsoli języka JavaScript i ustawianie punktów przerwania, zobacz [Szybki Start: debugowanie JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="inspecting-the-live-dom"></a><a name="InspectingDOM"></a> Sprawdzanie aktywnego modelu DOM  
 DOM Explorer przedstawia widok renderowanej strony i można użyć DOM Explorer, aby zmienić wartości i natychmiast zobaczyć wyniki. Dzięki temu można testować zmiany bez zatrzymywania i ponownego uruchamiania debugera. Kod źródłowy w projekcie nie zmienia się podczas pracy ze stroną przy użyciu tej metody, więc po znalezieniu żądanych korekt kodu wprowadzasz zmiany w kodzie źródłowym.  
  
> [!TIP]
> Aby uniknąć zatrzymywania i ponownego uruchamiania debugera po wprowadzeniu zmian w kodzie źródłowym, można odświeżyć aplikację przy użyciu przycisku **Odśwież aplikację systemu Windows** na pasku narzędzi debugowania (lub naciskając klawisz F4). Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
 DOM Explorer można użyć do:  
  
- Przejdź do poddrzewa elementu DOM i sprawdź renderowany kod HTML, CSS i JavaScript.  
  
- Dynamicznie Edytuj atrybuty i style CSS dla renderowanych elementów i natychmiast Zobacz wyniki.  
  
- Sprawdź, jak style CSS zostały zastosowane do elementów strony i śledź zastosowane reguły.  
  
  Podczas debugowania aplikacji często trzeba wybrać elementy w DOM Explorer. Po wybraniu elementu wartości, które pojawiają się na kartach po prawej stronie DOM Explorer są automatycznie aktualizowane w celu odzwierciedlenia zaznaczonego elementu w DOM Explorer. Oto karty: **Style**, **obliczone**, **Układ**. Aplikacje ze sklepu Windows obsługują również karty **zdarzenia** i **zmiany** . Aby uzyskać więcej informacji na temat wybierania elementów, zobacz [Wybieranie elementów](#SelectingElements).  
  
> [!TIP]
> Jeśli okno dom Explorer jest zamknięte, wybierz **Debuguj** > **Windows**  >  **dom Explorer** Windows, aby je ponownie otworzyć. Okno pojawia się tylko podczas sesji debugowania skryptu.  
  
 W poniższej procedurze przejdziemy do interaktywnego debugowania aplikacji przy użyciu DOM Explorer. Utworzymy aplikację, która używa `FlipView` kontrolki, a następnie ją debuguje. Aplikacja zawiera kilka błędów.  
  
> [!WARNING]
> Następująca przykładowa aplikacja jest aplikacją ze sklepu Windows. Te same funkcje są obsługiwane przez oprogramowanie Cordova, ale aplikacja byłaby inna.  
  
#### <a name="to-debug-by-inspecting-the-live-dom"></a>Aby debugować za pomocą inspekcji na żywo modelu DOM  
  
1. Utwórz nowe rozwiązanie w programie Visual Studio, wybierając pozycję **plik**  >  **Nowy projekt**.  
  
2. Wybierz pozycję **JavaScript**  >  **sklep**JavaScript, wybierz pozycję **aplikacje systemu Windows** lub **Windows Phone aplikacje**, a następnie wybierz pozycję **pusta aplikacja**.  
  
3. Wpisz nazwę projektu, na przykład `FlipViewApp` , i wybierz **przycisk OK** , aby utworzyć aplikację.  
  
4. W elemencie BODY default.html Dodaj następujący kod:  
  
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
  
5. Otwórz pozycję Default. CSS i Dodaj następujący kod CSS:  
  
   ```css  
   #fView {  
       background-color:#0094ff;  
       height: 100%;  
       width: 100%;  
       margin: 25%;  
   }  
   ```  
  
6. Zastąp kod w default.js tym kodem:  
  
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
  
           pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
           pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
           pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
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
  
    Na poniższej ilustracji przedstawiono, co chcemy sprawdzić, czy aplikacja jest uruchamiana w emulatorze telefonu (wygląda podobnie w symulatorze). Aby jednak uzyskać dostęp do tego stanu aplikacji, należy najpierw naprawić liczbę usterek.  
  
    ![Aplikacja FlipView pokazująca oczekiwane wyniki](../debugger/media/js-dom-appfixed.png "JS_DOM_AppFixed")  
  
7. Wybierz opcję **symulator** lub **emulator 8,1 WVGA (4 cala** z listy rozwijanej obok przycisku **Rozpocznij debugowanie** na pasku narzędzi **debugowania** :  
  
    ![Wybierz listę obiektów docelowych debugowania](../debugger/media/js-select-target.png "JS_Select_Target")  
  
8. Wybierz **Debuguj**  >  **Rozpocznij debugowanie**lub naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
    Spowoduje to uruchomienie aplikacji w symulatorze lub emulatora telefonu, ale zobaczysz głównie pusty ekran, ponieważ styl zawiera kilka błędów. Pierwszy `FlipView` obraz jest wyświetlany w małym kwadracie obok środka ekranu.  
  
9. Jeśli aplikacja jest uruchamiana w symulatorze, wybierz polecenie **Zmień rozdzielczość** paska narzędzi po prawej stronie symulatora, aby skonfigurować rozdzielczość ekranu 1280 x 800. Zapewni to, że wartości pokazane w poniższych krokach odpowiadają elementom widocznym w symulatorze.  
  
10. Przejdź do programu Visual Studio i wybierz kartę **dom Explorer** .  
  
    > [!TIP]
    > Możesz nacisnąć klawisze ALT + TAB lub F12, aby przełączać się między programem Visual Studio i uruchomioną aplikacją.  
  
11. W oknie DOM Explorer wybierz element DIV dla sekcji o IDENTYFIKATORze `"fView"` . Użyj klawiszy strzałek, aby wyświetlić i wybrać poprawny element DIV. (Klawisz Strzałka w prawo umożliwia wyświetlenie elementów podrzędnych elementu).  
  
     ![Eksplorator DOM](../debugger/media/js-dom-explorer.png "JS_DOM_Explorer")  
  
    > [!TIP]
    > Możesz również wybrać element DIV w lewym dolnym rogu okna konsoli JavaScript, wpisując `select(fView)` w wierszu polecenia >> Input i naciskając klawisz ENTER.  
  
     Wartości, które pojawiają się na kartach po prawej stronie okna DOM Explorer są automatycznie aktualizowane w celu odzwierciedlenia bieżącego elementu w DOM Explorer.  
  
12. Wybierz kartę **obliczaną** po prawej stronie.  
  
     Na tej karcie są wyświetlane wartości obliczone lub końcowe dla każdej właściwości wybranego elementu DOM.  
  
13. Otwórz regułę CSS height. Zwróć uwagę, że istnieje styl wbudowany ustawiony na 100px, który jest niespójny z wartością wysokości 100% ustawioną dla `#fView` selektora CSS. Tekst przekreślony dla `#fView` selektora wskazuje, że styl wbudowany ma pierwszeństwo przed tym stylem.  
  
     Na poniższej ilustracji przedstawiono kartę **obliczaną** .  
  
     ![Karta obliczana DOM Explorer](../debugger/media/js-dom-explorer-computed.png "JS_DOM_Explorer_Computed")  
  
14. W oknie głównym DOM Explorer kliknij dwukrotnie styl wbudowany dla wysokości i szerokości `fView` elementu DIV. Teraz można edytować wartości w tym miejscu. W tym scenariuszu chcemy usunąć je całkowicie.  
  
15. Wybierz `width: 100px;height: 100px;` , naciśnij klawisz Delete, a następnie naciśnij klawisz ENTER. Po naciśnięciu klawisza ENTER nowe wartości zostaną natychmiast odzwierciedlone w symulatorze lub emulatorze telefonu, mimo że sesja debugowania nie została zatrzymana.  
  
    > [!IMPORTANT]
    > Jak można aktualizować atrybuty w oknie DOM Explorer, można także aktualizować wartości, które są wyświetlane na kartach **Style**, **obliczone**i **Układ** . Aby uzyskać więcej informacji, zobacz [debugowanie stylów CSS przy użyciu dom Explorer](../debugger/debug-css-styles-using-dom-explorer.md) i [układu debugowania przy użyciu dom Explorer](../debugger/debug-layout-using-dom-explorer.md).  
  
16. Przejdź do aplikacji, wybierając symulator lub emulator telefonu albo używając klawiszy Alt + Tab.  
  
     Teraz `FlipView` formant jest wyświetlany w rozmiarze większym niż rozmiar ekranu lub na ekranie emulatora telefonu. To nie jest zamierzony wynik. Aby zbadać, przełącz się z powrotem do programu Visual Studio.  
  
17. W DOM Explorer wybierz ponownie kartę **obliczoną** i Otwórz regułę wysokości. Element fView nadal zawiera wartość 100%, zgodnie z oczekiwaniami, ale obliczona wartość jest równa wysokości ekranu symulatora (na przykład 800px lub 667.67 px), co nie jest wymagane dla tej aplikacji. Aby zbadać, można usunąć wysokość i szerokość `fView` elementu DIV.  
  
18. Na karcie **Style** Usuń zaznaczenie pola właściwości wysokość i szerokość dla `#fView` selektora CSS.  
  
     Karta **obliczona** zawiera teraz wysokość 400px. Informacje wskazują, że ta wartość pochodzi z selektora. win-FlipView określonej w UI-Dark. CSS, czyli pliku CSS platformy.  
  
19. Przełącz się z powrotem do aplikacji.  
  
     Udoskonalone elementy. Jednak nadal występuje jeszcze jeden problem do naprawienia: marginesy są zbyt duże.  
  
20. Aby zbadać, przełącz się do programu Visual Studio i wybierz kartę **Układ** , aby sprawdzić model pola elementu.  
  
     Na karcie **Układ** zostaną wyświetlone następujące wartości:  
  
    - Dla symulatora: 320px (offset) i 320px (Margin).  
  
    - Dla emulatora telefonu: 100px (offset) i 100px (Margin).  
  
      Na poniższej ilustracji przedstawiono wygląd karty **Układ** , jeśli używasz emulatora telefonu (przesunięcie i margines 100px).  
  
      ![Karta układ DOM Explorer](../debugger/media/js-dom-explorer-layout.png "JS_DOM_Explorer_Layout")  
  
      To nie jest właściwe. Karta **obliczona** zawiera również te same wartości marginesów.  
  
21. Wybierz kartę **Style** i Znajdź `#fView` Selektor CSS. W tym miejscu zostanie wyświetlona wartość 25% dla właściwości **Margin** .  
  
22. Wybierz 25% i zmień go na 25px, a następnie naciśnij klawisz ENTER.  
  
23. Na karcie **Style** wybierz regułę wysokość dla selektora. win-FlipView i zmień wartość 400px na 500 px, a następnie naciśnij klawisz ENTER.  
  
24. Przełącz się z powrotem do aplikacji i zobaczysz, że położenie elementów pojawia się prawidłowo. Aby wprowadzić poprawki do źródła i odświeżyć aplikację bez zatrzymywania i ponownego uruchamiania debugera, zobacz poniższą procedurę.  
  
#### <a name="to-refresh-your-app-while-debugging"></a>Aby odświeżyć aplikację podczas debugowania  
  
1. Gdy aplikacja jest nadal uruchomiona, przełącz się do programu Visual Studio.  
  
2. Otwórz default.html i zmodyfikuj kod źródłowy, zmieniając wysokość i szerokość `"fView"` elementu DIV na 100%.  
  
3. Wybierz przycisk **Odśwież aplikację systemu Windows** na pasku narzędzi debugowania (lub naciśnij klawisz F4). Przycisk jest podobny do tego: ![Odśwież przycisk aplikacji systemu Windows](../debugger/media/js-refresh.png "JS_Refresh").  
  
     Strony aplikacji ładują się ponownie i symulator lub emulator telefonu powraca do pierwszego planu.  
  
     Aby uzyskać więcej informacji na temat funkcji odświeżania, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="selecting-elements"></a><a name="SelectingElements"></a> Wybieranie elementów  
 W przypadku debugowania aplikacji można wybrać elementy DOM na trzy sposoby:  
  
- Klikając elementy bezpośrednio w oknie DOM Explorer (lub za pomocą klawiszy strzałek).  
  
- Za pomocą przycisku **Wybierz element** (Ctrl + B).  
  
- Za pomocą `select` polecenia, które jest jednym z [poleceń konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
  Gdy używasz okna DOM Explorer do zaznaczania elementów i umieścisz wskaźnik myszy na elemencie, odpowiadający element zostanie wyróżniony w działającej aplikacji. Należy kliknąć element w DOM Explorer, aby go zaznaczyć, lub użyć klawiszy strzałek, aby wyróżnić i wybrać elementy. Możesz również wybrać elementy w DOM Explorer przy użyciu przycisku **Wybierz element** . Na poniższej ilustracji przedstawiono przycisk **Wybierz element** .  
  
  ![Przycisk wyboru elementu w DOM Explorer](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
  Po kliknięciu przycisku **Wybierz element** (lub naciśnięciu kombinacji klawiszy CTRL + B) spowoduje to zmianę trybu zaznaczania, aby można było wybrać element w Dom Explorer, klikając go w działającej aplikacji. Tryb zmieni się z powrotem na normalny tryb zaznaczenia po pojedynczym kliknięciu. Po kliknięciu pozycji **Wybierz element**aplikacja zostanie przełączona na pierwszy plan, a kursor zmieni się w celu odzwierciedlenia nowego trybu zaznaczania. Po kliknięciu elementu konturowego DOM Explorer powraca do pierwszego planu z wybranym elementem.  
  
  Przed wybraniem opcji **Wybierz element**można określić, czy elementy w działającej aplikacji mają być wyróżniać, przełączając przycisk **Wyświetl wyróżnione strony sieci Web** . Na poniższej ilustracji przedstawiono ten przycisk. Najważniejsze są wyświetlane domyślnie.  
  
  ![Przycisk wyświetlania podświetlenia strony sieci Web](../debugger/media/js-dom-display-highlights-button.png "JS_DOM_Display_Highlights_Button")  
  
  Po wybraniu opcji wyróżniania elementów elementy, które znajdują się w symulatorze, są wyróżnione. Kolory dla wyróżnionych elementów są zgodne z modelem Box, który pojawia się na karcie **układ** dom Explorer.  
  
> [!NOTE]
> Wyróżnianie elementów przez umieszczenie ich nad nimi jest tylko częściowo obsługiwane w emulatorze Windows Phone.  
  
 Aby zapoznać się z przykładem, który ilustruje sposób wybierania elementów przy użyciu przycisku **Wybierz element** , zobacz [debugowanie stylów CSS przy użyciu dom Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="browser-and-platform-support"></a><a name="BrowserSupport"></a> Obsługa przeglądarek i platform  
 Narzędzia Visual Studio Tools for JavaScript, DOM Explorer i okno konsoli JavaScript są obsługiwane na następujących platformach:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje i Windows Phone ze sklepu przy użyciu języków JavaScript i HTML  
  
- Program Internet Explorer 11 uruchomiony w systemie [!INCLUDE[win81](../includes/win81-md.md)]  
  
- Program Internet Explorer 10 uruchomiony na [!INCLUDE[win8](../includes/win8-md.md)]  
  
  Przejdź [tutaj](https://developer.microsoft.com/windows/downloads/sdk-archive) , aby pobrać [!INCLUDE[win8](../includes/win8-md.md)] i Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Debugowanie stylów CSS przy użyciu DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Debugowanie układu przy użyciu DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)   
 [Wyświetl detektory zdarzeń DOM](../debugger/view-dom-event-listeners.md)   
 [Odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md)   
 [Debugowanie kontrolki WebView](../debugger/debug-a-webview-control.md)   
 [Skróty klawiaturowe](../debugger/keyboard-shortcuts-html-and-javascript.md)   
 [Polecenia konsoli JavaScript](../debugger/javascript-console-commands.md)   
 [Debugowanie przykładowego kodu HTML, CSS i JavaScript](../debugger/debug-html-css-and-javascript-sample-code.md)   
 [Pomoc techniczna i ułatwienia dostępu](https://msdn.microsoft.com/library/tzbxw1af\(VS.120\).aspx)

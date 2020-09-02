---
title: 'Przewodnik: poprawianie czasu odpowiedzi interfejsu użytkownika (HTML) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- performance tools, JavaScript [Store apps]
- performance, JavaScript [Store apps]
- performance, HTML [Store apps]
- performance tools, HTML [Store apps]
ms.assetid: 7e5a2524-dbf5-4a40-b5d6-2d1ed7fff3de
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7224dc1ddcffc203c930a3ead01c2f541af2122f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64792880"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>Przewodnik: skracanie czasu odpowiedzi interfejsu użytkownika (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten Instruktaż prowadzi przez proces identyfikowania i rozwiązywania problemów z wydajnością przy użyciu [profilera czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md). Profiler jest dostępny w programie Visual Studio dla aplikacji uniwersalnych i ze sklepu Windows w systemie Windows przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację testową wydajności, która aktualizuje elementy DOM zbyt często, i można użyć profilera do zidentyfikowania i rozwiązania tego problemu.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Tworzenie i uruchamianie aplikacji testowej wydajności  
  
1. W programie Visual Studio Utwórz nowy uniwersalny projekt systemu Windows w języku JavaScript. (Wybierz **plik/nowy/projekt**. W lewym okienku wybierz pozycję **JavaScript** , a następnie wybierz pozycję **Windows**, **Windows 10**, a następnie opcję **uniwersalne**lub **Windows Phone**.  
  
2. > [!IMPORTANT]
    > Wyniki diagnostyki przedstawione w tym temacie są wyświetlane dla aplikacji systemu Windows 8.  
  
3. Wybierz jeden z pustych szablonów projektu w środkowym okienku, na przykład **pustą aplikację**.  
  
4. W polu **Nazwa** Określ nazwę, na przykład `JS_Perf_Tester` , a następnie wybierz przycisk **OK**.  
  
5. W **Eksplorator rozwiązań**Otwórz default.html i wklej następujący kod między \<body> tagami:  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6. Otwórz domyślny. CSS i Dodaj następujący kod CSS:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7. Otwórz default.js i Zastąp cały kod tym kodem:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var content;  
        var wrapper;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
  
                    content = document.getElementById("content");  
                    wrapper = document.querySelector(".wrapper");  
  
                    content.addEventListener("click", handler);  
  
                } else {  
                }  
  
                args.setPromise(WinJS.UI.processAll());  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        var idx = 0;  
        var count = 0;  
        var max = 5000;  
        var text = ["what", "is", "the", "Matrix?"];  
        var color = ["red", "crimson", "maroon", "purple"];  
  
        function increment() {  
  
            setTimeout(function () {  
  
                idx++;  
                count++;  
  
                if (idx > 3) { idx = 0; }  
                if (count < max) { increment(); }  
  
            }, 1000);  
        }  
  
        function setValues() {  
  
            content = document.getElementById("content");  
            content.removeNode(true);  
  
            var newNode = document.createElement("button");  
            newNode.id = "content";  
            newNode.textContent = text[idx];  
            //newNode.textContent = getData();  
            newNode.style.backgroundColor = color[idx];  
            //newNode.style.animationName = "move";  
            //count++;  
  
            wrapper.appendChild(newNode);  
  
        }  
  
        function update() {  
  
            setTimeout(function () {  
  
                setValues();  
                if (count < max) { update(); }  
            });  
        }  
  
        function handler(args) {  
  
            content.textContent = "eenie";  
            increment();  
            update();  
        }  
  
    })();  
  
    ```  
  
8. Wybierz klawisz F5, aby rozpocząć debugowanie. Sprawdź, czy na stronie jest wyświetlany przycisk " **oczekiwanie na wartości** ".  
  
9. Wybierz pozycję **oczekiwanie na wartości** i sprawdź, czy tekst przycisku i kolor są aktualizowane około raz na sekundę. Jest to celowe.  
  
10. Przełącz się z powrotem do programu Visual Studio (Alt + Tab), a następnie naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Po zweryfikowaniu, że aplikacja działa, możesz sprawdzić jej wydajność przy użyciu profilera.  
  
### <a name="analyzing-performance-data"></a>Analizowanie danych wydajności  
  
1. Na pasku narzędzi **debugowania** na liście **Rozpocznij debugowanie** wybierz jeden z Windows Phone emulatorów lub **symulatora**.  
  
2. W menu **debugowanie** wybierz pozycję **wydajność i Diagnostyka**.  
  
3. W obszarze **dostępne narzędzia**wybierz pozycję **czas odpowiedzi interfejsu użytkownika HTML**, a następnie wybierz polecenie **Uruchom**.  
  
    W tym samouczku dodasz Profiler do projektu startowego. Aby uzyskać informacje na temat innych opcji, takich jak dołączanie profilera do zainstalowanej aplikacji, zobacz [czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md).  
  
    Po uruchomieniu profilera może zostać wyświetlona Kontrola konta użytkownika z prośbą o zgodę na uruchomienie VsEtwCollector.exe. Wybierz opcję **tak**.  
  
4. W uruchomionej aplikacji wybierz pozycję **oczekiwanie na wartości** i odczekaj około 10 sekund. Upewnij się, że tekst i kolor przycisku są aktualizowane około raz na sekundę.  
  
5. W uruchomionej aplikacji przejdź do programu Visual Studio (Alt + Tab).  
  
6. Wybierz pozycję **Zatrzymaj zbieranie**.  
  
    Profiler wyświetla informacje na nowej karcie w programie Visual Studio. Po przeszukiwaniu użycia procesora CPU i danych przepływności (FPS) można łatwo zidentyfikować kilka trendów:  
  
   - Użycie procesora CPU wzrasta znacznie po około 3 sekundach (po naciśnięciu przycisku " **oczekiwanie na wartości** ") i wyświetleniu czystego wzorca zdarzeń (spójnej kombinacji skryptów, stylu i zdarzeń renderowania) od tego momentu.  
  
   - Nie ma to wpływu na przepływność wizualną, a liczba klatek na sekundę pozostaje w 60 (to oznacza, że nie ma żadnych porzuconych ramek).  
  
     Przyjrzyjmy się typowej sekcji wykresu użycia procesora CPU, aby dowiedzieć się, co aplikacja wykonuje w tym okresie.  
  
7. Wybierz jedną część drugiej części w środku wykresu użycia procesora CPU (kliknij przycisk-i-przeciągnij lub użyj kart i klawiszy strzałek). Na poniższej ilustracji przedstawiono wykres użycia procesora CPU po dokonaniu wyboru. Obszar nieudostępniony jest zaznaczeniem.  
  
    ![Wykres użycia procesora CPU](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. Wybierz pozycję **Powiększ**.  
  
    Wykres zostanie zmieniony, aby pokazać wybrany okres bardziej szczegółowo. Na poniższej ilustracji przedstawiono wykres użycia procesora CPU po powiększeniu. (Określone dane mogą się różnić, ale ogólny wzorzec będzie widoczny).  
  
    ![Powiększone w widoku](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Szczegóły osi czasu w dolnym okienku przedstawiają przykład szczegółów dla wybranego okresu.  
  
    ![Szczegóły osi czasu](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    Zdarzenia w szczegółach osi czasu potwierdzają widoczne trendy w grafie użycia procesora CPU: wiele zdarzeń odbywa się w krótkim czasie. Widok Szczegóły osi czasu pokazuje, że te zdarzenia to `Timer` , `Layout` i `Paint` zdarzenia.  
  
9. Użyj menu kontekstowego (lub kliknij prawym przyciskiem myszy) jednego ze `Timer` zdarzeń w dolnym okienku, a następnie wybierz polecenie **Filtruj do zdarzenia**. Na poniższej ilustracji przedstawiono przykład typowe szczegóły dla jednego ze `Timer` zdarzeń w tej aplikacji testowej.  
  
     ![Zdarzenie czasomierza](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Różne fakty mogą być wydobyć z danych. Na przykład:  
  
    - Każde `Timer` zdarzenie, kodowane kolorami w celu zidentyfikowania go jako zdarzenia skryptu, zawiera wywołanie `document.createElement` , po którym następuje obliczenie stylu i wywołanie do `style.backgroundColor` i `appendChild()` .  
  
    - W krótkim przedziale czasu (w przybliżeniu do dwóch sekund) istnieje świetna liczba `Timer` wydarzeń, które mają `Layout` `Paint` miejsce. `Timer`Zdarzenia występują znacznie częściej niż jedna aktualizacja na sekundę, która jest widoczna po uruchomieniu aplikacji i wybiera przycisk " **oczekiwanie na wartości** ".  
  
10. Aby zbadać, wybierz link do funkcji anonimowej dla jednego ze `Timer` zdarzeń w lewym dolnym okienku. W default.js zostanie otwarta następująca funkcja:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Ta funkcja cykliczna konfiguruje pętlę, która wywołuje `setValues()` funkcję, która aktualizuje przycisk w interfejsie użytkownika. Badając różne zdarzenia czasomierza w profilerze, można stwierdzić, że większość lub wszystkie zdarzenia czasomierza wynikają z tego kodu, który jest zbyt często uruchamiany, dlatego wydaje się, że problem nie pochodzi tutaj.  
  
### <a name="fixing-the-performance-issue"></a>Rozwiązywanie problemów z wydajnością  
  
1. Zastąp `update()` funkcję następującym kodem:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Ta stała wersja kodu obejmuje opóźnienie 1000 milisekund, który został pominięty w poprzedniej wersji kodu, co spowodowało użycie domyślnej wartości opóźnienia. Dane z profilera są wyświetlane, ponieważ wartość domyślna to zero milisekund, co spowodowało `setValues()` zbyt częste uruchamianie funkcji.  
  
2. Uruchom ponownie Profiler czas odpowiedzi interfejsu użytkownika HTML i sprawdź wykres użycia procesora CPU. Okaże się, że nadmierne zdarzenia znikły, a wykorzystanie procesora CPU zostało przerwane do najbliższego zera. FIXED!  
  
## <a name="see-also"></a>Zobacz też  
 [Czas odpowiedzi interfejsu użytkownika języka HTML](../profiling/html-ui-responsiveness.md)

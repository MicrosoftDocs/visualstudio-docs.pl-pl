---
title: 'Wskazówki: Poprawianie czasu odpowiedzi interfejsu użytkownika (HTML) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f0cf1b080a0e803beda6682265dc383dc43a33d0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791151"
---
# <a name="walkthrough-improving-ui-responsiveness-html"></a>Wskazówki: Poprawianie czasu odpowiedzi interfejsu użytkownika (HTML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten instruktaż poprowadzi Cię przez proces identyfikowanie i rozwiązywanie problemów z wydajnością za pomocą [profiler czasu odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md). Program profilujący jest dostępna w aplikacjach Visual Studio for Windows Universal a Windows Store przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację test wydajności, która aktualizuje elementów DOM zbyt często, a następnie użyć profiler zidentyfikować i rozwiązać ten problem.  
  
### <a name="creating-and-running-the-performance-test-app"></a>Tworzenie i uruchamianie wykonywania testowanie aplikacji  
  
1.  W programie Visual Studio Utwórz nowy projekt Windows Universal JavaScript. (Wybierz **plik / nowy / Project**. Wybierz **JavaScript** w okienku po lewej stronie, a następnie wybierz **Windows**, **systemu Windows 10**, a następnie **Universal**, lub  **Windows Phone**.  
  
2.  > [!IMPORTANT]
    >  Wyniki diagnostyki, przedstawione w tym temacie przedstawiono aplikacji systemu Windows 8.  
  
3.  Wybierz jeden z szablonów pustego projektu w środkowym okienku, taki jak **pusta aplikacja**.  
  
4.  W **nazwa** polu Określ nazwę, taką jak `JS_Perf_Tester`, a następnie wybierz **OK**.  
  
5.  W **Eksploratora rozwiązań**, otwórz plik default.html i wklej następujący kod między \<treści > znaczniki:  
  
    ```html  
    <div class="wrapper">  
        <button id="content">Waiting for values</button>  
    </div>  
    ```  
  
6.  Otwórz default.css i Dodaj następujący kod CSS:  
  
    ```css  
    #content {  
        margin-left: 100px;  
        margin-top: 100px;  
    }  
    ```  
  
7.  Otwórz default.js i Zastąp cały kod przy użyciu tego kodu:  
  
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
  
8.  Wybierz klawisz F5, aby rozpocząć debugowanie. Upewnij się, że **oczekiwanie na wartości** na stronie pojawi się przycisk.  
  
9. Wybierz **oczekiwanie na wartości** i sprawdź, czy tekst przycisku i kolor na około aktualizacji raz na sekundę. To jest celowe.  
  
10. Przejdź z powrotem do programu Visual Studio (Alt + Tab), a następnie wybierz klawisz Shift + F5, aby zatrzymać debugowanie.  
  
     Teraz, gdy upewnieniu się, że aplikacja działa, jego wydajność, można sprawdzić za pomocą profilera.  
  
### <a name="analyzing-performance-data"></a>Analizowanie danych dotyczących wydajności  
  
1. Na **debugowania** narzędzi w **Rozpocznij debugowanie** listy, wybierz jedną z emulatory Windows Phone lub **symulator**.  
  
2. Na **debugowania** menu, wybierz **wydajności i diagnostyki**.  
  
3. W **dostępnych narzędzi**, wybierz **HTML UI Responsiveness**, a następnie wybierz **Start**.  
  
    W tym samouczku jest będzie dołączania profilera do projektu startowego. Aby uzyskać informacje na temat innych opcji, takich jak Dołączanie programu profiler do zainstalowanych aplikacji, zobacz [HTML UI responsiveness](../profiling/html-ui-responsiveness.md).  
  
    Kiedy uruchamiasz program profilujący, można napotkać Kontrola konta użytkownika, która żąda uprawnienia do uruchomienia VsEtwCollector.exe. Wybierz **tak**.  
  
4. W działającej aplikacji wybierz **oczekiwanie na wartości** i Odczekaj około 10 sekund. Upewnij się, tekst przycisku i kolor na około aktualizacji raz na sekundę.  
  
5. W uruchomionej aplikacji Przełącz się do programu Visual Studio (Alt + Tab).  
  
6. Wybierz **Zatrzymaj Kolekcjonowanie**.  
  
    Program profilujący Wyświetla informacje na nowej karcie w programie Visual Studio. Jeśli przyjrzymy się wykorzystanie procesora CPU i danych przepustowość wizualna (kl. / s), można łatwo identyfikować trendy w kilku:  
  
   - Użycie procesora CPU zwiększa się znacznie po około 3 sekundy (po naciśnięciu **oczekiwanie na wartości** przycisku) i wyświetla wyczyść wzorców zdarzeń (spójne kombinację skryptów, stylów i zdarzenia renderowania) z tego punktu w.  
  
   - Nie ma to wpływ na przepustowość wizualna i kl. / s pozostaje na 60 w całym (oznacza to, że nie ma żadnych porzuconych ramek).  
  
     Przyjrzyjmy się typowe części Wykres wykorzystania procesora CPU, aby dowiedzieć się, jakie działania aplikacji w tym okresie dużej aktywności.  
  
7. Wybieranie drugiej części jednej do dwóch w środku Wykres wykorzystania procesora CPU (albo kliknięcia i przeciągnięcia lub używać kluczy karty i strzałka). Poniższa ilustracja przedstawia Wykres wykorzystania procesora CPU, po dokonaniu wyboru. Nieudostępnione obszaru to zaznaczenie.  
  
    ![Wykres wykorzystania procesora CPU](../profiling/media/js-htmlviz-app-cpu.png "JS_HTMLViz_App_CPU")  
  
8. Wybierz **powiększyć**.  
  
    Zmiany wykresu do wyświetlenia na wybrany okres bardziej szczegółowo. Poniższa ilustracja przedstawia Wykres wykorzystania procesora CPU po powiększyć. (Określone dane mogą się różnić, ale ogólny wzorzec będzie widoczna).  
  
    ![Powiększenie w widoku](../profiling/media/js-htmlviz-app-zoom.png "JS_HTMLViz_App_Zoom")  
  
    Szczegóły osi czasu w dolnym okienku przedstawiono przykład szczegółów dla wybranego okresu.  
  
    ![Szczegóły osi czasu](../profiling/media/js-htmlviz-app-details.png "JS_HTMLViz_App_Details")  
  
    Upewnij się, zdarzenia w szczegółach oś czasu widoczny trendów w wykres wykorzystania procesora CPU: wiele zdarzeń zajmuje miejsce w krótkich okresach czasu. Wyświetl szczegóły osi czasu wskazuje, że te zdarzenia są `Timer`, `Layout`, i `Paint` zdarzenia.  
  
9. Użyj menu kontekstowego (lub kliknij prawym przyciskiem myszy) jeden z `Timer` zdarzenia w dolnym okienku i wybierz polecenie **filtr, aby zdarzenia**. Na poniższej ilustracji przedstawiono przykład szczegółów typowe dla jednego z `Timer` zdarzeń w tym testowanie aplikacji.  
  
     ![Zdarzenie czasomierza](../profiling/media/js-htmlviz-app-timer.png "JS_HTMLViz_App_Timer")  
  
     Szereg fakty może zebrać dane. Na przykład:  
  
    -   Każdy `Timer` zdarzenia oznaczone kolorami, aby je zidentyfikować jako zdarzenie obsługi skryptów, zawiera wywołanie `document.createElement`, a następnie obliczenia stylu i wywołania `style.backgroundColor` i `appendChild()`.  
  
    -   W krótkim przedział czasu zaznaczone (około jednej do dwóch sekund), istnieją wielu `Timer`, `Layout`, i `Paint` zdarzenia mające miejsce. `Timer` Zdarzenia zachodzą znacznie częściej niż jedna aktualizacja na sekundę, gdy jest widoczne oczywiste, po uruchomieniu aplikacji i wybierz **oczekiwanie na wartości** przycisku.  
  
10. Aby zbadać, wybierz link, aby funkcja anonimowa dla jednego z `Timer` zdarzenia w dolnym okienku po lewej stronie. W pliku default.js spowoduje otwarcie następującą funkcję:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        });  
    }  
    ```  
  
     Ta funkcja cyklicznego konfiguruje pętli, która wywołuje `setValues()` funkcji, która aktualizuje przycisku w interfejsie użytkownika. Badanie zdarzeń inny czasomierz w profilerze, użytkownik stwierdza, że większość lub wszystkie zdarzenia czasomierza wynika z tego kodu, która jest uruchomiona zbyt często, więc pojawia się ono prawdopodobnie tutaj pochodzi ten problem.  
  
### <a name="fixing-the-performance-issue"></a>Rozwiązywanie problemów z wydajnością  
  
1.  Zastąp `update()` funkcji następującym kodem:  
  
    ```javascript  
    function update() {  
  
        setTimeout(function () {  
  
            setValues();  
            if (count < max) { update(); }  
        }, 1000 );  
    }  
    ```  
  
     Tej wersji Naprawiono kodu obejmuje 1000 Opóźnienie milisekund, który został pominięty z poprzedniej wersji kodu, zmniejsza opóźnienie wartości domyślnej. Z danych profilera, wydaje się, że wartością domyślną jest zero milisekund, które spowodowały `setValues()` zbyt częste uruchamianie funkcji.  
  
2.  Ponownie uruchomić profiler czas odpowiedzi interfejsu użytkownika HTML i sprawdź wykres wykorzystania procesora CPU. Można zauważyć, że nadmierne zdarzenia zostaną usunięte, a użycie procesora CPU została obniżona do umieszczonej blisko zero. Naprawiono!  
  
## <a name="see-also"></a>Zobacz też  
 [Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)




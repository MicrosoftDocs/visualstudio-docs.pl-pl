---
title: 'Przewodnik: Znajdowanie przecieku pamięci (JavaScript) | Microsoft Docs'
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
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5617dc6cbe4b7ba096afe1f308d06e7f4aaf9c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785512"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Wskazówki: Znajdowanie wycieku pamięci (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Ten Instruktaż prowadzi przez proces identyfikowania i rozwiązywania problemów z pamięcią prostego przy użyciu analizatora pamięci języka JavaScript. Analizator pamięci języka JavaScript jest dostępny w programie Visual Studio dla aplikacji ze sklepu Windows tworzonych dla systemu Windows przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację, która nieprawidłowo zachowuje elementy DOM w pamięci zamiast zbywania elementów w tej samej szybkości, w której zostały utworzone.  
  
 Chociaż przyczyną przecieku pamięci w tej aplikacji jest bardzo szczegółowa, kroki przedstawione w tym miejscu demonstrują przepływ pracy, który zwykle jest skuteczny w odizolowaniu obiektów, które powodują przeciek pamięci.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Uruchamianie aplikacji testowej analizatora pamięci JavaScript  
  
1. W programie Visual Studio wybierz pozycje **Plik**, **Nowy**, **Projekt**.  
  
2. Wybierz **JavaScript** w lewym okienku, a następnie wybierz pozycję **Windows**, **Windows 8**, a następnie pozycję Aplikacje **uniwersalne** lub **Windows Phone**.  
  
    > [!IMPORTANT]
    > Wyniki użycia pamięci przedstawione w tym temacie są testowane w odniesieniu do aplikacji systemu Windows 8.  
  
3. W środkowym okienku wybierz szablon projektu **pustej aplikacji** .  
  
4. W polu **Nazwa** Określ nazwę, na przykład `JS_Mem_Tester` , a następnie wybierz przycisk **OK**.  
  
5. W **Eksplorator rozwiązań**Otwórz default.html i wklej następujący kod między \<body> tagami:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    > Jeśli używasz szablonu aplikacji uniwersalnej Windows 8.1, musisz zaktualizować kod HTML i CSS w obu. Windows i. WindowsPhone projekty.  
  
6. Otwórz domyślny. CSS i Dodaj następujący kod CSS:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7. Otwórz default.js i Zastąp cały kod tym kodem:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8. Wybierz klawisz F5, aby rozpocząć debugowanie. Sprawdź, czy na stronie jest wyświetlany przycisk **przeciek pamięci** .  
  
9. Przełącz się z powrotem do programu Visual Studio (Alt + Tab), a następnie naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Po zweryfikowaniu, że aplikacja działa, możesz sprawdzić użycie pamięci.  
  
### <a name="analyzing-the-memory-usage"></a>Analizowanie użycia pamięci  
  
1. Na pasku narzędzi **debugowania** na liście **Rozpocznij debugowanie** wybierz element docelowy debugowania dla zaktualizowanego projektu: jeden z Windows Phone emulatorów lub **symulatorów**.  
  
   > [!TIP]
   > W przypadku aplikacji ze sklepu Windows można również wybrać **maszynę lokalną** lub **zdalną** na tej liście. Jednak zaletą korzystania z emulatora lub symulatorem jest to, że można je umieścić obok programu Visual Studio i łatwo przełączać się między uruchomioną aplikacją a analizatorem pamięci JavaScript. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji z programu Visual Studio](../debugger/run-store-apps-from-visual-studio.md) i [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. W menu **debugowanie** wybierz pozycję **Profiler wydajności.**...  
  
3. W obszarze **dostępne narzędzia**wybierz pozycję **pamięć JavaScript**, a następnie wybierz polecenie **Uruchom**.  
  
    W tym samouczku zostanie dołączany Analizator pamięci do projektu startowego. Aby uzyskać informacje na temat innych opcji, takich jak dołączanie analizatora pamięci do zainstalowanej aplikacji, zobacz [JavaScript Memory](../profiling/javascript-memory.md).  
  
    Po uruchomieniu analizatora pamięci może zostać wyświetlona Kontrola konta użytkownika z prośbą o zgodę na uruchomienie VsEtwCollector.exe. Wybierz opcję **tak**.  
  
4. Wybierz przycisk **przeciek pamięci** cztery razy.  
  
    Po wybraniu przycisku kod obsługi zdarzeń w default.js działa, co spowoduje przeciek pamięci. Ta funkcja będzie używana do celów diagnostycznych.  
  
   > [!TIP]
   > Powtarzanie scenariusza, który ma zostać przetestowany w celu wycieku pamięci ułatwia odfiltrowanie nieinteresujących informacji, takich jak obiekty dodawane do sterty podczas inicjowania aplikacji lub podczas ładowania strony.  
  
5. W uruchomionej aplikacji przejdź do programu Visual Studio (Alt + Tab).  
  
    Analizator pamięci JavaScript wyświetla informacje na nowej karcie w programie Visual Studio.  
  
    Wykres pamięci w tym widoku podsumowania przedstawia użycie pamięci przez proces w czasie. Widok udostępnia również polecenia takie jak **migawka sterty**. Migawka zawiera szczegółowe informacje o wykorzystaniu pamięci w określonym czasie. Aby uzyskać więcej informacji, zobacz [JavaScript Memory](../profiling/javascript-memory.md).  
  
6. Wybierz polecenie **Wykonaj migawkę sterty**.  
  
7. Przejdź do aplikacji i wybierz **przeciek pamięci**.  
  
8. Przełącz się do programu Visual Studio i ponownie wybierz pozycję **Wykonaj migawkę sterty** .  
  
    Na tej ilustracji przedstawiono migawki linii bazowej (#1) i #2 migawek.  
  
    ![Migawka podstawowa i migawka 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   > Emulator Windows Phone nie pokazuje zrzutu ekranu aplikacji w momencie utworzenia migawki.  
  
9. Przejdź do aplikacji i ponownie wybierz przycisk **przeciek pamięci** .  
  
10. Przejdź do programu Visual Studio i wybierz opcję **Utwórz migawkę sterty** po raz trzeci.  
  
    > [!TIP]
    > Wykonując trzecią migawkę w tym przepływie pracy, można odfiltrować zmiany z migawki linii bazowej do drugiej migawki, która nie jest skojarzona z przeciekami pamięci. Na przykład mogą wystąpić takie zmiany, jak aktualizowanie nagłówków i stopek na stronie, które spowodują wygenerowanie pewnych zmian w pamięci, ale mogą być niezwiązane z przeciekami pamięci.  
  
     Na tej ilustracji przedstawiono #2 migawek i #3 migawek.  
  
     ![Migawka 2 i migawka 3](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. W programie Visual Studio wybierz pozycję **Zatrzymaj** , aby zatrzymać profilowanie.  
  
12. W programie Visual Studio Porównaj migawki. W #2 migawek przedstawiono następujące elementy:  
  
    - Rozmiar sterty (wyświetlany przez czerwoną strzałkę w górę po lewej stronie) wzrósł o kilka KB w porównaniu do #1 migawek.  
  
      > [!IMPORTANT]
      > Dokładne wartości użycia pamięci dla rozmiaru sterty zależą od elementu docelowego debugowania.  
  
    - Liczba obiektów na stercie (pokazywanych przez czerwoną strzałkę w górę po prawej stronie) została zwiększona w porównaniu do #1 migawek. Dodano jeden obiekt (+ 1) i nie usunięto żadnych obiektów (-0).  
  
      W #3 migawek przedstawiono następujące elementy:  
  
    - Rozmiar sterty został zwiększony ponownie o kilka bajtów w porównaniu do #2 migawek.  
  
    - Liczba obiektów w stercie została jeszcze zwiększona w porównaniu do #2 migawek. Dodano jeden obiekt (+ 1) i nie usunięto żadnych obiektów (-0).  
  
13. W obszarze migawka #3 Wybierz tekst łącza po prawej stronie, w którym zostanie wyświetlona wartość + 1/ -0 obok czerwonej strzałki w górę.  
  
     ![Łączenie z innym widokiem obiektów sterty](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Spowoduje to otwarcie widoku różnicowego obiektów na stercie o nazwie **migawka #3-migawka #2**, z widokiem typ widoczny domyślnie. Domyślnie zostanie wyświetlona lista obiektów dodanych do sterty między #2 migawek i #3 migawek.  
  
14. W filtrze **zakres** wybierz **obiekty pozostałe z migawki #2**.  
  
15. Otwórz obiekt HTMLDivElement w górnej części drzewa obiektów, jak pokazano poniżej.  
  
     ![Widok różnic liczby obiektów na stercie](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Ten widok przedstawia przydatne informacje o przecieku pamięci, takie jak następujące:  
  
    - Ten widok przedstawia element DIV o IDENTYFIKATORze `item` , a zachowany rozmiar obiektu to kilka setek bajtów (dokładna wartość będzie różna).  
  
    - Ten obiekt jest pozostałym obiektem z migawki #2 i reprezentuje Potencjalny przeciek pamięci.  
  
      Niektóre informacje o aplikacji ułatwiają następujące działania: wybranie przycisku **przeciek pamięci** powinno spowodować usunięcie elementu DIV i dodanie elementu, więc kod nie jest prawidłowym działaniem (oznacza to, że wyciekuje pamięć). W następnej sekcji wyjaśniono, jak rozwiązać ten problem.  
  
    > [!TIP]
    > Czasami lokalizowanie obiektu w odniesieniu do `Global` obiektu może pomóc w zidentyfikowaniu tego obiektu. W tym celu otwórz menu skrótów dla identyfikatora, a następnie wybierz **Pokaż w widoku elementów głównych**.  
  
## <a name="fixing-the-memory-issue"></a><a name="FixingMemory"></a> Rozwiązywanie problemu z pamięcią  
  
1. Korzystając z danych ujawnionych przez profiler, badasz kod, który jest odpowiedzialny za usuwanie elementów DOM o IDENTYFIKATORze "Item". Występuje w `initialize()` funkcji.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` jest, prawdopodobnie, nie działa poprawnie. Należy sprawdzić, w jaki sposób kod jest buforowany elementu DOM i znaleźć problem; odwołanie do buforowanego elementu nie zostanie zaktualizowane.  
  
2. W default.js Dodaj następujący wiersz kodu do funkcji Load, tuż przed wywołaniem `appendChild` :  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Ten kod aktualizuje odwołanie do pamięci podręcznej, dzięki czemu element zostanie prawidłowo usunięty po wybraniu przycisku **przeciek pamięci** . Pełny kod dla funkcji Load wygląda teraz następująco:  
  
   ```javascript  
   function load() {  
  
       wrapper = document.querySelector(".wrapper");  
  
       var newDiv = document.createElement("div");  
  
       newDiv.style.zIndex = "-1";  
       newDiv.id = "item";  
       elem = newDiv;  
  
       wrapper.appendChild(newDiv);  
   }  
   ```  
  
3. W menu **debugowanie** wybierz pozycję **wydajność i Diagnostyka**.  
  
4. W obszarze **dostępne narzędzia**wybierz pozycję **pamięć JavaScript**, a następnie wybierz polecenie **Uruchom**.  
  
5. Wykonaj tę samą procedurę jak wcześniej, aby wykonać trzy migawki. Kroki są podsumowane w tym miejscu:  
  
   1. W aplikacji wybierz przycisk **przeciek pamięci** cztery razy.  
  
   2. Przejdź do programu Visual Studio i wybierz opcję **Utwórz migawkę sterty** dla migawki linii bazowej.  
  
   3. W aplikacji wybierz przycisk **przeciek pamięci** .  
  
   4. Przejdź do programu Visual Studio i wybierz opcję **Utwórz migawkę sterty** dla drugiej migawki.  
  
   5. W aplikacji wybierz przycisk **przeciek pamięci** .  
  
   6. Przejdź do programu Visual Studio i wybierz opcję **Utwórz migawkę sterty** dla trzeciej migawki.  
  
      Migawka #3 teraz pokazuje rozmiar sterty, ponieważ **nie zwiększa** się z #2 migawek, a liczba obiektów to + 1/ -1, co oznacza, że jeden obiekt został dodany, a jeden z nich został usunięty. Jest to pożądane zachowanie.  
  
      Na poniższej ilustracji przedstawiono #2 migawek i #3 migawek.  
  
      ![Migawki pokazujące trwały przeciek pamięci](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć języka JavaScript](../profiling/javascript-memory.md)

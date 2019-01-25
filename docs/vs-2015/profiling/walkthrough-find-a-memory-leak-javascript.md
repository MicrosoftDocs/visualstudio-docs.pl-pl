---
title: 'Przewodnik: Znajdowanie wycieku pamięci (JavaScript) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 88f9d8fc871f182bb3a6d7f36c3648982e7a9684
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780937"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Przewodnik: Znajdowanie wycieku pamięci (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Ten instruktaż prowadzi przez proces identyfikacji i rozwiązywania problemu proste pamięci za pomocą analizatora pamięci JavaScript. Analizator pamięci JavaScript są dostępne w Visual Studio for Windows Store aplikacje są kompilowane dla Windows przy użyciu języka JavaScript. W tym scenariuszu utworzysz aplikację, która zachowuje niepoprawnie elementów DOM w pamięci, zamiast usuwania elementów znajdujących się na tej samej stawki, w którym są tworzone.  
  
 Mimo, że przyczyną przecieku pamięci w tej aplikacji jest bardzo specyficzny, kroki opisane w tym miejscu pokazują przepływ pracy, który jest zazwyczaj efektywne polega na wyizolowaniu obiektów, które są przeciek pamięci.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Uruchomiona aplikacja testowa analizatora pamięci JavaScript  
  
1.  W programie Visual Studio, wybierz **pliku**, **New**, **projektu**.  
  
2.  Wybierz **JavaScript** w okienku po lewej stronie, a następnie wybierz **Windows**, **systemu Windows 8**, a następnie **Universal** lub  **Windows Phone aplikacje**.  
  
    > [!IMPORTANT]
    >  Wyniki użycia pamięci, które są wyświetlane w tym temacie są sprawdzane pod względem aplikacji systemu Windows 8.  
  
3.  Wybierz **pusta aplikacja** szablonu projektu w środkowym okienku.  
  
4.  W **nazwa** polu Określ nazwę, taką jak `JS_Mem_Tester`, a następnie wybierz **OK**.  
  
5.  W **Eksploratora rozwiązań**, otwórz plik default.html i wklej następujący kod między \<treści > znaczniki:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Jeśli używasz szablonu aplikacji uniwersalnej dla Windows 8.1, musisz zaktualizować kod HTML i CSS w obu. Windows i. Projekty WindowsPhone.  
  
6.  Otwórz default.css i Dodaj następujący kod CSS:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Otwórz default.js i Zastąp cały kod przy użyciu tego kodu:  
  
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
  
8.  Wybierz klawisz F5, aby rozpocząć debugowanie. Upewnij się, że **przeciek pamięci** na stronie pojawi się przycisk.  
  
9. Przejdź z powrotem do programu Visual Studio (Alt + Tab), a następnie wybierz klawisz Shift + F5, aby zatrzymać debugowanie.  
  
     Teraz, gdy upewnieniu się, że aplikacja działa, można sprawdzić użycie pamięci.  
  
### <a name="analyzing-the-memory-usage"></a>Analizowanie użycia pamięci  
  
1. Na **debugowania** narzędzi w **Rozpocznij debugowanie** wybierz cel debugowania dla zaktualizowanego projektu: jeden z emulatory Windows Phone lub **symulator**.  
  
   > [!TIP]
   >  Dla aplikacji Windows Store, możesz również **komputera lokalnego** lub **maszyny zdalnej** na tej liście. Jednak zaletą przy użyciu emulatora lub symulator jest można umieścić go obok programu Visual Studio i łatwo przełączać się między uruchomionej aplikacji i analizatora pamięci JavaScript. Aby uzyskać więcej informacji, zobacz [uruchamiać aplikacje w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md) i [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. Na **debugowania** menu, wybierz **Profiler wydajności...** .  
  
3. W **dostępnych narzędzi**, wybierz **pamięci JavaScript**, a następnie wybierz **Start**.  
  
    W tym samouczku jest będzie dołączanie analizator pamięci do projektu startowego. Aby uzyskać informacje na temat innych opcji, takich jak dołączanie analizator pamięci do zainstalowanej aplikacji, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).  
  
    Po uruchomieniu analizator pamięci, można napotkać Kontrola konta użytkownika, która żąda uprawnienia do uruchomienia VsEtwCollector.exe. Wybierz **tak**.  
  
4. Wybierz **przeciek pamięci** przycisk cztery razy pod rząd.  
  
    Po wybraniu przycisku, kod w pracy ma default.js, która spowoduje przeciek pamięci do obsługi zdarzeń. Służy to do celów diagnostycznych.  
  
   > [!TIP]
   >  Powtórzenie tego scenariusza, który chcesz przetestować przeciek pamięci ułatwia odfiltrować postrzegać informacji, takich jak obiekty, które są dodawane do stosu podczas inicjowania aplikacji lub podczas ładowania strony.  
  
5. W uruchomionej aplikacji Przełącz się do programu Visual Studio (Alt + Tab).  
  
    Analizator pamięci JavaScript Wyświetla informacje na nowej karcie w programie Visual Studio.  
  
    Wykres pamięci w tym użycie pamięci przez widok podsumowania przedstawia proces wraz z upływem czasu. Widok zawiera, polecenia takie jak **wykonaj migawkę sterty**. Migawka zawiera szczegółowe informacje na temat użycia pamięci w danym momencie. Aby uzyskać więcej informacji, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).  
  
6. Wybierz **wykonaj migawkę sterty**.  
  
7. Przejdź do aplikacji i wybierz **przeciek pamięci**.  
  
8. Przejdź do programu Visual Studio i wybierz **wykonaj migawkę sterty** ponownie.  
  
    Ta ilustracja przedstawia migawką będącą punktem odniesienia (#1) i migawki nr 2.  
  
    ![Linia bazowa migawka i migawka 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   >  Emulator Windows Phone nie są wyświetlane zrzut ekranu przedstawiający aplikację w momencie utworzenia migawki.  
  
9. Przejdź do aplikacji i wybierz **przeciek pamięci** ponownie przycisk.  
  
10. Przejdź do programu Visual Studio i wybierz **wykonaj migawkę sterty** po raz trzeci.  
  
    > [!TIP]
    >  Wykonując trzecią migawki w tym przepływie pracy można odfiltrować zmian z migawką będącą punktem odniesienia do drugiego migawki, które nie są skojarzone z przecieków pamięci. Na przykład może być oczekiwany zmiany, takie jak Aktualizowanie nagłówków i stopek na stronie spowoduje wygenerowanie pewnych zmian użycia pamięci, ale może być powiązana przecieków pamięci.  
  
     Ta ilustracja przedstawia migawki nr 2 i 3 migawki.  
  
     ![Migawki 2 i 3 migawki](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. W programie Visual Studio, wybierz **zatrzymać** Aby zatrzymać profilowanie.  
  
12. W programie Visual Studio Porównaj migawki. Migawka #2 ilustruje następujące czynności:  
  
    - Rozmiar sterty (przedstawione przez czerwony Strzałka po lewej stronie w górę) został zwiększony przez kilka bazy wiedzy, w porównaniu z migawki nr 1.  
  
      > [!IMPORTANT]
      >  Wartości użycia pamięci dokładny rozmiar sterty zależą od docelowego debugowania.  
  
    - Liczba obiektów na stosie (przedstawione przez czerwony Strzałka w górę na prawo) został zwiększony w porównaniu do migawki nr 1. Jeden obiekt został dodany (+ 1) i żadne obiekty nie zostały usunięte (-0).  
  
      Migawka #3 przedstawiono poniżej:  
  
    - Rozmiar sterty został zwiększony ponownie za kilka kilkuset bajtów w porównaniu do migawki nr 2.  
  
    - Liczba obiektów na stercie został zwiększony, ponownie w porównaniu do migawki nr 2. Jeden obiekt został dodany (+ 1) i żadne obiekty nie zostały usunięte (-0).  
  
13. W migawki nr 3, wybierz tekst łącza po prawej stronie znajduje się wartość + 1 / - 0 obok czerwona strzałka w górę.  
  
     ![Link do innego widoku obiektów na stercie](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Spowoduje to otwarcie różnicowej widoku obiektów na stosie, o nazwie **migawki nr 3 — migawka nr 2**, przy użyciu widoku typy wyświetlane domyślnie. Domyślnie zobaczysz listę obiekty dodane do sterty między 2 migawka i migawka nr 3.  
  
14. W **zakres** filtrowania, wybierz **obiekty pozostałe z migawki nr 2**.  
  
15. Otwórz obiekt HTMLDivElement w górnej części drzewa obiektów, jak pokazano poniżej.  
  
     ![Widok różnic tego obiektu możesz liczyć na stosie](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Ten widok przedstawia przydatne informacje dotyczące przeciek pamięci, takie jak następujące:  
  
    - Ten widok przedstawia elementu DIV z Identyfikatorem `item`, i rozmiaru zachowanego dla obiektu jest kilka kilkuset bajtów (dokładna wartość mogą się różnić).  
  
    - Ten obiekt jest obiekt pozostałość z migawki nr 2 i przedstawia Potencjalny przeciek pamięci.  
  
      Pewną wiedzę na temat aplikacji pomaga w tym momencie: Wybieranie **przeciek pamięci** przycisk powinien usunąć DIV element i Dodaj element, dzięki czemu kod nie wygląda na działający bezpośrednio (czyli go występuje przeciek pamięci). Następna sekcja wyjaśnia, jak rozwiązać ten problem.  
  
    > [!TIP]
    >  Czasami, lokalizowanie obiektu w odniesieniu do `Global` obiektu może pomóc w zidentyfikowaniu tego obiektu. Aby to zrobić, otwórz menu skrótów dla identyfikatora, a następnie wybierz **Pokaż w widoku elementów głównych**.  
  
##  <a name="FixingMemory"></a> Rozwiązywanie problemu pamięci  
  
1. Korzystanie z danych, które ujawniło przez profiler, sprawdź kod, który jest odpowiedzialny za usunięcie elementów modelu DOM o identyfikatorze "item". Odbywa się w `initialize()` funkcji.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    `elem.removeNode(true)` być może, nie działa prawidłowo. Sprawdź, jak kod jest buforowanie elementu DOM i Znajdź problem; Odwołanie do pamięci podręcznej elementu nie są aktualizowane.  
  
2. W pliku default.js, Dodaj następujący wiersz kodu do funkcji obciążenia, tuż przed wywołaniem `appendChild`:  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Ten kod aktualizuje odwołanie do pamięci podręcznej elementu tak, aby element poprawnie zostanie usunięty po wybraniu **przeciek pamięci** przycisku. Kompletny kod dla funkcji obciążenia wygląda teraz następująco:  
  
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
  
3. Na **debugowania** menu, wybierz **wydajności i diagnostyki**.  
  
4. W **dostępnych narzędzi**, wybierz **pamięci JavaScript**, a następnie wybierz **Start**.  
  
5. Wykonaj tę samą procedurę, jako przed do wykonania trzech migawek. Kroki są podsumowywane w tym miejscu:  
  
   1. W aplikacji, wybierz **przeciek pamięci** przycisk cztery razy pod rząd.  
  
   2. Przejdź do programu Visual Studio i wybierz **wykonaj migawkę sterty** dla migawką będącą punktem odniesienia.  
  
   3. W aplikacji, wybierz **przeciek pamięci** przycisku.  
  
   4. Przejdź do programu Visual Studio i wybierz **wykonaj migawkę sterty** dla drugiego migawki.  
  
   5. W aplikacji, wybierz **przeciek pamięci** przycisku.  
  
   6. Przejdź do programu Visual Studio i wybierz **wykonaj migawkę sterty** trzeci migawki.  
  
      Migawka #3 zawiera obecnie Rozmiar sterty jako **bez zwiększania** z migawki nr 2, a obiekt liczone jako + 1 / -1, co oznacza, że jeden obiekty zostały dodane i jeden obiekt został usunięty. Jest to żądane zachowanie.  
  
      Na poniższej ilustracji przedstawiono migawki nr 2 i 3 migawki.  
  
      ![Migawki przedstawiający przeciek pamięci stałej](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Zobacz też  
 [Pamięć języka JavaScript](../profiling/javascript-memory.md)

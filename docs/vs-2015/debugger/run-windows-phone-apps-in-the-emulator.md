---
title: Uruchamianie aplikacji Windows Phone w emulatorze | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bc85d1a38143e626fc659979eea727a0b41ef00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761769"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Uruchamianie aplikacji Windows Phone w emulatorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Emulator Windows Phone zawiera środowisku wirtualnym, w którym można debugowania i testowania aplikacji Windows Phone na komputerze bez urządzenia fizycznego. Można symulacji typowe touch i obrót zdarzeń i wybrać rozmiar ekranu fizycznego i rozwiązania, który chcesz emulować. Możesz także testować wiele często używane funkcje, takie jak lokalizacja, sieci, powiadomienia, czujników, przyspieszeniomierza i opcjonalnie karta SD.  
  
 Aby uzyskać więcej informacji o funkcjach, które można przetestować w emulatorze, zobacz [testowania aplikacji funkcji w Windows Phone Emulator](http://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Razem z Visual Studio emulator zapewnia kompletne środowisko, w którym można projektowania, tworzenia, debugowania i testowania aplikacji Windows Phone.  
  
##  <a name="BKMK_run"></a> Uruchamianie aplikacji Windows Phone w emulatorze  
 Gdy tworzysz aplikację Windows Phone można użyć emulatora Windows Phone do wdrażania i testowania aplikacji, szybko. Zaleca się, że możesz testować swoją aplikację na rzeczywistego urządzenia Windows Phone, jednak przed opublikowaniem aplikacji w Windows Phone Store. Pozwala to środowisko aplikacji, ponieważ na czym polega przez użytkowników.  
  
 Po uruchomieniu aplikacji Windows Phone po raz pierwszy w Emulator Windows Phone, zachodzą następujące zdarzenia:  
  
1. Zostanie uruchomiony emulator.  
  
2. Emulator ładuje system operacyjny Windows Phone.  
  
3. Emulator wyświetlane na ekranie Start systemu Windows Phone.  
  
4. Twoja aplikacja jest wdrożona w emulatorze.  
  
5. Aplikacja działa w emulatorze.  
  
   Jeśli wybrany emulator jest już uruchomiona, Twoja aplikacja jest wdrożona i uruchomiona w emulatorze uruchomione. Tylko jedno wystąpienie każdego emulator można uruchomić w danym momencie.  
  
> [!TIP]
>  Podczas testowania aplikacji w emulatorze, pozostaw emulator otwarte między sesjami debugowania, aby można było ponownie szybko uruchomić aplikację.  
  
###  <a name="BKMK_vs"></a> Uruchamianie aplikacji z programu Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Aby wdrożyć i uruchomić aplikację w programie Visual Studio  
  
1.  W programie Visual Studio Otwórz projekt Windows Phone.  
  
2.  Na **standardowa** narzędzi, wybierz jedną z opcji emulatora.  
  
     ![Listy obrazów systemu Windows Phone Emulator](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3.  Wdrażanie i uruchamianie aplikacji za pomocą debugowania na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**, lub naciśnij klawisz F5.  
  
     Aby wdrożyć i uruchomić aplikację bez debugowania, na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**, lub naciśnij klawisze Ctrl + F5.  
  
     Twoja aplikacja jest wdrożona i uruchomiona.  
  
     Do wdrożenia aplikacji bez konieczności uruchamiania go na **kompilacji** menu, kliknij przycisk **wdrożyć rozwiązanie**.  
  
##### <a name="to-stop-a-running-app"></a>Aby zatrzymać uruchomionej aplikacji  
  
- Aby zatrzymać uruchomionej aplikacji, wykonaj jedną z następujących czynności:  
  
  - W programie Visual Studio na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**, lub naciśnij klawisze Shift + F5.  
  
  - W emulatorze, naciśnij klawisz **ponownie** przycisk, aby zamknąć aplikację. Jeśli się stroną aktywną aplikacji nie było strony początkowej aplikacji, może być konieczne naciśnij **ponownie** przycisk więcej niż jeden raz.  
  
    Umożliwia zamknięcie aplikacji i uruchomienia zostanie otwarty ekran. To kończy bieżącą sesję debugowania.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Aby ponownie uruchomić aplikację bez debugowania  
  
1.  W emulatorze na ekranie startowym Przesuń palcem od lewej do wyświetlania listy aplikacji.  
  
2.  Na liście aplikacji naciśnij ikonę aplikacji. Aplikacja uruchamia ponownie bez debugowania.  
  
##### <a name="to-deactivate-a-running-app"></a>Aby dezaktywować uruchomionej aplikacji  
  
1.  Przed uruchomieniem aplikacji w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości** otworzyć **projektanta projektu**.  
  
2.  W **projektanta projektu**na **debugowania** zostaw **reliktu po dezaktywacji podczas debugowania** zaznacz pole niezaznaczone, jeśli chcesz, aby aplikacja, aby przejść do nieaktywni stan, kiedy zdezaktywowane. Zaznacz pole wyboru, jeśli chcesz, aby aplikacja schowane podczas dezaktywacji.  
  
3.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**, lub naciśnij klawisz F5, aby uruchomić aplikację.  
  
4.  W emulatorze, naciśnij klawisz **Start** przycisku. Zostanie wyświetlone na ekranie startowym, a aplikacja jest nieaktywne. Aplikacja albo przechodzi w stan nieaktywni lub jest schowane, w zależności od ustawień **reliktu po dezaktywacji podczas debugowania** pole wyboru.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Aby ponownie aktywować nieaktywni lub schowane aplikacji  
  
-   W emulatorze, naciśnij klawisz **ponownie** przycisk, aby powrócić do aplikacji. Jeśli przejście do innych stron, lub otworzyć innej aplikacji, może być konieczne naciśnij **ponownie** przycisk więcej niż jeden raz, aby ponownie aktywować aplikację.  
  
     Wznawia sesję debugowania. Jeśli debuger został odłączony z aplikacji, może być konieczne naciśnij klawisz F5, aby wznowić sesji debugowania.  
  
###  <a name="BKMK_depltool"></a> Uruchamianie aplikacji za pomocą narzędzia do wdrażania aplikacji  
 Można również użyć narzędzia do wdrażania aplikacji Windows Phone (**AppDeploy.exe**) aby uruchomić aplikację w emulatorze. To narzędzie jest autonomiczną aplikację, która jest instalowana podczas instalacji narzędzi deweloperskich programu Windows Phone.  
  
 Aby uzyskać więcej informacji, zobacz [aplikacji wdrożenia Windows Phone 8.1 przy użyciu narzędzia Application Deployment](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a> Konfigurowanie emulator Windows Phone przy użyciu narzędzi emulatora  
 W poniższej tabeli przedstawiono dostępne przyciski konfiguracji, na pasku narzędzi emulatora.  
  
|Przyciski paska narzędzi|Opcje konfiguracji|  
|---------------------|---------------------------|  
|![Dane wejściowe opcji paska narzędzi Windows Phone Emulator](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurowanie jednego lub wielu danych wejściowych**<br /><br /> Po włączeniu punktu wielu danych wejściowych, kliknąć prawym przyciskiem myszy, aby przenieść punkty dotykowe bez dotykania ekranu. Następnie użytkownik może kliknij lewym przyciskiem myszy do przeniesienia punkty dotykowe: obu jednocześnie.|  
|![Orientacja na pasku narzędzi Windows Phone Emulator](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurowanie orientację emulatora**<br /><br /> Można zmienić orientację w Emulator Windows Phone do jednej z trzech orientacje: pionowa, pozioma po lewej lub pozioma po prawej. Rozmiar emulatora nie ulega zmianie, gdy zmiana orientacji.<br /><br /> Aby zmienić orientację, kliknij przycisk **Obróć w lewo** przycisk lub **Obróć w prawo** przycisku.|  
|![Rozmiar opcji paska narzędzi Windows Phone Emulator](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Skonfiguruj rozmiar emulator**<br /><br /> Można zmienić rozmiar emulatora na ekranie komputera hosta. Punktów na cal (DPI) dla emulatora opiera się na hoście rozpoznawanie wartości DPI monitora, bez względu na wartość powiększenia.<br /><br /> -Aby dopasować emulatora do ekranu, kliknij pozycję **Dopasuj do ekranu** przycisku.<br />— Aby zmienić ustawienie powiększenia, kliknij przycisk **powiększenia** przycisku. **Powiększenia** zostanie otwarte okno dialogowe. W **powiększenia** okna dialogowego wprowadź wartość powiększenia od 33 do 100.|  
  
##  <a name="BKMK_buttons"></a> Użyj przycisków symulowane sprzętu w emulatorze  
 Symulowanie użyj przycisków sprzętowych na telefonie, korzystając z przycisków symulowane sprzętu po prawej stronie ekranu emulatora.  
  
- Kliknij przycisk **Power** przycisk, aby zasymulować, wyłączać i włączać włączenie wyświetlania. Kliknij i przytrzymaj je, aby zasymulować, wyłączając telefonu.  
  
- Kliknij przycisk **woluminu się** lub **woluminu w dół** przycisk, aby symulować zmiana ilości telefonu osoby mówiącej, połączeń telefonicznych i powiadomień.  
  
- **Aparatu** przycisk uruchamia aplikację aparatu. Można zasymulować, biorąc zdjęcie lub wideo za pomocą kontrolki w aplikacji aparatu.  
  
  Poniższy zrzut ekranu przedstawia przyciski symulowane sprzętu.  
  
1. Obraz po lewej stronie wyświetlane na ekranie startowym w emulatorze.  
  
2. Środkowy obraz przedstawia emulator po naciśnięciu **Power** przycisk, aby wyłączyć wyświetlanie.  
  
3. Właściwy obraz wyświetlany na ekranie emulatora po naciśnięciu **woluminu się** przycisk, aby zwiększyć wolumin.  
  
   ![Przyciski na emulator Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Korzystanie z klawiatury komputera za pomocą emulatora  
 Emulator obsługuje Mapowanie klawiatury sprzętu na komputerze deweloperskim do klawiatury na Windows Phone. Zachowanie kluczy jest taka sama jak na urządzeniu z systemem Windows Phone.  
  
 Klawiatura sprzętu nie jest włączona domyślnie. Ta implementacja jest odpowiednikiem przewijania klawiatury, który należy wdrożyć przed jego użyciem. Przed włączeniem klawiatury sprzętu emulator akceptuje kluczowych danych wejściowych jedynie z kluczy kontroli.  
  
 Znaki specjalne na klawiaturze zlokalizowaną wersję komputerze deweloperskim Windows nie są obsługiwane przez emulator. Aby wprowadzić znaki specjalne, które znajdują się na klawiaturze zlokalizowane, zamiast tego użyj panelu wprowadzania oprogramowania (SIP).  
  
 Aby użyć klawiatury na komputerze w emulatorze, naciśnij klawisz PAGE UP klucza lub klucza PAUSE/BREAK (emulatora systemu Windows 8/8.1) lub F4 (emulatora systemu Windows 10).  
  
 Aby zatrzymać za pomocą klawiatury na komputerze w emulatorze, naciśnij klawisz PAGE DOWN klucza lub klucza PAUSE/BREAK (emulatora systemu Windows 8/8.1) lub F4 (emulatora systemu Windows 10).  
  
 Poniższa tabela zawiera listę kluczy na klawiaturze sprzętu używanego do emulowania przyciski i inne kontrolki na Windows Phone.  
  
|Klucz sprzętu komputera|Przycisk sprzętu Windows Phone|Uwagi|  
|---------------------------|-----------------------------------|-----------|  
|F1|WSTECZ|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|F2|ROZPOCZNIJ|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|F3|WYSZUKIWANIE||  
|F4|W emulatorze systemu Windows 10 przełącza między za pomocą klawiatury na komputerze lokalnym, a nie za pomocą klawiatury na komputerze lokalnym.|Nie ma zastosowania w emulatorze systemu Windows 8/8.1.|  
|F5|Nie dotyczy.||  
|F6|APARAT FOTOGRAFICZNY PÓŁ|Przycisk dedykowanych aparatu, który jest wciśnięty połowie.|  
|F7|PEŁNY APARAT FOTOGRAFICZNY|Przycisk dedykowanych aparatu.|  
|F8|Nie dotyczy.||  
|F9|WOLUMIN W GÓRĘ||  
|F10|WOLUMIN SZCZEGÓŁÓW||  
|F11|Nie dotyczy.||  
|F12|ZASILANIA|Naciśnij klawisz F12, dwa razy, aby włączyć na ekranie blokady.<br /><br /> Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|ESC|WSTECZ|Długie naciśnięcie działać zgodnie z oczekiwaniami.|  
|PAUSE/BREAK|Przełącz klawiatury (tylko w emulatorze systemu windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|PAGE UP|Umożliwia sprzętu klawiatury (tylko emulator systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|PAGE DOWN|Wyłącza sprzętu klawiatury (tylko emulator systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a> Zapisywanie i ładowanie niestandardowych punktów kontrolnych  
 Zapisz migawkę stanu emulatora usługi za pomocą **punktów kontrolnych** kartę emulatora **dodatkowe narzędzia**. Ta funkcja jest przydatna, jeśli często testowanie aplikacji przy użyciu tych samych danych i ustawień.  
  
 Na przykład jeśli aplikacja wymaga kilku kontaktów, można utworzyć jeden raz rekordów kontaktów i zapisać migawkę emulatora. W przeciwnym razie musisz odtworzyć rekordów kontaktów, za każdym razem, gdy Uruchom emulator.  
  
- Kliknij przycisk **nowego punktu kontrolnego** do przechwytywania nową migawkę stanu emulator przy użyciu danych i ustawień wymaganych do testowania aplikacji ponownie później. Nowy punkt kontrolny jest dodawany do **punktów kontrolnych** listy.  
  
   Nie można przechwycić punktu kontrolnego, gdy debuger jest dołączony do emulatora.  
  
- Wybierz punkt kontrolny w **punktów kontrolnych** listy, aby wyświetlić informacje dotyczące punktu kontrolnego.  
  
- Wybierz przycisk radiowy na **domyślne** kolumnę, aby wyświetlić zapisane punktu kontrolnego domyślnego punktu kontrolnego dla emulatora usługi active.  
  
- Kliknij przycisk **przywrócić** konieczne ponowne uruchomienie systemu operacyjnego Windows Phone w emulatorze, a następnie załadować wybrana migawka.  
  
- Kliknij przycisk **Usuń** można usunąć migawki, które nie są już potrzebne.  
  
  Oryginalny obraz emulatora zawsze jest wyświetlany jako pierwszy element **punktów kontrolnych** listy i nie można zmienić ani usunąć. Jednak można wybrać innej migawki, jako domyślny obraz emulatora.  
  
  ![Punkty kontrolne na karcie Windows Phone Emulator](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Przechwytywanie zrzutów ekranu w emulatorze  
 Zrzuty ekranu swoich aplikacji Windows Phone można utworzyć za pomocą narzędzia zrzut ekranu z okna dodatkowe narzędzia. Narzędzie tworzy pliki PNG, pasujące rozwiązanie uruchomiony emulator.  
  
 ![Zrzuty ekranu z Windows Phone Emulator](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Aby utworzyć zrzut ekranu aplikacji za pomocą emulatora wbudowane narzędzie zrzut ekranu  
  
1. Aby zoptymalizować jakość usługi zrzuty ekranu, należy ustawić poziom powiększenia emulatora do 100 procent. Im większa ustawiamy poziom powiększenia, tym lepsze jakość zrzucie ekranu.  
  
2. Rozpocznij tworzenie aplikacji w emulatorze.  
  
3. Na pasku narzędzi emulator, kliknij przycisk Rozwiń, aby otworzyć **dodatkowe narzędzia** okna.  
  
4. Kliknij przycisk **zrzut ekranu** kartę.  
  
5. Gdy aplikacja jest gotowa, kliknij przycisk **przechwytywania** przycisku.  
  
    Zrzut ekranu pojawia się w obszarze roboczym.  
  
6. Kliknij przycisk **Zapisz** przycisk, aby otworzyć **Zapisz jako** okno dialogowe.  
  
7. Wybierz lokalizację i **nazwy pliku** , a następnie kliknij przycisk **Zapisz**.  
  
8. Opcjonalnie można przechodzić do innych stron w Twojej aplikacji i Przechwytywanie zrzutów ekranu dodatkowe.  
  
9. Uruchom emulator z dokładnością do innego ekranu do przechwytywania tego samego zrzuty ekranu w różnych rozdzielczości. Uruchomiono aplikację z debugowaniem, musisz zatrzymać debugowanie, przed uruchomieniem go ponownie innym emulatora.  
  
   Wyłącz liczniki szybkość klatek na ekranie emulatora, przed przechwyceniem zrzuty ekranu, które zostaną przesłane do Windows Phone Store.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Aby wyłączyć liczniki szybkość klatek w emulatorze przed rozpoczęciem przechwytywania zrzutów ekranu  
  
-   W programie Visual Studio, należy określić kompilację wydania. Po określeniu kompilację wydania, należy uruchomić aplikację, wybierając **Wdróż _[Nazwa aplikacji]_**  link **kompilacji** menu.  
  
-   Alternatywnie możesz przekształcić w komentarz komentarz wiersz kodu w pliku app.xaml.cs lub app.xaml.vb, który ustawia wartość `EnableFrameRateCounter` do `true`.

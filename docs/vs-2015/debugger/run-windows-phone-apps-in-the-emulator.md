---
title: Uruchamianie aplikacji Windows Phone w emulatorze | Microsoft Docs
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
ms.openlocfilehash: 5673ebf28cc652e3bcd973808db87b5bb058659c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683528"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Uruchamianie aplikacji systemu Windows Phone w emulatorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Emulator Windows Phone zapewnia zwirtualizowane środowisko, w którym można debugować i testować aplikacje Windows Phone na komputerze bez urządzenia fizycznego. Można symulować typowe zdarzenia dotknięcia i rotacji, a także wybrać rozmiar i rozdzielczość ekranu fizycznego, który ma być emulowany. Możesz również testować wiele powszechnie używanych funkcji, takich jak lokalizacja, Sieć, powiadomienia, czujniki, przyspieszeniomierz i opcjonalna karta SD.  
  
 Aby uzyskać więcej informacji na temat funkcji, które można testować w emulatorze, zobacz [testowanie funkcji aplikacji w emulatorze Windows Phone](https://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Wraz z programem Visual Studio Emulator oferuje kompletne środowisko, w którym można projektować, opracowywać, debugować i testować Windows Phone aplikacji.  
  
## <a name="run-a-windows-phone-app-in-the-emulator"></a><a name="BKMK_run"></a> Uruchamianie aplikacji Windows Phone w emulatorze  
 Podczas tworzenia aplikacji Windows Phone można użyć emulatora Windows Phone, aby szybko wdrożyć i przetestować aplikację. Zalecamy przetestowanie aplikacji na rzeczywistym urządzeniu Windows Phone, jednak przed opublikowaniem aplikacji w magazynie Windows Phone. Pozwala to na korzystanie z aplikacji w miarę ich korzystania przez użytkowników.  
  
 Po uruchomieniu aplikacji Windows Phone po raz pierwszy w emulatorze Windows Phone wystąpią następujące zdarzenia:  
  
1. Emulator rozpocznie działanie.  
  
2. Emulator ładuje Windows Phone system operacyjny.  
  
3. Emulator wyświetla ekran startowy Windows Phone.  
  
4. Aplikacja jest wdrażana w emulatorze.  
  
5. Twoja aplikacja jest uruchamiana na emulatorze.  
  
   Jeśli wybrany emulator jest już uruchomiony, aplikacja zostanie wdrożona i uruchomiona w uruchomionym emulatorze. Jednocześnie można uruchomić tylko jedno wystąpienie każdego emulatora.  
  
> [!TIP]
> Jeśli testujesz aplikację w emulatorze, pozostaw emulator otwarty między sesjami debugowania, aby szybko uruchomić aplikację.  
  
### <a name="run-an-app-from-visual-studio"></a><a name="BKMK_vs"></a> Uruchamianie aplikacji z programu Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Aby wdrożyć i uruchomić aplikację z programu Visual Studio  
  
1. W programie Visual Studio Otwórz projekt Windows Phone.  
  
2. Na pasku narzędzi **Standardowy** wybierz jedną z opcji emulatora.  
  
     ![Lista obrazów emulatora Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3. Aby wdrożyć i uruchomić aplikację z debugowaniem, w menu **debugowanie** kliknij polecenie **Rozpocznij debugowanie**lub naciśnij klawisz F5.  
  
     Aby wdrożyć i uruchomić aplikację bez debugowania, w menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**lub naciśnij klawisze CTRL + F5.  
  
     Twoja aplikacja została wdrożona i uruchomiona.  
  
     Aby wdrożyć aplikację bez jej uruchamiania, w menu **kompilacja** kliknij polecenie **Wdróż rozwiązanie**.  
  
##### <a name="to-stop-a-running-app"></a>Aby zatrzymać uruchomioną aplikację  
  
- Aby zatrzymać uruchomioną aplikację, wykonaj jedną z następujących czynności:  
  
  - W programie Visual Studio w menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie**lub naciśnij klawisze Shift + F5.  
  
  - W emulatorze naciśnij przycisk **Wstecz** , aby zakończyć działanie aplikacji. Jeśli aktywna Strona aplikacji nie jest stroną początkową aplikacji, może być konieczne naciśnięcie przycisku **Wstecz** więcej niż jeden raz.  
  
    Aplikacja zostanie zamknięta i zostanie otwarty ekran startowy. Spowoduje to zakończenie bieżącej sesji debugowania.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Aby ponownie uruchomić aplikację bez debugowania  
  
1. W emulatorze na ekranie startowym przesuń w lewo, aby wyświetlić listę aplikacji.  
  
2. Na liście aplikacji naciśnij ikonę aplikacji. Aplikacja zostanie ponownie uruchomiona bez debugowania.  
  
##### <a name="to-deactivate-a-running-app"></a>Aby dezaktywować działającą aplikację  
  
1. Przed uruchomieniem aplikacji w programie Visual Studio kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, a następnie wybierz pozycję **Właściwości** , aby otworzyć **projektanta projektu**.  
  
2. W **projektancie projektu**na stronie **debugowanie** pozostaw pole **relikt przy zdezaktywowaniu podczas dezaktywacji** , gdy debugowanie nie jest zaznaczone, jeśli chcesz, aby aplikacja przejdzie w stan uśpienia po zdezaktywowaniu. Zaznacz to pole wyboru, jeśli chcesz, aby aplikacja była schowane Po zdezaktywowaniu.  
  
3. W menu **debugowanie** kliknij **Rozpocznij debugowanie**lub naciśnij klawisz F5, aby uruchomić aplikację.  
  
4. W emulatorze naciśnij przycisk **Start** . Zostanie wyświetlony ekran startowy i aplikacja zostanie zdezaktywowana. Aplikacja przechodzi w stan uśpienia lub jest schowany, w zależności od ustawienia **reliktu podczas dezaktywacji w trakcie debugowania** pola wyboru.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Aby ponownie uaktywnić aplikację uśpioną lub schowane  
  
- W emulatorze naciśnij przycisk **Wstecz** , aby powrócić do aplikacji. Jeśli przejdziesz do innych stron lub otwarto inną aplikację, może być konieczne naciśnięcie przycisku **Wstecz** w celu ponownego aktywowania aplikacji.  
  
     Sesja debugowania zostaje wznowiona. Jeśli debuger został odłączony od aplikacji, może być konieczne naciśnięcie klawisza F5 w celu wznowienia sesji debugowania.  
  
### <a name="run-an-app-with-the-application-deployment-tool"></a><a name="BKMK_depltool"></a> Uruchamianie aplikacji za pomocą narzędzia do wdrażania aplikacji  
 Możesz również użyć narzędzia wdrażania aplikacji Windows Phone (**AppDeploy.exe**), aby uruchomić aplikację w emulatorze. To narzędzie jest aplikacją autonomiczną, która jest instalowana podczas instalowania Windows Phone narzędzi programistycznych.  
  
 Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji Windows Phone 8,1 przy użyciu narzędzia do wdrażania aplikacji](https://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
## <a name="configure-the-windows-phone-emulator-with-the-emulator-toolbar"></a><a name="BKMK_toolbar"></a> Konfigurowanie emulatora Windows Phone za pomocą paska narzędzi emulatora  
 W tej tabeli przedstawiono przyciski konfiguracji dostępne na pasku narzędzi emulatora.  
  
|Przyciski paska narzędzi|Opcje konfiguracji|  
|---------------------|---------------------------|  
|![Opcje wprowadzania na pasku narzędzi emulatora Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Konfigurowanie danych wejściowych pojedynczego punktu lub wielopunktowego**<br /><br /> Po włączeniu wprowadzania wielopunktowego można kliknąć prawym przyciskiem myszy, aby przenieść punkty dotykowe bez dotykania ekranu. Następnie możesz kliknąć lewym przyciskiem myszy, aby przesunąć oba punkty dotykowe jednocześnie.|  
|![Orientacja na pasku narzędzi emulatora Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Konfigurowanie orientacji emulatora**<br /><br /> Orientację w emulatorze Windows Phone można zmienić na jedną z trzech orientacji: pionową, poziomą w lewo lub poziomą. Rozmiar emulatora nie zmienia się w przypadku zmiany orientacji.<br /><br /> Aby zmienić orientację, kliknij przycisk **Obróć w lewo** lub przycisk **Obróć w prawo** .|  
|![Opcje rozmiaru na pasku narzędzi emulatora Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Konfigurowanie rozmiaru emulatora**<br /><br /> Można zmienić rozmiar emulatora na ekranie komputera hosta. Punkty na cal (DPI) emulatora bazują na rozdzielczości DPI monitora hosta, bez względu na wartość powiększenia.<br /><br /> -Aby dopasować emulator do ekranu, kliknij przycisk **Dopasuj do ekranu** .<br />-Aby zmienić ustawienie powiększenia, kliknij przycisk **powiększenia** . Zostanie otwarte okno dialogowe **powiększenie** . W oknie dialogowym **powiększenie** wprowadź wartość powiększenia z zakresu od 33 do 100.|  
  
## <a name="use-the-simulated-hardware-buttons-on-the-emulator"></a><a name="BKMK_buttons"></a> Używanie przycisków symulowanych sprzętu na emulatorze  
 Symuluj korzystanie z przycisków sprzętowych telefonu przy użyciu przycisków symulowanych sprzętu po prawej stronie ekranu emulatora.  
  
- Kliknij przycisk **zasilanie** , aby symulować wyłączenie i włączenie ekranu. Kliknij i przytrzymaj, aby symulować wyłączenie telefonu.  
  
- Kliknij przycisk **głośność w górę** lub **w dół** , aby symulować zmianę głośności głośnika telefonu na potrzeby połączeń telefonicznych i powiadomień.  
  
- Przycisk **kamera** uruchamia aplikację aparatu. Możesz symulować zdjęcie lub wideo przy użyciu kontrolek w aplikacji aparatu.  
  
  Poniższy zrzut ekranu przedstawia symulowane przyciski sprzętu.  
  
1. Po lewej stronie jest wyświetlany ekran startowy na emulatorze.  
  
2. Środkowy obraz wyświetla emulator po naciśnięciu przycisku **zasilanie** , aby wyłączyć ekran.  
  
3. Po naciśnięciu przycisku **głośności w górę** w celu zwiększenia głośności zostanie wyświetlony ekran emulatora.  
  
   ![Przyciski na emulatorze Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
## <a name="use-the-computer-keyboard-with-the-emulator"></a><a name="BKMK_tasks_kbd"></a> Korzystanie z klawiatury komputera z emulatorem  
 Emulator obsługuje mapowanie klawiatury sprzętowej na komputerze deweloperskim na klawiaturę na Windows Phone. Zachowanie kluczy jest takie samo jak na urządzeniu Windows Phone.  
  
 Domyślnie Klawiatura sprzętowa nie jest włączona. Ta implementacja jest równoznaczna z przesuwaną klawiaturą, która musi zostać wdrożona, zanim będzie można jej użyć. Przed włączeniem klawiatury sprzętowej emulator akceptuje tylko dane wejściowe z kluczy kontrolnych.  
  
 Emulator nie obsługuje znaków specjalnych na klawiaturze zlokalizowanej wersji komputera deweloperskiego z systemem Windows. Aby wprowadzić znaki specjalne, które znajdują się na zlokalizowanej klawiaturze, użyj panelu wprowadzania oprogramowania (SIP).  
  
 Aby użyć klawiatury komputera w emulatorze, naciśnij klawisz PAGE UP lub klucz PAUSE/BREAK (emulator systemu Windows 8/8.1) lub F4 (emulator systemu Windows 10).  
  
 Aby zatrzymać korzystanie z klawiatury komputera w emulatorze, naciśnij klawisz PAGE DOWN lub klucz PAUZy/PRZERWAnia (emulator systemu Windows 8/8.1) lub F4 (emulator systemu Windows 10).  
  
 Poniższa tabela zawiera listę kluczy na klawiaturze sprzętowej, których można użyć do emulowania przycisków i innych kontrolek na Windows Phone.  
  
|Klucz sprzętowy komputera|Przycisk Windows Phone sprzętu|Uwagi|  
|---------------------------|-----------------------------------|-----------|  
|F1|Wstecz|Długie naciśnięcia działają zgodnie z oczekiwaniami.|  
|F2|START|Długie naciśnięcia działają zgodnie z oczekiwaniami.|  
|F3|SEARCH||  
|F4|W emulatorze systemu Windows 10 przełącza się między przy użyciu klawiatury komputera lokalnego i nie używa klawiatury komputera lokalnego.|Nie dotyczy emulatora systemu Windows 8/8.1.|  
|F5|Nie dotyczy.||  
|F6|POŁOWA APARATU|Przycisk dedykowanego aparatu fotograficznego, który jest wciśnięty w połowie.|  
|F7|KAMERA ZAPEŁNIONA|Przycisk dedykowany aparat.|  
|F8|Nie dotyczy.||  
|F9|GŁOŚNOŚĆ W GÓRĘ||  
|F10|WOLUMIN W DÓŁ||  
|F11|Nie dotyczy.||  
|F12|POWER|Naciśnij dwukrotnie klawisz F12, aby włączyć ekran blokady.<br /><br /> Długie naciśnięcia działają zgodnie z oczekiwaniami.|  
|ESC|Wstecz|Długie naciśnięcia działają zgodnie z oczekiwaniami.|  
|WSTRZYMAJ/PRZERWIJ|Przełącz klawiaturę (tylko emulator systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|PAGE UP|Włącza klawiaturę sprzętową (tylko emulator systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
|PAGE DOWN|Wyłącza klawiaturę sprzętową (tylko emulator systemu Windows 8/8.1).|Nie dotyczy emulatora systemu Windows 10.|  
  
## <a name="save-and-load-custom-checkpoints"></a><a name="BKMK_checkpoints"></a> Zapisz i Załaduj niestandardowe punkty kontrolne  
 Zapisz migawkę stanu emulatora przy użyciu karty **punkty kontrolne** **dodatkowych narzędzi**emulatora. Ta funkcja jest przydatna, jeśli często testujesz aplikację przy użyciu tych samych danych i ustawień.  
  
 Na przykład jeśli aplikacja wymaga kilku kontaktów, można utworzyć rekordy kontaktów jeden raz i zapisać migawkę emulatora. W przeciwnym razie musisz ponownie utworzyć rekordy kontaktów przy każdym uruchomieniu emulatora.  
  
- Kliknij pozycję **nowy punkt kontrolny** , aby przechwycić nową migawkę stanu emulatora przy użyciu danych i ustawień wymaganych do ponownego przetestowania aplikacji. Nowy punkt kontrolny zostanie dodany do listy **punktów kontrolnych** .  
  
   Nie można przechwycić punktu kontrolnego, gdy debuger jest dołączony do emulatora.  
  
- Wybierz punkt kontrolny na liście **punktów kontrolnych** , aby wyświetlić informacje dotyczące punktu kontrolnego.  
  
- Wybierz przycisk radiowy w kolumnie **domyślne** , aby zapisać punkt kontrolny jako domyślny punkt kontrolny dla aktywnego emulatora.  
  
- Kliknij przycisk **Przywróć** , aby ponownie uruchomić system operacyjny Windows Phone na emulatorze i załadować wybraną migawkę.  
  
- Kliknij przycisk **Usuń** , aby usunąć migawkę, która nie jest już potrzebna.  
  
  Oryginalny obraz emulatora zawsze pojawia się jako pierwszy element na liście **punktów kontrolnych** i nie można go zmienić ani usunąć. Można jednak wybrać inną migawkę jako domyślny obraz emulatora.  
  
  ![Karta punktów kontrolnych emulatora Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
## <a name="capture-screenshots-in-the-emulator"></a><a name="BKMK_tasks_shot"></a> Przechwytywanie zrzutów ekranu w emulatorze  
 Zrzuty ekranu aplikacji Windows Phone można tworzyć przy użyciu narzędzia zrzutu systemu z okna dodatkowe narzędzia. Narzędzie tworzy pliki PNG, które pasują do rozdzielczości działającego emulatora.  
  
 ![Zrzuty ekranu z emulatora Windows Phone](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Aby utworzyć zrzut ekranu aplikacji przy użyciu wbudowanego narzędzia zrzutu ekranu emulatora  
  
1. Aby zoptymalizować jakość zrzutów ekranu, ustaw poziom powiększenia emulatora na 100%. Im większa jest wartość powiększenia, tym większa jakość zrzutu ekranu.  
  
2. Uruchom aplikację w emulatorze.  
  
3. Na pasku narzędzi emulatora kliknij przycisk Rozwiń, aby otworzyć okno **dodatkowe narzędzia** .  
  
4. Kliknij kartę **zrzut ekranu** .  
  
5. Gdy aplikacja jest gotowa, kliknij przycisk **przechwytywania** .  
  
    Zrzut ekranu pojawi się w obszarze roboczym.  
  
6. Kliknij przycisk **Zapisz** , aby otworzyć okno dialogowe **Zapisywanie jako** .  
  
7. Wybierz lokalizację i **nazwę pliku** , a następnie kliknij przycisk **Zapisz**.  
  
8. Opcjonalnie przejdź do innych stron w aplikacji i Przechwyć dodatkowe zrzuty ekranu.  
  
9. Uruchom emulator z inną rozdzielczością ekranu, aby przechwycić te same zrzuty ekranu pod inną rozdzielczością. Jeśli aplikacja została uruchomiona z debugowaniem, należy zatrzymać debugowanie, zanim będzie można uruchomić ją ponownie w innym emulatorze.  
  
   Przed przechwyceniem zrzutów ekranu, które zostaną przesłane do magazynu Windows Phone, wyłącz liczniki szybkości klatek na ekranie emulatora.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Aby wyłączyć liczniki szybkości klatek w emulatorze przed przechwyceniem zrzutów ekranu  
  
- Określ kompilację wydania w programie Visual Studio. Po określeniu kompilacji wydania Uruchom aplikację, wybierając link **Wdróż _[App Name]_ ** w menu **kompilacja** .  
  
- Alternatywnie można skomentować wiersz kodu w pliku app.xaml.cs lub App. XAML. vb, który ustawia wartość `EnableFrameRateCounter` na `true` .

---
title: Uruchom Windows Store aplikacji w symulatorze | Dokumentacja firmy Microsoft
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 504a63d0f99a1a96d1192a1666d45dafde037253
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775111"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Uruchamianie Windows Store apps w symulatorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Symulatorze programu Visual Studio dla aplikacji Windows Store to aplikacja komputerowa, która symuluje aplikacji Windows Store. Można uruchamiać aplikacje i symulacji typowe touch i obrót zdarzeń na komputerze deweloperskim. Możesz również, rozmiar ekranu fizycznego i rozwiązania, który chcesz emulować i symulowanie właściwości połączenia sieciowego.  
  
 Symulator udostępnia środowisko, w którym można projektować, tworzenia, debugowania i testowania aplikacji Windows Store. Jednak przed opublikowaniem aplikacji Windows Store powinny testować swoją aplikację na rzeczywistego urządzenia.  
  
 Symulatorze programu Visual Studio dla aplikacji Windows Store nie działa w izolowanym środowisku na komputerze lokalnym. W związku z tym błędów występujących w symulatorze, takich jak nieodwracalny błąd całego systemu, może również wpływać na całej maszyny.  
  
 Zobacz [aplikacji Windows Phone uruchamianie w emulatorze](../debugger/run-windows-phone-apps-in-the-emulator.md) informacji Windows Phone.  
  
> [!IMPORTANT]
>  Symulator programu Visual Studio 2015 nie ma przycisku geolokalizacji. Jest to spowodowane symulator systemu Windows 10 nie zawiera geograficzną symulacji. Jeśli zachodzi potrzeba zrobić tego rodzaju symulacji, można użyć symulatora programu Visual Studio 2013 na Windows 8.1 lub starszymi systemami operacyjnymi.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Ustaw symulator jako element docelowy  
 Aby uruchomić aplikację Windows Store w symulatorze, zaznacz **symulator** z listy rozwijanej obok listy **Rozpocznij debugowanie** przycisku w debugerze **standardowa** narzędzi.  
  
 ![Działających w symulatorze](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Wybierz tryb interakcji  
 Możesz wybrać następujące tryby interakcji  
  
-   ![Tryb myszy](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") tryb myszy: Ustawia tryb interakcji gesty myszy. Gesty myszy obejmują kliknięć, kliknie dwukrotnie i drags.  
  
-   ![Przycisk emulacji dotykowej Start](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") emulacji dotykowej rozpoczęcia: Ustawia tryb interakcji na gesty pojedynczej linii papilarnych touch. Finger pojedynczego zdarzenia obejmują, naciskając, przeciągając i szybko przesuwając.  
  
     ![Cel jednym palcem symulatora](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") ikona pojedynczy element docelowy wskazuje lokalizację zdarzenia w symulatorze. Umieść wskaźnik za pomocą myszy.  
  
     ![Jednej linii papilarnych touch docelowej](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") naciśnij przycisk myszy po lewej stronie, aby uaktywnić tryb dotykowy. Na przykład kliknij przycisk, aby symulować tap, lub naciśnij i przytrzymaj klawisz przycisku, przeciągania lub przesunięcia.  
  
## <a name="pinch-and-zoom"></a>Ściśnięcie i powiększenia  
 Ustawia tryb interakcji do ściśnięcie i powiększania gestów dwóch palców.  
  
-   ![Docelowy finger Siimulator dwóch](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  
  
     Ikonę docelową double wskazuje lokalizację, z dwoma palcami na ekranie urządzenia.  
  
    -   Przesuń mysz, aby umieścić ikony na obiekcie na ekranie urządzenia.  
  
    -   Obrót kółkiem myszy do tyłu lub do przodu, aby zmienić symulowane odległość między dwoma palcami przed ściśnięcie lub powiększenia.  
  
-   -   ![Ściśnięcie, powiększania i obracania elementów docelowych](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Naciśnij przycisk z lewej strony i Obróć koło z poprzednimi wersjami (w stronę ty) aby powiększyć (uszczypnięcia).  
  
    -   Naciśnij przycisk z lewej strony i obrót kółkiem myszy do przodu (od siebie), aby pomniejszyć (Powiększenie).  
  
## <a name="object-rotation"></a>Obracanie obiektu  
 **Obróć emulacji dotykowej** przycisk ustawia tryb interakcji gestów obrotu, używając dwóch palców.  
  
-   -   Przesuń mysz, aby umieścić ikony na obiekcie na ekranie urządzenia.  
  
    -   Obrót kółkiem myszy do tyłu lub do przodu, aby zmienić orientację symulowane dwóch palców przed obracania obiektu.  
  
-   -   Naciśnij przycisk z lewej strony i Obróć koło z poprzednimi wersjami (w stronę ty) aby obrócić obiekt przeciwnie do ruchu wskazówek zegara. Obracając kółkiem myszy jedną z ikon dwóch docelowej obraca się wokół drugiego, aby wskazać względne obrotu.  
  
    -   Naciśnij przycisk z lewej strony i obrót kółkiem myszy do przodu (od siebie), aby obrócić obiekt z ruchem wskazówek zegara.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Włączanie lub wyłączanie zawsze najważniejsze tryb  
 Możesz ustawić okno symulatora, aby być zawsze na wierzchu. **Oknie Przełącz** przycisku Włącza lub wyłącza **zawsze na wierzchu** tryb okno symulatora.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Zmiana orientacji urządzenia  
 Możesz przełączać orientacji urządzenia między pionowa i pozioma obracając symulatora w dowolnym kierunku o 90 stopni.  
  
> [!NOTE]
>  Symulator nie przestrzega [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) właściwość projektu. Na przykład, jeśli projekt Ustawia orientację `Landscape`i następnie obracać simulator do orientacji pionowej, symulator wyświetlany obraz będzie również obracać i zmienić jego rozmiaru. Przetestuj te ustawienia na urządzeniu z systemem rzeczywistych.  
  
> [!NOTE]
>  Symulator jest obracania, tak aby jednej krawędzi symulator jest większy niż ekranu, na którym jest wyświetlany na, symulator jest automatycznie dopasowane do ekranu. Symulator nie jest rozmiar oryginalnego rozmiaru obrócenie go ponownie.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Zmienianie rozmiaru ekranu symulowanego i rozwiązania  
 Aby zmienić rozmiar ekranu symulowanego i rozwiązanie, wybierz **zmiana rozdzielczości** znajdujący się na palecie kolorów i wybierz z listy nowy rozmiar i rozwiązanie.  
  
 Rozmiar ekranu i rozwiązanie, które są wyświetlane jako *cali szerokość ekranu, piksel szerokość i wysokość pikseli*. Należy pamiętać, symulowane rozmiar ekranu i rozwiązania. Współrzędne lokalizacji w symulatorze są tłumaczone na współrzędne rozmiaru wybranego urządzenia i rozdzielczości.  
  
> [!NOTE]
>  Może zapisywać skalowanych wersje obrazy mapy bitowej w swojej aplikacji i Windows będzie ładować prawidłowy obraz dla bieżącego skalowania. Aby uzyskać więcej informacji, zobacz [dynamiczny projekt 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Jednakże jeśli zmienisz rozwiązania symulatora, tak że Windows wybierze inny obraz, aby dopasować rozwiązanie, należy zatrzymać i ponownie uruchomić sesję debugowania, aby wyświetlić nowy obraz.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Przechwycić zrzut ekranu aplikacji do przesłania do Windows Store  
 Podczas przesyłania aplikacji do Sklepu Windows, musi zawierać zrzuty ekranu aplikacji.  
  
> [!NOTE]
>  Zrzut ekranu zostanie zapisany w bieżącym rozdzielczości symulatora. Aby zmienić rozwiązanie, wybierz **zmiana rozdzielczości** przycisku.  
  
-   Aby utworzyć zrzuty ekranu aplikacji w symulatorze, wybierz **Przechwyć zrzut ekranu do Schowka** przycisku.  
  
-   Do ustawiania lokalizacji, w którym znajdują się zrzuty ekranu, wybierz **ustawienia zrzutu ekranu** przycisk, a następnie wybierz lokalizację, z menu skrótów.  
  
     ![Menu kontekstowe ustawienia zrzut ekranu](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Symulowanie właściwości połączenia sieciowego  
 Możesz pomóc użytkownikom aplikacji zarządzania kosztami mierzonych połączeń sieciowych, utrzymywanie rozpoznawanie sieci połączenia kosztów ani danych plan zmian stanu i włączając aplikację do używania tych informacji, aby uniknąć ponoszenia dodatkowych kosztów dla mobilnych lub przekroczenie limit transferu określone dane. [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) interfejsów API pozwala reagować na [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) i [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) zdarzenia, które podpisują. Zobacz [Szybki Start: Zarządzanie sieci taryfowej koszt ograniczenia](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Debugowanie lub testowanie kodu uwzględnieniem kosztów sieci, symulator może naśladują właściwości sieci, które są udostępniane za pośrednictwem [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) obiektu zwróconego przez [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)...  
  
 Do symulacji sieci: właściwości:  
  
1. Na pasku narzędzi symulator wybierz **Zmień właściwości sieci** przycisku.  
  
2. Na **ustawić właściwości sieci** okno dialogowe, wybierz opcję **Użyj symulowane właściwości sieci**.  
  
    Wyczyść pole wyboru, aby usunąć symulacji i wróć do właściwości sieci aktualnie połączonych interfejsu.  
  
3. Wprowadź **nazwa profilu** do symulowanej sieci. Firma Microsoft zaleca używanie unikatową nazwę, która służy do identyfikowania symulacji w [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) właściwość [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) obiektu.  
  
4. Wybierz [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) wartość na profil **typ kosztu sieci** listy.  
  
5. Z **Flaga statusu limitu danych** listy, możesz ustawić [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) właściwości lub [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)właściwości na wartość true, lub możesz wybrać  **Poniżej limitu danych** do obu wartości ustawione na wartość false.  
  
6. Z **roamingu stanu** listę, ustaw [roamingu](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) właściwości.  
  
7. Wybierz **ustawiania właściwości** symulowanie właściwości sieci, wyzwalając planu [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) zdarzeń i tło [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) typu  **NetworkStateChange**.  
  
   **Więcej informacji na temat zarządzania połączeniami sieciowymi**  
  
   [Szybki Start: Zarządzanie mierzone ograniczenia kosztów sieci](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Przykładowe informacje o sieci](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analiza zużycia energii](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Sposób reagowania na zdarzenia systemu przy użyciu zadań w tle](http://msdn.microsoft.com/en-us/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Porady: wyzwalanie wstrzymania, wznowienia i zdarzeń w aplikacjach Windows Store w tle](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Przejdź symulator za pomocą klawiatury  
 Możesz przejść na pasku narzędzi w symulatorze, naciskając klawisz **strzałkę CTRL + ALT + Strzałka w górę** można przełączać fokus z okna simulator do paska narzędzi symulatora. Użyj **Strzałka w górę** i **strzałkę w dół** przenoszenia między przyciskami na pasku narzędzi.  
  
 Symulator można zamknąć, naciskając klawisz **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)




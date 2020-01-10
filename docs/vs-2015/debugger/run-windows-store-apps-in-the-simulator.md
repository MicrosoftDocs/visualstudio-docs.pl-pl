---
title: Uruchamianie aplikacji ze sklepu Windows w symulatorze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d072f54dfe351d54e3e115dca7a91bec77fbb9e6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844930"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Uruchamianie aplikacji ze Sklepu Windows w symulatorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Symulator programu Visual Studio dla aplikacji ze sklepu Windows to aplikacja klasyczna, która symuluje aplikację ze sklepu Windows. Można uruchamiać aplikacje i symulować typowe zdarzenia dotknięcia i rotacji na komputerze deweloperskim. Można również wybrać rozmiar i rozdzielczość ekranu fizycznego, który ma być emulowany, i symulować właściwości połączenia sieciowego.  
  
 Symulator zapewnia środowisko, w którym można projektować, opracowywać, debugować i testować aplikacje ze sklepu Windows. Jednak przed opublikowaniem aplikacji w Sklepie Windows należy przetestować aplikację na rzeczywistym urządzeniu.  
  
 Symulator programu Visual Studio dla aplikacji ze sklepu Windows nie działa w izolowanym środowisku na komputerze lokalnym. W związku z tym błędy występujące w symulatorze, takie jak nieodwracalny błąd systemu, mogą również wpływać na cały komputer.  
  
 Aby uzyskać informacje o Windows Phone, zobacz [uruchamianie Windows Phone aplikacje w emulatorze](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
> Symulator programu Visual Studio 2015 nie zawiera przycisku geolokalizacji. Jest to spowodowane tym, że symulator systemu Windows 10 nie obejmuje symulacji geolokalizacji. Jeśli potrzebujesz tego rodzaju symulacji, możesz użyć symulatora Visual Studio 2013 w Windows 8.1 lub wcześniejszych systemach operacyjnych.  
  
## <a name="BKMK_Set_the_simulator_as_the_target"></a>Ustaw symulator jako element docelowy  
 Aby uruchomić aplikację ze sklepu Windows w symulatorze, wybierz z listy rozwijanej pozycję **symulator** , obok przycisku **Rozpocznij debugowanie** na pasku narzędzi **Standardowy** debuger.  
  
 ![Uruchamianie w symulatorze](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="BKMK_Choose_an_interaction_mode"></a>Wybierz tryb interakcji  
 Można wybrać następujące tryby interakcji  
  
- ![Przycisk Tryb myszy](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Tryb myszy: ustawia tryb interakcji na gesty myszy. Gesty myszy obejmują kliknięcia, podwójne kliknięcia i przeciąganie.  
  
- ![Przycisk Rozpocznij emulację dotyku](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Rozpocznij emulację dotykową: ustawia tryb interakcji na dotknięcie gestów pojedynczego palca. Zdarzenia pojedynczego palca obejmują naciskanie, przeciąganie i szybkie przesuwanie.  
  
     ![Docelowa symulator jednego palca](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") Ikona pojedynczego elementu docelowego wskazuje lokalizację zdarzeń w symulatorze. Użyj myszy, aby ustawić wskaźnik.  
  
     ![Jeden element docelowy Touch Finger](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Naciśnij lewym przyciskiem myszy, aby aktywować tryb dotyku. Na przykład kliknij przycisk, aby symulować naciśnięcie klawisza, lub naciśnij i przytrzymaj przycisk podczas przeciągania lub przesunięcia.  
  
## <a name="pinch-and-zoom"></a>Szczypania i zoom  
 Ustawia tryb interakcji na szczypania i powiększanie gestów dwóch palców.  
  
- ![Obiekt docelowy symulatora z dwoma palcami](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - Ikona podwójnego elementu docelowego wskazuje lokalizację dwóch palców na ekranie urządzenia.  

  - Przesuń wskaźnik myszy, aby umieścić ikony na obiekcie na ekranie urządzenia.  

  - Obróć kółko myszy do tyłu lub do przodu, aby zmienić symulowaną odległość dwóch palców przed szczypania lub powiększaniem.  

- ![Szczypania, Powiększ i obróć elementy docelowe](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Naciśnij przycisk z lewej strony i obróć kółko do tyłu (w ten sposób), aby powiększyć (szczypania).  

  - Naciśnij przycisk z lewej strony i obróć kółko myszy do przodu (od użytkownika), aby pomniejszyć (Powiększ).  
  
## <a name="object-rotation"></a>Obrót obiektu  
 Przycisk **Obróć emulacji dotykowej** ustawia tryb interakcji, aby obracał gesty przy użyciu dwóch palców.  
  
- Przesuń wskaźnik myszy, aby umieścić ikony na obiekcie na ekranie urządzenia.  
  
  - Obróć kółko myszy do tyłu lub do przodu, aby zmienić symulowaną orientację dwóch palców przed obróceniem obiektu.  

- Naciśnij przycisk z lewej strony i obróć kółko do tyłu, aby obrócić licznik obiektów w prawo. Podczas obracania kółka myszy jeden z dwóch ikon docelowych jest obracany wokół drugiego, aby wskazać względny rozmiar obrotu.  

  - Naciśnij przycisk z lewej strony i obróć kółko myszy do przodu (od użytkownika), aby obrócić obiekt w prawo.  

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a>Włącz lub Wyłącz zawsze włączony tryb górny  
 Okno symulatora można ustawić zawsze na wierzchu innych okien. Przycisk **przełączania okna** z góry włącza lub wyłącza tryb **zawsze włączony** w oknie symulatora.  
  
## <a name="BKMK_Change_the_device_orientation"></a>Zmiana orientacji urządzenia  
 Orientację urządzenia można zmienić między pionową i poziomą, obracając symulatora o 90 stopni w dowolnym kierunku.  
  
> [!NOTE]
> Symulator nie szanuje właściwości [DisplayProperties. AutoRotationPreferences](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayproperties.autorotationpreferences.aspx) projektu. Na przykład jeśli projekt Ustawia orientację na `Landscape`, a następnie przeniesiesz symulator do orientacji pionowej, obraz ekranu wyświetlania symulatora zostanie również obrócony i zmieniony. Przetestuj te ustawienia na rzeczywistym urządzeniu.  
  
> [!NOTE]
> W przypadku obrócenia symulatora tak, aby jedna krawędź symulatora była większa niż ekran, na którym jest wyświetlana, symulator zostanie automatycznie zmieniony w celu dopasowania do ekranu. Zmiany rozmiaru symulatora nie są zmieniane na oryginalny rozmiar, jeśli zostanie on ponownie obrócony.  
  
## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a>Zmiana rozmiaru i rozdzielczości ekranu symulowanego  
 Aby zmienić rozmiar symulowanego ekranu i rozdzielczość, wybierz przycisk **Zmień rozdzielczość** na palecie, a następnie wybierz nowy rozmiar i rozdzielczość z listy.  
  
 Rozmiar i rozdzielczość ekranu są wyświetlane jako *Szerokość ekranu, Szerokość pikseli (* w pikselach). Należy zauważyć, że zarówno rozmiar ekranu, jak i rozdzielczość są symulowane. Lokalizacje współrzędnych w symulatorze są tłumaczone na współrzędne wybranego rozmiaru i rozdzielczości urządzenia.  
  
> [!NOTE]
> Możesz zapisywać skalowane wersje obrazów mapy bitowej w aplikacji, a system Windows załaduje prawidłowy obraz dla bieżącej skali. Aby uzyskać więcej informacji, zobacz temat [reagowanie na projekt 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Jednakże w przypadku zmiany rozdzielczości symulatora tak, aby system Windows pobierał inny obraz w celu dopasowania go do rozdzielczości, należy zatrzymać i ponownie uruchomić sesję debugowania, aby wyświetlić nowy obraz.  
  
## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Przechwyć zrzut ekranu aplikacji na potrzeby przesłania do sklepu Windows  
 Gdy przesyłasz aplikację do sklepu Windows App Store, musisz dołączyć zrzuty ekranu aplikacji.  
  
> [!NOTE]
> Zrzut ekranu jest zapisywany w bieżącej rozdzielczości symulatora. Aby zmienić rozwiązanie, wybierz przycisk **Zmień rozdzielczość** .  
  
- Aby utworzyć zrzuty ekranu aplikacji z symulatora, wybierz przycisk **Przechwytuj zrzut ekranu do schowka** .  
  
- Aby ustawić lokalizację, w której znajdują się zrzuty ekranu, wybierz przycisk **Ustawienia zrzutu ekranu** i wybierz lokalizację z menu skrótów.  
  
     ![Menu kontekstowe ustawień zrzutu ekranu](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="BKMK_Simulate_network_connection_properties"></a>Symulowanie właściwości połączenia sieciowego  
 Aby ułatwić użytkownikom aplikacji Zarządzanie kosztami mierzonych połączeń sieciowych, należy utrzymać świadomość kosztu połączenia sieciowego lub zmienić stan planu danych i umożliwić aplikacji korzystanie z tych informacji w celu uniknięcia ponoszenia dodatkowych kosztów dla roamingu lub przekroczenia określony limit transferu danych. Interfejsy API [Windows. Networking. Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) umożliwiają reagowanie na zdarzenia [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) i [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) , które są podpisywany. Zobacz [Szybki Start: Zarządzanie naliczanymi ograniczeniami kosztów sieci](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Aby debugować lub testować kod obsługujący koszt sieci, symulator może naśladować właściwości sieci, które są udostępniane za pomocą obiektu [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) zwróconego przez [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)..  
  
 Aby zasymulować właściwości sieci:  
  
1. Na pasku narzędzi symulatora wybierz przycisk **Zmień właściwości sieci** .  
  
2. W oknie dialogowym **Ustawianie właściwości sieci** wybierz opcję **Użyj symulowanych właściwości sieci**.  
  
    Usuń zaznaczenie tego pola wyboru, aby usunąć symulację i wrócić do właściwości sieci aktualnie podłączonego interfejsu.  
  
3. Wprowadź **nazwę profilu** dla symulowanej sieci. Zalecamy użycie unikatowej nazwy, której można użyć do zidentyfikowania symulacji we właściwości [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) obiektu [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) .  
  
4. Wybierz wartość [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) dla profilu z listy **Typ kosztu sieci** .  
  
5. Na liście **Flaga stanu limitu danych** można ustawić właściwość [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) lub właściwość [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)na wartość true lub wybrać opcję **w obszarze limit danych** , aby ustawić obie wartości na wartość false.  
  
6. Na liście **stan roamingu** ustaw właściwość [roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Wybierz pozycję **Ustaw właściwości** , aby symulować właściwości sieci przez wyzwolenie zdarzenia [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) pierwszego planu oraz [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) w tle typu **NetworkStateChange**.  
  
   **Więcej informacji na temat zarządzania połączeniami sieciowymi**  
  
   [Szybki Start: zarządzanie ograniczeniami kosztami sieci mierzonymi](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Przykład informacji o sieci](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analiza zużycia energii](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Reagowanie na zdarzenia systemowe z zadaniami w tle](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Jak wyzwolić wstrzymanie, wznowienie i zdarzenia w tle w aplikacjach ze sklepu Windows](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a>Nawigowanie po symulatorze przy użyciu klawiatury  
 Możesz nawigować na pasku narzędzi symulatora, naciskając **klawisze Ctrl + Alt + Strzałka w górę** , aby przełączyć fokus z okna symulatora na pasek narzędzi symulatora. Użyj **strzałki w górę** i **strzałki w dół** , aby przejść między przyciskami paska narzędzi.  
  
 Symulator można zamknąć przez naciśnięcie **klawiszy Ctrl + Alt + F4**.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie aplikacji w programie Visual Studio](../debugger/run-store-apps-from-visual-studio.md)

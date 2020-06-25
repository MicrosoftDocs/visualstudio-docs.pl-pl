---
title: Uruchom aplikacje platformy UWP w symulatorze | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 1c208e435e63891c71fe47ebd64c5fe1307e0c82
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348144"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Uruchamianie aplikacji platformy UWP w symulatorze

Program Visual Studio symulator for platformy UWP Apps to aplikacja klasyczna, która symuluje aplikację platformy UWP. Zazwyczaj użytkownik chce debugować na komputerze lokalnym, podłączonym urządzeniu lub maszynie zdalnej. Jednak w niektórych scenariuszach warto użyć symulatora programu Visual Studio do emulowania innego rozmiaru i rozdzielczości ekranu fizycznego. Można również symulować typowe zdarzenia dotknięcia i rotacji oraz symulować właściwości połączenia sieciowego.

Symulator zapewnia środowisko, w którym można projektować, opracowywać, debugować i testować aplikacje platformy UWP. Jednak przed opublikowaniem aplikacji w Microsoft Store należy przetestować aplikację na rzeczywistym urządzeniu.

Program Visual Studio symulator for platformy UWP Apps nie działa w izolowanym środowisku na komputerze lokalnym. W związku z tym błędy występujące w symulatorze, takie jak nieodwracalny błąd systemu, mogą również wpływać na cały komputer.

> [!IMPORTANT]
> Symulator programu Visual Studio 2015 nie zawiera przycisku geolokalizacji. Jest to spowodowane tym, że symulator systemu Windows 10 nie obejmuje symulacji geolokalizacji.

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a>Ustaw symulator jako element docelowy

Aby uruchomić aplikację platformy UWP w symulatorze, wybierz z listy rozwijanej pozycję **symulator** , obok przycisku **Rozpocznij debugowanie** na pasku narzędzi **Standardowy** debuger. Ta opcja jest dostępna tylko wtedy, gdy **minimalna wersja platformy docelowej** aplikacji jest mniejsza lub równa systemowi operacyjnemu na komputerze deweloperskim.

![Uruchamianie w symulatorze](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a>Wybierz tryb interakcji

Można wybrać następujące tryby interakcji:

- ![Przycisk Tryb myszy](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Tryb myszy: ustawia tryb interakcji na gesty myszy. Gesty myszy obejmują kliknięcia, podwójne kliknięcia i przeciąganie.

- ![Przycisk Rozpocznij emulację dotyku](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Rozpocznij emulację dotykową: ustawia tryb interakcji na dotknięcie gestów pojedynczego palca. Zdarzenia pojedynczego palca obejmują naciskanie, przeciąganie i szybkie przesuwanie.

   ![Docelowa symulator jednego palca](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Ikona pojedynczego elementu docelowego wskazuje lokalizację zdarzeń w symulatorze. Użyj myszy, aby ustawić wskaźnik.

   ![Jeden element docelowy Touch Finger](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Naciśnij lewym przyciskiem myszy, aby aktywować tryb dotyku. Na przykład kliknij przycisk, aby symulować naciśnięcie klawisza, lub naciśnij i przytrzymaj przycisk podczas przeciągania lub przesunięcia.

## <a name="pinch-and-zoom"></a>Szczypania i zoom

Ustawia tryb interakcji na szczypania i powiększanie gestów dwóch palców.

![Obiekt docelowy symulatora z dwoma palcami](../debugger/media/simulator_twofinger.png)

Ikona podwójnego elementu docelowego wskazuje lokalizację dwóch palców na ekranie urządzenia.

- Przesuń wskaźnik myszy, aby umieścić ikony na obiekcie na ekranie urządzenia.

- Obróć kółko myszy do tyłu lub do przodu, aby zmienić symulowaną odległość dwóch palców przed szczypania lub powiększaniem.

![Szczypania, Powiększ i obróć elementy docelowe](../debugger/media/simulator_twofingerengaged.png)

- Naciśnij przycisk z lewej strony i obróć kółko do tyłu (w ten sposób), aby powiększyć (szczypania).

- Naciśnij przycisk z lewej strony i obróć kółko myszy do przodu (od użytkownika), aby pomniejszyć (Powiększ).

## <a name="object-rotation"></a>Obrót obiektu

Przycisk **Obróć emulacji dotykowej** ustawia tryb interakcji, aby obracał gesty przy użyciu dwóch palców.

- Przesuń wskaźnik myszy, aby umieścić ikony na obiekcie na ekranie urządzenia. Obróć kółko myszy do tyłu lub do przodu, aby zmienić symulowaną orientację dwóch palców przed obróceniem obiektu.

- Naciśnij przycisk z lewej strony i obróć kółko do tyłu, aby obrócić licznik obiektów w prawo. Podczas obracania kółka myszy jeden z dwóch ikon docelowych jest obracany wokół drugiego, aby wskazać względny rozmiar obrotu.

- Naciśnij przycisk z lewej strony i obróć kółko myszy do przodu (od użytkownika), aby obrócić obiekt w prawo.

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a>Włącz lub Wyłącz zawsze włączony tryb górny
 Okno symulatora można ustawić zawsze na wierzchu innych okien. Przycisk **przełączania okna** z góry włącza lub wyłącza tryb **zawsze włączony** w oknie symulatora.

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a>Zmiana orientacji urządzenia
 Orientację urządzenia można zmienić między pionową i poziomą, obracając symulatora o 90 stopni w dowolnym kierunku.

> [!NOTE]
> Symulator nie szanuje właściwości [DisplayProperties. AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) projektu. Na przykład jeśli projekt Ustawia orientację na `Landscape` , a następnie przeniesiesz symulator do orientacji pionowej, obraz ekranu wyświetlania symulatora zostanie również obrócony i zmieniony rozmiar. Przetestuj te ustawienia na rzeczywistym urządzeniu.

> [!NOTE]
> W przypadku obrócenia symulatora tak, aby jedna krawędź symulatora była większa niż ekran, na którym jest wyświetlana, symulator zostanie automatycznie zmieniony w celu dopasowania do ekranu. Zmiany rozmiaru symulatora nie są zmieniane na oryginalny rozmiar, jeśli zostanie on ponownie obrócony.

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a>Zmiana rozmiaru i rozdzielczości ekranu symulowanego
 Aby zmienić rozmiar symulowanego ekranu i rozdzielczość, wybierz przycisk **Zmień rozdzielczość** na palecie, a następnie wybierz nowy rozmiar i rozdzielczość z listy.

 Rozmiar i rozdzielczość ekranu są wyświetlane jako *Szerokość ekranu, Szerokość pikseli (* w pikselach). Należy zauważyć, że zarówno rozmiar ekranu, jak i rozdzielczość są symulowane. Lokalizacje współrzędnych w symulatorze są tłumaczone na wybrane rozmiary i rozdzielczość urządzenia.

> [!NOTE]
> Możesz zapisywać skalowane wersje obrazów mapy bitowej w aplikacji, a system Windows załaduje prawidłowy obraz dla bieżącej skali. Aby uzyskać więcej informacji, zobacz [projektowanie i wprowadzenie do interfejsu użytkownika](/windows/uwp/layout/design-and-ui-intro). Jednakże w przypadku zmiany rozdzielczości symulatora tak, aby system Windows pobierał inny obraz w celu dopasowania go do rozdzielczości, należy zatrzymać i ponownie uruchomić sesję debugowania, aby wyświetlić nowy obraz.

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Przechwyć zrzut ekranu aplikacji na potrzeby przesłania do Microsoft Store
 Po przesłaniu aplikacji do Microsoft Store należy dołączyć zrzuty ekranu aplikacji.

> [!NOTE]
> Zrzut ekranu jest zapisywany w bieżącej rozdzielczości symulatora. Aby zmienić rozwiązanie, wybierz przycisk **Zmień rozdzielczość** .

- Aby utworzyć zrzuty ekranu aplikacji z symulatora, wybierz przycisk **Przechwytuj zrzut ekranu do schowka** .

- Aby ustawić lokalizację, w której znajdują się zrzuty ekranu, wybierz przycisk **Ustawienia zrzutu ekranu** i wybierz lokalizację z menu skrótów.

   ![Menu kontekstowe ustawień zrzutu ekranu](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a>Symulowanie właściwości połączenia sieciowego

Aby ułatwić użytkownikom aplikacji Zarządzanie kosztami taryfowych połączeń sieciowych, należy utrzymać świadomość kosztu połączenia sieciowego lub zmian stanu planu danych oraz umożliwić aplikacji korzystanie z tych informacji w celu uniknięcia ponoszenia dodatkowych kosztów dla roamingu lub przekroczenia określonego limitu transferu danych. Interfejsy API [Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity) umożliwiają reagowanie na zdarzenia [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) i [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) , które są podpisywany. Zobacz [Szybki Start: Zarządzanie naliczanymi ograniczeniami kosztów sieci](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).

Aby debugować lub testować kod obsługujący koszt sieci, symulator może naśladować właściwości sieci, które są udostępniane za pomocą obiektu [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) zwróconego przez [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).

Aby zasymulować właściwości sieci:

1. Na pasku narzędzi symulatora wybierz przycisk **Zmień właściwości sieci** .

2. W oknie dialogowym **Ustawianie właściwości sieci** wybierz opcję **Użyj symulowanych właściwości sieci**.

    Usuń zaznaczenie tego pola wyboru, aby usunąć symulację i wrócić do właściwości sieci aktualnie podłączonego interfejsu.

3. Wprowadź **nazwę profilu** dla symulowanej sieci. Zalecamy użycie unikatowej nazwy, której można użyć do zidentyfikowania symulacji we właściwości [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) obiektu [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) .

4. Wybierz wartość [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) dla profilu z listy **Typ kosztu sieci** .

5. Na liście **Flaga stanu limitu danych** można ustawić właściwość [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) lub właściwość [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) na wartość true lub wybrać opcję **w obszarze limit danych** , aby ustawić obie wartości na wartość false.

6. Na liście **stan roamingu** ustaw właściwość [roaming](/uwp/api/windows.networking.connectivity.connectioncost) .

7. Wybierz pozycję **Ustaw właściwości** , aby symulować właściwości sieci przez wyzwolenie zdarzenia [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) pierwszego planu oraz [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) w tle typu **NetworkStateChange**.

Aby uzyskać więcej informacji na temat zarządzania połączeniami sieciowymi, zobacz:

[Szybki Start: zarządzanie ograniczeniami kosztami sieci mierzonymi](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)

[Przykład informacji o sieci](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Analizowanie zużycia energii](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows. Networking. Connectivity](/uwp/api/windows.networking.connectivity)

[Reagowanie na zdarzenia systemowe z zadaniami w tle](/previous-versions/windows/apps/hh977058(v=win.10))

[Porady: wyzwalanie wstrzymania, wznowienia i zdarzeń w tle w aplikacjach platformy UWP](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a>Nawigowanie po symulatorze przy użyciu klawiatury

Możesz nawigować na pasku narzędzi symulatora, naciskając **klawisze Ctrl + Alt + Strzałka w górę** , aby przełączyć fokus z okna symulatora na pasek narzędzi symulatora. Użyj **strzałki w górę** i **strzałki w dół** , aby przejść między przyciskami paska narzędzi.

Symulator można zamknąć przez naciśnięcie **klawiszy Ctrl + Alt + F4**.

## <a name="see-also"></a>Zobacz też

- [Uruchamianie aplikacji w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)

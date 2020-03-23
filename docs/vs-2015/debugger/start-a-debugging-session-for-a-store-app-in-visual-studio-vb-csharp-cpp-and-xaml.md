---
title: Uruchamianie sesji debugowania dla aplikacji ze Sklepu (VB, C#, C++ i XAML) | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f12d6cde30dec9062dd67a18558bd0571e6fe6b1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302477"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Uruchamianie sesji debugowania dla aplikacji ze Sklepu w programie Visual Studio (VB, C#, C++ i XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone](.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji ze Sklepu napisanych w języku XAML i visual C++, Visual C#lub Visual Basic. Debugowanie aplikacji obejmuje zarówno konfigurowanie sesji debugowania i wybieranie sposobu uruchamiania aplikacji.

> [!NOTE]
> W przypadku aplikacji napisanych w językach JavaScript i HTML zobacz [Uruchamianie sesji debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>W tym temacie
 [Łatwy sposób na rozpoczęcie debugowania](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybieranie opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz miejsce docelowe wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger, którego chcesz użyć](#BKMK_Choose_the_debugger_to_use)

- [(Opcjonalnie) Opóźnienie rozpoczęcia sesji debugowania](#BKMK__Optional__Delay_starting_the_debug_session)

- [(Opcjonalnie) Wyłączanie sprzężenia zwrotnego sieci](#BKMK__Optional__Disable_network_loopbacks)

- [(Opcjonalnie) Zainstaluj ponownie aplikację po uruchomieniu debugowania](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(Opcjonalnie) Wyłączanie wymogu uwierzytelniania w celu uruchomienia zdalnego debugera](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Rozpoczynanie sesji debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale opóźnij uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Uruchamianie zainstalowanej aplikacji w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

- [Dołączanie debugera do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Ustawianie uruchamiania aplikacji w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Dołączanie debugera](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwy sposób na rozpoczęcie debugowania

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Wybierz F5.

   Visual Studio tworzy i uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, un obsługiwane wyjątek występuje lub kończy się aplikacja. Aby uzyskać więcej informacji, zobacz [Nawigacja po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Konfigurowanie sesji debugowania

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu

1. W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. Aby otworzyć stronę właściwości debugowania dla projektu:

    - W przypadku aplikacji Visual C# i Visual Basic wybierz pozycję **Debug .**

         ![C&#35; &#47; strona właściwości debugowania projektu VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - W przypadku aplikacji Visual C++ rozwiń węzeł **Właściwości konfiguracji,** a następnie wybierz polecenie **Debugowanie**.

         ![C&#43;&#43; strona właściwości debugowania aplikacji ze Sklepu Windows](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** wybierz pozycję **Debugowanie** lub **(Aktywne) Debugowanie**.

2. Z listy **Platforma** wybierz platformę docelową do utworzenia. W większości przypadków **każdy procesor (wszystkie** **platformy** w języku Visual C++) jest najlepszym wyborem.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Wybierz miejsce docelowe wdrożenia
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Aplikację ze Sklepu Windows można wdrażać i debugować na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na urządzeniu zdalnym.

- W przypadku aplikacji języka C# i Visual Basic wybierz obiekt docelowy z listy **urządzeń docelowych** na stronie właściwości **Debug** dla projektu.

- W przypadku aplikacji języka C++ wybierz obiekt docelowy z listy **Debuger, aby uruchomić go** na stronie właściwości **Debugowanie:**

  Wybierz jedną z następujących opcji:

|||
|-|-|
|**Maszyna lokalna**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulator**|Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i obracanie urządzenia, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem intranetu lub bezpośrednio połączonym za pomocą kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **Komputer zdalny**należy określić nazwę lub adres IP komputera zdalnego na jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego.

  - W przypadku aplikacji języka C# i Visual Basic wprowadź nazwę lub adres IP w polu **Komputer zdalny.**

  - W przypadku aplikacji języka C++ wprowadź nazwę lub adres IP w polu **Nazwa komputera.**

- Wybierz komputer zdalny z okna dialogowego **Wybieranie połączenia debugera zdalnego.**

   Aby otworzyć okno dialogowe:

  - W przypadku aplikacji języka C# i Visual Basic wybierz pozycję **Znajdź**.

  - W przypadku aplikacji języka C++ wybierz strzałkę w dół w polu **Nazwa komputera** i wybierz polecenie ** \<Znajdź...>**.

    ![Okno dialogowe Wybieranie okna dialogowego Podłączanie zdalnego debugera](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > W oknie dialogowym **Wybieranie zdalnego debugera połączenie** wyświetla maszyny, które znajdują się w lokalnej podseczce i maszyny, które są bezpośrednio połączone z komputerem programu Visual Studio za pomocą kabla Ethernet. Aby określić inny komputer, wprowadź nazwę w polu **Nazwa komputera.**

  ![Dotyczy tylko systemu Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Aplikację ze Sklepu Windows Phone można wdrażać i debugować na urządzeniu lub w jednym z emulatorów telefonu programu Visual Studio. Wybierz urządzenie lub emulator z listy **Urządzenia docelowego.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger, którego chcesz użyć
 Domyślnie program Visual Studio debuguje kod zarządzany w językach C# i aplikacjach Języka Visual Basic.

 W przypadku aplikacji języka C# i Visual Basic można debugować kod zarządzany i natywny kod C/C++ w aplikacji. Zaznacz pole wyboru **Włącz debugowanie kodu niezarządzanego,** aby uwzględnić kod macierzysty w sesji debugowania.

 Domyślnie visual studio debuguje kod macierzysty w aplikacji Języka C++.

 W przypadku aplikacji języka C++ można debugować określone typy kodu, które znajdują się w składnikach aplikacji zamiast lub oprócz kodu macierzystego. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowanie** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **Proces aplikacji:**

|||
|-|-|
|**Tylko skrypt**|Debugowanie kodu JavaScript w aplikacji. Kod zarządzany i kod macierzysty są ignorowane.|
|**Tylko natywny**|Debugowanie natywnego kodu C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Tylko zarządzane**|Debug kodu zarządzanego w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Mieszane (zarządzane i rodzime)**|Debugowanie natywnego kodu C/C++ i kodu zarządzanego w aplikacji. Kod JavaScript jest ignorowany.|
|**Tylko GPU**|Debugowanie natywnego kodu C++, który działa na procesorze graficznym (GPU).|

 ![Dotyczy tylko systemu Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 W przypadku aplikacji ze Sklepu Windows Phone można również wybrać debuger, który ma być używany w procesach w tle, z **procesu zadań W tle**.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcjonalnie) Opóźnienie rozpoczęcia sesji debugowania
 Domyślnie visual studio natychmiast uruchamia aplikację po uruchomieniu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Po wybraniu tej opcji aplikacja jest uruchamiana w debugerze, gdy jest uruchamiana z ekranu startowego lub przez umowę aktywacji lub gdy jest uruchamiana przez inny proces lub metodę. Należy również opóźnić uruchomienie aplikacji, gdy chcesz debugować zadanie w tle, gdy sama aplikacja nie jest uruchomiona.

 Aby opóźnić uruchomienie aplikacji, możesz:

- W przypadku aplikacji Visual C# i Visual Basic wybierz pozycję **Nie uruchamiaj, ale debuguj mój kod po uruchomieniu** na stronie właściwości **Debug.**

- W przypadku aplikacji visual c++ wybierz pozycję **Tak** z listy **Uruchom aplikację** na stronie właściwości **Debugowanie.**

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcjonalnie) Wyłączanie sprzężenia zwrotnego sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacja ze Sklepu Windows zainstalowana w standardowy sposób nie może nawiązywać połączeń sieciowych z urządzeniem, na które jest zainstalowana. Domyślnie wdrożenie programu Visual Studio tworzy zwolnienie z tej reguły dla wdrożonej aplikacji. To zwolnienie umożliwia testowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji do Sklepu Windows należy przetestować aplikację bez zwolnienia.

 Aby usunąć zwolnienie z pętli zwrotnej sieci:

- W przypadku aplikacji Visual C# i Visual Basic wyczyść pole wyboru Zezwalaj na **sprzężenie zwrotne sieci** na stronie właściwości **Debugowania.**

- W przypadku aplikacji visual c++ wybierz pozycję **Nie** z listy Zezwalaj na **sprzężenie zwrotne sieci** na stronie właściwości **Debugowanie.**

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcjonalnie) Zainstaluj ponownie aplikację po uruchomieniu debugowania
 Aby zdiagnozować problemy z instalacją i początkową konfiguracją aplikacji Visual C# lub Visual Basic, wybierz pozycję **Odinstaluj, a następnie ponownie zainstaluj mój pakiet** na stronie właściwości **Debugowania,** aby ponownie utworzyć oryginalną instalację po uruchomieniu debugowania. Ta opcja nie jest dostępna dla projektów języka Visual C++.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcjonalnie) Wyłączanie wymogu uwierzytelniania w celu uruchomienia zdalnego debugera
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Domyślnie należy podać poświadczenia, aby uruchomić debuger zdalny.

> [!IMPORTANT]
> Debuger zdalny można uruchomić w trybie Bez uwierzytelniania, ale ten tryb jest zdecydowanie odradzany. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.

 Aby usunąć wymóg uwierzytelniania:

1. W przypadku aplikacji Visual C# i Visual Basic wyczyść pole wyboru **Użyj uwierzytelniania** na stronie właściwości **debugowania.**

2. W przypadku aplikacji visual c++ wybierz pozycję **Nie** z listy **Wymagaj uwierzytelniania** na stronie właściwości **Debugowanie.**

   [W tym temacie](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Rozpoczynanie sesji debugowania

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)
 Po **wybraniu opcji Rozpocznij debugowanie** (klawiatura: F5) w menu **debugowania** program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, występuje wyjątek lub kończy się aplikacja.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale opóźnij uruchomienie aplikacji
 Można ustawić aplikację do uruchamiania w trybie debugowania, ale uruchomić go za pomocą metody innej niż debuger. Na przykład można debugować uruchomienie aplikacji z menu Start lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące następujące

- Na stronie właściwości **Debugowanie** aplikacji **(Debug** w języku Visual C++)

  - W przypadku aplikacji Visual C# i Visual Basic wybierz pozycję **Nie uruchamiaj, ale debuguj mój kod po jego uruchomieniu**.

  - W przypadku aplikacji visual c++ wybierz pozycję **Tak** z listy **Uruchamianie aplikacji.**

- W menu **Debugowania** wybierz **polecenie Rozpocznij debugowanie** (klawiatura: F5).

- Uruchom aplikację z menu Start, umowy wykonania lub według innej procedury.

  Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja.

  . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [Wyzwalanie zawieszania, wznawiania i zdarzeń w tle dla Sklepu Windows).](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchamianie zainstalowanej aplikacji w debugerze
 Po uruchomieniu debugowania przy użyciu F5 Visual Studio tworzy i wdraża aplikację, ustawia aplikację do uruchamiania w trybie debugowania, a następnie uruchamia ją. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego Debug installed App Package. Ta procedura jest przydatna, gdy trzeba debugować aplikację, która została zainstalowana ze sklepu Windows lub gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może mieć niestandardowy system kompilacji, który nie używa projektów lub rozwiązań programu Visual Studio.

 Aplikację można zainstalować na urządzeniu lokalnym lub na urządzeniu zdalnym.  Możesz uruchomić aplikację natychmiast lub można ustawić ją tak, aby działała w debugerze, gdy jest uruchamiana przez inny proces lub metodę, na przykład z menu Start lub przez umowę aktywacji, Można również ustawić aplikację tak, aby działała w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [Wyzwalanie zawieszania, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Aby ustawić zainstalowaną aplikację do uruchamiania w trybie debugowania, wykonaj tę te te te działania:

> [!NOTE]
> Aplikacja nie może być uruchomiona po uruchomieniu tej procedury.

1. W menu **Debugowanie** wybierz polecenie **Debugowanie zainstalowanego pakietu aplikacji**

2. Wybierz jedną z następujących opcji z listy:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maszyna lokalna**  |                                                                                                                Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulator**    | Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i obracanie urządzenia, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Maszyna zdalna** |                          Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem intranetu lub bezpośrednio połączonym za pomocą kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Wybierz aplikację z listy **Zainstalowane pakiety aplikacji.**

4. Wybierz aparat debugowania do użycia z listy **Debugowania tego typu kodu.**

5. (Opcjonalnie). Wybierz **pozycję Nie uruchamiaj, ale debuguj mój kod, gdy zaczyna** debugować aplikację, gdy jest uruchamiana za pomocą innej metody lub debugować proces w tle.

   Po **kliknięciu przycisku Start**aplikacja zostanie uruchomiona lub zostanie ustawiona na działanie w trybie debugowania.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołączanie debugera do uruchomionej aplikacji
 Aby dołączyć debuger [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] do aplikacji, należy użyć Debuggable Package Manager, aby ustawić aplikację do uruchamiania w trybie debugowania. Debuggable Package Manager jest zainstalowany z visual studio zdalnych narzędzi.

 Dołączanie debugera do aplikacji jest przydatne, gdy trzeba debugować już zainstalowaną aplikację, [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]taką jak aplikacja zainstalowana z pliku . Dołączanie jest wymagane, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może mieć niestandardowy system kompilacji, który nie używa projektów lub rozwiązań programu Visual Studio.

 Dołączanie debugera do aplikacji wymaga następujących kroków:

1. Ustaw aplikację tak, aby działała w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Aplikację można uruchomić na ekranie startowym, umowie wykonawczej lub innej metodzie.

3. Dołącz debuger do uruchomionej aplikacji.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustawianie uruchamiania aplikacji w trybie debugowania

1. Zainstaluj narzędzia zdalne programu Visual Studio na urządzeniu, na którym jest zainstalowana aplikacja. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na ekranie startowym `Debuggable Package Manager` wyszukaj go, a następnie uruchom.

     Zostanie wyświetlone okno programu PowerShell poprawnie skonfigurowane dla polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, która zawiera `Get-AppxPackage` PackageFullName, wpisz w programie PowerShell monit.

4. W programie PowerShell `Enable-AppxDebug` monit wprowadź *PackageFullName* gdzie *PackageFullName* jest PackageFullName identyfikator aplikacji.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Dołączanie debugera
 Aby dołączyć debuger:

1. W menu **Debugowanie** wybierz polecenie **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołączanie do procesu.**

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **Kwalifikator.** Możesz:

   - Wprowadź nazwę w polu **Kwalifikacje.**

   - Wybierz strzałkę w dół w polu **Kwalifikacje,** a następnie wybierz urządzenie z listy urządzeń, do których wcześniej dołączono.

   - Wybierz **pozycję Znajdź,** aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do.**

    Wybierz **pozycję Wybierz,** a następnie wykonaj jedną z następujących czynności:

   - Wybierz **pozycję Automatycznie określaj typ kodu do debugowania**

   - Wybierz **pozycję Debugowanie tych typów kodu,** a następnie wybierz jeden lub więcej typów z listy.

4. Na liście **Dostępne procesy** wybierz proces aplikacji.

5. Wybierz **pozycję Dołącz**.

   Visual Studio dołącza debugera do procesu. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja.

   [W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [Nawigacja sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)

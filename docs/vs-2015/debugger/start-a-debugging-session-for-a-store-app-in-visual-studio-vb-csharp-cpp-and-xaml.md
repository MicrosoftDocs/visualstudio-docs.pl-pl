---
title: Rozpocznij sesję debugowania dla Store app (VB, C#, C++ i XAML) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409703"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Uruchamianie sesji debugowania dla aplikacji Store w programie Visual Studio (VB, C#, C++ i XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji Store w XAML i Visual C++, Visual C# lub Visual Basic. Debugowanie aplikacji obejmuje zarówno Konfigurowanie sesji debugowania, jak i wybierając sposób, aby uruchomić aplikację.

> [!NOTE]
> W przypadku aplikacji pisanych w języku JavaScript i HTML zobacz [Rozpoczynanie sesji debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="BKMK_In_this_topic"></a>W tym temacie
 [Łatwy sposób rozpoczęcia debugowania](#BKMK_The_easy_way_to_start_debugging)

 [Skonfiguruj sesję debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybieranie opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)

- [Obowiązkowe Opóźnienie rozpoczęcia sesji debugowania](#BKMK__Optional__Delay_starting_the_debug_session)

- [Obowiązkowe Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)

- [Obowiązkowe Zainstaluj ponownie aplikację po rozpoczęciu debugowania](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [Obowiązkowe Wyłącz Wymaganie uwierzytelniania, aby uruchomić zdalny debuger](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Rozpocznij sesję debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Uruchamianie zainstalowanej aplikacji w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

- [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Ustawianie uruchamiania aplikacji w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Dołącz debuger](#BKMK_Attach_the_debugger)

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwy sposób rozpoczęcia debugowania

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Wybierz F5.

   Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane do momentu punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi wyjątek un obsłużony, lub zakończenia aplikacji. Aby uzyskać więcej informacji, zobacz [nawigowanie po sesji debugowania ( C#XAML i)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="BKMK_Configure_the_debugging_session"></a>Skonfiguruj sesję debugowania

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu

1. W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. To zrobić, aby otworzyć stronę właściwości debugowania dla projektu:

    - W przypadku C# aplikacji wizualnych i Visual Basic wybierz **Debuguj**.

         ![Strona&#35; &#47; właściwości debugowania projektu języka C VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - W przypadku C++ aplikacji wizualnych rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.

         ![&#43; &#43; Strona właściwości debugowania aplikacji ze sklepu Windows](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="BKMK_Choose_the_build_configuration_options"></a>Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** **Wybierz Debugowanie** lub **(aktywny) Debuguj**.

2. Z listy **platform** Wybierz platformę docelową do skompilowania. W większości przypadków najlepszym wyborem jest **każdy procesor** (**wszystkie platformy** w wizualizacji C++).

### <a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Można wdrożyć i debugowanie aplikacji Windows Store na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na urządzeniu zdalnym.

- W C# przypadku aplikacji i Visual Basic wybierz obiekt docelowy z listy **urządzeń docelowych** na stronie właściwości **debugowania** dla projektu.

- W C++ przypadku aplikacji wybierz element docelowy z listy **debuger do uruchomienia** na stronie właściwości **debugowania** :

  Wybierz jedną z następujących opcji:

|||
|-|-|
|**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Wykorzystaniem**|Debuguj aplikację w symulatorze programu Visual Studio dla aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **maszyna zdalna**Określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego.

  - W C# przypadku aplikacji i Visual Basic wprowadź nazwę lub adres IP w polu **maszyna zdalna** .

  - W C++ przypadku aplikacji wprowadź nazwę lub adres IP w polu **Nazwa komputera** .

- Wybierz maszynę zdalną w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .

   Aby otworzyć okno dialogowe:

  - W C# przypadku aplikacji i Visual Basic wybierz pozycję **Znajdź**.

  - W C++ obszarze Aplikacje wybierz strzałkę w dół w polu **Nazwa komputera** , a następnie wybierz polecenie **\<Znajdź... >** .

    ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > W oknie dialogowym **Wybieranie połączenia debugera zdalnego** są wyświetlane maszyny znajdujące się w lokalnej podsieci i maszynach, które są bezpośrednio połączone z maszyną programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w polu **Nazwa komputera** .

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Można wdrożyć i debugowanie aplikacji Windows Phone Store na urządzeniu lub w jednym z emulatorów phone programu Visual Studio. Wybierz urządzenie lub emulator z listy **urządzeń docelowych** .

### <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia
 Domyślnie program Visual Studio debugować kodu zarządzanego w aplikacjach języka C# i Visual Basic.

 W przypadku aplikacji C# i Visual Basic można debugować zarówno zarządzanego i natywnego kodu C/C++ w aplikacji. Zaznacz pole wyboru **Włącz debugowanie kodu niezarządzanego** , aby uwzględnić kod natywny w sesji debugowania.

 Domyślnie program Visual Studio debuguje kodu macierzystego w aplikacji C++.

 W aplikacjach C++ można debugować określone typy kodu, które znajdują się w części aplikacji zamiast lub oprócz kodu natywnego. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowania** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **procesów aplikacji** :

|||
|-|-|
|**Tylko skrypt**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu są ignorowane.|
|**Tylko natywny**|Debugowanie kodu natywnego języka C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Tylko zarządzane**|Debugowanie kodu zarządzanego w aplikacji. Kod języka JavaScript i kodu natywnego języka C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowany.|
|**Tylko procesor GPU**|Debugowanie kodu natywnego języka C++ jest uruchamiany na jednostka przetwarzania grafiki (GPU).|

 ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 W przypadku aplikacji do sklepu Windows można również wybrać debuger do użycia dla procesów w tle z **procesu zadania w tle**.

### <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>Obowiązkowe Opóźnienie rozpoczęcia sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Po wybraniu tej opcji, aplikacja jest uruchomiona w debugerze po uruchomieniu na ekranie startowym lub umowy o aktywacji, lub gdy jest uruchomiona przez inny proces lub metody. Jeśli chcesz debugować zadanie w tle, gdy aplikacja nie jest uruchomiony, również opóźnić uruchomienie aplikacji.

 Aby opóźnić uruchomienie aplikacji, możesz wykonywać następujące czynności:

- W przypadku C# aplikacji wizualnych i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po rozpoczęciu** na stronie właściwości **debugowania** .

- W przypadku C++ aplikacji wizualnych wybierz pozycję **tak** na liście **uruchamiania aplikacji** na stronie właściwości **debugowania** .

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Obowiązkowe Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacji Windows Store, która jest zainstalowana w sposób standardowy jest niedozwolone wykonywania wywołań sieci do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji Windows Store, należy przetestować aplikację bez zwolnienia.

 Aby usunąć wykluczenie sprzężenie zwrotne sieci:

- W przypadku C# aplikacji wizualnych i Visual Basic wyczyść pole wyboru **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

- W przypadku C++ aplikacji wizualnych wybierz pozycję **nie** z listy **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Obowiązkowe Zainstaluj ponownie aplikację po rozpoczęciu debugowania
 Aby zdiagnozować problemy z instalacją i początkową konfiguracją aplikacji C# wizualizacji lub Visual Basic, wybierz opcję **Odinstaluj, a następnie zainstaluj ponownie pakiet** na stronie właściwości **debugowania** , aby ponownie utworzyć oryginalną instalację po rozpoczęciu debugowania. Ta opcja nie jest dostępna dla projektów Visual C++.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Obowiązkowe Wyłącz Wymaganie uwierzytelniania, aby uruchomić zdalny debuger
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Domyślnie musisz podać poświadczenia, aby uruchomić zdalny debuger.

> [!IMPORTANT]
> Istnieje możliwość uruchomienia zdalnego debugera w trybie bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.

 Aby usunąć wymaganie uwierzytelniania:

1. W przypadku C# aplikacji wizualnych i Visual Basic wyczyść pole wyboru **Użyj uwierzytelniania** na stronie właściwości **debugowania** .

2. W przypadku C++ aplikacji wizualnych wybierz pozycję **nie** z listy **Wymagaj uwierzytelniania** na stronie właściwości **debugowania** .

   [W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Start_the_debugging_session"></a>Rozpocznij sesję debugowania

### <a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)
 Po wybraniu opcji **Rozpocznij debugowanie** (klawiatura: F5) w menu **debugowanie** program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawieszenie wykonywania, wystąpi wyjątek, lub aplikacja kończy się.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji
 Możesz ustawić aplikację, aby uruchomić tryb debugowania, ale początek metody innej niż debugera. Na przykład możesz zechcieć, debugowanie, uruchamianie aplikacji z Start menu lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

- Na stronie właściwości **debugowania** aplikacji (**debugowanie** w wizualizacji C++)

  - W przypadku C# aplikacji wizualnych i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po rozpoczęciu**.

  - W przypadku C++ aplikacji wizualnych wybierz pozycję **tak** na liście **Uruchom aplikację** .

- Wybierz **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

- Rozpocznij tworzenie aplikacji z menu Start, kontrakt wykonywania lub innej procedury.

  Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

  . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchamianie zainstalowanej aplikacji w debugerze
 Po rozpoczęciu debugowania przy użyciu klawisza F5, Visual Studio tworzy aplikacja jest wdrażana, ustawia aplikację do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego pakietu debugowania zainstalowanej aplikacji. Ta procedura jest przydatna, gdy trzeba debugować aplikację, która została zainstalowana ze Sklepu Windows lub, jeśli pliki źródłowe dla aplikacji, lecz nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Aplikację można zainstalować na urządzeniu lokalnym lub można go na urządzeniu zdalnym.  Aplikację można rozpocząć natychmiast, lub można ustawić go do uruchamiania w debugerze, gdy jest uruchomiona przez inny proces lub metody, np. w menu Start lub przez kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Aby ustawić zainstalowanej aplikacji do uruchamiania w trybie debugowania, wykonaj następujące czynności:

> [!NOTE]
> Aplikacja nie może być uruchomiona, po uruchomieniu tej procedury.

1. W menu **debugowanie** wybierz **Debuguj zainstalowany pakiet aplikacji**

2. Z listy, wybierz jedną z następujących opcji:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Komputer lokalny**  |                                                                                                                Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Wykorzystaniem**    | Debuguj aplikację w symulatorze programu Visual Studio dla aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Maszyna zdalna** |                          Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Wybierz aplikację z listy **zainstalowane pakiety aplikacji** .

4. Wybierz aparat debugowania do użycia na liście **Debuguj ten typ kodu** .

5. (Opcjonalnie). Wybierz pozycję **nie uruchamiaj, ale Debuguj mój kod, gdy rozpocznie** debugowanie aplikacji, gdy jest uruchomiona przez inną metodę lub aby debugować proces w tle.

   Po kliknięciu przycisku **Rozpocznij**aplikacja zostanie uruchomiona lub jest uruchomiona w trybie debugowania.

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger do aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Debugowalny Menedżer pakietów jest instalowany z narzędzia zdalne programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne, gdy zachodzi potrzeba debugowania już zainstalowanej aplikacji, takiej jak aplikacja zainstalowana z [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Dołączanie jest wymagany w przypadku, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Dołączanie debugera do aplikacji wymaga wykonania tych kroków:

1. Ustaw aplikację do uruchamiania w trybie debugowania. Jest to niezbędne, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Aplikację można uruchomić z ekranu startowego, kontrakt wykonywania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

#### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustawianie uruchamiania aplikacji w trybie debugowania

1. Na urządzeniu, w którym aplikacja jest zainstalowana, należy zainstalować narzędzia zdalne programu Visual Studio. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na ekranie startowym Wyszukaj `Debuggable Package Manager` a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawierają PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4. W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *PackageFullName* , gdzie *PackageFullName* jest identyfikatorem PackageFullName aplikacji.

#### <a name="BKMK_Attach_the_debugger"></a>Dołącz debuger
 Aby dołączyć debuger:

1. W menu **debugowanie** wybierz **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołącz do procesu** .

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **kwalifikator** . Możesz:

   - Wprowadź nazwę w polu **kwalifikator** .

   - Wybierz strzałkę w dół w polu **kwalifikator** , a następnie wybierz urządzenie z listy urządzeń, które zostały wcześniej dołączone do usługi.

   - Wybierz pozycję **Znajdź** , aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do** .

    Wybierz **pozycję Wybierz** , a następnie wykonaj jedną z następujących czynności:

   - Wybierz opcję **automatycznie Określ typ kodu do debugowania**

   - Wybierz **Debuguj te typy kodu** , a następnie wybierz jeden lub więcej typów z listy.

4. Z listy **dostępne procesy** wybierz proces aplikacji.

5. Wybierz **Dołącz**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

   [W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [nawigowanie po sesji debugowania ( C#XAML i)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)

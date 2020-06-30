---
title: Rozpocznij sesję debugowania dla aplikacji ze sklepu (VB, C#, C++ i XAML) | Microsoft Docs
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
ms.openlocfilehash: bd0a89ac1d96e2d1af829ba04e6e164f8fae7f8f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542184"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Uruchamianie sesji debugowania dla aplikacji ze Sklepu w programie Visual Studio (VB, C#, C++ i XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji ze sklepu pisanych w języku XAML i Visual C++, Visual C# lub Visual Basic. Debugowanie aplikacji obejmuje zarówno skonfigurowanie sesji debugowania, jak i wybranie sposobu uruchomienia aplikacji.

> [!NOTE]
> W przypadku aplikacji pisanych w języku JavaScript i HTML zobacz [Rozpoczynanie sesji debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>W tym temacie
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

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwy sposób rozpoczęcia debugowania

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Wybierz klawisz F5.

   Program Visual Studio kompiluje i uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręczne wstrzymanie wykonywania, wystąpił wyjątek nieobsłużony lub aplikacja zostanie zakończona. Aby uzyskać więcej informacji, zobacz [nawigowanie po sesji debugowania (XAML i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Skonfiguruj sesję debugowania

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu

1. W Eksplorator rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. Zrób to, aby otworzyć stronę właściwości debugowania dla projektu:

    - W przypadku aplikacji Visual C# i Visual Basic wybierz pozycję **Debuguj**.

         ![Strona właściwości debugowania projektu języka C&#35; &#47; VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - W przypadku aplikacji Visual C++ rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.

         ![Strona właściwości debugowania aplikacji ze sklepu Windows C&#43;&#43; ](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** **Wybierz Debugowanie** lub **(aktywny) Debuguj**.

2. Z listy **platform** Wybierz platformę docelową do skompilowania. W większości przypadków najlepszym wyborem jest **każdy procesor** (**wszystkie platformy** w Visual C++).

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Aplikację ze sklepu Windows można wdrożyć i debugować na maszynie programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na urządzeniu zdalnym.

- W przypadku aplikacji C# i Visual Basic wybierz obiekt docelowy z listy **urządzeń docelowych** na stronie właściwości **debugowania** dla projektu.

- W przypadku aplikacji C++ wybierz element docelowy z listy **debuger do uruchomienia** na stronie właściwości **debugowania** :

  Wybierz jedną z następujących opcji:

|Opcja|Opis|
|-|-|
|**Maszyna lokalna**|Debuguj aplikację w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulator**|Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i rotacja urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu połączonym z maszyną lokalną za pośrednictwem intranetu lub połączonego bezpośrednio przy użyciu kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **maszyna zdalna**Określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego.

  - W przypadku aplikacji C# i Visual Basic wprowadź nazwę lub adres IP w polu **maszyna zdalna** .

  - W przypadku aplikacji C++ wprowadź nazwę lub adres IP w polu **Nazwa komputera** .

- Wybierz maszynę zdalną w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .

   Aby otworzyć okno dialogowe:

  - W przypadku aplikacji C# i Visual Basic wybierz pozycję **Znajdź**.

  - W przypadku aplikacji C++ wybierz strzałkę w dół w polu **Nazwa komputera** , a następnie wybierz polecenie **\<Locate...>** .

    ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > W oknie dialogowym **Wybieranie połączenia debugera zdalnego** są wyświetlane maszyny znajdujące się w lokalnej podsieci i maszynach, które są bezpośrednio połączone z maszyną programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w polu **Nazwa komputera** .

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Możesz wdrażać i debugować aplikację ze sklepu Windows Phone na urządzeniu lub w jednym z emulatorów telefonu programu Visual Studio. Wybierz urządzenie lub emulator z listy **urządzeń docelowych** .

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia
 Domyślnie program Visual Studio debuguje kod zarządzany w aplikacjach C# i Visual Basic.

 W przypadku aplikacji C# i Visual Basic można wybrać Debugowanie kodu zarządzanego i natywnego języka C/C++ w aplikacji. Zaznacz pole wyboru **Włącz debugowanie kodu niezarządzanego** , aby uwzględnić kod natywny w sesji debugowania.

 Domyślnie program Visual Studio debuguje kod natywny w aplikacji C++.

 W przypadku aplikacji C++ można wybrać debugowanie określonych typów kodu, które znajdują się w składnikach aplikacji zamiast lub oprócz kodu natywnego. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowania** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **procesów aplikacji** :

|Typ debugera|Opis|
|-|-|
|**Tylko skrypt**|Debuguj kod JavaScript w aplikacji. Kod zarządzany i kod natywny zostały zignorowane.|
|**Tylko natywny**|Debuguj natywny kod C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Tylko zarządzane**|Debuguj kod zarządzany w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debuguj natywny kod C/C++ i kod zarządzany w aplikacji. Kod JavaScript jest ignorowany.|
|**Tylko procesor GPU**|Debuguj natywny kod języka C++, który działa w procesorze GPU.|

 ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 W przypadku aplikacji do sklepu Windows można również wybrać debuger do użycia dla procesów w tle z **procesu zadania w tle**.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>Obowiązkowe Opóźnienie rozpoczęcia sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Możesz również rozpocząć sesję debugowania, ale opóźnić początek aplikacji. Po wybraniu tej opcji aplikacja zostanie uruchomiona w debugerze, gdy zostanie uruchomiony z ekranu startowego lub przez kontrakt aktywacji lub gdy zostanie uruchomiona przez inny proces lub metodę. Możesz również opóźnić początek aplikacji, gdy chcesz debugować zadanie w tle, gdy sama aplikacja nie jest uruchomiona.

 Aby opóźnić uruchamianie aplikacji, możesz:

- W przypadku aplikacji Visual C# i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po uruchomieniu** na stronie właściwości **debugowania** .

- W przypadku aplikacji Visual C++ wybierz pozycję **tak** na liście **uruchamiania aplikacji** na stronie właściwości **debugowania** .

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Obowiązkowe Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacja ze sklepu Windows, która jest zainstalowana w standardowym sposobie, nie może wykonywać wywołań sieciowych na urządzeniu, na którym jest zainstalowana. Domyślnie wdrożenie programu Visual Studio tworzy wykluczenie z tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia testowanie procedur komunikacji na pojedynczym komputerze. Przed przesłaniem aplikacji do sklepu Windows należy przetestować aplikację bez wykluczania.

 Aby usunąć wyłączenie sprzężenia zwrotnego sieci:

- W przypadku aplikacji Visual C# i Visual Basic wyczyść pole wyboru **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

- W przypadku aplikacji Visual C++ wybierz pozycję **nie** z listy **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Obowiązkowe Zainstaluj ponownie aplikację po rozpoczęciu debugowania
 Aby zdiagnozować problemy z instalacją i początkową konfiguracją aplikacji Visual C# lub Visual Basic, wybierz opcję **Odinstaluj, a następnie zainstaluj ponownie pakiet** na stronie właściwości **debugowania** , aby ponownie utworzyć oryginalną instalację po rozpoczęciu debugowania. Ta opcja nie jest dostępna dla projektów Visual C++.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Obowiązkowe Wyłącz Wymaganie uwierzytelniania, aby uruchomić zdalny debuger
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Domyślnie należy podać poświadczenia, aby uruchomić zdalny debuger.

> [!IMPORTANT]
> Można uruchomić zdalny debuger w trybie bez uwierzytelniania, ale nie jest to zdecydowanie zalecane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.

 Aby usunąć wymaganie uwierzytelniania:

1. W przypadku aplikacji Visual C# i Visual Basic wyczyść pole wyboru **Użyj uwierzytelniania** na stronie właściwości **debugowania** .

2. W przypadku aplikacji Visual C++ wybierz pozycję **nie** z listy **Wymagaj uwierzytelniania** na stronie właściwości **debugowania** .

   [W tym temacie](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Rozpocznij sesję debugowania

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)
 Po wybraniu opcji **Rozpocznij debugowanie** (klawiatura: F5) w menu **debugowanie** program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy zostanie osiągnięty punkt przerwania, zostanie wykonane ręczne wstrzymanie wykonywania, wystąpił wyjątek lub aplikacja zostanie zakończona.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji
 Można ustawić uruchamianie aplikacji w trybie debugowania, ale uruchomić ją za pomocą metody innej niż debuger. Na przykład może być konieczne debugowanie uruchamiania aplikacji z menu Start lub debugowanie procesu w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

- Na stronie właściwości **debugowania** aplikacji (**debugowanie** w Visual C++)

  - W przypadku aplikacji Visual C# i Visual Basic, wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod podczas uruchamiania**.

  - W przypadku aplikacji Visual C++ wybierz pozycję **tak** na liście **Uruchom aplikację** .

- Wybierz **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

- Uruchom aplikację z menu Start, kontraktu wykonywania lub przez inną procedurę.

  Aplikacja jest uruchamiana w trybie debugowania. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

  . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchamianie zainstalowanej aplikacji w debugerze
 Po rozpoczęciu debugowania za pomocą klawisza F5 program Visual Studio kompiluje i wdraża aplikację, ustawia aplikację do uruchamiania w trybie debugowania, a następnie uruchamia ją. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego Debuguj zainstalowany pakiet aplikacji. Ta procedura jest przydatna, gdy trzeba debugować aplikację, która została zainstalowana ze sklepu Windows, lub jeśli masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może istnieć niestandardowy system kompilacji, który nie używa projektów ani rozwiązań programu Visual Studio.

 Aplikację można zainstalować na urządzeniu lokalnym lub na urządzeniu zdalnym.  Możesz uruchomić aplikację natychmiast lub ustawić ją do uruchomienia w debugerze, gdy zostanie uruchomiony przez inny proces lub metodę, na przykład z menu Start lub z kontraktu aktywacji, można również ustawić aplikację do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Aby ustawić uruchomioną aplikację w trybie debugowania, wykonaj następujące czynności:

> [!NOTE]
> Po uruchomieniu tej procedury aplikacja nie może być uruchomiona.

1. W menu **debugowanie** wybierz **Debuguj zainstalowany pakiet aplikacji**

2. Wybierz jedną z następujących opcji z listy:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maszyna lokalna**  |                                                                                                                Debuguj aplikację w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulator**    | Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i rotacja urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Maszyna zdalna** |                          Debuguj aplikację na urządzeniu połączonym z maszyną lokalną za pośrednictwem intranetu lub połączonego bezpośrednio przy użyciu kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Wybierz aplikację z listy **zainstalowane pakiety aplikacji** .

4. Wybierz aparat debugowania do użycia na liście **Debuguj ten typ kodu** .

5. (Opcjonalnie). Wybierz pozycję **nie uruchamiaj, ale Debuguj mój kod, gdy rozpocznie** debugowanie aplikacji, gdy jest uruchomiona przez inną metodę lub aby debugować proces w tle.

   Po kliknięciu przycisku **Rozpocznij**aplikacja zostanie uruchomiona lub jest uruchomiona w trybie debugowania.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Menedżer pakietów możliwością debugowania jest instalowany z narzędziami zdalnymi programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne, gdy zachodzi potrzeba debugowania już zainstalowanej aplikacji, takiej jak aplikacja zainstalowana z programu [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] . Dołączanie jest wymagane, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może istnieć niestandardowy system kompilacji, który nie używa projektów ani rozwiązań programu Visual Studio.

 Dołączanie debugera do aplikacji wymaga wykonania następujących czynności:

1. Ustaw aplikację do uruchamiania w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Możesz uruchomić aplikację z ekranu startowego, kontraktu wykonywania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustawianie uruchamiania aplikacji w trybie debugowania

1. Zainstaluj narzędzia zdalne programu Visual Studio na urządzeniu, na którym zainstalowano aplikację. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Na ekranie startowym Wyszukaj, `Debuggable Package Manager` a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell prawidłowo skonfigurowane dla polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawierają PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4. W wierszu polecenia programu PowerShell wpisz `Enable-AppxDebug` *PackageFullName* , gdzie *PackageFullName* jest identyfikatorem PackageFullName aplikacji.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Dołącz debuger
 Aby dołączyć debuger:

1. W menu **debugowanie** wybierz **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołącz do procesu** .

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **kwalifikator** . Można:

   - Wprowadź nazwę w polu **kwalifikator** .

   - Wybierz strzałkę w dół w polu **kwalifikator** , a następnie wybierz urządzenie z listy urządzeń, które zostały wcześniej dołączone do usługi.

   - Wybierz pozycję **Znajdź** , aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do** .

    Wybierz **pozycję Wybierz** , a następnie wykonaj jedną z następujących czynności:

   - Wybierz opcję **automatycznie Określ typ kodu do debugowania**

   - Wybierz **Debuguj te typy kodu** , a następnie wybierz jeden lub więcej typów z listy.

4. Z listy **dostępne procesy** wybierz proces aplikacji.

5. Wybierz **Dołącz**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

   [W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [nawigowanie po sesji debugowania (XAML i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)

---
title: Rozpocznij sesję debugowania dla aplikacji platformy UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: how-to
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b11ea380f9012bc64f577d2da54a4a88b9f94daf
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348239"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Rozpoczynanie sesji debugowania aplikacji platformy UWP

W tym artykule opisano sposób uruchamiania sesji debugowania programu Visual Studio dla aplikacji platforma uniwersalna systemu Windows (platformy UWP). Aplikacje platformy UWP można pisać w językach XAML i C++, XAML i C#/Visual Basic. Aby rozpocząć debugowanie aplikacji platformy UWP, skonfiguruj sesję debugowania i wybierz sposób uruchomienia aplikacji.

::: moniker range=">=vs-2019"
> [!NOTE]
> Począwszy od programu Visual Studio 2019, platformy UWP aplikacje dla języka HTML i języka JavaScript nie są już obsługiwane.
::: moniker-end
::: moniker range="vs-2017"
W programie Visual Studio 2017 większość poleceń i opcji przedstawionych w tym artykule ma również zastosowanie do aplikacji platformy UWP dla języka HTML i języka JavaScript. W przypadku, gdy polecenia są różne w aplikacjach zarządzanych i C++, aplikacje JavaScript zwykle są takie same jak polecenia dla aplikacji C++ platformy UWP.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Rozpocznij debugowanie na pasku narzędzi programu Visual Studio

Najprostszym sposobem konfigurowania i uruchamiania debugowania jest ze standardowego paska narzędzi programu Visual Studio.

![Debuguj z paska narzędzi](../debugger/media/vsrun_select_target_device.png)

1. Na liście rozwijanej **Konfiguracja** na pasku narzędzi **Standardowy** wybierz pozycję **Debuguj**.

1. Z listy rozwijanej **platforma** Wybierz platformę docelową do skompilowania.

1. Z listy rozwijanej obok zielonej strzałki wybierz element docelowy debugowania. Można wybrać maszynę lokalną, urządzenie połączone bezpośrednio, lokalny symulator programu Visual Studio, urządzenie zdalne lub emulator.

1. Aby rozpocząć debugowanie, wybierz zieloną strzałkę **startową** na pasku narzędzi lub wybierz polecenie **Debuguj**  >  **Rozpocznij debugowanie**lub naciśnij klawisz **F5**.

   Program Visual Studio kompiluje i uruchamia aplikację z dołączonym debugerem.

Debugowanie jest kontynuowane do momentu, gdy zostanie osiągnięty punkt przerwania, zostanie ręcznie zawieszone wykonanie, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a>Opcje elementu docelowego wdrożenia

Możesz ustawić cel debugowania na pasku narzędzi programu Visual Studio lub na stronie właściwości debugowania projektu. Wybierz jedną z następujących opcji:

|||
|-|-|
|**Maszyna lokalna**|Debuguj aplikację w bieżącej sesji na komputerze lokalnym.|
|**Simulator**|Debuguj aplikację w symulatorze programu Visual Studio dla aplikacji platformy UWP. Symulator to okno pulpitu, które symuluje funkcje urządzenia, takie jak gesty dotykowe i rotacja urządzeń, które mogą nie istnieć na komputerze lokalnym. Opcja symulator jest dostępna tylko wtedy, gdy **minimalna wersja platformy docelowej** aplikacji jest mniejsza lub równa systemowi operacyjnemu na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem sieci lub kabla Ethernet. Remote Tools for Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Urządzenie**|Debuguj aplikację na urządzeniu podłączonym do portu USB. Urządzenie musi być odblokowane przez dewelopera i mieć odblokowany ekran.|
|**Emulator urządzenia przenośnego**|Wykonaj rozruch emulatora określonego w polu Nazwa emulatora, wdróż aplikację i Rozpocznij debugowanie. Emulatory są dostępne tylko na maszynach z obsługą funkcji Hyper-V.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Konfigurowanie debugowania na stronie właściwości projektu

Aby skonfigurować dodatkowe opcje debugowania, użyj strony właściwości debugowania projektu.

**Aby otworzyć właściwości debugowania:**

1. W **Eksplorator rozwiązań**wybierz projekt, a następnie wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. Po lewej stronie okienka **Właściwości** :

   - W przypadku aplikacji C# i Visual Basic wybierz pozycję **Debuguj**.

     ![Strona właściwości debugowania projektu C# i Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)

   - W przypadku aplikacji C++ wybierz pozycję Debugowanie **Właściwości konfiguracji**  >  **Debugging**.

     ![Strona właściwości debugowania aplikacji C++ platformy UWP](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia

W przypadku aplikacji C# i Visual Basic program Visual Studio domyślnie debuguje kod zarządzany. Możesz wybrać opcję debugowania innych lub dodatkowych typów kodu. Możesz również ustawić wartości **typu debugera** dla wszystkich zadań w tle, które są częścią projektu.

W aplikacjach C++ Program Visual Studio domyślnie Debuguj kod natywny. Można zdecydować się na debugowanie określonych typów kodu zamiast lub oprócz kodu natywnego.

**Aby określić typy kodu do debugowania:**

- W przypadku aplikacji C# i Visual Basic wybierz jeden z następujących debugerów z listy rozwijanej Typ **aplikacji** i **Typ procesu w tle** w obszarze **Typ debugera** na stronie właściwości **debugowania** .

- W przypadku aplikacji C++ wybierz jeden z następujących debugerów z listy rozwijanej **Typ debugera** na stronie właściwości **debugowania** .

|||
|-|-|
|**Tylko zarządzane**|Debuguj kod zarządzany w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Tylko natywny**|Debuguj natywny kod C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debuguj natywny kod C/C++ i kod zarządzany w aplikacji. Kod JavaScript jest ignorowany. W projektach w języku C++ ta opcja jest nazywana **zarządzanym i natywnym**.|
|**Skrypt**|Debuguj kod JavaScript w aplikacji. Kod zarządzany i kod natywny zostały zignorowane.|
|**Natywny ze skryptem**|Debuguj natywny kod C/C++ i kod JavaScript w aplikacji. Kod zarządzany jest ignorowany. Dostępne tylko w projektach C++ lub w tle.|
|**Tylko procesor GPU (C++ AMP)**|Debuguj natywny kod języka C++, który działa w procesorze GPU. Dostępne tylko w projektach C++.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Wyłącz sprzężenia zwrotne sieci (opcjonalnie)

 W przypadku zabezpieczeń aplikacja platformy UWP zainstalowana w standardowym sposobie nie może nawiązywać połączeń sieciowych z urządzeniem, na którym jest ono zainstalowane. Program Visual Studio domyślnie wyłącza wdrożone aplikacje z tej reguły, dzięki czemu można testować procedury komunikacji na pojedynczym komputerze. Przed udostępnieniem aplikacji należy przetestować aplikację bez wykluczania.

**Aby usunąć wyłączenie sprzężenia zwrotnego sieci:**

- W przypadku aplikacji C# i Visual Basic Usuń zaznaczenie pola wyboru **Zezwalaj na sprzężenie zwrotne sieci lokalnej** w obszarze **Opcje uruchamiania** na stronie właściwości **debugowania** .

- W przypadku aplikacji C++ wybierz pozycję **nie** z listy rozwijanej **Zezwalaj na sprzężenie zwrotne sieci lokalnej** na stronie właściwości **debugowania** .

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Zainstaluj ponownie aplikację po rozpoczęciu debugowania (opcjonalnie)
 Aby zdiagnozować problemy z instalacją przy użyciu aplikacji C# lub Visual Basic, wybierz opcję **Odinstaluj, a następnie zainstaluj ponownie pakiet** na stronie właściwości **debugowania** . Ta opcja powoduje odtworzenie oryginalnej instalacji po rozpoczęciu debugowania. Ta opcja jest niedostępna dla projektów C++.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Ustawianie opcji uwierzytelniania dla zdalnego debugowania

Domyślnie należy podać poświadczenia systemu Windows w celu uruchomienia debugera zdalnego po wybraniu **maszyny zdalnej** jako celu wdrożenia. Istnieje możliwość zmiany wymagania dotyczącego uwierzytelniania.

Tryb uwierzytelniania **uniwersalnego (nieszyfrowanego protokołu)** jest przeznaczony dla urządzeń IoT, Xbox i HoloLens oraz do aktualizacji lub nowszych komputerów z systemem Windows 10 dla twórców.

**Aby zmienić metodę uwierzytelniania:**

- W przypadku aplikacji C# i Visual Basic, na stronie właściwości **debugowania** wybierz pozycję **maszyna zdalna** jako **urządzenie docelowe**. Następnie wybierz pozycję **Brak** lub **uniwersalny (niezaszyfrowany protokół)** w **trybie uwierzytelniania**.

- W przypadku aplikacji C++ wybierz pozycję **maszyna zdalna** w obszarze **debuger, aby uruchomić** program na stronie właściwości **debugowania** . Następnie wybierz opcję **Brak uwierzytelniania** lub **uniwersalnego (nieszyfrowanego protokołu)** dla **typu uwierzytelniania**.

> [!CAUTION]
> Po uruchomieniu zdalnego debugera w trybie **Brak** lub **uniwersalne (nieszyfrowane protokoły)** nie ma zabezpieczeń sieci. Wybierz te tryby tylko dla zaufanych sieci, na których pewno nie są narażone złośliwe lub zagrożone dane.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a>Opcje uruchamiania debugowania

Po wybraniu opcji **Debuguj**  >  **Rozpocznij debugowanie** lub naciśnij klawisz **F5**program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie, ale Opóźnij uruchomienie aplikacji

Domyślnie program Visual Studio uruchamia aplikację natychmiast po rozpoczęciu debugowania. Możesz również ustawić aplikację do uruchamiania w trybie debugowania, ale uruchomić aplikację poza debugerem. Na przykład możesz chcieć debugować uruchamianie aplikacji z menu **Start** systemu Windows lub debugować proces w tle w aplikacji. W przypadku wybrania tej opcji aplikacja zostanie uruchomiona w debugerze przy uruchamianiu.

**Aby wyłączyć automatyczne uruchamianie aplikacji:**

- W przypadku aplikacji C# i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po uruchomieniu** w obszarze **Opcje uruchamiania** na stronie właściwości **debugowania** .

- W przypadku aplikacji C++ wybierz pozycję **nie** na liście rozwijanej **uruchamiania aplikacji** na stronie właściwości **debugowania** .

Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla aplikacji platformy UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Debuguj zainstalowaną lub uruchomioną aplikację platformy UWP

W celu debugowania aplikacji platformy UWP, która jest już zainstalowana lub uruchomiona na urządzeniu lokalnym lub zdalnym, można użyć **debugowania zainstalowanego pakietu aplikacji** . Aplikacja mogła zostać zainstalowana z poziomu Microsoft Store lub nie jest projektem programu Visual Studio. Na przykład aplikacja może mieć niestandardowy system kompilacji, który nie używa programu Visual Studio.

Możesz natychmiast uruchomić zainstalowaną aplikację lub można ją skonfigurować do uruchamiania w debugerze po uruchomieniu z inną metodą. Aby uzyskać więcej informacji, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla aplikacji platformy UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Aby uruchomić zainstalowaną lub uruchomioną aplikację platformy UWP w debugerze, wybierz pozycję **Debuguj**  >  **inne elementy docelowe debugowania**  >  **Debuguj zainstalowany pakiet aplikacji**. Aby uzyskać więcej instrukcji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji systemu Windows 8. x

Aby dołączyć debuger do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Menedżer pakietów możliwością debugowania jest instalowany z Remote Tools for Visual Studio.

1. Zainstaluj Remote Tools for Visual Studio na urządzeniu, na którym zainstalowano aplikację. Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzi zdalnych](../debugger/remote-debugging.md).

1. Na ekranie **startowym** systemu Windows wyszukaj i uruchom **Menedżera pakietów możliwością debugowania**.

   Zostanie wyświetlone okno programu PowerShell prawidłowo skonfigurowane dla polecenia cmdlet AppxDebug.

1. Określ identyfikator PackageFullName aplikacji.

   1. Aby wyświetlić listę zawierającą PackageFullName wszystkich aplikacji, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

   1. W wierszu polecenia programu PowerShell wpisz `Enable-AppxDebug <PackageFullName>` , gdzie \<PackageFullName> jest PackageFullName identyfikator aplikacji.

1. Wybierz pozycję **Debuguj**  >  **Dołącz do procesu**.

1. W oknie dialogowym **Dołącz do procesu** Określ urządzenie zdalne w polu **cel połączenia** .

   Możesz wprowadzić nazwę urządzenia, wybrać ją z listy rozwijanej w polu **cel połączenia** lub wybrać opcję **Znajdź** , aby znaleźć urządzenie w oknie dialogowym **połączenia zdalne** .

1. Aby określić typ kodu, który ma być debugowany, obok pola **Dołącz do** wybierz pozycję **Wybierz**.

1. W oknie dialogowym **Wybierz typ kodu** wybierz jedną z opcji:
   - **Automatycznie Określ typ kodu do debugowania**lub
   - **Debuguj te typy kodu**, a następnie wybierz jeden lub więcej typów kodu z listy.

1. Z listy **dostępne procesy** wybierz proces aplikacji do debugowania.

1. Wybierz pozycję **Dołącz**.

 Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

::: moniker range="vs-2017"
> [!NOTE]
> Aplikacje JavaScript działają w wystąpieniu procesu *wwahost.exe* . Jeśli więcej niż jedna aplikacja JavaScript jest uruchomiona, należy znać identyfikator procesu *wwahost.exe* aplikacji, aby dołączyć do niego.
>
> Najprostszym sposobem dołączenia do aplikacji JavaScript jest zamknięcie wszystkich innych aplikacji JavaScript. Można też zauważyć identyfikatory PID uruchomionych *wwahost.exe* procesów w Menedżerze zadań systemu Windows przed rozpoczęciem aplikacji. Po uruchomieniu aplikacji jego identyfikator PID *wwahost.exe* będzie różnić się od podanych wcześniej.
::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Debugowanie aplikacji w programie Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)
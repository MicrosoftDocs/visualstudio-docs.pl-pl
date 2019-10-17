---
title: Rozpocznij sesję debugowania dla aplikacji platformy UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
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
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436004"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Rozpoczynanie sesji debugowania aplikacji platformy UWP

W tym artykule opisano sposób uruchamiania sesji debugowania programu Visual Studio dla aplikacji platforma uniwersalna systemu Windows (platformy UWP). Aplikacje platformy UWP można pisać w języku XAML C++, w języku XAML C#i w warstwie Podstawowa/Visual. Aby rozpocząć debugowanie aplikacji platformy UWP, skonfiguruj sesję debugowania i wybierz sposób uruchomienia aplikacji.

::: moniker range=">=vs-2019"
> [!NOTE]
> Począwszy od programu Visual Studio 2019, platformy UWP aplikacje dla języka HTML i języka JavaScript nie są już obsługiwane.
::: moniker-end
::: moniker range="vs-2017"
W programie Visual Studio 2017 większość poleceń i opcji przedstawionych w tym artykule ma również zastosowanie do aplikacji platformy UWP dla języka HTML i języka JavaScript. W przypadku, gdy polecenia są różne C++ w aplikacjach zarządzanych i aplikacji, aplikacje JavaScript zwykle są takie C++ same jak polecenia dla aplikacji platformy UWP.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Rozpocznij debugowanie na pasku narzędzi programu Visual Studio

Najprostszym sposobem konfigurowania i uruchamiania debugowania jest ze standardowego paska narzędzi programu Visual Studio.

![Debuguj z paska narzędzi](../debugger/media/vsrun_select_target_device.png)

1. Na liście rozwijanej **Konfiguracja** na pasku narzędzi **Standardowy** wybierz pozycję **Debuguj**.

1. Z listy rozwijanej **platforma** Wybierz platformę docelową do skompilowania.

1. Z listy rozwijanej obok zielonej strzałki wybierz element docelowy debugowania. Można wybrać maszynę lokalną, urządzenie połączone bezpośrednio, lokalny symulator programu Visual Studio, urządzenie zdalne lub emulator.

1. Aby rozpocząć debugowanie, wybierz zieloną strzałkę **startową** na pasku narzędzi lub wybierz kolejno opcje **Debuguj** > **Rozpocznij debugowanie**lub naciśnij klawisz **F5**.

   Program Visual Studio kompiluje i uruchamia aplikację z dołączonym debugerem.

Debugowanie jest kontynuowane do momentu, gdy zostanie osiągnięty punkt przerwania, zostanie ręcznie zawieszone wykonanie, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

### <a name="BKMK_Choose_the_deployment_target"></a>Opcje elementu docelowego wdrożenia

Możesz ustawić cel debugowania na pasku narzędzi programu Visual Studio lub na stronie właściwości debugowania projektu. Wybierz jedną z następujących opcji:

|||
|-|-|
|**Komputer lokalny**|Debuguj aplikację w bieżącej sesji na komputerze lokalnym.|
|**Wykorzystaniem**|Debuguj aplikację w symulatorze programu Visual Studio dla aplikacji platformy UWP. Symulator to okno pulpitu, które symuluje funkcje urządzenia, takie jak gesty dotykowe i rotacja urządzeń, które mogą nie istnieć na komputerze lokalnym. Opcja symulator jest dostępna tylko wtedy, gdy **minimalna wersja platformy docelowej** aplikacji jest mniejsza lub równa systemowi operacyjnemu na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem sieci lub kabla Ethernet. Remote Tools for Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Pliku**|Debuguj aplikację na urządzeniu podłączonym do portu USB. Urządzenie musi być odblokowane przez dewelopera i mieć odblokowany ekran.|
|**Emulator urządzenia przenośnego**|Wykonaj rozruch emulatora określonego w polu Nazwa emulatora, wdróż aplikację i Rozpocznij debugowanie. Emulatory są dostępne tylko na maszynach z obsługą funkcji Hyper-V.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Konfigurowanie debugowania na stronie właściwości projektu

Aby skonfigurować dodatkowe opcje debugowania, użyj strony właściwości debugowania projektu.

**Aby otworzyć właściwości debugowania:**

1. W **Eksplorator rozwiązań**wybierz projekt, a następnie wybierz ikonę **Właściwości** lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.

1. Po lewej stronie okienka **Właściwości** :

   - W C# przypadku aplikacji i Visual Basic wybierz pozycję **Debuguj**.

     ![C#i Visual Basic strony właściwości debugowania projektu](../debugger/media/dbg_csvb_debugpropertypage.png)

   - W C++ przypadku aplikacji wybierz pozycję **Właściwości konfiguracji** > **debugowanie**.

     ![C++Strona właściwości debugowania aplikacji platformy UWP](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia

W C# przypadku aplikacji i Visual Basic program Visual Studio domyślnie debuguje kod zarządzany. Możesz wybrać opcję debugowania innych lub dodatkowych typów kodu. Możesz również ustawić wartości **typu debugera** dla wszystkich zadań w tle, które są częścią projektu.

W C++ aplikacjach program Visual Studio domyślnie debuguje kod natywny. Można zdecydować się na debugowanie określonych typów kodu zamiast lub oprócz kodu natywnego.

**Aby określić typy kodu do debugowania:**

- W C# przypadku aplikacji i Visual Basic wybierz jeden z następujących debugerów z listy rozwijanej Typ **aplikacji** i **Typ procesu w tle** w obszarze **Typ debugera** na stronie właściwości **debugowania** .

- W C++ przypadku aplikacji wybierz jeden z następujących debugerów z listy rozwijanej **Typ debugera** na stronie właściwości **debugowania** .

|||
|-|-|
|**Tylko zarządzane**|Debuguj kod zarządzany w aplikacji. Kod JavaScript i natywny kodC++ C/Code są ignorowane.|
|**Tylko natywny**|Debuguj natywny kodC++ C/w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debuguj natywny kodC++ C/Code i kod zarządzany w aplikacji. Kod JavaScript jest ignorowany. W C++ projektach ta opcja jest nazywana **zarządzanym i natywnym**.|
|**Skrypt**|Debuguj kod JavaScript w aplikacji. Kod zarządzany i kod natywny zostały zignorowane.|
|**Natywny ze skryptem**|Debuguj natywny kodC++ C/Code i JavaScript w aplikacji. Kod zarządzany jest ignorowany. Dostępne tylko C++ w projektach lub zadaniach w tle.|
|**Tylko procesor GPUC++ (amp)**|Debuguj kod C++ natywny, który jest URUCHAMIANY w procesorze GPU. Dostępne tylko C++ w projektach.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Wyłącz sprzężenia zwrotne sieci (opcjonalnie)

 W przypadku zabezpieczeń aplikacja platformy UWP zainstalowana w standardowym sposobie nie może nawiązywać połączeń sieciowych z urządzeniem, na którym jest ono zainstalowane. Program Visual Studio domyślnie wyłącza wdrożone aplikacje z tej reguły, dzięki czemu można testować procedury komunikacji na pojedynczym komputerze. Przed udostępnieniem aplikacji należy przetestować aplikację bez wykluczania.

**Aby usunąć wyłączenie sprzężenia zwrotnego sieci:**

- W C# przypadku aplikacji i Visual Basic Usuń zaznaczenie pola wyboru **Zezwalaj na sprzężenie zwrotne sieci lokalnej** w obszarze **Opcje uruchamiania** na stronie właściwości **debugowania** .

- W C++ przypadku aplikacji wybierz pozycję **nie** z listy rozwijanej **Zezwalaj na sprzężenie zwrotne sieci lokalnej** na stronie właściwości **debugowania** .

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Zainstaluj ponownie aplikację po rozpoczęciu debugowania (opcjonalnie)
 Aby zdiagnozować problemy z instalacją C# aplikacji lub Visual Basic, wybierz opcję **Odinstaluj, a następnie zainstaluj ponownie pakiet** na stronie właściwości **debugowania** . Ta opcja powoduje odtworzenie oryginalnej instalacji po rozpoczęciu debugowania. Ta opcja jest niedostępna dla C++ projektów.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Ustawianie opcji uwierzytelniania dla zdalnego debugowania

Domyślnie należy podać poświadczenia systemu Windows w celu uruchomienia debugera zdalnego po wybraniu **maszyny zdalnej** jako celu wdrożenia. Istnieje możliwość zmiany wymagania dotyczącego uwierzytelniania.

Tryb uwierzytelniania **uniwersalnego (nieszyfrowanego protokołu)** jest przeznaczony dla urządzeń IoT, Xbox i HoloLens oraz do aktualizacji lub nowszych komputerów z systemem Windows 10 dla twórców.

**Aby zmienić metodę uwierzytelniania:**

- W C# przypadku aplikacji i Visual Basic na stronie właściwości **debugowania** wybierz pozycję **maszyna zdalna** jako **urządzenie docelowe**. Następnie wybierz pozycję **Brak** lub **uniwersalny (niezaszyfrowany protokół)** w **trybie uwierzytelniania**.

- W C++ przypadku aplikacji wybierz pozycję **maszyna zdalna** w obszarze **debuger do uruchomienia** na stronie właściwości **debugowania** . Następnie wybierz opcję **Brak uwierzytelniania** lub **uniwersalnego (nieszyfrowanego protokołu)** dla **typu uwierzytelniania**.

> [!CAUTION]
> Po uruchomieniu zdalnego debugera w trybie **Brak** lub **uniwersalne (nieszyfrowane protokoły)** nie ma zabezpieczeń sieci. Wybierz te tryby tylko dla zaufanych sieci, na których pewno nie są narażone złośliwe lub zagrożone dane.

## <a name="BKMK_Start_the_debugging_session"></a>Opcje uruchamiania debugowania

Po wybraniu opcji **debuguj** > **Rozpocznij debugowanie** lub naciśnij klawisz **F5**program Visual Studio uruchomi aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie, ale Opóźnij uruchomienie aplikacji

Domyślnie program Visual Studio uruchamia aplikację natychmiast po rozpoczęciu debugowania. Możesz również ustawić aplikację do uruchamiania w trybie debugowania, ale uruchomić aplikację poza debugerem. Na przykład możesz chcieć debugować uruchamianie aplikacji z menu **Start** systemu Windows lub debugować proces w tle w aplikacji. W przypadku wybrania tej opcji aplikacja zostanie uruchomiona w debugerze przy uruchamianiu.

**Aby wyłączyć automatyczne uruchamianie aplikacji:**

- W C# przypadku aplikacji i Visual Basic wybierz pozycję nie **uruchamiaj, ale Debuguj mój kod po uruchomieniu** w obszarze **Opcje uruchamiania** na stronie właściwości **debugowania** .

- W C++ przypadku aplikacji wybierz pozycję **nie** na liście rozwijanej **uruchamiania aplikacji** na stronie właściwości **debugowania** .

Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla aplikacji platformy UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Debuguj zainstalowaną lub uruchomioną aplikację platformy UWP

W celu debugowania aplikacji platformy UWP, która jest już zainstalowana lub uruchomiona na urządzeniu lokalnym lub zdalnym, można użyć **debugowania zainstalowanego pakietu aplikacji** . Aplikacja mogła zostać zainstalowana z poziomu Microsoft Store lub nie jest projektem programu Visual Studio. Na przykład aplikacja może mieć niestandardowy system kompilacji, który nie używa programu Visual Studio.

Możesz natychmiast uruchomić zainstalowaną aplikację lub można ją skonfigurować do uruchamiania w debugerze po uruchomieniu z inną metodą. Aby uzyskać więcej informacji, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla aplikacji platformy UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Aby uruchomić zainstalowaną lub uruchomioną aplikację platformy UWP w debugerze, wybierz pozycję **debuguj** > **inne elementy docelowe debugowania** > **debugowanie zainstalowanego pakietu aplikacji**. Aby uzyskać więcej instrukcji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji systemu Windows 8. x

Aby dołączyć debuger do aplikacji [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Menedżer pakietów możliwością debugowania jest instalowany z Remote Tools for Visual Studio.

1. Zainstaluj Remote Tools for Visual Studio na urządzeniu, na którym zainstalowano aplikację. Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzi zdalnych](../debugger/remote-debugging.md).

1. Na ekranie **startowym** systemu Windows wyszukaj i uruchom **Menedżera pakietów możliwością debugowania**.

   Zostanie wyświetlone okno programu PowerShell prawidłowo skonfigurowane dla polecenia cmdlet AppxDebug.

1. Określ identyfikator PackageFullName aplikacji.

   1. Aby wyświetlić listę zawierającą PackageFullName wszystkich aplikacji, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

   1. W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug <PackageFullName>`, gdzie \<PackageFullName > jest identyfikatorem PackageFullName aplikacji.

1. Wybierz pozycję **debuguj** > **Dołącz do procesu**.

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
> Aplikacje JavaScript działają w wystąpieniu procesu *wwahost. exe* . Jeśli więcej niż jedna aplikacja JavaScript jest uruchomiona, należy znać identyfikator procesu *wwahost. exe* aplikacji, aby dołączyć do niego.
>
> Najprostszym sposobem dołączenia do aplikacji JavaScript jest zamknięcie wszystkich innych aplikacji JavaScript. Można też zauważyć identyfikatory PID uruchomionych procesów *wwahost. exe* w Menedżerze zadań systemu Windows przed rozpoczęciem aplikacji. Po uruchomieniu aplikacji jego identyfikator PID *wwahost. exe* będzie inny niż te, które zanotowano wcześniej.
::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Debugowanie aplikacji w programie Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)
---
title: Rozpoczynanie sesji debugowania dla aplikacji platformy UWP | Microsoft Docs
description: Uruchom sesję Visual Studio debugowania aplikacji platforma uniwersalna systemu Windows (UWP). Skonfiguruj sesję debugowania i wybierz sposób uruchamiania aplikacji.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d0669f9838073571018eb762e98aa6d907456f12
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386465"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Rozpoczynanie sesji debugowania aplikacji platformy UWP

W tym artykule opisano sposób uruchamiania Visual Studio debugowania dla aplikacji platforma uniwersalna systemu Windows (UWP). Aplikacje platformy uniwersalnej systemu Windows można zapisywać w językach XAML i C++, XAML oraz C#/Visual Basic. Aby rozpocząć debugowanie aplikacji platformy UWP, skonfiguruj sesję debugowania i wybierz sposób uruchamiania aplikacji.

::: moniker range=">=vs-2019"
> [!NOTE]
> Począwszy od Visual Studio 2019 r., aplikacje platformy UWP dla języków HTML i JavaScript nie są już obsługiwane.
::: moniker-end
::: moniker range="vs-2017"
W Visual Studio 2017 r. większość poleceń i opcji pokazanych w tym artykule dotyczy również aplikacji platformy UWP dla języków HTML i JavaScript. Tam, gdzie polecenia są różne w aplikacjach zarządzanych i w języku C++, aplikacje JavaScript są zwykle takie same jak polecenia dla aplikacji platformy UWP w języku C++.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Rozpoczynanie debugowania z Visual Studio narzędzi

Najprostszym sposobem skonfigurowania i uruchomienia debugowania jest standardowe Visual Studio narzędzi.

![Debugowanie z paska narzędzi](../debugger/media/vsrun_select_target_device.png)

1. Z listy **rozwijanej** Konfiguracja na pasku **narzędzi Standardowa** wybierz pozycję **Debuguj**.

1. Z listy **rozwijanej** Platforma wybierz platformę docelową, dla której chcesz utworzyć kompilację.

1. Z listy rozwijanej obok zielonej strzałki wybierz element docelowy debugowania. Możesz wybrać maszynę lokalną, urządzenie połączone bezpośrednio, lokalny Visual Studio, urządzenie zdalne lub emulator.

1. Aby rozpocząć debugowanie, wybierz zieloną strzałkę **Start** na pasku narzędzi lub wybierz pozycję **Debuguj** rozpocznij debugowanie  >  lub naciśnij **klawisz F5.**

   Visual Studio kompilacji i uruchamiania aplikacji z dołączonym debugerem.

Debugowanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie wstrzymasz wykonywanie, wystąpi nieobsługiwany wyjątek lub aplikacja zakończy się.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Opcje celu wdrożenia

Element docelowy debugowania można ustawić na pasku Visual Studio narzędziu lub na stronie właściwości debugowania projektu. Wybierz jedną z następujących opcji:

|Nazwa|Opis|
|-|-|
|**Maszyna lokalna**|Debuguj aplikację w bieżącej sesji na komputerze lokalnym.|
|**Symulator**|Debuguj aplikację w symulatorze Visual Studio dla aplikacji platformy UWP. Symulator to okno pulpitu, które symuluje funkcje urządzenia, takie jak gesty dotykowe i obracanie urządzenia, które mogą nie istnieć na komputerze lokalnym. Opcja symulatora jest dostępna tylko  wtedy, gdy minimalna wersja platformy docelowej aplikacji jest mniejsza niż lub równa systemowi operacyjneowi na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz [Run UWP apps in the simulator (Uruchamianie aplikacji platformy UWP w symulatorze).](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem sieci lub kabla Ethernet. Urządzenie Remote Tools for Visual Studio musi być zainstalowane i uruchomione na urządzeniu zdalnym. Aby uzyskać więcej informacji, zobacz [Run UWP apps on a remote machine (Uruchamianie aplikacji platformy UWP na maszynie zdalnej).](../debugger/run-windows-store-apps-on-a-remote-machine.md)|
|**Urządzenie**|Debuguj aplikację na urządzeniu podłączonym do portu USB. Urządzenie musi być odblokowane przez dewelopera i mieć odblokowany ekran.|
|**Emulator urządzeń przenośnych**|Uruchom emulator określony w nazwie emulatora, wd wdrażaj aplikację i rozpocznij debugowanie. Emulatory są dostępne tylko na maszynach z włączoną obsługą funkcji Hyper-V.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Konfigurowanie debugowania na stronie właściwości projektu

Aby skonfigurować dodatkowe opcje debugowania, użyj strony właściwości debugowania projektu.

**Aby otworzyć właściwości debugowania:**

1. W **Eksplorator rozwiązań** projektu wybierz projekt, a  następnie wybierz ikonę Właściwości lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Właściwości.**

1. Po lewej stronie **okienka** Właściwości:

   - W przypadku aplikacji w języku C# Visual Basic wybierz pozycję **Debuguj**.

     ![Strona właściwości debugowania Visual Basic C# i projektu](../debugger/media/dbg_csvb_debugpropertypage.png)

   - W przypadku aplikacji języka C++ wybierz **pozycję Debugowanie właściwości**  >  **konfiguracji.**

     ![Strona właściwości debugowania aplikacji platformy UWP w języku C++](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Wybieranie debugera do użycia

W przypadku aplikacji w Visual Basic C# Visual Studio debugowanie kodu zarządzanego. Możesz debugować inne lub dodatkowe typy kodu. Można również ustawić **wartości typu debugera** dla dowolnych zadań w tle, które są częścią projektu.

W aplikacjach języka C++ Visual Studio debugowanie kodu natywnego. Możesz debugować określone typy kodu zamiast lub oprócz kodu natywnego.

**Aby określić typy kodu do debugowania:**

- W przypadku aplikacji Visual Basic c# i aplikacji wybierz jeden z  następujących  debugerów z listy rozwijanej Typ aplikacji i Typ procesu w tle w obszarze **Typ debugera** na stronie właściwości **Debugowanie.**

- W przypadku aplikacji języka C++ wybierz jeden z następujących debugerów z **listy rozwijanej Typ debugera** na **stronie właściwości** Debugowanie.

|Nazwa|Opis|
|-|-|
|**Tylko zarządzane**|Debugowanie kodu zarządzanego w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Tylko natywne**|Debugowanie natywnego kodu C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Mieszane (zarządzane i natywne)**|Debugowanie natywnego kodu C/C++ i kodu zarządzanego w aplikacji. Kod JavaScript jest ignorowany. W projektach W języku C++ ta opcja ma nazwę **Managed (Zarządzane) i Native (Natywne).**|
|**Skrypt**|Debugowanie kodu JavaScript w aplikacji. Kod zarządzany i kod natywny są ignorowane.|
|**Natywne ze skryptem**|Debugowanie natywnego kodu C/C++ i kodu JavaScript w aplikacji. Kod zarządzany jest ignorowany. Dostępne tylko w projektach języka C++ lub zadaniach w tle.|
|**Tylko procesor GPU (C++ AMP)**|Debugowanie natywnego kodu C++ uruchamianego na procesorze graficznym (GPU). Dostępne tylko w projektach języka C++.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Wyłączanie sprzężenia zwrotnego sieci (opcjonalnie)

 Ze względów bezpieczeństwa aplikacja platformy uniwersalnej systemu Windows zainstalowana w standardowy sposób nie może wykonać wywołań sieciowych do urządzenia, na których jest zainstalowana. Visual Studio domyślnie wyklucza wdrożone aplikacje z tej reguły, dzięki czemu można testować procedury komunikacji na jednym komputerze. Przed wydaniem aplikacji należy ją przetestować bez zwolnienia.

**Aby usunąć wyłączenie sprzężenia zwrotnego sieci:**

- W przypadku aplikacji Visual Basic C# i  aplikacji usuń zaznaczenie pola wyboru Zezwalaj na sprzężenia zwrotne sieci lokalnej w obszarze **Opcje** uruchamiania na **stronie właściwości** Debugowanie.

- W przypadku aplikacji języka C++ wybierz pozycję **Nie** z listy rozwijanej Zezwalaj na sprzężenia **zwrotne** sieci lokalnej na **stronie właściwości** Debugowanie.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Zainstaluj ponownie aplikację po rozpoczęciu debugowania (opcjonalnie)
 Aby zdiagnozować problemy z instalacją aplikacji w języku C# lub Visual Basic, wybierz pozycję Odinstaluj, a następnie ponownie zainstaluj mój **pakiet** na **stronie Właściwości**  debugowania. Ta opcja powoduje ponowne utworzenie oryginalnej instalacji po rozpoczęciu debugowania. Ta opcja nie jest dostępna dla projektów w języku C++.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Ustawianie opcji uwierzytelniania na potrzeby debugowania zdalnego

Domyślnie należy podać poświadczenia systemu Windows, aby uruchomić debuger zdalny po wybraniu **maszyny** zdalnej jako celu wdrożenia. Można zmienić wymaganie dotyczące uwierzytelniania.

Tryb **uwierzytelniania universal (Unencrypted Protocol)** jest używany dla urządzeń IoT, Xbox i HoloLens, a aktualizacja dla twórców lub Windows 10 komputerów.

**Aby zmienić metodę uwierzytelniania:**

- W przypadku aplikacji Visual Basic C# na stronie **Właściwości debugowania** wybierz pozycję **Maszyna** zdalna jako **urządzenie docelowe.** Następnie wybierz opcję **Brak lub** **Uniwersalny (protokół niezaszyfrowany) dla** opcji Tryb **uwierzytelniania.**

- W przypadku aplikacji języka C++ wybierz pozycję **Maszyna zdalna** w **obszarze Debuger, aby** uruchomić polecenie na stronie **właściwości** Debugowanie. Następnie wybierz opcję **Bez uwierzytelniania** lub **Uniwersalne (protokół niezaszyfrowany) dla** opcji Typ **uwierzytelniania.**

> [!CAUTION]
> Po uruchomieniu zdalnego debugera w trybie **Brak** lub Uniwersalny (protokół niezaszyfrowany) nie ma zabezpieczeń sieci.  Wybierz te tryby tylko w zaufanych sieciach, które na pewno nie są narażone na ryzyko ze strony złośliwego kodu lub złośliwego ruchu.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Opcje uruchamiania debugowania

Po wybraniu opcji **Debuguj** rozpocznij debugowanie lub  >   naciśnij **klawisz F5,** Visual Studio uruchomi aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie wstrzymasz wykonywanie, wystąpi nieobsługiwany wyjątek lub aplikacja zakończy się.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Rozpocznij debugowanie, ale opóźnij uruchamianie aplikacji

Domyślnie program Visual Studio natychmiast po rozpoczęciu debugowania. Można również ustawić uruchamianie aplikacji w trybie debugowania, ale uruchomić ją poza debugerem. Możesz na przykład debugować uruchamianie aplikacji z menu **Start** systemu Windows lub debugować proces w tle w aplikacji. Jeśli wybierzesz tę opcję, aplikacja zostanie uruchamiana w debugerze po uruchomieniu.

**Aby wyłączyć automatyczne uruchamianie aplikacji:**

- W przypadku aplikacji Visual Basic C# wybierz pozycję Nie **uruchamiaj,** ale debuguj mój kod po uruchomieniu w obszarze **Opcje** uruchamiania na **stronie właściwości Debugowanie.**

- W przypadku aplikacji języka C++ wybierz **pozycję Nie** z **listy rozwijanej Uruchom aplikację** na stronie **właściwości** Debugowanie.

Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz Wyzwalanie wstrzymania, wznowienia i [zdarzeń w tle dla aplikacji platformy UWP.](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Debugowanie zainstalowanej lub uruchomionej aplikacji platformy UWP

Za pomocą polecenia **Debuguj zainstalowany pakiet aplikacji można** debugować aplikację platformy UWP, która jest już zainstalowana lub uruchomiona na urządzeniu lokalnym lub zdalnym. Aplikacja może zostać zainstalowana z Microsoft Store lub nie może być Visual Studio projektu. Na przykład aplikacja może mieć niestandardowy system kompilacji, który nie używa Visual Studio.

Możesz natychmiast uruchomić zainstalowaną aplikację lub ustawić ją tak, aby była uruchamiana w debugerze po uruchomieniu przy użyciu innej metody. Aby uzyskać więcej informacji, zobacz [Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle dla aplikacji platformy UWP).](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

Aby uruchomić zainstalowaną lub uruchamianą aplikację platformy UWP w debugerze, wybierz pozycję **Debuguj** inne obiekty docelowe debugowania  >    >  **Debuguj zainstalowany pakiet aplikacji.** Aby uzyskać więcej instrukcji, zobacz [Debugowanie zainstalowanego pakietu aplikacji.](../debugger/debug-installed-app-package.md)

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Dołączanie debugera do uruchomionej Windows 8.x

Aby dołączyć debuger do aplikacji, musisz użyć menedżer pakietów z możliwością debugowania, aby ustawić aplikację do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uruchamiania w trybie debugowania. Program menedżer pakietów z możliwością debugowania instalowany wraz z Remote Tools for Visual Studio.

1. Zainstaluj Remote Tools for Visual Studio na urządzeniu, na którym zainstalowano aplikację. Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzi zdalnych.](../debugger/remote-debugging.md)

1. Na **ekranie startowym** systemu Windows wyszukaj i uruchom **menedżer pakietów z możliwością debugowania**.

   Zostanie wyświetlone okno programu PowerShell prawidłowo skonfigurowane dla polecenia cmdlet AppxDebug.

1. Określ identyfikator PackageFullName aplikacji.

   1. Aby wyświetlić listę, która zawiera nazwę PackageFullName wszystkich aplikacji, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

   1. W wierszu polecenia programu PowerShell wprowadź , gdzie to identyfikator `Enable-AppxDebug <PackageFullName>` \<PackageFullName> PackageFullName aplikacji.

1. Wybierz pozycję   >  **Debuguj dołączanie do procesu.**

1. W **oknie dialogowym Dołączanie** do procesu określ urządzenie zdalne w **polu Cel** połączenia.

   Możesz wprowadzić nazwę urządzenia, wybrać ją z  listy rozwijanej w  polu Miejsce docelowe połączenia lub wybrać pozycję Znajdź, aby znaleźć urządzenie w oknie **dialogowym Połączenia** zdalne.

1. Aby określić typ kodu, który chcesz debugować, obok pola **Dołącz** do wybierz pozycję **Wybierz**.

1. W **oknie dialogowym Wybieranie typu** kodu wybierz jedną z opcji:
   - **Automatycznie określ typ kodu do debugowania**, lub
   - **Debuguj te typy** kodu , a następnie wybierz z listy co najmniej jeden typ kodu.

1. Z listy **Dostępne procesy**  wybierz proces aplikacji do debugowania.

1. Wybierz pozycję **Dołącz**.

 Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie wstrzymasz wykonywanie, wystąpi nieobsługiwany wyjątek lub aplikacja zakończy się.

::: moniker range="vs-2017"
> [!NOTE]
> Aplikacje JavaScript działają w wystąpieniuwwahost.exe *procesu.* Jeśli jest uruchomiona więcej niż jedna aplikacja JavaScript, musisz znać numeryczny identyfikator procesu  (PID) procesu aplikacji,wwahost.exedołączyć do niego.
>
> Najprostszym sposobem dołączenia do aplikacji JavaScript jest zamknięcie wszystkich innych aplikacji JavaScript. Możesz też zanotować identyfikatory PID uruchamiania *procesówwwahost.exe* w systemie Windows Menedżer zadań przed uruchomieniem aplikacji. Po uruchomieniu aplikacji jego identyfikator *PIDwwahost.exe* będzie tym, który różni się od tych, które wcześniej zanotował.
::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Debugowanie aplikacji w programie Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)
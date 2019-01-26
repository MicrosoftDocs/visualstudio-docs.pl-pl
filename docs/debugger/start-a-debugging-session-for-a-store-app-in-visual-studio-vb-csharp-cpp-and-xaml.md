---
title: Rozpocznij sesję debugowania dla aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 02a8a2645453d1f170085998bf12412eb7eb5925
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918462"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Rozpoczynanie sesji debugowania aplikacji platformy UWP
  
W tym artykule opisano sposób uruchamiania sesji debugowania programu Visual Studio dla aplikacji uniwersalnych platformy Windows (UWP). Aplikacje platformy uniwersalnej systemu Windows mogą być napisane w XAML i C++, XAML i C#/Visual Basic, lub HTML i JavaScript. Aby rozpocząć debugowanie aplikacji platformy uniwersalnej systemu Windows, skonfiguruj sesję debugowania, a następnie wybierz sposób, aby uruchomić aplikację.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Uruchom debugowanie z narzędzi programu Visual Studio 
  
Jest najprostszym sposobem, aby skonfigurować i rozpocząć debugowanie ze standardowych narzędzi programu Visual Studio. 

![Debuguj z poziomu paska narzędzi](../debugger/media/vsrun_select_target_device.png)  
  
1. Z **konfiguracji** menu rozwijane **standardowa** narzędzi, wybierz opcję **debugowania**.  
  
1. Z **platformy** listy rozwijanej wybierz platformę docelową kompilacji dla. 
   
1. Z listy rozwijanej obok zielona strzałka wybierz cel debugowania. Można wybrać komputer lokalny, połączonych urządzeń, symulatora lokalnego programu Visual Studio, urządzenie zdalne lub emulator. 
   
1. Aby rozpocząć debugowanie, wybierz zielony **Start** strzałkę na pasku narzędzi lub wybierz **debugowania** > **Rozpocznij debugowanie**, lub naciśnij **F5**. 
   
   Visual Studio kompiluje i uruchamia aplikację w debugerze. 

Debugowanie kontynuowany do momentu punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub zakończenia aplikacji.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Target — opcje wdrażania 
  
Możesz ustawić docelowy debugowania na pasku narzędzi programu Visual Studio lub projektu na debugowanie strony właściwości. Wybierz jedną z następujących opcji:

|||  
|-|-|  
|**Maszyna lokalna**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym.|  
|**Symulator**|Debugowanie aplikacji w symulatorze programu Visual Studio dla aplikacji platformy uniwersalnej systemu Windows. Symulator jest oknem pulpitu, która symuluje urządzenie funkcje, takie jak touch gestów i obracanie urządzeń, które mogą nie istnieć na komputerze lokalnym. Opcja symulator jest dostępna tylko wtedy, gdy Twoja aplikacja **minimalnej platformy docelowej. Wersja** jest mniejsza niż system operacyjny na komputerze lokalnym. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu podłączone do komputera lokalnego za pośrednictwem sieci lub kabla Ethernet. Remote Tools for Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**urządzenia**|Debugowanie aplikacji na urządzeniu z portu USB. Urządzenie musi być odblokowane dla deweloperów i mieć ekranu odblokowane.|  
|**Mobile Emulator**|Rozruch emulatora określony w nazwie emulatora, Wdróż aplikację i Rozpocznij debugowanie. Emulatory są dostępne tylko dla maszyn Hyper-V jest włączona.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Konfigurowanie debugowania na stronie właściwości projektu 

Aby skonfigurować dodatkowe opcje debugowania, należy użyć strony właściwości debugowania projektu. 

**Aby otworzyć właściwości debugowania:**

1. W **Eksploratora rozwiązań**, wybierz projekt, a następnie wybierz **właściwości** ikonę, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**.  
   
1. W lewej części **właściwości** okienka:
   
   - Aby uzyskać C# i aplikacji Visual Basic, wybierz opcję **debugowania**.  
     
     ![C#i strony właściwości debugowania projektu w języku Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - W przypadku aplikacji C++ i JavaScript, wybierz **właściwości konfiguracji** > **debugowanie**.  
     
     ![Debugowania strona właściwości aplikacji platformy uniwersalnej systemu Windows w języku C++](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Wybierz debuger do użycia  

Aby uzyskać C# i aplikacji Visual Basic, Visual Studio debuguje kodzie zarządzanym domyślnie. Można debugować kodu inne lub dodatkowe typy. Można również ustawić **typ debugera** wartości dla dowolnego zadania w tle, które są częścią projektu.

W aplikacjach C++ Visual Studio debuguje kodu natywnego, domyślnie. W aplikacji JavaScript programu Visual Studio debugować skrypt domyślnie. Można debugować określone typy kodu, zamiast lub oprócz kodu natywnego. 

**Aby określić typy kodu do debugowania:**

- Dla C# i aplikacji w języku Visual Basic, wybierz jedną z następujących debugery z **typ aplikacji** i **typu proces w tle** listy rozwijane w obszarze **typ debugera** na **debugowania** stronę właściwości.  
  
- C + +/ aplikacji JavaScript, wybierz jedną z następujących debugery z **typ debugera** menu rozwijane **debugowanie** stronę właściwości.

|||  
|-|-|  
|**Tylko zarządzany**|Debugowanie kodu zarządzanego w aplikacji. Kod języka JavaScript i kodu natywnego języka C/C++ są ignorowane.|  
|**Tylko w trybie macierzystym**|Debugowanie kodu natywnego języka C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|  
|**Mieszany (zarządzany i natywny)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowany. W projektach C++, ta opcja jest wywoływana **zarządzany i natywny**.|  
|**Skrypt**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu są ignorowane.|  
|**Natywny ze skryptem**|Debugowanie kodu natywnego języka C/C++ oraz kodu JavaScript w aplikacji. Kod zarządzany jest ignorowany. Dostępne w projektach C++ lub tylko zadania w tle.|  
|**Tylko procesor GPU (C++ AMP)**|Debugowanie kodu natywnego języka C++ jest uruchamiany na jednostka przetwarzania grafiki (GPU). Dostępne w tylko dla projektów C++.|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Wyłącz sprzężenia zwrotne w sieci (opcjonalnie) 
  
 Dla bezpieczeństwa aplikacji platformy UWP, który jest zainstalowany w standardowy sposób nie może wprowadzać wywołań sieci do zainstalowania na urządzeniu. Visual Studio wyłącza wdrożone aplikacje od tej reguły domyślnie, aby możliwe było przetestowanie procedur komunikacji na jednym komputerze. Przed publikacją aplikacji należy przetestować aplikację bez zwolnienia.  
  
**Aby usunąć wykluczenie sprzężenie zwrotne sieci:**  
  
-   Dla C# i aplikacji w języku Visual Basic, usuń zaznaczenie opcji **Zezwalaj na sprzężenie zwrotne sieci lokalnej** pole wyboru w obszarze **opcje uruchamiania** na **debugowania** stronę właściwości.  
  
-   W przypadku aplikacji Visual C++ i JavaScript, wybierz **nie** z **Zezwalaj na sprzężenie zwrotne lokalnej sieci** menu rozwijane **debugowanie** stronę właściwości.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Ponownie zainstaluje aplikację po rozpoczęciu debugowania (opcjonalnie) 
 Do diagnozowania problemów z instalacją przy użyciu C# lub aplikacji Visual Basic, wybierz opcję **Odinstaluj i zainstaluj ponownie mój pakiet** na **debugowania** stronę właściwości. Ta opcja odtwarza oryginalnej instalacji, po rozpoczęciu debugowania. Ta opcja jest niedostępna dla projektów C++ i JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Ustaw opcje uwierzytelniania dla zdalnego debugowania  
  
Domyślnie, należy podać poświadczenia Windows, aby uruchomić zdalny debuger po wybraniu **maszyny zdalnej** jako cel wdrożenia. Możesz zmienić wymogu uwierzytelniania. 

**Uniwersalny (protokół niezaszyfrowanym)** tryb uwierzytelniania jest urządzeń IoT i konsoli Xbox, HoloLens i twórcy Update lub nowszej komputerów z systemem Windows 10.  

**Aby zmienić metodę uwierzytelniania:**  

- Dla C# aplikacji Visual Basic i na **debugowania** strony właściwości, wybierz opcję **maszyny zdalnej** jako **urządzenie docelowe**. Następnie wybierz **Brak** lub **uniwersalny (protokół niezaszyfrowanym)** dla **tryb uwierzytelniania**. 
  
- W przypadku aplikacji C++ i JavaScript, wybierz **maszyny zdalnej** w obszarze **debuger do uruchomienia** na **debugowanie** stronę właściwości. Następnie wybierz **bez uwierzytelniania** lub **uniwersalny (protokół niezaszyfrowanym)** dla **typ uwierzytelniania**. 
  
> [!CAUTION]
> Istnieje nie zabezpieczeń sieci podczas uruchamiania zdalnego debugera w **Brak** lub **uniwersalny (protokół niezaszyfrowanym)** tryby. Wybierz te tryby wyłącznie w zaufanych sieciach, które są się, że nie są zagrożone przez złośliwego kodu lub szkodliwy ruch.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Opcje uruchamiania debugowania  
  
Po wybraniu **debugowania** > **Rozpocznij debugowanie** lub naciśnij **F5**, Visual Studio uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Rozpocznij debugowanie, ale opóźnienie uruchomienie aplikacji  

Domyślnie program Visual Studio uruchamia aplikację natychmiast, po rozpoczęciu debugowania. Można również ustawić aplikację, aby uruchomić tryb debugowania, ale uruchamiają aplikację poza debugerem. Na przykład możesz chcieć debugowanie, uruchamianie aplikacji z Windows **Start** menu lub debugowania proces w tle w aplikacji. Jeśli wybierzesz tę opcję, aplikacja uruchamia się w debugerze w momencie uruchomienia. 

**Aby wyłączyć automatyczne uruchomienia:**  
  
- Dla C# i aplikacji Visual Basic, wybierz opcję **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** w obszarze **opcje uruchamiania** na **debugowania** stronę właściwości.  
   
- W przypadku aplikacji C++ i JavaScript, wybierz **nie** z **Uruchom aplikację** menu rozwijane **debugowanie** stronę właściwości.  
  
Aby uzyskać więcej informacji na temat debugowania zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń aplikacji platformy UWP w tle](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Debugowanie aplikacji platformy uniwersalnej systemu Windows zainstalowany lub włączony 

Możesz użyć **pakietu debugowania zainstalowanej aplikacji** do debugowania aplikacji platformy UWP, który jest już zainstalowany lub włączony na urządzeniu lokalnym lub zdalnym. Aplikacja została zainstalowana z Microsoft Store lub może nie być projektu programu Visual Studio. Na przykład aplikacja może mieć system kompilacji niestandardowej, która nie korzysta z programu Visual Studio.  
  
Natychmiast rozpocząć zainstalowaną aplikację lub ustawić jego uruchomienie w debugerze, gdy uruchomiony przy użyciu innej metody. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń aplikacji platformy UWP w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Aby uruchomić aplikację platformy uniwersalnej systemu Windows zainstalowany lub włączony w debugerze, zaznacz **debugowania** > **inne cele debugowania** > **pakietu debugowania zainstalowanej aplikacji**. Aby uzyskać więcej instrukcji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Dołącz debuger do uruchomionej aplikacji Windows 8.x

Aby dołączyć debuger [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji, musisz podać Debugowalny Menedżer pakietów do zestawu aplikacji do uruchamiania w trybie debugowania. Debugowalny Menedżer pakietów jest zainstalowany za pomocą narzędzi Remote Tools for Visual Studio.  
  
1. Instalowanie narzędzi Remote Tools dla programu Visual Studio na urządzeniu, w którym aplikacja zostanie zainstalowana. Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzi zdalnych](../debugger/remote-debugging.md).  
   
1. W Windows **Start** ekranu, wyszukiwanie i Rozpocznij **Debugowalny Menedżer pakietów**.  
   
   Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.  
   
1. Określ element PackageFullName identyfikator aplikacji. 
   
   1. Aby wyświetlić listę, która zawiera element PackageFullName wszystkie aplikacje, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.  
   
   1. W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug <PackageFullName>`, gdzie \<Pełna_nazwa_pakietu > jest identyfikatorem element PackageFullName aplikacji.  
   
1. Wybierz **debugowania** > **dołączyć do procesu**.  
   
1. W **dołączyć do procesu** okna dialogowego należy określić urządzenie zdalne w **adres docelowy połączenia** pole. 
   
   Można wprowadzić nazwę urządzenia, wybierz ją z listy rozwijanej w **adres docelowy połączenia** , albo pozycję **znaleźć** można znaleźć urządzenia w **połączeń zdalnych** okno dialogowe.  
   
1. Do określania typu kod chcesz debugować obok **dołączyć do** wybierz opcję **wybierz**.  
   
1. W **Wybieranie typu kodu** okna dialogowego wybierz opcję:
   - **Automatycznie Określ typ kodu do debugowania**, lub 
   - **Debugowania tych typów kodu**, a następnie wybierz jeden lub więcej typów kodu z listy.  
   
1. W **dostępne procesy** wybierz proces aplikacji do debugowania.  
   
1. Wybierz **dołączyć**.  
  
 Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

> [!NOTE]
> JavaScript aplikacje uruchamiane w wystąpieniu *wwahost.exe* procesu. Jeśli więcej niż jednej aplikacji JavaScript działa, konieczne będzie znany identyfikator liczbowych procesu (PID) aplikacji *wwahost.exe* proces do dołączenia do niej.  
> 
> Najprostszym sposobem, aby dołączyć do aplikacji JavaScript jest Zamknij wszystkie inne aplikacje języka JavaScript. Lub możesz zauważyć identyfikatory PID uruchomiona *wwahost.exe* procesy Windows Menedżera zadań przed rozpoczęciem korzystania z aplikacji. Po uruchomieniu aplikacji, jego *wwahost.exe* identyfikator PID będzie ten, który różni się od innych niż wymienione wcześniej.  

## <a name="see-also"></a>Zobacz także  
 [Debugowanie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)   
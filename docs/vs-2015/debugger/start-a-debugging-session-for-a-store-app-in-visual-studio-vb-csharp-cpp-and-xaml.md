---
title: Rozpocznij sesję debugowania dla Store app (VB, C#, C++ i XAML) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 0e66c47c0bf36bf98e4d5f0439d1c3cb84c6b999
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955411"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Uruchamianie sesji debugowania dla aplikacji Store w programie Visual Studio (VB, C#, C++ i XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji Store w XAML i Visual C++, Visual C# lub Visual Basic. Debugowanie aplikacji obejmuje zarówno Konfigurowanie sesji debugowania, jak i wybierając sposób, aby uruchomić aplikację.

> [!NOTE]
>  Aplikacje napisane w języku JavaScript i HTML można znaleźć [rozpocząć sesję debugowania (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

##  <a name="BKMK_In_this_topic"></a> W tym temacie
 [Prosty sposób Rozpocznij debugowanie](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybór opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)

- [(Opcjonalnie) Opóźnienie uruchamiania sesji debugowania](#BKMK__Optional__Delay_starting_the_debug_session)

- [(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)

- [(Opcjonalnie) Ponownie zainstaluje aplikację po rozpoczęciu debugowania](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(Opcjonalnie) Wyłączyć wymaganie uwierzytelniania można uruchomić debugera zdalnego](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Rozpocznij sesję debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale opóźnić uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Uruchom zainstalowaną aplikację w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

- [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

  -   [Ustaw aplikację do uruchamiania w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

  -   [Dołącz debuger](#BKMK_Attach_the_debugger)

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Prosty sposób Rozpocznij debugowanie

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Wybierz F5.

   Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane do momentu punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi wyjątek un obsłużony, lub zakończenia aplikacji. Aby uzyskać więcej informacji, zobacz [nawigowanie po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

##  <a name="BKMK_Configure_the_debugging_session"></a> Konfigurowanie sesji debugowania

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otwórz stronę właściwości debugowania projektu

1.  W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz **właściwości**.

2.  To zrobić, aby otworzyć stronę właściwości debugowania dla projektu:

    -   W przypadku aplikacji języka Visual C# i Visual Basic, wybierz **debugowania**.

         ![C&#35; &#47; strony właściwości debugowania projektu VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    -   W przypadku aplikacji Visual C++, rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.

         ![C&#43; &#43; debugowania strona właściwości aplikacji Windows Store](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Wybór opcji konfiguracji kompilacji

1.  Z **konfiguracji** wybierz **debugowania** lub **debugowania (aktywny)**.

2.  Z **platformy** listy wybierz platformę docelową kompilacji dla. W większości przypadków **dowolny Procesor** (**wszystkich platform** w programie Visual C++) to najlepszy wybór.

###  <a name="BKMK_Choose_the_deployment_target"></a> Wybierz cel wdrożenia
 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Można wdrożyć i debugowanie aplikacji Windows Store na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na urządzeniu zdalnym.

- W przypadku aplikacji C# i Visual Basic, wybierz obiekt docelowy z **urządzenie docelowe** listy na **debugowania** strony właściwości dla projektu.

- W aplikacjach C++, wybierz obiekt docelowy z **debuger do uruchomienia** listy na **debugowanie** strona właściwości:

  Wybierz jedną z następujących opcji:

|||
|-|-|
|**Maszyna lokalna**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchom Windows Store apps na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Symulator**|Debugowanie aplikacji w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchom Windows Store aplikacji w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Jeśli wybierzesz **maszyny zdalnej**, określ nazwę lub adres IP komputera zdalnego, w jednym z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego.

  -   W przypadku aplikacji C# i Visual Basic, wprowadź nazwę lub adres IP w **maszyny zdalnej** pole.

  -   W aplikacjach C++, wprowadź nazwę lub adres IP w **NazwaKomputera** pole.

- Wybierz komputer zdalny z **wybierz połączenie ze zdalnym debugerem** okno dialogowe.

   Aby otworzyć okno dialogowe:

  - W przypadku aplikacji C# i Visual Basic, wybierz **znaleźć**.

  - W aplikacjach C++, wybierz strzałkę w dół w **NazwaKomputera** pole, a następnie wybierz  **\<zlokalizuj... >**.

    ![Okno dialogowe Wybierz połączenie ze zdalnym debugerem](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  >  **Wybierz połączenie ze zdalnym debugerem** wyświetlone okno dialogowe, które znajdują się w lokalnej podsieci i maszyn, które są podłączone bezpośrednio do maszyny programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w **NazwaKomputera** pole.

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Można wdrożyć i debugowanie aplikacji Windows Phone Store na urządzeniu lub w jednym z emulatorów phone programu Visual Studio. Wybierz urządzenie lub emulator z **urządzenie docelowe** listy.

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Wybierz debuger do użycia
 Domyślnie program Visual Studio debugować kodu zarządzanego w aplikacjach języka C# i Visual Basic.

 W przypadku aplikacji C# i Visual Basic można debugować zarówno zarządzanego i natywnego kodu C/C++ w aplikacji. Wybierz **Włącz debugowanie kodu niezarządzanego** pole wyboru, aby uwzględnić kodu natywnego w sesji debugowania.

 Domyślnie program Visual Studio debuguje kodu macierzystego w aplikacji C++.

 W aplikacjach C++ można debugować określone typy kodu, które znajdują się w części aplikacji zamiast lub oprócz kodu natywnego. Określ kod do debugowania **typ debugera** listy na **debugowanie** strony właściwości projektu aplikacji.

 Wybierz jedną z tych debugerów z **proces aplikacji** listy:

|||
|-|-|
|**Jenom skript**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu są ignorowane.|
|**Tylko w trybie macierzystym**|Debugowanie kodu natywnego języka C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Tylko zarządzany**|Debugowanie kodu zarządzanego w aplikacji. Kod języka JavaScript i kodu natywnego języka C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowany.|
|**Tylko procesor GPU**|Debugowanie kodu natywnego języka C++ jest uruchamiany na jednostka przetwarzania grafiki (GPU).|

 ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

 W przypadku aplikacji Windows Store telefon, można także debugera do użycia dla procesów w tle z **proces zadania w tle**.

###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Opcjonalnie) Opóźnienie uruchamiania sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Po wybraniu tej opcji, aplikacja jest uruchomiona w debugerze po uruchomieniu na ekranie startowym lub umowy o aktywacji, lub gdy jest uruchomiona przez inny proces lub metody. Jeśli chcesz debugować zadanie w tle, gdy aplikacja nie jest uruchomiony, również opóźnić uruchomienie aplikacji.

 Aby opóźnić uruchomienie aplikacji, możesz wykonywać następujące czynności:

-   W przypadku aplikacji języka Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** na **debugowania** stronę właściwości.

-   W przypadku aplikacji Visual C++, wybierz **tak** z **Uruchom aplikację** listy na **debugowanie** stronę właściwości.

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Opcjonalnie) Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacji Windows Store, która jest zainstalowana w sposób standardowy jest niedozwolone wykonywania wywołań sieci do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji Windows Store, należy przetestować aplikację bez zwolnienia.

 Aby usunąć wykluczenie sprzężenie zwrotne sieci:

-   W przypadku aplikacji języka Visual C# i Visual Basic, wyczyść **Zezwalaj na sprzężenie zwrotne sieci** pole wyboru na **debugowania** stronę właściwości.

-   W przypadku aplikacji Visual C++, wybierz **nie** z **Zezwalaj na sprzężenie zwrotne sieci** listy na **debugowanie** stronę właściwości.

###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Opcjonalnie) Ponownie zainstaluje aplikację po rozpoczęciu debugowania
 Diagnozowanie problemów z instalacji i wstępnej konfiguracji aplikacji języka Visual C# lub Visual Basic, wybierz **Odinstaluj i ponownie zainstaluj Mój pakiet** na **debugowania** stronie właściwości, aby odtworzyć oryginalnej instalacji podczas uruchamiania debugowania. Ta opcja nie jest dostępna dla projektów Visual C++.

###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Opcjonalnie) Wyłączyć wymaganie uwierzytelniania można uruchomić debugera zdalnego
 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Domyślnie musisz podać poświadczenia, aby uruchomić zdalny debuger.

> [!IMPORTANT]
>  Istnieje możliwość uruchomienia zdalnego debugera w trybie bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.

 Aby usunąć wymaganie uwierzytelniania:

1. W przypadku aplikacji języka Visual C# i Visual Basic, wyczyść **uwierzytelnianie** pole wyboru na **debugowania** stronę właściwości.

2. W przypadku aplikacji Visual C++, wybierz **nie** z **wymagają uwierzytelniania** listy na **debugowanie** stronę właściwości.

   [W tym temacie](#BKMK_In_this_topic)

##  <a name="BKMK_Start_the_debugging_session"></a> Rozpocznij sesję debugowania

###  <a name="BKMK_Start_debugging__F5_"></a> Rozpocznij debugowanie (F5)
 Po wybraniu **Rozpocznij debugowanie** (klawiatury: F5) na **debugowania** menu programu Visual Studio uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawieszenie wykonywania, wystąpi wyjątek, lub aplikacja kończy się.

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Rozpocznij debugowanie (F5), ale opóźnić uruchomienie aplikacji
 Możesz ustawić aplikację, aby uruchomić tryb debugowania, ale początek metody innej niż debugera. Na przykład możesz zechcieć, debugowanie, uruchamianie aplikacji z Start menu lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

- Na **debugowanie** strona właściwości aplikacji (**debugowania** w programie Visual C++)

  -   W przypadku aplikacji języka Visual C# i Visual Basic, wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu**.

  -   W przypadku aplikacji Visual C++, wybierz **tak** z **Uruchom aplikację** listy.

- Wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).

- Rozpocznij tworzenie aplikacji z menu Start, kontrakt wykonywania lub innej procedury.

  Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

  . Aby uzyskać więcej informacji na temat debugowania zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Uruchom zainstalowaną aplikację w debugerze
 Po rozpoczęciu debugowania przy użyciu klawisza F5, Visual Studio tworzy aplikacja jest wdrażana, ustawia aplikację do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego pakietu debugowania zainstalowanej aplikacji. Ta procedura jest przydatna, gdy trzeba debugować aplikację, która została zainstalowana ze Sklepu Windows lub, jeśli pliki źródłowe dla aplikacji, lecz nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Aplikację można zainstalować na urządzeniu lokalnym lub można go na urządzeniu zdalnym.  Aplikację można rozpocząć natychmiast, lub można ustawić go do uruchamiania w debugerze, gdy jest uruchomiona przez inny proces lub metody, np. w menu Start lub przez kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Aby ustawić zainstalowanej aplikacji do uruchamiania w trybie debugowania, wykonaj następujące czynności:

> [!NOTE]
>  Aplikacja nie może być uruchomiona, po uruchomieniu tej procedury.

1. Na **debugowania** menu, wybierz **pakietu debugowania zainstalowanej aplikacji**

2. Z listy, wybierz jedną z następujących opcji:


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Maszyna lokalna**  |                                                                                                                Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchom Windows Store apps na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Symulator**    | Debugowanie aplikacji w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchom Windows Store aplikacji w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Komputer zdalny** |                          Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |


3. Wybierz aplikację z **zainstalowane pakiety aplikacji** listy.

4. Wybierz aparat debugowania do użycia z **debugować tego typu kodu** listy.

5. (Opcjonalnie). Wybierz **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** do debugowania aplikacji, gdy jest ona uruchamiana za pomocą innej metody, lub Aby debugować proces w tle.

   Po kliknięciu **Start**, aplikacja jest uruchomiona lub jest ustawiony do pracy w trybie debugowania.

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, musisz podać Debugowalny Menedżer pakietów do zestawu aplikacji do uruchamiania w trybie debugowania. Debugowalny Menedżer pakietów jest instalowany z narzędzia zdalne programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne, gdy potrzebujesz debugować aplikację już zainstalowane, takie jak aplikacja, która została zainstalowana z [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Dołączanie jest wymagany w przypadku, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Dołączanie debugera do aplikacji wymaga wykonania tych kroków:

1.  Ustaw aplikację do uruchamiania w trybie debugowania. Jest to niezbędne, gdy aplikacja nie jest uruchomiona.

2.  Uruchom aplikację. Aplikację można uruchomić z ekranu startowego, kontrakt wykonywania lub innej metody.

3.  Dołącz debuger do uruchomionej aplikacji.

####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Ustaw aplikację do uruchamiania w trybie debugowania

1.  Na urządzeniu, w którym aplikacja jest zainstalowana, należy zainstalować narzędzia zdalne programu Visual Studio. Zobacz [Instalowanie narzędzi zdalnych](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2.  Na ekranie startowym Wyszukaj `Debuggable Package Manager` , a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.

3.  Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawiera element PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4.  W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *Pełna_nazwa_pakietu* gdzie *Pełna_nazwa_pakietu* jest identyfikatorem element PackageFullName aplikacji.

####  <a name="BKMK_Attach_the_debugger"></a> Dołącz debuger
 Aby dołączyć debuger:

1. Na **debugowania** menu, wybierz **dołączyć do procesu**.

    **Dołączyć do procesu** pojawi się okno dialogowe.

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, należy określić urządzenie zdalne w **kwalifikator** pole. Można:

   -   Wprowadź nazwę w **kwalifikator** pole.

   -   Wybierz strzałkę w dół w **kwalifikator** pole, a następnie wybierz urządzenie z listy urządzeń dołączonych do przed.

   -   Wybierz **znaleźć** do wybierz urządzenie z listy urządzeń w danej podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w **dołączyć do** pola.

    Wybierz **wybierz** , a następnie wykonaj jedną z następujących czynności:

   -   Wybierz **automatycznie Określ typ kodu do debugowania**

   -   Wybierz **debugowania tych typów kodu** a następnie wybierz jeden lub więcej typów z listy.

4. W **dostępne procesy** wybierz proces aplikacji.

5. Wybierz **dołączyć**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

   [W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [nawigowanie po sesji debugowania (Xaml i C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)

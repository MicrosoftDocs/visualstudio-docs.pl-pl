---
title: Uruchamianie sesji debugowania dla aplikacji Store (JavaScript) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 630b2896e7446cf62982dd62ed12f9f7b7ca4aa9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427297"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Uruchamianie sesji debugowania dla aplikacji Store w programie Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji Windows Store napisanych w języku JavaScript i HTML5. Można uruchomić debugowania za pomocą pojedynczego naciśnięcia klawisza lub możesz skonfigurować sesję debugowania dla konkretnych scenariuszy, a następnie wybrać sposób, aby uruchomić aplikację.

> [!NOTE]
> Aby uzyskać aplikacje napisane w XAML i Visual C#, Visual C++ lub Visual Basic, zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="BKMK_In_this_topic"></a> W tym temacie
 [W tym temacie](#BKMK_In_this_topic)

 [Prosty sposób Rozpocznij debugowanie](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybór opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)

- [(Opcjonalnie) Opóźnienie uruchamiania aplikacji w sesji debugowania](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Opcjonalnie) Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)

  [Rozpocznij sesję debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale opóźnić uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Uruchom zainstalowaną aplikację w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

  [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Ustaw aplikację do uruchamiania w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Dołącz debuger](#BKMK_Attach_the_debugger)

## <a name="BKMK_The_easy_way_to_start_debugging"></a> Prosty sposób Rozpocznij debugowanie
 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Jeśli rozwiązanie zawiera projekty dla aplikacji Windows Store i Windows Store telefonu, upewnij się, że projekt, który chcesz debugować projekt startowy. W Eksploratorze rozwiązań, wybierz projekt, a następnie wybierz **Ustaw jako projekt startowy** z menu kontekstowego.

3. Naciśnij F5.

   ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji. Aby uzyskać więcej informacji, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a> Konfigurowanie sesji debugowania
 Ponieważ skrypt nie jest kompilowana, ustawienia konfiguracji i platformy kompilacji nie mają zastosowania. Jeśli debugujesz, C++ lub zarządzanego składnika, ustawić **konfiguracji** do **debugowania** i wybierz platformę docelową z **konfiguracji** okna dialogowego.

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otwórz stronę właściwości debugowania projektu

1. W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz **właściwości**.

2. Rozwiń **właściwości konfiguracji** węzeł, a następnie wybierz **debugowania**

### <a name="BKMK_Choose_the_build_configuration_options"></a> Wybór opcji konfiguracji kompilacji

1. Z **konfiguracji** wybierz **debugowania** lub **debugowania (aktywny)**.

2. Z **platformy** listy wybierz platformę docelową kompilacji dla. W większości przypadków **dowolny Procesor** jest najlepszym wyborem.

### <a name="BKMK_Choose_the_deployment_target"></a> Wybierz cel wdrożenia
 Można wdrażać i debugować aplikację na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na komputerze zdalnym. Wybierz obiekt docelowy z **debuger do uruchomienia** listy na **debugowanie** strony właściwości dla projektu.

 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Dla aplikacji Windows Store, wybierz jedną z następujących opcji z **urządzenie docelowe** listy:

|||
|-|-|
|**Maszyna lokalna**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchom Windows Store apps na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Symulator**|Debugowanie aplikacji w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchom Windows Store aplikacji w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Komputer zdalny**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Jeśli wybierzesz **maszyny zdalnej**, określ nazwę lub adres IP komputera zdalnego, w jednym z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego w **NazwaKomputera** pole.

- Wybierz strzałkę w dół w **NazwaKomputera** pole, a następnie wybierz  **\<zlokalizuj... >**. Następnie wybierz komputer zdalny z **wybierz połączenie ze zdalnym debugerem** okno dialogowe.

   ![Wybierz połączenie zdalnego debugera](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Okno dialogowe Wybierz połączenie ze zdalnym debugerem Wyświetla znajdujących się w lokalnej podsieci i maszyn, które są podłączone bezpośrednio do maszyny programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w **NazwaKomputera** pole.

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Dla aplikacji Windows Store telefonu, wybierz **urządzenia** lub jednego z emulatorów z **urządzenie docelowe** listy.

### <a name="BKMK_Choose_the_debugger_to_use"></a> Wybierz debuger do użycia
 Domyślnie debuger dołącza do kodu JavaScript w aplikacji. Istnieje możliwość debugowania natywnych języka C++ i kodzie zarządzanym składników aplikacji zamiast kodu JavaScript. Określ kod do debugowania **typ debugera** listy na **debugowanie** strony właściwości projektu aplikacji.

 Wybierz jedną z tych debugerów z **typ debugera** listy:

|||
|-|-|
|**Jenom skript**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu są ignorowane.|
|**Tylko w trybie macierzystym**|Debugowanie kodu natywnego języka C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Natywny ze skryptem**|Debugowanie kodu natywnego języka C++ i kodu JavaScript w aplikacji.|
|**Tylko zarządzany**|Debugowanie kodu zarządzanego w aplikacji. Kod języka JavaScript i kodu natywnego języka C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowany.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (Opcjonalnie) Opóźnienie uruchamiania aplikacji w sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Aplikacja jest uruchamiana w debugerze, po uruchomieniu z Start menu lub przez kontrakt aktywacji lub gdy jest ona uruchamiana przez inny proces lub metody. Opóźnienia uruchomienia umożliwia również debugowanie zdarzeń w tle w swojej aplikacji, które występują, gdy aplikacja nie jest uruchomiona.

 Możesz określić, czy opóźnienia uruchomienia aplikacji w **Uruchom aplikację** listy na **debugowanie** strony właściwości projektu aplikacji. Wybierz jedną z następujących opcji:

- Wybierz **nie** opóźnienia uruchomienia aplikacji.

- Wybierz **tak** Aby natychmiast uruchomić aplikację.

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Opcjonalnie) Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacji Windows Store, która jest zainstalowana w sposób standardowy jest niedozwolone wykonywania wywołań sieci do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji Windows Store, należy przetestować aplikację bez zwolnienia.

 Aby usunąć wykluczenie sprzężenie zwrotne sieci, wybierz **nie** z **Zezwalaj na sprzężenie zwrotne sieci** listy na **debugowanie** stronę właściwości.

## <a name="BKMK_Start_the_debugging_session"></a> Rozpocznij sesję debugowania

### <a name="BKMK_Start_debugging__F5_"></a> Rozpocznij debugowanie (F5)
 Po wybraniu **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5), program Visual Studio uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Rozpocznij debugowanie (F5), ale opóźnić uruchomienie aplikacji
 Możesz ustawić aplikację, aby uruchomić tryb debugowania, ale zapewnia on zostać uruchomiony przez metody innej niż debugera. Na przykład możesz zechcieć, debugowanie, uruchamianie aplikacji z Start menu lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

1. Na **debugowania** strony aplikacji właściwości projektu, wybierz polecenie **nie** z **Uruchom aplikację** listy.

2. Wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5).

3. Rozpocznij tworzenie aplikacji z menu Start, kontrakt wykonywania lub innej procedury.

   Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

   . Aby uzyskać więcej informacji na temat debugowania zadania w tle, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Uruchom zainstalowaną aplikację w debugerze
 Po rozpoczęciu debugowania przy użyciu klawisza F5, Visual Studio tworzy aplikacja jest wdrażana, ustawia aplikację do uruchamiania w trybie debugowania i następnie rozpoczyna się. Aby uruchomić aplikację, która jest już zainstalowana na urządzeniu, użyj okna dialogowego pakietu debugowania zainstalowanej aplikacji. Ta procedura jest przydatna, gdy trzeba debugować aplikację, która została zainstalowana ze Sklepu Windows lub, jeśli pliki źródłowe dla aplikacji, lecz nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Aplikację można zainstalować na urządzeniu lokalnym lub można go na urządzeniu zdalnym.  Aplikację można rozpocząć natychmiast, lub można ustawić go do uruchamiania w debugerze, gdy jest uruchomiona przez inny proces lub metody, np. w menu Start lub przez kontrakt aktywacji, można również ustawić aplikacji do uruchamiania w trybie debugowania, gdy chcesz debugować proces w tle bez uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Aby ustawić zainstalowanej aplikacji do uruchamiania w trybie debugowania, wykonaj następujące czynności:

> [!NOTE]
> Aplikacja nie może być uruchomiona, po uruchomieniu tej procedury.

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

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, musisz podać Debugowalny Menedżer pakietów do zestawu aplikacji do uruchamiania w trybie debugowania. Debugowalny Menedżer pakietów jest instalowany z narzędzia zdalne programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne, gdy potrzebujesz debugować aplikację już zainstalowane, takie jak aplikacja, która została zainstalowana z Windows przechowywania. Dołączanie jest wymagany w przypadku, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Aby dołączyć do aplikacji:

1. Ustaw aplikację do uruchamiania w trybie debugowania. Jest to niezbędne, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Aplikację można uruchomić z Start menu, kontrakt wykonywania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Ustaw aplikację do uruchamiania w trybie debugowania

1. Na urządzeniu, w którym aplikacja jest zainstalowana, należy zainstalować narzędzia zdalne programu Visual Studio. Zobacz [Instalowanie narzędzi zdalnych](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. W Start menu, wyszukaj `Debuggable Package Manager` , a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawiera element PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4. W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *Pełna_nazwa_pakietu* gdzie *Pełna_nazwa_pakietu* jest identyfikatorem element PackageFullName aplikacji.

### <a name="BKMK_Attach_the_debugger"></a> Dołącz debuger

> [!TIP]
> Uruchamianie aplikacji JavaScript w wystąpieniu procesu wwahost.exe. Innym aplikacjom JavaScript są uruchomione po dołączeniu do aplikacji, musisz jest znany identyfikator liczbowych procesu (PID) wwahost.exe działający w aplikacji.
>
> Najprostszym sposobem, aby rozwiązać ten problem dotyczy Zamknij wszystkie inne aplikacje języka JavaScript. W przeciwnym razie można otworzyć Menedżera zadań Windows, aby uruchomić aplikację i zanotuj identyfikatorów procesów wwahost.exe. Po określeniu proces do dołączenia w **dostępne procesy** okno dialogowe wwahost.exe aplikacji będzie mieć identyfikator, który jest inny niż te, które zostały zanotowane.

 Aby dołączyć debuger:

1. Na **debugowania** menu, wybierz **dołączyć do procesu**.

    **Dołączyć do procesu** pojawi się okno dialogowe.

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, należy określić urządzenie zdalne w **kwalifikator** pole. Można:

   - Wprowadź nazwę w **kwalifikator** pole.

   - Wybierz strzałkę w dół w **kwalifikator** pole, a następnie wybierz urządzenie z listy urządzeń dołączonych do przed.

   - Wybierz **znaleźć** do wybierz urządzenie z listy urządzeń w danej podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w **dołączyć do** pola.

    Wybierz **wybierz** , a następnie wykonaj jedną z następujących czynności:

   - Wybierz **automatycznie Określ typ kodu do debugowania**

   - Wybierz **debugowania tych typów kodu** a następnie wybierz jeden lub więcej typów z listy.

4. W **dostępne procesy** listy, wybierz odpowiedni **wwahost.exe** procesu. Użyj **tytuł** kolumny do identyfikowania Twojej aplikacji.

5. Wybierz **dołączyć**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

## <a name="see-also"></a>Zobacz też
 [Kontrolować wykonywanie w trakcie sesji debugowania (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) [wyzwalacza wstrzymania, wznowienia i zdarzeń Windows Store w tle)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

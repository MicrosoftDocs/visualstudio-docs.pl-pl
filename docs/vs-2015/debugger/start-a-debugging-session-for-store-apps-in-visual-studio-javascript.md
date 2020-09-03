---
title: Rozpocznij sesję debugowania dla aplikacji ze sklepu (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 634051d47b3462e2462c5592448b20f70d09ae71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531940"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Uruchamianie sesji debugowania dla aplikacji ze Sklepu w programie Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji ze sklepu Windows, które zostały zapisane w języku JavaScript i HTML5. Można rozpocząć debugowanie za pomocą jednego naciśnięcia klawisza lub można skonfigurować sesję debugowania dla konkretnych scenariuszy, a następnie wybrać sposób uruchamiania aplikacji.

> [!NOTE]
> W przypadku aplikacji pisanych w języku XAML i Visual C#, Visual C++ lub Visual Basic, zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [W tym temacie](#BKMK_In_this_topic)

 [Łatwy sposób rozpoczęcia debugowania](#BKMK_The_easy_way_to_start_debugging)

 [Skonfiguruj sesję debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybieranie opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz cel wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger do użycia](#BKMK_Choose_the_debugger_to_use)

- [Obowiązkowe Opóźnij uruchamianie aplikacji w sesji debugowania](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Obowiązkowe Wyłącz sprzężenia zwrotne sieci](#BKMK__Optional__Disable_network_loopbacks)

  [Rozpocznij sesję debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Uruchamianie zainstalowanej aplikacji w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

  [Dołącz debuger do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Ustawianie uruchamiania aplikacji w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Dołącz debuger](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a> Łatwy sposób rozpoczęcia debugowania
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Jeśli rozwiązanie zawiera projekty dla aplikacji ze sklepu Windows i sklepu Windows, upewnij się, że projekt, który ma być debugowany, jest projektem startowym. W obszarze Eksplorowanie rozwiązań wybierz projekt, a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu kontekstowego.

3. Naciśnij F5.

   ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Program Visual Studio kompiluje i uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona. Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a> Skonfiguruj sesję debugowania
 Ponieważ skrypt nie jest kompilowany, konfiguracja kompilacji i ustawienia platformy nie są stosowane. Jeśli debugujesz składnik C++ lub zarządzany, ustaw **konfigurację** na **Debuguj** i wybierz platformę docelową z okna dialogowego **konfiguracji** .

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Otwórz stronę właściwości debugowania dla projektu

1. W Eksplorator rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. Rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie** .

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** **Wybierz Debugowanie** lub **(aktywny) Debuguj**.

2. Z listy **platform** Wybierz platformę docelową do skompilowania. W większości przypadków najlepszym wyborem jest **każdy procesor CPU** .

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a> Wybierz cel wdrożenia
 Aplikację można wdrożyć i debugować na maszynie programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na komputerze zdalnym. Wybierz element docelowy z listy **debuger do uruchomienia** na stronie właściwości **debugowania** projektu.

 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 W przypadku aplikacji ze sklepu Windows wybierz jedną z następujących opcji z listy **urządzeń docelowych** :

|Opcja|Opis|
|-|-|
|**Maszyna lokalna**|Debuguj aplikację w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Symulator**|Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i rotacja urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu połączonym z maszyną lokalną za pośrednictwem intranetu lub połączonego bezpośrednio przy użyciu kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **maszyna zdalna**Określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego w polu **Nazwa komputera** .

- Wybierz strzałkę w dół w polu **Nazwa komputera** , a następnie wybierz polecenie **\<Locate...>** . Następnie wybierz opcję komputer zdalny z okna dialogowego **Wybieranie połączenia debugera zdalnego** .

   ![Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > W oknie dialogowym Wybieranie połączenia debugera zdalnego są wyświetlane maszyny znajdujące się w lokalnej podsieci i maszynach, które są bezpośrednio połączone z maszyną programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w polu **Nazwa komputera** .

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  W przypadku aplikacji dla Sklepu Windows Phone wybierz pozycję **urządzenie** lub jeden z emulatorów z listy **urządzeń docelowych** .

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Wybierz debuger do użycia
 Domyślnie debuger dołącza do kodu JavaScript w aplikacji. Możesz wybrać debugowanie natywnego języka C++ i zarządzanego kodu składników aplikacji zamiast kodu JavaScript. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowania** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **Typ debugera** :

|Typ|Opis|
|-|-|
|**Tylko skrypt**|Debuguj kod JavaScript w aplikacji. Kod zarządzany i kod natywny zostały zignorowane.|
|**Tylko natywny**|Debuguj natywny kod C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Natywny ze skryptem**|Debuguj natywny kod C++ i kod JavaScript w aplikacji.|
|**Tylko zarządzane**|Debuguj kod zarządzany w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debuguj natywny kod C/C++ i kod zarządzany w aplikacji. Kod JavaScript jest ignorowany.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> Obowiązkowe Opóźnij uruchamianie aplikacji w sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Możesz również rozpocząć sesję debugowania, ale opóźnić początek aplikacji. Aplikacja jest uruchamiana w debugerze, gdy jest uruchamiana z menu Start lub według kontraktu aktywacji, lub gdy jest uruchomiona przez inny proces lub metodę. Możesz również użyć opóźnionego startu, aby debugować zdarzenia w tle w aplikacji, które mają być wykonywane, gdy aplikacja nie jest uruchomiona.

 Należy określić, czy należy opóźnić uruchamianie aplikacji na liście **uruchamiania aplikacji** na stronie właściwości **debugowania** projektu aplikacji. Wybierz jedną z następujących opcji:

- Wybierz pozycję **nie** , aby opóźnić uruchamianie aplikacji.

- Wybierz opcję **tak** , aby natychmiast uruchomić aplikację.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Obowiązkowe Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacja ze sklepu Windows, która jest zainstalowana w standardowym sposobie, nie może wykonywać wywołań sieciowych na urządzeniu, na którym jest zainstalowana. Domyślnie wdrożenie programu Visual Studio tworzy wykluczenie z tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia testowanie procedur komunikacji na pojedynczym komputerze. Przed przesłaniem aplikacji do sklepu Windows należy przetestować aplikację bez wykluczania.

 Aby usunąć wykluczenie sprzężenia zwrotnego sieci, wybierz pozycję **nie** z listy **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a> Rozpocznij sesję debugowania

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a> Rozpocznij debugowanie (F5)
 Po wybraniu opcji **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5) program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji
 Można ustawić uruchamianie aplikacji w trybie debugowania, ale zezwolić na uruchomienie jej przez metodę inną niż debuger. Na przykład może być konieczne debugowanie uruchamiania aplikacji z menu Start lub debugowanie procesu w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

1. Na stronie **debugowanie** właściwości projektu aplikacji wybierz pozycję **nie** z listy **Uruchom aplikację** .

2. Wybierz **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

3. Uruchom aplikację z menu Start, kontraktu wykonywania lub przez inną procedurę.

   Aplikacja jest uruchamiana w trybie debugowania. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

   . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Uruchamianie zainstalowanej aplikacji w debugerze
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
   |   **Symulator**    | Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i rotacja urządzeń, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Maszyna zdalna** |                          Debuguj aplikację na urządzeniu połączonym z maszyną lokalną za pośrednictwem intranetu lub połączonego bezpośrednio przy użyciu kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Wybierz aplikację z listy **zainstalowane pakiety aplikacji** .

4. Wybierz aparat debugowania do użycia na liście **Debuguj ten typ kodu** .

5. (Opcjonalnie). Wybierz pozycję **nie uruchamiaj, ale Debuguj mój kod, gdy rozpocznie** debugowanie aplikacji, gdy jest uruchomiona przez inną metodę lub aby debugować proces w tle.

   Po kliknięciu przycisku **Rozpocznij**aplikacja zostanie uruchomiona lub jest uruchomiona w trybie debugowania.

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Menedżer pakietów możliwością debugowania jest instalowany z narzędziami zdalnymi programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne w przypadku konieczności debugowania już zainstalowanej aplikacji, takiej jak aplikacja zainstalowana ze sklepu Windows. Dołączanie jest wymagane, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może istnieć niestandardowy system kompilacji, który nie używa projektów ani rozwiązań programu Visual Studio.

 Aby dołączyć do aplikacji:

1. Ustaw aplikację do uruchamiania w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Możesz uruchomić aplikację z menu Start, kontraktu wykonywania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Ustawianie uruchamiania aplikacji w trybie debugowania

1. Zainstaluj narzędzia zdalne programu Visual Studio na urządzeniu, na którym zainstalowano aplikację. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. W menu Start Wyszukaj, `Debuggable Package Manager` a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell prawidłowo skonfigurowane dla polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawierają PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4. W wierszu polecenia programu PowerShell wpisz `Enable-AppxDebug` *PackageFullName* , gdzie *PackageFullName* jest identyfikatorem PackageFullName aplikacji.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a> Dołącz debuger

> [!TIP]
> Aplikacje JavaScript działają w wystąpieniu procesu wwahost.exe. Jeśli inne aplikacje JavaScript są uruchomione po dołączeniu do aplikacji, musisz znać identyfikator procesu liczbowego (PID) wwahost.exe, w którym działa aplikacja.
>
> Najprostszym sposobem postępowania z tą sytuacją jest zamknięcie wszystkich innych aplikacji JavaScript. W przeciwnym razie można otworzyć Menedżera zadań systemu Windows przed uruchomieniem aplikacji i zanotować identyfikatory procesów wwahost.exe. Po określeniu procesu dołączenia do okna dialogowego **dostępne procesy**  wwahost.exe aplikacji będzie mieć identyfikator inny niż te, które zostały odnotowane.

 Aby dołączyć debuger:

1. W menu **debugowanie** wybierz **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołącz do procesu** .

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **kwalifikator** . Można:

   - Wprowadź nazwę w polu **kwalifikator** .

   - Wybierz strzałkę w dół w polu **kwalifikator** i wybierz urządzenie z listy urządzeń, które zostały wcześniej dołączone do usługi.

   - Wybierz pozycję **Znajdź** , aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do** .

    Wybierz **pozycję Wybierz** , a następnie wykonaj jedną z następujących czynności:

   - Wybierz opcję **automatycznie Określ typ kodu do debugowania**

   - Wybierz **Debuguj te typy kodu** , a następnie wybierz jeden lub więcej typów z listy.

4. Z listy **dostępne procesy**  wybierz odpowiedni proces **wwahost.exe** . Użyj kolumny **title** , aby zidentyfikować aplikację.

5. Wybierz **Dołącz**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane do momentu, gdy punkt przerwania zostanie osiągnięty, zostanie wykonane ręcznie wstrzymanie wykonywania, wystąpił nieobsługiwany wyjątek lub aplikacja zostanie zakończona.

## <a name="see-also"></a>Zobacz też
 [Kontrola wykonywania w sesji debugowania (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [— Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) [Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

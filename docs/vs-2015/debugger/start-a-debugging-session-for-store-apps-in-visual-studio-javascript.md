---
title: Rozpoczynanie sesji debugowania aplikacji ze Sklepu (JavaScript) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302484"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Uruchamianie sesji debugowania dla aplikacji ze Sklepu w programie Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone](.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji ze Sklepu Windows napisanych w językach JavaScript i HTML5. Można rozpocząć debugowanie za pomocą pojedynczego naciśnięcia klawisza lub można skonfigurować sesję debugowania dla określonych scenariuszy, a następnie wybrać sposób uruchamiania aplikacji.

> [!NOTE]
> W przypadku aplikacji napisanych w językach XAML i Visual C#, Visual C++ lub Visual Basic zobacz [Uruchamianie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>W tym temacie
 [W tym temacie](#BKMK_In_this_topic)

 [Łatwy sposób na rozpoczęcie debugowania](#BKMK_The_easy_way_to_start_debugging)

 [Konfigurowanie sesji debugowania](#BKMK_Configure_the_debugging_session)

- [Otwórz stronę właściwości debugowania dla projektu](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Wybieranie opcji konfiguracji kompilacji](#BKMK_Choose_the_build_configuration_options)

- [Wybierz miejsce docelowe wdrożenia](#BKMK_Choose_the_deployment_target)

- [Wybierz debuger, którego chcesz użyć](#BKMK_Choose_the_debugger_to_use)

- [(Opcjonalnie) Opóźnienie uruchomienia aplikacji w sesji debugowania](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Opcjonalnie) Wyłączanie sprzężenia zwrotnego sieci](#BKMK__Optional__Disable_network_loopbacks)

  [Rozpoczynanie sesji debugowania](#BKMK_Start_the_debugging_session)

- [Rozpocznij debugowanie (F5)](#BKMK_Start_debugging__F5_)

- [Rozpocznij debugowanie (F5), ale opóźnij uruchomienie aplikacji](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Uruchamianie zainstalowanej aplikacji w debugerze](#BKMK_Start_an_installed_app_in_the_debugger)

  [Dołączanie debugera do uruchomionej aplikacji](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Ustawianie uruchamiania aplikacji w trybie debugowania](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Dołączanie debugera](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwy sposób na rozpoczęcie debugowania
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Jeśli rozwiązanie zawiera projekty dla aplikacji ze Sklepu Windows i Sklepu Windows Phone, upewnij się, że projekt, który chcesz debugować, jest projektem rozruchowym. W obszarze Eksplorowanie rozwiązania wybierz projekt, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu kontekstowego.

3. Naciśnij F5.

   ![Dotyczy tylko systemu Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio tworzy i uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja. Aby uzyskać więcej informacji, zobacz [Szybki start: Debugowanie HTML i CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Konfigurowanie sesji debugowania
 Ponieważ skrypt nie jest skompilowany, konfiguracja kompilacji i ustawienia platformy nie mają zastosowania. Jeśli debugowanie C++ lub składnik zarządzany, ustaw **konfigurację** do **debugowania** i wybierz platformę docelową z okna dialogowego **Konfiguracja.**

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu

1. W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. Rozwiń węzeł **Właściwości konfiguracji,** a następnie wybierz polecenie **Debugowanie**

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** wybierz pozycję **Debugowanie** lub **(Aktywne) Debugowanie**.

2. Z listy **Platforma** wybierz platformę docelową do utworzenia. W większości przypadków najlepszym wyborem jest **dowolny procesor.**

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Wybierz miejsce docelowe wdrożenia
 Aplikację można wdrożyć i debugować na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na komputerze zdalnym. Wybierz obiekt docelowy z **debugera, aby uruchomić** listę na stronie właściwości **Debugowanie** dla projektu.

 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 W przypadku aplikacji ze Sklepu Windows wybierz jedną z następujących opcji z listy **Urządzeń docelowych:**

|||
|-|-|
|**Maszyna lokalna**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulator**|Debuguj aplikację w symulatorze programu Visual Studio dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Symulator to okno pulpitu, które umożliwia debugowanie funkcji urządzenia, takich jak gesty dotykowe i obracanie urządzenia, które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debuguj aplikację na urządzeniu podłączonym do komputera lokalnego za pośrednictwem intranetu lub bezpośrednio połączonym za pomocą kabla Ethernet. Aby debugować zdalnie, narzędzia zdalne programu Visual Studio muszą być zainstalowane i uruchomione na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze Sklepu Windows na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **Komputer zdalny**należy określić nazwę lub adres IP komputera zdalnego na jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP urządzenia zdalnego w polu **Nazwa komputera.**

- Wybierz strzałkę w dół w polu **Nazwa maszyny** i wybierz polecenie ** \<Znajdź...>**. Następnie wybierz komputer zdalny z okna dialogowego **Wybieranie połączenia debugera zdalnego.**

   ![Wybieranie opcji Podłączenie zdalnego debugera](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > W oknie dialogowym Wybieranie zdalnego debugera połączenie wyświetla maszyny, które znajdują się w lokalnej podseczce i maszyny, które są bezpośrednio połączone z komputerem programu Visual Studio za pomocą kabla Ethernet. Aby określić inny komputer, wprowadź nazwę w polu **Nazwa komputera.**

  ![Dotyczy tylko systemu Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  W przypadku aplikacji ze Sklepu Windows Phone wybierz **pozycję Urządzenie** lub jeden z emulatorów z listy **urządzeń docelowych.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger, którego chcesz użyć
 Domyślnie debuger dołącza do kodu JavaScript w aplikacji. Można debugować natywnego języka C++ i zarządzanego kodu składników aplikacji zamiast kodu JavaScript. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowanie** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **Typ debugera:**

|||
|-|-|
|**Tylko skrypt**|Debugowanie kodu JavaScript w aplikacji. Kod zarządzany i kod macierzysty są ignorowane.|
|**Tylko natywny**|Debugowanie natywnego kodu C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Natywny ze skryptem**|Debugowanie natywnego kodu C++ i kodu JavaScript w aplikacji.|
|**Tylko zarządzane**|Debug kodu zarządzanego w aplikacji. Kod JavaScript i natywny kod C/C++ są ignorowane.|
|**Mieszane (zarządzane i rodzime)**|Debugowanie natywnego kodu C/C++ i kodu zarządzanego w aplikacji. Kod JavaScript jest ignorowany.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Opcjonalnie) Opóźnienie uruchomienia aplikacji w sesji debugowania
 Domyślnie visual studio natychmiast uruchamia aplikację po uruchomieniu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Aplikacja jest uruchamiana w debugerze, gdy jest uruchamiana z menu Start lub przez umowę aktywacji lub gdy jest uruchamiana przez inny proces lub metodę. Można również użyć opóźnionego startu do debugowania zdarzeń w tle w aplikacji, które mają wystąpić, gdy aplikacja nie jest uruchomiona.

 Należy określić, czy opóźnić uruchomienie aplikacji na liście **Uruchom aplikację** na **debugowanie** strony właściwości projektu aplikacji. Wybierz jedną z następujących opcji:

- Wybierz **pozycję Nie,** aby opóźnić uruchomienie aplikacji.

- Wybierz **pozycję Tak,** aby natychmiast uruchomić aplikację.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcjonalnie) Wyłączanie sprzężenia zwrotnego sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacja ze Sklepu Windows zainstalowana w standardowy sposób nie może nawiązywać połączeń sieciowych z urządzeniem, na które jest zainstalowana. Domyślnie wdrożenie programu Visual Studio tworzy zwolnienie z tej reguły dla wdrożonej aplikacji. To zwolnienie umożliwia testowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji do Sklepu Windows należy przetestować aplikację bez zwolnienia.

 Aby usunąć wyłączenie sprzężenia zwrotnego sieci, wybierz **nie** z listy Zezwalaj na **sprzężenie zwrotne sieci** na stronie właściwości **Debugowanie.**

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Rozpoczynanie sesji debugowania

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)
 Po **wybraniu opcji Rozpocznij debugowanie** w menu **debugowania** (klawiatura: F5), program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale opóźnij uruchomienie aplikacji
 Można ustawić aplikację do uruchamiania w trybie debugowania, ale niech zostanie uruchomiony przez metodę inną niż debuger. Na przykład można debugować uruchomienie aplikacji z menu Start lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące następujące

1. Na stronie **Debugowanie** właściwości projektu aplikacji wybierz pozycję **Nie** z listy **Uruchom aplikację.**

2. W menu **Debugowania** wybierz **polecenie Rozpocznij debugowanie** (klawiatura: F5).

3. Uruchom aplikację z menu Start, umowy wykonania lub według innej procedury.

   Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja.

   . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [Wyzwalanie zawieszania, wznawiania i zdarzeń w tle dla Sklepu Windows).](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchamianie zainstalowanej aplikacji w debugerze
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołączanie debugera do uruchomionej aplikacji
 Aby dołączyć debuger [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] do aplikacji, należy użyć Debuggable Package Manager, aby ustawić aplikację do uruchamiania w trybie debugowania. Debuggable Package Manager jest zainstalowany z visual studio zdalnych narzędzi.

 Dołączanie debugera do aplikacji jest przydatne, gdy trzeba debugować już zainstalowaną aplikację, taką jak aplikacja zainstalowana ze Sklepu Windows. Dołączanie jest wymagane, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład może mieć niestandardowy system kompilacji, który nie używa projektów lub rozwiązań programu Visual Studio.

 Aby dołączyć do aplikacji:

1. Ustaw aplikację tak, aby działała w trybie debugowania. Należy to zrobić, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Aplikację można uruchomić z menu Start, umowy wykonania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustawianie uruchamiania aplikacji w trybie debugowania

1. Zainstaluj narzędzia zdalne programu Visual Studio na urządzeniu, na którym jest zainstalowana aplikacja. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. W menu Start wyszukaj go, `Debuggable Package Manager` a następnie uruchom.

     Zostanie wyświetlone okno programu PowerShell poprawnie skonfigurowane dla polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, która zawiera `Get-AppxPackage` PackageFullName, wpisz w programie PowerShell monit.

4. W programie PowerShell `Enable-AppxDebug` monit wprowadź *PackageFullName* gdzie *PackageFullName* jest PackageFullName identyfikator aplikacji.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Dołączanie debugera

> [!TIP]
> Aplikacje JavaScript działają w wystąpieniu procesu wwahost.exe. Jeśli inne aplikacje JavaScript są uruchomione po dołączeniu do aplikacji, musisz znać identyfikator procesu numerycznego (PID) pliku wwahost.exe, w którym aplikacja jest uruchomiona.
>
> Najprostszym sposobem radzenia sobie z tą sytuacją jest zamknięcie wszystkich innych aplikacji JavaScript. W przeciwnym razie można otworzyć Menedżera zadań systemu Windows przed uruchomieniem aplikacji i zanotować identyfikatory procesów wwahost.exe. Po określeniu procesu dołączenia do w oknie dialogowym **Dostępne procesy,** wwahost.exe aplikacji będzie miał identyfikator, który jest inny niż te, które zostały odnotowane.

 Aby dołączyć debuger:

1. W menu **Debugowanie** wybierz polecenie **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołączanie do procesu.**

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **Kwalifikator.** Możesz:

   - Wprowadź nazwę w polu **Kwalifikacje.**

   - Wybierz strzałkę w dół w polu **Kwalifikacje** i wybierz urządzenie z listy urządzeń, do których wcześniej był dołączony.

   - Wybierz **pozycję Znajdź,** aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do.**

    Wybierz **pozycję Wybierz,** a następnie wykonaj jedną z następujących czynności:

   - Wybierz **pozycję Automatycznie określaj typ kodu do debugowania**

   - Wybierz **pozycję Debugowanie tych typów kodu,** a następnie wybierz jeden lub więcej typów z listy.

4. Na liście **Dostępne procesy** wybierz odpowiedni proces **wwahost.exe.** Użyj kolumny **Tytuł,** aby zidentyfikować aplikację.

5. Wybierz **pozycję Dołącz**.

   Visual Studio dołącza debugera do procesu. Wykonywanie jest kontynuowane, dopóki nie zostanie osiągnięty punkt przerwania, ręcznie zawiesić wykonanie, wystąpi nieobsługiowany wyjątek lub kończy się aplikacja.

## <a name="see-also"></a>Zobacz też
 [Sterowanie wykonywaniem w szybki start sesji debugowania (JavaScript):](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Debugowanie HTML i css](../debugger/quickstart-debug-html-and-css.md) [wyzwalacz zawiesić, wznowić i zdarzenia w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

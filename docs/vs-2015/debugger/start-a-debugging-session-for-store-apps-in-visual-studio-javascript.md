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
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406342"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Uruchamianie sesji debugowania dla aplikacji Store w programie Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 W tym temacie opisano sposób uruchamiania sesji debugowania dla aplikacji Windows Store napisanych w języku JavaScript i HTML5. Można uruchomić debugowania za pomocą pojedynczego naciśnięcia klawisza lub możesz skonfigurować sesję debugowania dla konkretnych scenariuszy, a następnie wybrać sposób, aby uruchomić aplikację.

> [!NOTE]
> W przypadku aplikacji pisanych w języku XAML C#i wizualizacji, wizualizacji C++lub Visual Basic, zobacz [Rozpoczynanie sesji debugowania C#( C++ VB, i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="BKMK_In_this_topic"></a>W tym temacie
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

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Łatwy sposób rozpoczęcia debugowania
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Otwórz rozwiązanie aplikacji w programie Visual Studio.

2. Jeśli rozwiązanie zawiera projekty dla aplikacji Windows Store i Windows Store telefonu, upewnij się, że projekt, który chcesz debugować projekt startowy. W obszarze Eksplorowanie rozwiązań wybierz projekt, a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu kontekstowego.

3. Naciśnij F5.

   ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio kompiluje i uruchamia aplikację w debugerze. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji. Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a>Skonfiguruj sesję debugowania
 Ponieważ skrypt nie jest kompilowana, ustawienia konfiguracji i platformy kompilacji nie mają zastosowania. C++ Jeśli debugujesz składnik lub zarządzasz, ustaw **konfigurację** na **Debuguj** i wybierz platformę docelową z okna dialogowego **konfiguracji** .

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Otwórz stronę właściwości debugowania dla projektu

1. W Eksploratorze rozwiązań wybierz projekt. W menu skrótów wybierz polecenie **Właściwości**.

2. Rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie** .

### <a name="BKMK_Choose_the_build_configuration_options"></a>Wybieranie opcji konfiguracji kompilacji

1. Z listy **Konfiguracja** **Wybierz Debugowanie** lub **(aktywny) Debuguj**.

2. Z listy **platform** Wybierz platformę docelową do skompilowania. W większości przypadków najlepszym wyborem jest **każdy procesor CPU** .

### <a name="BKMK_Choose_the_deployment_target"></a>Wybierz cel wdrożenia
 Można wdrażać i debugować aplikację na komputerze programu Visual Studio, w symulatorze programu Visual Studio na komputerze lokalnym lub na komputerze zdalnym. Wybierz element docelowy z listy **debuger do uruchomienia** na stronie właściwości **debugowania** projektu.

 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 W przypadku aplikacji ze sklepu Windows wybierz jedną z następujących opcji z listy **urządzeń docelowych** :

|||
|-|-|
|**Komputer lokalny**|Debugowanie aplikacji w bieżącej sesji na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Wykorzystaniem**|Debuguj aplikację w symulatorze programu Visual Studio dla aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Symulator jest oknem pulpitu, które umożliwia debugowanie funkcji urządzeniami — takich jak gestów dotykowych i obracanie urządzeń — które nie są dostępne na komputerze lokalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Maszyna zdalna**|Debugowanie aplikacji na urządzeniu, do którego jest podłączony do komputera lokalnego za pośrednictwem intranetu lub podłączone bezpośrednio za pomocą kabla Ethernet. Zdalne debugowanie narzędzia zdalne programu Visual Studio musi być zainstalowana i uruchomiona na urządzeniu zdalnym. Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 W przypadku wybrania opcji **maszyna zdalna**Określ nazwę lub adres IP komputera zdalnego w jeden z następujących sposobów:

- Wprowadź nazwę lub adres IP komputera zdalnego w polu **Nazwa komputera** .

- Wybierz strzałkę w dół w polu **Nazwa komputera** , a następnie wybierz polecenie **\<Znajdź... >** . Następnie wybierz opcję komputer zdalny z okna dialogowego **Wybieranie połączenia debugera zdalnego** .

   ![Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Okno dialogowe Wybierz połączenie ze zdalnym debugerem Wyświetla znajdujących się w lokalnej podsieci i maszyn, które są podłączone bezpośrednio do maszyny programu Visual Studio za pomocą kabla Ethernet. Aby określić inną maszynę, wprowadź nazwę w polu **Nazwa komputera** .

  ![Dotyczy tylko Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  W przypadku aplikacji dla Sklepu Windows Phone wybierz pozycję **urządzenie** lub jeden z emulatorów z listy **urządzeń docelowych** .

### <a name="BKMK_Choose_the_debugger_to_use"></a>Wybierz debuger do użycia
 Domyślnie debuger dołącza do kodu JavaScript w aplikacji. Istnieje możliwość debugowania natywnych języka C++ i kodzie zarządzanym składników aplikacji zamiast kodu JavaScript. Należy określić kod do debugowania na liście **Typ debugera** na stronie właściwości **debugowania** projektu aplikacji.

 Wybierz jeden z tych debugerów z listy **Typ debugera** :

|||
|-|-|
|**Tylko skrypt**|Debugowanie kodu JavaScript w aplikacji. Kodu zarządzanego i natywnego kodu są ignorowane.|
|**Tylko natywny**|Debugowanie kodu natywnego języka C/C++ w aplikacji. Kod zarządzany i kod JavaScript są ignorowane.|
|**Natywny ze skryptem**|Debugowanie kodu natywnego języka C++ i kodu JavaScript w aplikacji.|
|**Tylko zarządzane**|Debugowanie kodu zarządzanego w aplikacji. Kod języka JavaScript i kodu natywnego języka C/C++ są ignorowane.|
|**Mieszany (zarządzany i natywny)**|Debugowanie kodu C/C++ natywnego i zarządzanego kodu w aplikacji. Kod JavaScript jest ignorowany.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Obowiązkowe Opóźnij uruchamianie aplikacji w sesji debugowania
 Domyślnie program Visual Studio natychmiast uruchamia aplikację po rozpoczęciu debugowania. Można również uruchomić sesję debugowania, ale opóźnić uruchomienie aplikacji. Aplikacja jest uruchamiana w debugerze, po uruchomieniu z Start menu lub przez kontrakt aktywacji lub gdy jest ona uruchamiana przez inny proces lub metody. Opóźnienia uruchomienia umożliwia również debugowanie zdarzeń w tle w swojej aplikacji, które występują, gdy aplikacja nie jest uruchomiona.

 Należy określić, czy należy opóźnić uruchamianie aplikacji na liście **uruchamiania aplikacji** na stronie właściwości **debugowania** projektu aplikacji. Wybierz jedną z następujących opcji:

- Wybierz pozycję **nie** , aby opóźnić uruchamianie aplikacji.

- Wybierz opcję **tak** , aby natychmiast uruchomić aplikację.

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Obowiązkowe Wyłącz sprzężenia zwrotne sieci
 ![Dotyczy tylko systemu Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Ze względów bezpieczeństwa aplikacji Windows Store, która jest zainstalowana w sposób standardowy jest niedozwolone wykonywania wywołań sieci do zainstalowania na urządzeniu. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji Windows Store, należy przetestować aplikację bez zwolnienia.

 Aby usunąć wykluczenie sprzężenia zwrotnego sieci, wybierz pozycję **nie** z listy **Zezwalaj na sprzężenie zwrotne sieci** na stronie właściwości **debugowania** .

## <a name="BKMK_Start_the_debugging_session"></a>Rozpocznij sesję debugowania

### <a name="BKMK_Start_debugging__F5_"></a>Rozpocznij debugowanie (F5)
 Po wybraniu opcji **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5) program Visual Studio uruchamia aplikację z dołączonym debugerem. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Rozpocznij debugowanie (F5), ale Opóźnij uruchomienie aplikacji
 Możesz ustawić aplikację, aby uruchomić tryb debugowania, ale zapewnia on zostać uruchomiony przez metody innej niż debugera. Na przykład możesz zechcieć, debugowanie, uruchamianie aplikacji z Start menu lub debugować proces w tle w aplikacji bez uruchamiania aplikacji. Aby opóźnić uruchomienie aplikacji, wykonaj następujące czynności:

1. Na stronie **debugowanie** właściwości projektu aplikacji wybierz pozycję **nie** z listy **Uruchom aplikację** .

2. Wybierz **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5).

3. Rozpocznij tworzenie aplikacji z menu Start, kontrakt wykonywania lub innej procedury.

   Aplikacja uruchamia się w trybie debugowania. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

   . Aby uzyskać więcej informacji na temat debugowania zadań w tle, zobacz [wyzwalacze wstrzymywanie, wznawiania i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Uruchamianie zainstalowanej aplikacji w debugerze
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

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Dołącz debuger do uruchomionej aplikacji
 Aby dołączyć debuger do aplikacji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], należy użyć Menedżera pakietów możliwością debugowania, aby skonfigurować aplikację do uruchamiania w trybie debugowania. Debugowalny Menedżer pakietów jest instalowany z narzędzia zdalne programu Visual Studio.

 Dołączanie debugera do aplikacji jest przydatne, gdy potrzebujesz debugować aplikację już zainstalowane, takie jak aplikacja, która została zainstalowana z Windows przechowywania. Dołączanie jest wymagany w przypadku, gdy masz pliki źródłowe dla aplikacji, ale nie masz projektu programu Visual Studio dla aplikacji. Na przykład Niewykluczone, że system kompilacji niestandardowej, która nie korzysta z programu Visual Studio projektów i rozwiązań.

 Aby dołączyć do aplikacji:

1. Ustaw aplikację do uruchamiania w trybie debugowania. Jest to niezbędne, gdy aplikacja nie jest uruchomiona.

2. Uruchom aplikację. Aplikację można uruchomić z Start menu, kontrakt wykonywania lub innej metody.

3. Dołącz debuger do uruchomionej aplikacji.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Ustawianie uruchamiania aplikacji w trybie debugowania

1. Na urządzeniu, w którym aplikacja jest zainstalowana, należy zainstalować narzędzia zdalne programu Visual Studio. Zobacz [Instalowanie narzędzi zdalnych](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. W menu Start Wyszukaj `Debuggable Package Manager` a następnie uruchom go.

     Zostanie wyświetlone okno programu PowerShell, poprawnie skonfigurowany na potrzeby polecenia cmdlet AppxDebug.

3. Aby włączyć debugowanie aplikacji, należy określić identyfikator element PackageFullName aplikacji. Aby wyświetlić listę wszystkich aplikacji, które zawierają PackageFullName, wpisz `Get-AppxPackage` w wierszu polecenia programu PowerShell.

4. W wierszu polecenia programu PowerShell wprowadź `Enable-AppxDebug` *PackageFullName* , gdzie *PackageFullName* jest identyfikatorem PackageFullName aplikacji.

### <a name="BKMK_Attach_the_debugger"></a>Dołącz debuger

> [!TIP]
> Uruchamianie aplikacji JavaScript w wystąpieniu procesu wwahost.exe. Innym aplikacjom JavaScript są uruchomione po dołączeniu do aplikacji, musisz jest znany identyfikator liczbowych procesu (PID) wwahost.exe działający w aplikacji.
>
> Najprostszym sposobem, aby rozwiązać ten problem dotyczy Zamknij wszystkie inne aplikacje języka JavaScript. W przeciwnym razie można otworzyć Menedżera zadań Windows, aby uruchomić aplikację i zanotuj identyfikatorów procesów wwahost.exe. Po określeniu procesu dołączenia do okna dialogowego **dostępne procesy** program wwahost. exe aplikacji będzie miał identyfikator inny niż te, które zostały zanotowane.

 Aby dołączyć debuger:

1. W menu **debugowanie** wybierz **Dołącz do procesu**.

    Zostanie wyświetlone okno dialogowe **Dołącz do procesu** .

2. Aby dołączyć do aplikacji na urządzeniu zdalnym, określ urządzenie zdalne w polu **kwalifikator** . Możesz:

   - Wprowadź nazwę w polu **kwalifikator** .

   - Wybierz strzałkę w dół w polu **kwalifikator** i wybierz urządzenie z listy urządzeń, które zostały wcześniej dołączone do usługi.

   - Wybierz pozycję **Znajdź** , aby wybrać urządzenie z listy urządzeń w podsieci lokalnej.

3. Określ typ kodu, który chcesz debugować w polu **Dołącz do** .

    Wybierz **pozycję Wybierz** , a następnie wykonaj jedną z następujących czynności:

   - Wybierz opcję **automatycznie Określ typ kodu do debugowania**

   - Wybierz **Debuguj te typy kodu** , a następnie wybierz jeden lub więcej typów z listy.

4. Na liście **dostępne procesy** wybierz odpowiedni proces **wwahost. exe** . Użyj kolumny **title** , aby zidentyfikować aplikację.

5. Wybierz **Dołącz**.

   Program Visual Studio dołącza debuger do procesu. Wykonywanie jest kontynuowane, dopóki punkt przerwania zostanie osiągnięty, ręcznie zawieszenie wykonywania, wystąpi nieobsługiwany wyjątek, lub kończy się w aplikacji.

## <a name="see-also"></a>Zobacz też
 [Kontrola wykonywania w sesji debugowania (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [— Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) [Wyzwalanie wstrzymania, wznowienia i zdarzeń w tle dla Sklepu Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

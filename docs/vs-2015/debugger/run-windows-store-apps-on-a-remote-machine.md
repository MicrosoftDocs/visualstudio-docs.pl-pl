---
title: Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e53e05d9df5a7bbdca5fd8a9b74dd9325dc7aae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794811"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Uruchamianie aplikacji ze Sklepu Windows na maszynie zdalnej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko systemu Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aplikacja Remote Tools programu Visual Studio umożliwia uruchamianie, debugowanie, profilowanie i testowanie aplikacji ze sklepu Windows działającej na jednym urządzeniu z innego komputera, na którym działa program Visual Studio. Uruchamianie na urządzeniu zdalnym może być szczególnie skuteczne, gdy komputer z programem Visual Studio nie obsługuje funkcji specyficznych dla aplikacji ze sklepu Windows, takich jak Touch, lokalizacja geograficzna i orientacja fizyczna. W tym temacie opisano procedury konfigurowania i uruchamiania sesji zdalnej.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie  
 Możesz dowiedzieć się:  
  
 [Wymagania wstępne](#BKMK_Prerequisites)  
  
 [Bezpieczeństwo](#BKMK_Security)  
  
 [Jak połączyć się bezpośrednio z urządzeniem zdalnym](#BKMK_DirectConnect)  
  
 [Instalowanie narzędzi zdalnych](#BKMK_Installing_the_Remote_Tools)  
  
 [Uruchamianie Monitora zdalnego debugera](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Konfigurowanie zdalnego debugera](#BKMK_ConfigureRemoteDebugger)  
  
 [Konfigurowanie projektu programu Visual Studio na potrzeby debugowania zdalnego](#BKMK_ConnectVS)  
  
- [Wybieranie urządzenia zdalnego dla projektów C# i Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Wybieranie urządzenia zdalnego dla projektów JavaScript i C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Uruchamianie zdalnej sesji debugowania](#BKMK_RunRemoteDebug)  
  
## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Wymagany  
 Aby debugować na urządzeniu zdalnym:  
  
- Urządzenie zdalne i komputer z programem Visual Studio muszą być połączone przez sieć lub podłączone bezpośrednio za pomocą kabla Ethernet. Debugowanie przez Internet nie jest obsługiwane.  
  
- Na urządzeniu zdalnym musi być zainstalowana licencja dewelopera.  
  
- Na urządzeniu zdalnym muszą być uruchomione składniki debugowania zdalnego.  
  
- Aby skonfigurować zaporę podczas instalacji, należy mieć uprawnienia administratora na urządzeniu zdalnym. Aby można było uruchomić zdalny debuger lub połączyć się z nim, musisz mieć dostęp użytkownika do zdalnego urządzenia.  
  
## <a name="security"></a><a name="BKMK_Security"></a> Bezpieczeństw  
 Domyślnie zdalny debuger używa uwierzytelniania systemu Windows.  
  
> [!WARNING]
> Możesz również uruchomić zdalny debuger w trybie bez uwierzytelniania, ale nie jest to zdecydowanie zalecane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.  
  
## <a name="how-to-connect-directly-to-a-remote-device"></a><a name="BKMK_DirectConnect"></a> Jak połączyć się bezpośrednio z urządzeniem zdalnym  
 Aby połączyć się bezpośrednio z urządzeniem zdalnym, podłącz komputer z programem Visual Studio do urządzenia przy użyciu standardowego kabla Ethernet. Jeśli urządzenie nie ma portu sieci Ethernet, do nawiązania połączenia z kablem można użyć karty USB do sieci Ethernet.  
  
## <a name="installing-the-remote-tools"></a><a name="BKMK_Installing_the_Remote_Tools"></a> Instalowanie narzędzi zdalnych  
  
> [!NOTE]
> **Wersje i aktualizacje**  
>   
> **Remote Tools for Visual Studio 2015** nie są obsługiwane we wcześniejszych wersjach programu Visual Studio.  
>   
> Zalecamy zainstalowanie wersji aktualizacji Remote Tools for Visual Studio 2015 zgodnej z wersją aktualizacji instalacji programu Visual Studio.  
>   
> Debuger VS jest zgodny z dowolną kombinacją wersji programu VS 2015 i narzędzi zdalnych dla programu VS 2015. Najnowsze funkcje w programie Visual Studio wymagają jednak zarówno Visual Studio, jak i narzędzi zdalnych, aby mieć najbardziej aktualne wersje.  
>   
> Inne narzędzia diagnostyczne mogą wymagać tych samych wersji narzędzi zdalnych i programu Visual Studio.  
  
 **Instalowanie składników zdalnego debugowania na urządzeniu zdalnym**  
  
 Aby uruchomić lub zapisać program instalacyjny dla narzędzi zdalnych, wybierz jedno z łączy w tej tabeli, które pasuje do używanej wersji programu Visual Studio:  
  
|Wersja|Link|Uwagi|
|-|-|-|
|Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do grupy bezpłatna Visual Studio Dev Essentials lub po prostu zaloguj się przy użyciu ważnej subskrypcji programu Visual Studio. Następnie w razie potrzeby ponownie otwórz link. Zawsze pobieraj wersję zgodną z systemem operacyjnym urządzenia (wersja x86, x64 lub ARM)|
|Visual Studio 2015 (starsza wersja)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do grupy bezpłatna Visual Studio Dev Essentials lub po prostu zaloguj się przy użyciu ważnej subskrypcji programu Visual Studio. Następnie w razie potrzeby ponownie otwórz link. Zawsze pobieraj wersję zgodną z systemem operacyjnym urządzenia (wersja x86, x64 lub ARM)|
|Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Strona pobierania w dokumentacji Visual Studio 2013|
  
 Możesz pobrać program instalacyjny lub go od razu uruchomić. Po uruchomieniu programu instalacyjnego Zaakceptuj umowę użytkownika, a następnie wybierz **Zainstaluj**.  
  
 Domyślnie składniki debugowania zdalnego są instalowane w folderze **C:\Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger** .  
  
## <a name="starting-the-remote-debugger-monitor"></a><a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Uruchamianie Monitora zdalnego debugera  
  
> [!NOTE]
> Ponieważ zdalny debuger konfiguruje zaporę tak, aby zezwalała na komunikację z hostem programu Visual Studio, musisz mieć uprawnienia administratora na urządzeniu zdalnym po pierwszym uruchomieniu zdalnego debugera.  
  
 Po zainstalowaniu narzędzi zdalnych wybierz **zdalny debuger** na ekranie **startowym** . **Konfiguracja zdalnego debugowania** pojawia się po pierwszym uruchomieniu zdalnego debugera.  
  
 W oknie dialogowym **Konfiguracja debugowania zdalnego** :  
  
1. Jeśli nie zainstalowano interfejsu API usług sieci Web systemu Windows, wybierz pozycję **Zainstaluj** .  
  
2. W oknie **Konfigurowanie zapory systemu Windows** wybierz sieci, do których chcesz zezwolić na połączenia. Włączone są tylko te sieci, do których urządzenie jest obecnie połączone. Musisz wybrać co najmniej jedną sieć.  
  
3. Wybierz pozycję **Konfiguruj zdalne debugowanie** , aby ustawić opcje zapory i uruchom zdalny debuger.  Otwórz okno dialogowe **Monitor zdalnego debugowania programu Visual Studio** , aby przyznać użytkownikom uprawnienia do zdalnych narzędzi i ustawić inne opcje zaawansowane.  
  
4. Zostanie wyświetlone okno dialogowe **Monitor zdalnego debugowania programu Visual Studio** . Możesz nadać użytkownikom uprawnienia do zdalnych narzędzi i ustawić inną zaawansowaną opcję z tego okna dialogowego.  
  
## <a name="configuring-the-remote-debugger"></a><a name="BKMK_ConfigureRemoteDebugger"></a> Konfigurowanie zdalnego debugera  
 Używasz dwóch narzędzi do modyfikacji konfiguracji zdalnego debugera.  
  
1. W menu **Narzędzia** programu **Visual Studio Monitor zdalnego debugowania**:  
  
   1. Wybierz **Opcje** , aby zmienić numer portu, tryb uwierzytelniania lub interwał limitu czasu zdalnego debugera.  
  
   2. Wybierz **uprawnienia** do dodawania lub usuwania użytkowników, którzy mają uprawnienia do zdalnego debugowania.  
  
       > [!NOTE]
       > Uprawnienia muszą być udzielane każdemu kontu użytkownika, które debuguje się zdalnie.  
  
   **Kreator konfiguracji zdalnego debugera** służy do ustawiania opcji zaawansowanych dla zdalnego debugera. Aby otworzyć kreatora, wybierz **Kreatora konfiguracji debugera zdalnego** na ekranie startowym.  
  
2. Na stronie **konfigurowanie zdalny debuger programu Visual Studio** można wybrać uruchamianie zdalnego debugera jako usługi. W większości przypadków uruchamianie jako usługa nie jest wymagane.  
  
3. Na stronie **Konfigurowanie zapory systemu Windows na potrzeby debugowania** można dodać lub usunąć typ sieci, z którymi zdalny debuger ma nawiązać połączenie. Włączone są tylko te sieci, do których urządzenie jest obecnie połączone. Musisz wybrać co najmniej jedną sieć.  
  
## <a name="configuring-the-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio na potrzeby debugowania zdalnego  
 Należy określić urządzenie zdalne, z którym będzie nawiązywane połączenie we właściwościach projektu. Procedura różni się w zależności od języka programowania. Możesz wpisać nazwę sieciową urządzenia zdalnego lub wybrać ją z okna dialogowego wybierz połączenie debugera zdalnego.  
  
 ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 W oknie dialogowym są wyświetlane tylko te urządzenia, które znajdują się w lokalnej podsieci komputera programu Visual Studio i uruchomiono zdalny debuger.  
  
> [!TIP]
> Jeśli masz problemy z połączeniem się z urządzeniem zdalnym, spróbuj wprowadzić adres IP urządzenia. Aby określić adres IP urządzenia, Otwórz okno wiersza polecenia, a następnie wpisz **polecenie ipconfig**. Adres IP jest wyświetlany jako **adres IPv4**.  
  
### <a name="choosing-the-remote-device-for-c-and-visual-basic-projects"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Wybieranie urządzenia zdalnego dla projektów C# i Visual Basic  
 ![Zarządzane właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. Wybierz nazwę projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Właściwości** z menu skrótów.  
  
2. Wybierz pozycję **Debuguj**.  
  
3. Wybierz pozycję **maszyna zdalna** z listy **urządzeń docelowych** .  
  
4. Wprowadź nazwę sieciową urządzenia zdalnego w polu **maszyna zdalna** lub wybierz pozycję **Znajdź** , aby wybrać urządzenie w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .  
  
### <a name="choosing-the-remote-device-for-javascript-and-c-projects"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Wybieranie urządzenia zdalnego dla projektów JavaScript i C++  
 ![C&#43;&#43; właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. Wybierz nazwę projektu w Eksplorator rozwiązań a następnie wybierz polecenie **Właściwości** z menu skrótów.  
  
2. Rozwiń węzeł **Właściwości konfiguracji** , a następnie wybierz pozycję **debugowanie**.  
  
3. Wybierz **zdalny debuger** z listy **debuger do uruchomienia** .  
  
4. Wprowadź nazwę sieciową urządzenia zdalnego w polu **Nazwa komputera** lub wybierz strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .  
  
## <a name="running-a-remote-debugging-session"></a><a name="BKMK_RunRemoteDebug"></a> Uruchamianie zdalnej sesji debugowania  
 Uruchamianie, zatrzymywanie i nawigowanie po zdalnej sesji debugowania odbywa się tak samo, jak w przypadku sesji lokalnej. Przed rozpoczęciem debugowania upewnij się, że Monitor zdalnego debugowania jest uruchomiona na urządzeniu zdalnym.  
  
 Następnie wybierz **Rozpocznij debugowanie** w menu **debugowanie** (klawiatura: F5). Projekt zostanie ponownie skompilowany, a następnie wdrożony na urządzeniu zdalnym i uruchomiony na nim. Debuger wstrzymuje wykonywanie w punktach przerwania i można wykonać krok po kroku, przekroczenie i wyjście z kodu. Wybierz pozycję **Zatrzymaj debugowanie** , aby zakończyć sesję debugowania i zamknąć aplikację zdalną. Aby uzyskać więcej informacji, zobacz [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji ze sklepu za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

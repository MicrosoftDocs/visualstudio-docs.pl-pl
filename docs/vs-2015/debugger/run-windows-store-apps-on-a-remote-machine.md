---
title: Uruchom Windows Store apps na komputerze zdalnym z | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 262391145b5cfc3889b2eea32df4e0955ed71b1a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756913"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Uruchamianie aplikacji ze Sklepu Windows na maszynie zdalnej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aplikacja Visual Studio Remote Tools umożliwia uruchamianie, debugowanie, profilowanie i testowanie aplikacji Windows Store, która jest uruchamiana na jednym urządzeniu z drugiego komputera z programem Visual Studio. Uruchamianie na urządzeniu zdalnym może być szczególnie efektywna, gdy komputer z programem Visual Studio nie obsługuje funkcji, które są specyficzne dla aplikacji Windows Store, takich jak dotyk, lokalizacji geograficznej i fizycznej orientacji. W tym temacie opisano procedury, aby skonfigurować i uruchomić sesję zdalną.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 Możesz dowiedzieć się:  
  
 [Wymagania wstępne](#BKMK_Prerequisites)  
  
 [Zabezpieczenia](#BKMK_Security)  
  
 [Jak połączyć się bezpośrednio na urządzeniu zdalnym](#BKMK_DirectConnect)  
  
 [Instalowanie narzędzi zdalnych](#BKMK_Installing_the_Remote_Tools)  
  
 [Uruchamianie monitora debugera zdalnego](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Konfigurowanie zdalnego debugera](#BKMK_ConfigureRemoteDebugger)  
  
 [Konfigurowanie projektu programu Visual Studio dla zdalnego debugowania](#BKMK_ConnectVS)  
  
- [Wybieranie urządzenia zdalnego dla projektów C# i Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [Wybieranie urządzenia zdalnego dla projektów języka C++ i JavaScript](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Uruchamianie sesji debugowania zdalnego](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Wymagania wstępne  
 Aby debugować na urządzeniu zdalnym:  
  
-   Urządzenie zdalne i komputer z programem Visual Studio muszą być połączone przez sieć lub podłączone bezpośrednio za pomocą kabla Ethernet. Debugowanie przez Internet nie jest obsługiwane.  
  
-   Licencja dewelopera musi być zainstalowany na urządzeniu zdalnym.  
  
-   Na urządzeniu zdalnym muszą być uruchomione składniki debugowania zdalnego.  
  
-   Musisz być administratorem na urządzeniu zdalnym Skonfiguruj zaporę, podczas instalacji. Musi mieć dostęp użytkownika do urządzenia zdalnego, aby uruchomić lub połączyć się ze zdalnym debugerem.  
  
##  <a name="BKMK_Security"></a> Zabezpieczenia  
 Domyślnie debuger zdalny używa uwierzytelniania Windows.  
  
> [!WARNING]
>  Istnieje również możliwość uruchomienia zdalnego debugera w trybie bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb Bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub wrogie działania.  
  
##  <a name="BKMK_DirectConnect"></a> Jak połączyć się bezpośrednio na urządzeniu zdalnym  
 Aby połączyć się bezpośrednio na urządzeniu zdalnym, należy połączyć komputer z programem Visual Studio na urządzeniu za pomocą standardowego kabla Ethernet. Jeśli urządzenie nie ma portu Ethernet, można użyć USB do adaptera Ethernet do łączenia z kablem.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Instalowanie narzędzi zdalnych  
  
> [!NOTE]
>  **Wersje i aktualizacje**  
>   
>  **Remote Tools for Visual Studio 2015** nie są obsługiwane we wcześniejszych wersjach programu Visual Studio.  
>   
>  Firma Microsoft zaleca, zainstaluj zaktualizowaną wersję narzędzi Remote Tools for Visual Studio 2015, która jest zgodna z wersją aktualizacji instalacji programu Visual Studio.  
>   
>  Debuger VS jest zgodny z dowolną kombinacją wersji VS 2015 i Remote Tools for VS 2015. Najnowsze funkcje w programie Visual Studio wymagają jednak zarówno Visual Studio, jak i narzędzi zdalnych, aby mieć najbardziej aktualne wersje.  
>   
>  Inne narzędzia diagnostyczne mogą wymagać tych samych wersji narzędzi zdalnych i programu Visual Studio.  
  
 **Instalowanie składników zdalnego debugowania na urządzeniu zdalnym**  
  
 Aby uruchomić lub zapisać program instalacyjny dla narzędzi zdalnych, wybierz jedno z łączy w tej tabeli, który odpowiada używanej wersji programu Visual Studio:  
  
|Wersja|Łącze|Uwagi|
|-|-|-|
|Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego grupy programu Visual Studio Dev Essentials lub po prostu Zaloguj się ważną subskrypcją programu Visual Studio. Następnie ponownie otwórz link w razie potrzeby. Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x 86, x64 lub wersji ARM)|
|Visual Studio 2015 (older)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego grupy programu Visual Studio Dev Essentials lub po prostu Zaloguj się ważną subskrypcją programu Visual Studio. Następnie ponownie otwórz link w razie potrzeby. Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x 86, x64 lub wersji ARM)|
|Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
  
 Możesz pobrać program instalacyjny lub go od razu uruchomić. Po uruchomieniu programu instalacyjnego zaakceptuj umowę z użytkownikiem, a następnie wybierz **zainstalować**.  
  
 Domyślnie składniki zdalnego debugowania są instalowane w **14.0\Common7\IDE\Remote C:\Program Files\Microsoft Visual Studio Debugger** folderu.  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Uruchamianie monitora debugera zdalnego  
  
> [!NOTE]
>  Ponieważ zdalny debuger konfiguruje zaporę, aby umożliwić komunikację z hostem programu Visual Studio, musisz być administratorem na urządzeniu zdalnym podczas uruchamiania zdalnego debugera po raz pierwszy.  
  
 Po zainstalowaniu narzędzi zdalnych wybierz **zdalny debuger** na **Start** ekranu. **Konfiguracja zdalnego debugowania** pojawia się podczas pierwszego uruchomienia zdalnego debugera.  
  
 Na **Konfiguracja zdalnego debugowania** okno dialogowe:  
  
1.  Jeśli API usług sieci Web Windows nie jest zainstalowany, wybierz opcję **instalacji**  
  
2.  W **skonfigurować zaporę Windows** grupy, wybierz, które chcesz zezwolić na połączenia z sieci. Tylko te sieci, które urządzenia jest aktualnie połączony z są włączone. Musisz wybrać co najmniej jedna sieć.  
  
3.  Wybierz **Konfiguruj zdalne debugowanie** ustawić opcje zapory i uruchomić zdalny debuger.  Otwórz **zdalny Monitor debugowania Visual Studio** okno dialogowe, aby udzielić użytkownikom uprawnień do narzędzi zdalnych i ustawić inne opcje zaawansowane.  
  
4.  **Zdalny Monitor debugowania Visual Studio** pojawi się okno dialogowe. Można nadać użytkownikom uprawnienia do narzędzi zdalnych i ustawić inną zaawansowaną opcję z tego okna dialogowego.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Konfigurowanie zdalnego debugera  
 Dwa narzędzia służą do modyfikowania konfiguracji zdalnego debugera.  
  
1. Na **narzędzia** menu **zdalny Monitor debugowania Visual Studio**:  
  
   1.  Wybierz **opcje** do zmiany numeru portu, tryb uwierzytelniania lub interwał limitu czasu zdalnego debugera.  
  
   2.  Wybierz **uprawnienia** do dodawania lub usuwania użytkowników, którzy mają uprawnienia do zdalnego debugowania.  
  
       > [!NOTE]
       >  Muszą mieć uprawnienia do wszystkich kont użytkowników, które debuguje zdalnie.  
  
   Możesz użyć **Kreatora konfiguracji zdalnego debugera** Aby ustawić zaawansowane opcje dla zdalnego debugera. Aby otworzyć kreatora, wybierz opcję **Kreatora konfiguracji zdalnego debugera** na ekranie startowym.  
  
2. Na **Konfigurowanie debugera zdalnego programu Visual Studio** strony, istnieje możliwość uruchomienia zdalnego debugera jako usługi. W większości przypadków uruchamianie jako usługi nie jest wymagana.  
  
3. Na **skonfigurować zaporę Windows dla debugowania** strony, można dodać lub usunąć typ sieci, które mają zdalnego debugera, aby nawiązać połączenie. Tylko te sieci, które urządzenia jest aktualnie połączony z są włączone. Musisz wybrać co najmniej jedna sieć.  
  
##  <a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio dla zdalnego debugowania  
 Należy określić urządzenie zdalne, aby połączyć się we właściwościach projektu. Procedura różni się w zależności od języka programowania. Można wpisać nazwę sieciową urządzenia zdalnego lub wybrać go z okna dialogowego Wybierz połączenie ze zdalnym debugerem.  
  
 ![Okno dialogowe Wybierz połączenie ze zdalnym debugerem](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Okno dialogowe wyświetla listę tylko tych urządzeń, które są w lokalnej podsieci komputera Visual Studio i działają zdalnego debugera.  
  
> [!TIP]
>  Jeśli masz problemy z nawiązaniem połączenia z urządzeniem zdalnym, spróbuj wprowadzić adres IP urządzenia. Aby określić adres IP urządzenia, Otwórz okno polecenia, a następnie wpisz **ipconfig**. Adres IP jest wymieniony jako **adres IPv4**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Wybieranie urządzenia zdalnego dla projektów C# i Visual Basic  
 ![Właściwości projektu dla zdalnego debugowania zarządzane](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.  
  
2.  Wybierz **debugowania**.  
  
3.  Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.  
  
4.  Wprowadź nazwę sieciową urządzenia zdalnego w **maszyny zdalnej** pole, lub wybierz **znaleźć** do wyboru urządzenia z **wybierz połączenie ze zdalnym debugerem** okno dialogowe.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Wybieranie urządzenia zdalnego dla projektów języka C++ i JavaScript  
 ![C&#43; &#43; właściwości dla zdalnego debugowania projektu](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  Wybierz nazwę projektu w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.  
  
2.  Rozwiń **właściwości konfiguracji** węzeł, a następnie wybierz **debugowanie**.  
  
3.  Wybierz **zdalny debuger** z **debuger do uruchomienia** listy.  
  
4.  Wprowadź nazwę sieciową urządzenia zdalnego w **NazwaKomputera** pole, lub wybierz strzałkę w dół w polu, aby wybrać urządzenie w **wybierz połączenie ze zdalnym debugerem** okno dialogowe.  
  
##  <a name="BKMK_RunRemoteDebug"></a> Uruchamianie sesji debugowania zdalnego  
 Uruchom, Zatrzymaj i nawigowanie po sesji debugowania zdalnego taki sam sposób czy lokalnej sesji. Przed rozpoczęciem debugowania upewnij się, że Monitor debugera zdalnego działa na urządzeniu zdalnym.  
  
 Następnie wybierz **Rozpocznij debugowanie** na **debugowania** menu (klawiatury: F5). Projekt jest ponownie skompilowana, a następnie wdrożona i uruchomiona na urządzeniu zdalnym. Debuger zawiesza wykonywanie w punktach przerwania, a użytkownik może przechodzić do nad lub poza swój kod. Wybierz **Zatrzymaj debugowanie** aby zakończyć sesję debugowania i zamknąć zdalną aplikację. Aby uzyskać więcej informacji, zobacz [debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Testowanie aplikacji Store za pomocą programu Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debugowanie aplikacji w programie Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)

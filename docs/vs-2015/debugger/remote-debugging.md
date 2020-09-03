---
title: Debugowanie zdalne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300556"
---
# <a name="remote-debugging"></a>Debugowanie zdalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można debugować aplikację Visual Studio, która została wdrożona na innym komputerze.  W tym celu należy użyć zdalnego debugera programu Visual Studio.  
  
 Informacje zawarte w tym artykule dotyczą aplikacji klasycznych systemu Windows i aplikacji ASP.NET.  Aby uzyskać informacje o zdalnym debugowaniu aplikacji ze sklepu Windows i aplikacji platformy Azure, zobacz [zdalne debugowanie w Sklepie Windows i aplikacji platformy Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Pobierz narzędzia zdalne  
Można pobrać narzędzia zdalne bezpośrednio na urządzeniu lub serwerze, który ma być debugowany, lub pobrać zdalne narzędzia z komputera hosta z zainstalowanym programem Visual Studio.

### <a name="to-download-and-install-the-remote-tools"></a>Aby pobrać i zainstalować narzędzia zdalne
  
1. Na urządzeniu lub serwerze, który ma być debugowany (a nie na maszynie z programem Visual Studio), uzyskaj poprawną wersję narzędzi zdalnych.

    |Wersja|Link|Uwagi|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do grupy bezpłatna Visual Studio Dev Essentials lub po prostu zaloguj się przy użyciu ważnej subskrypcji programu Visual Studio. Następnie w razie potrzeby ponownie otwórz link. Zawsze pobieraj wersję zgodną z systemem operacyjnym urządzenia (wersja x86, x64 lub ARM)|
    |Visual Studio 2015 (starsza wersja)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do grupy bezpłatna Visual Studio Dev Essentials lub po prostu zaloguj się przy użyciu ważnej subskrypcji programu Visual Studio. Następnie w razie potrzeby ponownie otwórz link.|
    |Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Strona pobierania w dokumentacji Visual Studio 2013|
    |Visual Studio 2012|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Strona pobierania w dokumentacji programu Visual Studio 2012|
  
2. Na stronie Pobieranie wybierz wersję narzędzi, która odpowiada systemowi operacyjnemu (x86, x64 lub ARM), a następnie Pobierz narzędzia zdalne.
  
    > [!IMPORTANT]
    > Zalecamy zainstalowanie najnowszej wersji narzędzi zdalnych, która pasuje do używanej wersji programu Visual Studio. Nie zaleca się stosowania niezgodnych wersji.  
    >   
    >  Ponadto należy zainstalować narzędzia zdalne mające taką samą architekturę jak system operacyjny, na którym ma zostać zainstalowana. Innymi słowy, jeśli chcesz debugować aplikację 32-bitową na komputerze zdalnym z 64-bitowym systemem operacyjnym, należy zainstalować 64-bitową wersję narzędzi zdalnych na komputerze zdalnym.  
  
3. Po zakończeniu pobierania pliku wykonywalnego postępuj zgodnie z instrukcjami, aby zainstalować aplikację na komputerze zdalnym. Zobacz [instrukcje dotyczące instalacji](#bkmk_setup)

Jeśli spróbujesz skopiować zdalny debuger (msvsmon.exe) do komputera zdalnego i uruchomić go, pamiętaj, że **Kreator konfiguracji debugera zdalnego** (**rdbgwiz.exe**) jest instalowany tylko podczas pobierania narzędzi i może być konieczne użycie Kreatora w celu konfiguracji później, szczególnie jeśli chcesz, aby zdalny debuger działał jako usługa. Aby uzyskać więcej informacji, zobacz [(opcjonalnie). Skonfiguruj debuger zdalny jako usługę](#bkmk_configureService) poniżej.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Aby uruchomić zdalny debuger z udziału plików

Zdalny debuger (**msvsmon.exe**) można znaleźć na komputerze, na którym jest już zainstalowany program Visual Studio 2015 Community, Professional lub Enterprise. W wielu scenariuszach Najprostszym sposobem skonfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Aby uzyskać ograniczenia dotyczące użycia, zobacz stronę pomocy zdalnego debugera (**Pomoc/użycie** w debugerze zdalnym).

1. Znajdź **msvsmon.exe** w katalogu pasującym do używanej wersji programu Visual Studio. Dla programu Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Udostępnij folder **debugera zdalnego** na komputerze z Visual Studio.

3. Na komputerze zdalnym uruchom **msvsmon.exe**. Postępuj zgodnie z [instrukcjami instalacji](#bkmk_setup).

> [!TIP] 
> Aby uzyskać informacje na temat instalacji z wiersza polecenia i wiersza polecenia, zobacz stronę pomocy dla **msvsmon.exe** , wpisując ``msvsmon.exe /?`` w wierszu polecenia na komputerze z zainstalowanym programem Visual Studio (lub przejdź do okna **Pomoc/użycie** w debugerze zdalnym).

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne  
 Na komputerze zdalnym musi być uruchomiony jeden z następujących systemów operacyjnych:  
  
- Windows 10  
  
- System Windows 8 lub 8,1  
  
- Windows 7 z dodatkiem Service Pack 1  
  
- Windows Server 2012 lub Windows Server 2012 R2  
  
- Windows Server 2008 z dodatkiem Service Pack 2, Windows Server 2008 R2 z dodatkiem Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Obsługiwane konfiguracje sprzętu  
  
- Procesor 1,6 GHz lub szybszy  
  
- 1 GB pamięci RAM (1,5 GB w przypadku uruchamiania na maszynie wirtualnej)  
  
- 1 GB dostępnego miejsca na dysku twardym  
  
- Dysk twardy o szybkości 5400 obr./min  
  
- Karta wideo obsługująca technologię DirectX 9 i rozdzielczość ekranu 1024 x 768 lub wyższą  
  
## <a name="network-configuration"></a>Konfiguracja sieci  
 Komputer zdalny i komputer z programu Visual Studio muszą być połączone przez sieć, grupę roboczą lub grupę domową albo być połączone bezpośrednio za pośrednictwem kabla Ethernet. Debugowanie przez Internet nie jest obsługiwane.  
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Konfigurowanie zdalnego debugera  
 Użytkownik musi mieć uprawnienia administratora na komputerze zdalnym  
  
1. Znajdź aplikację Remote Debugger. (Otwórz menu Start i Wyszukaj **zdalny debuger**).
  
    Jeśli używasz zdalnego debugera na serwerze zdalnym, możesz kliknąć prawym przyciskiem myszy aplikację Remote Debugger i wybrać polecenie **Uruchom jako administrator** (lub można uruchomić zdalny debuger jako usługę). Jeśli nie jest uruchomiony na serwerze zdalnym, wystarczy uruchomić go normalnie.
  
2. Po pierwszym uruchomieniu narzędzi zdalnych (lub przed ich skonfigurowaniem) zostanie wyświetlone okno dalog **konfiguracji debugowania zdalnego** .  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Jeśli interfejs API usługi systemu Windows nie jest zainstalowany (co jest wykonywane tylko w systemie Windows Server 2008 R2), wybierz przycisk **Instaluj** .  
  
4. Wybierz typy sieci, na których chcesz korzystać z narzędzi zdalnych. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pomocą domeny, należy wybrać pierwszy element. Jeśli komputery są połączone przez grupę roboczą lub grupę domową, należy wybrać drugi lub trzeci element stosownie do potrzeb.  
  
5. Wybierz pozycję **Konfiguruj zdalne debugowanie** , aby skonfigurować zaporę i uruchomić narzędzie.  
  
6. Po zakończeniu konfiguracji zostanie wyświetlone okno zdalny debuger.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Zdalny debuger czeka teraz na połączenie. Zanotuj nazwę serwera i numer portu, który jest wyświetlany, ponieważ będzie on potrzebny później do konfiguracji w programie Visual Studio.  
  
   Po zakończeniu debugowania i zatrzymywaniu zdalnego debugera kliknij polecenie **plik/Wyjdź** w oknie. Można uruchomić je ponownie z menu **Start** lub z wiersza polecenia:  
  
   ** \<Visual Studio installation directory> Debuger \Common7\IDE\Remote \\<x86, x64 lub Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurowanie zdalnego debugera  
 Niektóre aspekty konfiguracji zdalnego debugera można zmienić po jego po raz pierwszy.
  
- Aby umożliwić innym użytkownikom łączenie się ze zdalnym debugerem, wybierz pozycję **Narzędzia/uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

  > [!IMPORTANT]
  > Zdalny debuger można uruchomić w ramach konta użytkownika, które różni się od konta użytkownika używanego na komputerze z programem Visual Studio, ale należy dodać inne konto użytkownika do uprawnień zdalnego debugera. 

   Alternatywnie można uruchomić zdalny debuger z wiersza polecenia z parametrem ** \<username> /Allow** : **msvsmon/Allow \<username@computer> **.
  
- Aby zmienić tryb uwierzytelniania lub numer portu lub określić wartość limitu czasu dla narzędzi zdalnych: Wybierz **Narzędzia/Opcje**.  
  
   Aby uzyskać listę numerów portów używanych domyślnie, zobacz [zdalne przydziały portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożona przez złośliwe lub szkodliwe dane.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Obowiązkowe Konfigurowanie zdalnego debugera jako usługi
 W przypadku debugowania w ASP.NET i innych środowiskach serwerów należy uruchomić zdalny debuger jako administrator lub, jeśli chcesz, aby zawsze działał, uruchom zdalny debuger jako usługę.
  
 Jeśli chcesz skonfigurować zdalny debuger jako usługę, wykonaj następujące kroki.  
  
1. Znajdź **Kreatora konfiguracji debugera zdalnego** (rdbgwiz.exe). (Jest to oddzielna aplikacja ze zdalnego debugera). Jest ona dostępna tylko podczas instalowania narzędzi zdalnych. Nie jest on instalowany z programem Visual Studio.  
  
2. Rozpocznij pracę z kreatorem konfiguracji. Gdy pierwsza strona zostanie wystawiona, kliknij przycisk **dalej**.  
  
3. Zaznacz pole wyboru **Uruchom Debuger zdalny programu Visual Studio 2015 jako usługę** .  
  
4. Dodaj nazwę konta użytkownika i hasło.  
  
    Może być konieczne dodanie uprawnienia **Zaloguj się jako użytkownik usługi** do tego konta. (Znajdź **zasady zabezpieczeń lokalnych** (secpol. msc) na stronie **startowej** lub w oknie (lub wpisz **secpol** w wierszu polecenia). Po wyświetleniu okna kliknij dwukrotnie pozycję **Przypisywanie praw użytkownika**, a następnie znajdź opcję **Zaloguj się jako usługa** w okienku po prawej stronie. Kliknij go dwukrotnie. Dodaj konto użytkownika do okna **Właściwości** , a następnie kliknij przycisk **OK**. Kliknij przycisk **dalej**.  
  
5. Wybierz typ sieci, z którą mają się komunikować narzędzia zdalne. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pomocą domeny, należy wybrać pierwszy element. Jeśli komputery są połączone przez grupę roboczą lub grupę domową, należy wybrać drugą lub trzecią pozycję. Kliknij przycisk **Dalej**.  
  
6. Jeśli usługa może zostać uruchomiona, zostanie wyświetlony **Kreator konfiguracji zdalny debuger programu Visual Studio, który pomyślnie ukończył**pracę. Jeśli nie można uruchomić usługi, **nie można ukończyć pracy Kreatora konfiguracji zdalny debuger programu Visual Studio**. Na stronie znajdują się również porady, które należy wykonać, aby rozpocząć pracę usługi.  
  
7. Kliknij przycisk **Zakończ**.  
  
   W tym momencie zdalny debuger działa jako usługa. Możesz to sprawdzić, przechodząc do **Panelu sterowania/usług** i szukając **zdalnego debugera programu Visual Studio 2015**.  
  
   Usługę zdalnego debugera można zatrzymać i uruchomić z poziomu **Panelu sterowania/usług**.  

## <a name="remote-debug-an-aspnet-application"></a>Zdalne debugowanie aplikacji ASP.NET  
 Wdrażanie aplikacji ASP.NET na komputerze zdalnym z uruchomionymi usługami IIS ma różne kroki, w zależności od systemu operacyjnego i wersji usług IIS. W przypadku komputerów zdalnych z systemem Windows Server 2008 lub Windows Server 2012 z zainstalowanymi usługami IIS 7,5 lub nowszym zapoznaj się z tematem [debugowanie zdalne ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Jeśli debugujesz aplikację ASP.NET Core, zobacz [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Do opublikowania ASP.NET Core w usługach IIS wymagane są różne czynności. Po pomyślnym opublikowaniu aplikacji ASP.NET Core można debugować debugowanie, podobnie [jak inne aplikacje ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), z tą różnicą, że proces, do którego należy dołączyć, jest dnx.exe zamiast w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Debugowanie zdalne projektu Visual C++  
 W poniższej procedurze nazwa i ścieżka projektu to C:\remotetemp\MyMfc, a nazwa komputera zdalnego to **MJO-DL**.  
  
1. Utwórz aplikację MFC o nazwie **mymfc.**  
  
2. Ustaw punkt przerwania w aplikacji, która jest łatwo dostępna, na przykład w **MainFrm. cpp**, na początku `CMainFrame::OnCreate` .  
  
3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Otwórz kartę **debugowanie** .  
  
4. Ustaw **debuger do uruchamiania** na **zdalny debuger systemu Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Wprowadź następujące zmiany właściwości:  
  
   |Ustawienie|Wartość|
   |-|-|  
   |Polecenie zdalne|C:\remotetemp\mymfc.exe|  
   |Katalog roboczy|C:\remotetemp|  
   |Nazwa serwera zdalnego|MJO-DL:*numer_portu*|  
   |Połączenie|Zdalne z uwierzytelnianiem systemu Windows|  
   |Typ debugera|Tylko natywny|  
   |Katalog wdrażania|C:\remotetemp.|  
   |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|  
  
    W przypadku wdrażania dodatkowych plików (opcjonalnie) folder musi istnieć na obu komputerach.  
  
6. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Configuration Manager**.  
  
7. W obszarze Konfiguracja **debugowania** zaznacz pole wyboru **Wdróż** .  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Rozpocznij debugowanie (**Debuguj/Rozpocznij debugowanie**lub **F5**).  
  
9. Plik wykonywalny jest automatycznie wdrażany na komputerze zdalnym.  
  
10. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieciowe, aby nawiązać połączenie z maszyną zdalną.  
  
     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wybrać certyfikat zabezpieczeń lub podać nazwę domeny i hasło. Na komputerze niebędącym domeną możesz wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, na przykład <strong>MJO-DL\name@something.com</strong> , wraz z prawidłowym hasłem.  
  
11. Na komputerze z Visual Studio powinno być widoczne, że wykonywanie zostało zatrzymane w punkcie przerwania.  
  
    > [!TIP]
    > Alternatywnie można wdrożyć pliki w osobnym kroku. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł **MyMfc** **,** a następnie wybierz polecenie **Wdróż**.  
  
    Jeśli masz pliki niebędące kodem, które muszą być używane przez aplikację, musisz je uwzględnić w projekcie programu Visual Studio. Utwórz folder projektu dla dodatkowych plików (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj/nowy folder**). Następnie Dodaj pliki do folderu (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj/istniejący element**, a następnie wybierz pliki). Na stronie **Właściwości** każdego pliku ustaw opcję **Kopiuj do katalogu wyjściowego** na wartość **Kopiuj zawsze**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Debugowanie zdalne projektu Visual C# lub Visual Basic  
 Debuger nie może wdrożyć aplikacji Visual C# lub Visual Basic Desktop na komputerze zdalnym, ale nadal można debugować je zdalnie w następujący sposób. W poniższej procedurze przyjęto założenie, że chcesz debugować ją na komputerze o nazwie **MJO-DL**, jak pokazano na poprzedniej ilustracji.
  
1. Utwórz projekt WPF o nazwie **MyWpf**.  
  
2. Ustaw punkt przerwania w miejscu w kodzie, który jest łatwo osiągalny.  
  
    Na przykład można ustawić punkt przerwania w obsłudze przycisku. Aby to zrobić, Otwórz MainWindow. XAML i Dodaj kontrolkę Button z przybornika, a następnie kliknij dwukrotnie przycisk, aby otworzyć jego program obsługi.
  
3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.  
  
4. Na stronie **Właściwości** wybierz kartę **debugowanie** .  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Upewnij się, że pole tekstowe **katalog roboczy** jest puste.  
  
6. Wybierz opcję **Użyj maszyny zdalnej**i wpisz **MJO-DL: 4020** w polu tekstowym. (4020 to numer portu wyświetlany w oknie Debuger zdalny).  
  
7. Upewnij się, że nie wybrano **debugowania kodu natywnego** .  
  
8. Skompiluj projekt.  
  
9. Utwórz folder na komputerze zdalnym, który jest tą samą ścieżką jak folder **debugowania** na komputerze programu Visual Studio: ** \<source path> \MyWPF\MyWPF\bin\Debug**.  
  
10. Skopiuj plik wykonywalny, który został utworzony z komputera programu Visual Studio, do nowo utworzonego folderu na komputerze zdalnym.
  
    > [!CAUTION]
    > Nie wprowadzaj zmian w kodzie ani nie Kompiluj ponownie (lub musisz powtórzyć ten krok). Plik wykonywalny skopiowany na komputer zdalny musi dokładnie pasować do lokalnego źródła i symboli.

    Projekt można skopiować ręcznie, użyć polecenia xcopy, Robocopy, PowerShell lub innych opcji.
  
11. Upewnij się, że zdalny debuger jest uruchomiony na maszynie docelowej. (Jeśli nie jest, Wyszukaj **zdalny debuger** w menu **Start** . ) Okno debugera zdalnego wygląda następująco.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. W programie Visual Studio Rozpocznij debugowanie (**Debuguj/Rozpocznij debugowanie**lub **F5**).  
  
13. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieciowe, aby nawiązać połączenie z maszyną zdalną.  
  
     Wymagane poświadczenia różnią się w zależności od konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wprowadzić nazwę domeny i hasło. Na komputerze niebędącym domeną możesz wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, na przykład <strong>MJO-DL\name@something.com</strong> , wraz z prawidłowym hasłem.

     Powinno zostać wyświetlone okno główne aplikacji WPF na komputerze zdalnym.
  
14. W razie potrzeby podejmij działanie, aby trafić w punkt przerwania. Powinieneś zobaczyć, że punkt przerwania jest aktywny. Jeśli tak nie jest, nie załadowano symboli aplikacji. Ponów próbę, a jeśli to nie zadziała, Uzyskaj informacje o ładowaniu symboli i sposobach ich rozwiązywania przy [zrozumieniu plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. Na maszynie programu Visual Studio powinno być widoczne, że wykonywanie zostało zatrzymane w punkcie przerwania.
  
    Jeśli masz pliki niebędące kodem, które muszą być używane przez aplikację, musisz je uwzględnić w projekcie programu Visual Studio. Utwórz folder projektu dla dodatkowych plików (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj/nowy folder**). Następnie Dodaj pliki do folderu (w **Eksplorator rozwiązań**kliknij pozycję **Dodaj/istniejący element**, a następnie wybierz pliki). Na stronie **Właściwości** każdego pliku ustaw opcję **Kopiuj do katalogu wyjściowego** na wartość **Kopiuj zawsze**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania ze zdalnymi symbolami  
 Powinno być możliwe debugowanie kodu przy użyciu symboli generowanych na komputerze z programem Visual Studio. Wydajność zdalnego debugera jest znacznie lepsza w przypadku używania symboli lokalnych.  Jeśli musisz użyć symboli zdalnych, musisz poinformować Monitor debugowania zdalnego, aby szukać symboli na maszynie zdalnej.  
  
 Począwszy od Visual Studio 2013 Update 2, można użyć następującego przełącznika wiersza polecenia msvsmon, aby użyć symboli zdalnych dla kodu zarządzanego: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Aby uzyskać więcej informacji, zobacz Pomoc dotyczącą debugowania zdalnego (naciśnij klawisz **F1** w oknie debugera zdalnego lub kliknij pozycję **Pomoc/użycie**). Więcej informacji można znaleźć w temacie [zdalne ładowanie symboli .NET w programie Visual Studio 2012 i 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Zdalne debugowanie w Sklepie Windows i aplikacje platformy Azure  
 Aby uzyskać informacje o zdalnym debugowaniu w aplikacjach ze sklepu Windows, zobacz [debugowanie i testowanie aplikacji ze sklepu Windows na urządzeniu zdalnym z programu Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Aby uzyskać informacje na temat debugowania na platformie Azure, zobacz jeden z następujących tematów:  
  
- [Debugowanie usługi w chmurze lub maszyny wirtualnej w programie Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debugowanie zaplecza platformy .NET w programie Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Wprowadzenie do zdalnego debugowania w witrynach sieci Web systemu Azure ([część 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [część 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [część 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)

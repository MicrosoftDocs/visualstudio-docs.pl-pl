---
title: Zdalne debugowanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c964eaa8e8c130516b29c88a3ccae78aa902c66a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649449"
---
# <a name="remote-debugging"></a>Debugowanie zdalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można debugować aplikację programu Visual Studio, która została wdrożona na innym komputerze.  Aby to zrobić, należy użyć zdalnego debugera programu Visual Studio.  
  
 Informacje w tym miejscu ma zastosowanie do aplikacji ASP.NET i aplikacji klasycznych Windows.  Aby uzyskać informacje o zdalnym debugowaniu aplikacji Windows Store i aplikacje platformy Azure, zobacz [zdalne debugowanie aplikacji Windows Store i Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Pobierz narzędzia zdalne  
Możesz albo pobierania, które narzędzia zdalnej bezpośrednio na urządzeniu lub na serwerze, na którym chcesz debugowania, lub można uzyskać narzędzi zdalnych z komputera-hosta za pomocą programu Visual Studio.

### <a name="to-download-and-install-the-remote-tools"></a>Aby pobrać i zainstalować narzędzia zdalne
  
1.  Na urządzeniu lub serwera maszyny, które chcesz debugować (a nie komputer z programem Visual Studio) Pobierz poprawną wersję narzędzi remote tools.

    |Wersja|Łącze|Uwagi|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego grupy programu Visual Studio Dev Essentials lub po prostu Zaloguj się ważną subskrypcją programu Visual Studio. Następnie ponownie otwórz link w razie potrzeby. Zawsze pobierana wersja dopasowania system operacyjny urządzenia (x 86, x64 lub wersji ARM)|
    |Visual Studio 2015 (older)|[Zdalne narzędzia](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Jeśli zostanie wyświetlony monit, Dołącz do bezpłatnego grupy programu Visual Studio Dev Essentials lub po prostu Zaloguj się ważną subskrypcją programu Visual Studio. Następnie ponownie otwórz link w razie potrzeby.|
    |Visual Studio 2013|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2013|
    |Visual Studio 2012|[Zdalne narzędzia](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Pobierz strony w dokumentacji programu Visual Studio 2012|
  
2.  Na stronie pobierania wybierz wersję narzędzi, który pasuje do systemu operacyjnego (x 86, x64 lub wersji ARM), a następnie Pobierz narzędzia remote tools.
  
    > [!IMPORTANT]
    >  Zaleca się, że możesz zainstalować najnowszą wersję narzędzi remote tools, który odpowiada używanej wersji programu Visual Studio. Niezgodność wersji nie jest zalecane.  
    >   
    >  Ponadto należy zainstalować narzędzi zdalnych, które mają taką samą architekturę co system operacyjny, na którym chcesz go zainstalować. Innymi słowy Jeśli chcesz debugować 32-bitowej aplikacji na komputerze zdalnym z systemem 64-bitowym systemie operacyjnym, należy zainstalować 64-bitowej wersji narzędzi zdalnych na komputerze zdalnym.  
  
3.  Po zakończeniu pobierania pliku wykonywalnego, postępuj zgodnie z instrukcjami, aby zainstalować aplikację na komputerze zdalnym. Zobacz [instrukcje instalacji](#bkmk_setup)

Próby skopiuj zdalny debuger (msvsmon.exe) z komputerem zdalnym i uruchom go, należy pamiętać, że **Kreatora konfiguracji zdalnego debugera** (**rdbgwiz.exe**) jest zainstalowana tylko wtedy, gdy możesz pobrać Narzędzia i może być konieczne użycie Kreatora konfiguracji później, zwłaszcza, jeśli chcesz, aby zdalnego debugera, aby uruchomić jako usługę. Aby uzyskać więcej informacji, zobacz [(opcjonalnie) Konfigurowanie debugera zdalnego jako usługę](#bkmk_configureService) poniżej.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Aby uruchomić zdalny debuger z udziału plików

Można znaleźć zdalnego debugera (**msvsmon.exe**) na komputerze przy użyciu programu Visual Studio 2015 Community, Professional lub Enterprise już zainstalowane. W wielu sytuacjach Najprostszym sposobem konfigurowania zdalnego debugowania jest uruchomienie zdalnego debugera (msvsmon.exe) z udziału plików. Dla ograniczenia użycia, zobacz stronę pomocy zdalny debuger (**pomocy / użycia** w zdalnym debugerze).

1. Znajdź **msvsmon.exe** w katalogu, zgodny z używaną wersją programu Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Udostępnij **zdalny debuger** folderu na komputerze programu Visual Studio.

3. Na komputerze zdalnym, uruchom **msvsmon.exe**. Postępuj zgodnie z [instrukcje instalacji](#bkmk_setup).

> [!TIP] 
> Aby instalacja przy użyciu wiersza polecenia i informacje w wierszu polecenia, zobacz stronę pomocy dla **msvsmon.exe** , wpisując ``msvsmon.exe /?`` w wierszu polecenia na komputerze przy użyciu programu Visual Studio (lub przejdź do **pomocy / użycia**w zdalnym debugerze).

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne  
 Komputer zdalny musi działać jeden z następujących systemów operacyjnych:  
  
-   Windows 10  
  
-   Windows 8 lub 8.1  
  
-   Windows 7 z dodatkiem Service Pack 1  
  
-   Windows Server 2012 lub Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 z dodatkiem Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Sprzęt obsługiwany w konfiguracji  
  
-   Procesor 1,6 GHz lub szybszy  
  
-   1 GB pamięci RAM (1,5 GB w przypadku uruchamiania na maszynie wirtualnej)  
  
-   1 GB dostępnego miejsca na dysku twardym  
  
-   Dysk twardy o szybkości 5400 obr./min  
  
-   Karta wideo obsługująca technologię DirectX 9 i rozdzielczość ekranu 1024 x 768 lub wyższą  
  
## <a name="network-configuration"></a>Konfiguracja sieci  
 Komputer zdalny i komputer z programem Visual Studio musi być połączone za pośrednictwem sieci, w grupie roboczej lub w grupie domowej, w przeciwnym razie podłączone bezpośrednio za pomocą kabla Ethernet. Debugowanie przez Internet nie jest obsługiwane.  
  
## <a name="bkmk_setup"></a>Konfigurowanie debugera zdalnego  
 Musi mieć uprawnienia administracyjne na komputerze zdalnym  
  
1. Znajdź aplikację zdalny debuger. (Otwórz Start menu i wyszukaj **zdalny debuger**.)
  
    Jeśli używasz zdalnego debugera na serwerze zdalnym, możesz kliknij prawym przyciskiem myszy aplikację zdalny debuger i wybrać **Uruchom jako administrator** (lub, można uruchomić zdalnego debugera jako usługi). Jeśli nie używasz go na serwerze zdalnym, wystarczy ją uruchomić normalnie.
  
2. Po uruchomieniu narzędzia zdalne po raz pierwszy (lub przed jej skonfigurowano), **Konfiguracja zdalnego debugowania** pojawi się okno dalog.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Jeśli interfejs API usługi Windows nie jest zainstalowany (co się stanie, tylko w systemie Windows Server 2008 R2), wybierz opcję **zainstalować** przycisku.  
  
4. Wybierz typy sieci, należy użyć narzędzi zdalnych na. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, należy wybrać pierwszy element. Jeśli komputery są połączone za pośrednictwem grupy roboczej lub grupa domowa, musisz wybrać drugi lub trzeci element zgodnie z potrzebami.  
  
5. Wybierz **Konfiguruj zdalne debugowanie** Aby skonfigurować zaporę i uruchomić narzędzie.  
  
6. Po zakończeniu konfiguracji zostanie wyświetlone okno zdalnego debugera.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Zdalny debuger jest teraz oczekiwania na połączenie. Zanotuj nazwę serwera i port numer, który jest wyświetlany, ponieważ będzie on potrzebny później dla konfiguracji w programie Visual Studio.  
  
   Po zakończeniu debugowania i musisz zatrzymać debuger zdalny kliknij **pliku / wyjść** w oknie. Możesz ponownie uruchomić go z **Start** menu lub z wiersza polecenia:  
  
   **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Remote debugera\\< x86, x64 lub Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Konfigurowanie debugera zdalnego  
 Po uruchomieniu go po raz pierwszy, można zmienić niektóre aspekty konfiguracji zdalnego debugera.
  
- Aby umożliwić innym użytkownikom na łączenie się ze zdalnym debugerem, wybierz opcję **narzędzia / uprawnienia**. Musisz mieć uprawnienia administratora, aby udzielić lub odmówić uprawnień.

  > [!IMPORTANT]
  > Można uruchomić debugera zdalnego przy użyciu konta użytkownika, który różni się z konta użytkownika, którego używasz na komputerze programu Visual Studio, ale należy dodać konta innego użytkownika do zdalnego debugera uprawnień. 

   Alternatywnie można uruchomić zdalnego debugera z wiersza polecenia za pomocą **/ allow \<username >** parametru: **msvsmon / allow \< username@computer>**.
  
- Aby zmienić tryb uwierzytelniania lub numer portu lub określić wartość limitu czasu dla narzędzi zdalnych: Wybierz **narzędzia / Opcje**.  
  
   Lista numerów portów, używany domyślnie znajduje się [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  >  Istnieje możliwość uruchomienia narzędzi zdalnych w trybie Bez uwierzytelnienia, ale używanie tego trybu jest zdecydowanie odradzane. Po uruchomieniu w tym trybie nie ma zabezpieczeń sieci. Wybierz tryb bez uwierzytelniania tylko wtedy, gdy masz pewność, że sieć nie jest zagrożone przez złośliwe lub wrogie działania.

##  <a name="bkmk_configureService"></a> (Opcjonalnie) Konfigurowanie debugera zdalnego jako usługi
 Do debugowania na platformie ASP.NET i innych środowisk serwera, należy uruchomić zdalny debuger jako Administrator lub, będzie zawsze działać, należy uruchomić debugera zdalnego jako usługi.
  
 Jeśli chcesz skonfigurować debugera zdalnego jako usługę, wykonaj następujące kroki.  
  
1. Znajdź **Kreator konfiguracji zdalnego debugera** (rdbgwiz.exe). (Jest oddzielną aplikację z debugera zdalnego). Jest ona dostępna tylko w przypadku instalowania narzędzi zdalnych. Nie zainstalowano programu Visual Studio.  
  
2. Uruchom Kreatora konfiguracji. Gdy pierwsza strona, kliknij przycisk **dalej**.  
  
3. Sprawdź **uruchomić debugera programu Visual Studio 2015 zdalne jako usługę** pola wyboru.  
  
4. Dodaj nazwę konta użytkownika i hasła.  
  
    Może być konieczne dodanie **Zaloguj się jako usługa** użytkownika bezpośrednio do tego konta. (Znajdź **zasady zabezpieczeń lokalnych** (secpol.msc) w **Start** strony lub okna (lub typu **secpol** polecenie w wierszu polecenia). Gdy pojawi się okno, kliknij dwukrotnie **Przypisywanie praw użytkownika**, następnie znajdź **Zaloguj się jako usługa** w okienku po prawej stronie. Kliknij go dwukrotnie. Dodaj konto użytkownika do **właściwości** oknie i kliknij przycisk **OK**.) Kliknij przycisk **Dalej**.  
  
5. Wybierz typ sieci, z którą komunikować narzędzia zdalne. Należy wybrać co najmniej jeden typ sieci. Jeśli komputery są połączone za pośrednictwem domeny, wybierz pierwszy element. Jeśli komputery są połączone za pośrednictwem grupy roboczej lub grupa domowa, należy wybrać elementy drugiego i trzeciego. Kliknij przycisk **Dalej**.  
  
6. Jeśli usługa może zostać uruchomiona, zostanie wyświetlony **została pomyślnie ukończona Visual Studio Kreator konfiguracji debugera zdalnego**. Jeśli nie można uruchomić usługi, zostanie wyświetlony **nie można ukończyć Visual Studio Kreator konfiguracji debugera zdalnego**. Strona zawiera także kilka wskazówek dotyczących wykonać, aby usługa zostanie uruchomiona.  
  
7. Kliknij przycisk **Zakończ**.  
  
   W tym momencie zdalny debuger działa jako usługa. Można to sprawdzić, przechodząc do **Panel sterowania / usług** i szuka **2015 zdalny debuger programu Visual Studio**.  
  
   Można zatrzymać i uruchomić usługę zdalnego debugera z **Panel sterowania / usług**.  

## <a name="remote-debug-an-aspnet-application"></a>Zdalne debugowanie aplikacji ASP.NET  
 Wdrażanie aplikacji ASP.NET do zdalnego komputera z programem IIS ma różne kroki, w zależności od systemu operacyjnego i wersji programu IIS. Dla zdalnego komputerów z systemem Windows Server 2008 lub Windows Server 2012, które usług IIS 7.5 lub nowszy, zobacz [zdalnego debugowania ASP.NET, na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Jeśli debugujesz aplikację ASP.NET Core, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Różne kroki są wymagane do publikowania platformy ASP.NET Core w usługach IIS. Po pomyślnym opublikowaniu aplikacji ASP.NET Core możesz zdalnego debugowania [podobnie jak inne aplikacje platformy ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), z tą różnicą, że proces, należy dołączyć do dnx.exe zamiast w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Debugowanie zdalne projektu Visual C++  
 W poniższej procedurze nazwa i ścieżka projektu jest C:\remotetemp\MyMfc, a nazwa komputera zdalnego jest **MJO DL**.  
  
1. Tworzenie aplikacji MFC o nazwie **mymfc.**  
  
2. Ustaw punkt przerwania gdzieś w aplikacji, które łatwo zostanie osiągnięty, na przykład w **MainFrm.cpp**, na początku `CMainFrame::OnCreate`.  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. Otwórz **debugowanie** kartę.  
  
4. Ustaw **debuger do uruchomienia** do **zdalny debuger Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Do właściwości, należy wprowadzić następujące zmiany:  
  
   |Ustawienie|Wartość|
   |-|-|  
   |Polecenie zdalne|C:\remotetemp\mymfc.exe|  
   |Katalog roboczy|C:\remotetemp|  
   |Nazwa serwera zdalnego|Listy Dystrybucyjnej MJO:*numer_portu*|  
   |Połączenie|Zdalny z uwierzytelnianiem Windows|  
   |Typ debugera|Tylko w trybie macierzystym|  
   |Katalog wdrażania|C:\remotetemp.|  
   |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|  
  
    Jeśli wdrożono dodatkowe pliki (opcjonalnie), folder musi istnieć na obu komputerach.  
  
6. W Eksploratorze rozwiązań kliknij rozwiązanie prawym przyciskiem myszy i wybierz polecenie **programu Configuration Manager**.  
  
7. Aby uzyskać **debugowania** konfigurację, kliknij przycisk **Wdróż** pole wyboru.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Rozpocznij debugowanie (**debugowania / uruchamiania debugowania**, lub **F5**).  
  
9. Plik wykonywalny jest automatycznie wdrażane na komputerze zdalnym.  
  
10. Po wyświetleniu monitu wprowadź poświadczenia sieci, aby nawiązać połączenie z komputerem zdalnym.  
  
     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń w sieci. Na przykład na komputerze domeny, możesz wybrać certyfikat zabezpieczeń, lub wprowadź nazwę domeny i hasło. Na komputerze nienależących do domeny, wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, takie jak <strong>MJO-DL\name@something.com</strong>, oraz prawidłowe hasło.  
  
11. Na komputerze programu Visual Studio powinien zostać wyświetlony, że wykonanie zostanie zatrzymana w punkcie przerwania.  
  
    > [!TIP]
    >  Alternatywnie można rozłożyć pliki w osobnym kroku. W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **mymfc** węzeł, a następnie wybierz **Wdróż**.  
  
    Jeśli masz pliki niezawierające kodu, które będzie używane przez aplikację, należy je uwzględnić w projekcie programu Visual Studio. Utworzenie folderu projektu do dodatkowych plików (w **Eksploratora rozwiązań**, kliknij przycisk **Add / nowy Folder**.) Następnie dodaj pliki do folderu (w **Eksploratora rozwiązań**, kliknij przycisk **dodawania / istniejącego elementu**, następnie wybierz pliki.). Na **właściwości** strony dla każdego pliku, należy ustawić **Kopiuj do katalogu wyjściowego** do **zawsze Kopiuj**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Zdalne debugowanie projektu programu Visual C# lub Visual Basic  
 Debuger nie można wdrożyć aplikacje klasyczne Visual C# lub Visual Basic do maszyny zdalnej, ale możesz nadal możesz debugować je zdalnie, w następujący sposób. W poniższej procedurze przyjęto, że chcesz debugować go na komputerze o nazwie **MJO DL**w sposób pokazany na wcześniejszej ilustracji.
  
1. Utwórz projekt WPF, o nazwie **MyWpf**.  
  
2. Ustaw punkt przerwania w jakimś miejscu w kodzie, który łatwo zostanie osiągnięty.  
  
    Na przykład można ustawić punkt przerwania w obsłudze przycisku. Aby to zrobić, otwórz MainWindow.xaml, Dodaj kontrolkę przycisk z przybornika, a następnie kliknij dwukrotnie przycisk aby otworzyć jego obsługi.
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **właściwości**.  
  
4. Na **właściwości** wybierz **debugowania** kartę.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Upewnij się, że **katalog roboczy** pole tekstowe jest puste.  
  
6. Wybierz **maszyny zdalnej użyj**i wpisz **MJO-DL:4020** w polu tekstowym. (4020 jest numerem portu, wyświetlane w oknie debugera zdalnego).  
  
7. Upewnij się, że **Włącz debugowanie kodu natywnego** nie jest zaznaczone.  
  
8. Skompiluj projekt.  
  
9. Utwórz folder na komputerze zdalnym, który jest taka sama ścieżka jak **debugowania** folderu na komputerze programu Visual Studio:  **\<ścieżki źródłowej > \MyWPF\MyWPF\bin\Debug**.  
  
10. Skopiuj plik wykonywalny, który właśnie zbudowany z komputera programu Visual Studio do nowo utworzonego folderu na komputerze zdalnym.
  
    > [!CAUTION]
    >  Nie należy wprowadzać zmian w kodzie lub ponownej kompilacji lub należy powtórzyć ten krok. Plik wykonywalny, który został skopiowany na komputerze zdalnym musi dokładnie odpowiadać, lokalne źródła i symboli.

    Można ręcznie skopiować projektu, użyj polecenia Xcopy, Robocopy, programu Powershell lub innych opcji.
  
11. Upewnij się, że debuger zdalny jest uruchomiony na komputerze docelowym. (Jeśli nie jest dostępne, wyszukaj **zdalny debuger** w **Start** menu. ) W oknie debugera zdalnego wygląda następująco.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. W programie Visual Studio, Rozpocznij debugowanie (**debugowania / uruchamiania debugowania**, lub **F5**).  
  
13. Po wyświetleniu monitu wprowadź poświadczenia sieci, aby nawiązać połączenie z komputerem zdalnym.  
  
     Wymagane poświadczenia różnią się w zależności od konfiguracji zabezpieczeń w sieci. Na przykład na komputerze domeny można wprowadzić nazwę domeny i hasła. Na komputerze nienależących do domeny, wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, takie jak <strong>MJO-DL\name@something.com</strong>, oraz prawidłowe hasło.

     Powinieneś zobaczyć, że okna głównego aplikacji WPF jest otwarty na komputerze zdalnym.
  
14. Jeśli to konieczne, należy podjąć działania w celu trafiony punkt przerwania. Powinieneś zobaczyć, czy punkt przerwania jest aktywny. Jeśli nie, nie zostały załadowane symbole dla aplikacji. Spróbuj ponownie, a jeśli to nie zadziała, uzyskać informacje na temat ładowania symboli i jak rozwiązywać je na [Opis plików symboli i programu Visual Studio ustawienia symboli](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. Na komputerze programu Visual Studio powinien zostać wyświetlony, że wykonywanie zostało zatrzymane w punkcie przerwania.
  
    Jeśli masz pliki niezawierające kodu, które będzie używane przez aplikację, należy je uwzględnić w projekcie programu Visual Studio. Utworzenie folderu projektu do dodatkowych plików (w **Eksploratora rozwiązań**, kliknij przycisk **Add / nowy Folder**.) Następnie dodaj pliki do folderu (w **Eksploratora rozwiązań**, kliknij przycisk **dodawania / istniejącego elementu**, następnie wybierz pliki.). Na **właściwości** strony dla każdego pliku, należy ustawić **Kopiuj do katalogu wyjściowego** do **zawsze Kopiuj**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli  
 Można debugować kodu za pomocą symboli, które można generować na komputerze programu Visual Studio. Wydajność debugera zdalnego jest znacznie lepiej, gdy używasz symboli lokalnych.  Jeśli musisz użyć zdalnego symbole, należy poinformować monitor debugera zdalnego do wyszukiwania symboli na komputerze zdalnym.  
  
 Począwszy od programu Visual Studio 2013 Update 2 umożliwia następujące polecenia msvsmon przełącznik wiersza polecenia za pomocą zdalnego symboli dla kodu zarządzanego: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Aby uzyskać więcej informacji, zobacz pomocy debugowania zdalnego (naciśnij klawisz **F1** w oknie zdalnego debugera, lub kliknij przycisk **pomocy / użycia**). Więcej informacji można znaleźć [.NET zdalnego ładowania zmiany symboli w programie Visual Studio 2012 i 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Zdalne debugowanie aplikacji Windows Store i Azure  
 Aby uzyskać informacje o zdalnym debugowaniu aplikacji Windows Store, zobacz [debugowania i testowania aplikacji Windows Store na urządzeniu zdalnym z programu Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Aby dowiedzieć się, jak debugowanie na platformie Azure zobacz jeden z tych tematów:  
  
-   [Debugowanie usługi w chmurze lub maszyny wirtualnej w programie Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
-   [Debugowanie zaplecza platformy .NET w programie Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Wprowadzenie do zdalnego debugowania w witrynach sieci Web platformy Azure ([część 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [część 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [część 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Skonfiguruj zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)

---
title: Korzystanie z programu Microsoft Monitoring Agent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ff316a9725692d228c9bc1e8d1415b5e458f4a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741712"
---
# <a name="using-the-microsoft-monitoring-agent"></a>Korzystanie z programu Microsoft Monitoring Agent
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [przy użyciu programu Microsoft Monitoring Agent](https://docs.microsoft.com/visualstudio/debugger/using-the-microsoft-monitoring-agent) w witrynie docs.microsoft.com.

Aplikacje sieci web ASP.NET hostowanych przez usługi IIS i programu SharePoint 2010 lub 2013 aplikacje błędy, problemy z wydajnością lub inne problemy można monitorować lokalnie za pomocą **Microsoft Monitoring Agent**. Zdarzenia diagnostyczne z poziomu agenta można zapisać do pliku dziennika (.iTrace) funkcji IntelliTrace. Następnie możesz otworzyć dziennika w Visual Studio Enterprise (ale nie w wersji Professional lub Community) do debugowania problemów ze wszystkim narzędziami diagnostyki programu Visual Studio. Istnieje też możliwość gromadzenia danych diagnostycznych IntelliTrace i metoda dane, uruchamiając agenta w **śledzenia** trybu. Program Microsoft Monitoring Agent można zintegrować z [usługi Application Insights](http://www.visualstudio.com/get-started/find-performance-problems-vs.aspx) i [System Center Operations Manager](http://technet.microsoft.com/library/hh205987.aspx). Program Microsoft Monitoring Agent zmienić środowiska systemu docelowego, po jej zainstalowaniu.  
  
> [!NOTE]
>  Może również zbierać dane diagnostyczne i metody funkcji IntelliTrace dla sieci web programu SharePoint, WPF i Windows aplikacje formularza na komputerach zdalnych, bez wprowadzania zmian w środowisku docelowym przy użyciu **autonomiczny moduł zbierający IntelliTrace**. Autonomiczny moduł zbierający ma większy wpływ na wydajność niż uruchomienie programu Microsoft Monitoring Agent **Monitor** trybu. Zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 Jeśli używasz programu System Center 2012, za pomocą programu Microsoft Monitoring Agent programu Operations Manager Otrzymuj alerty dotyczące problemów i tworzenie elementów roboczych serwera Team Foundation Server wraz z łączami do zapisane dzienniki IntelliTrace. Następnie można przypisać te elementy robocze z inne potrzeby dalszego debugowania. Zobacz [Integrowanie programu Operations Manager z procesami programowania](http://technet.microsoft.com/library/jj614609.aspx) i [monitorowanie przy użyciu programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
 Przed rozpoczęciem Sprawdź, czy zgodnego źródła i symboli dla kodu skompilowane i wdrożone. Dzięki temu można przejść bezpośrednio do kodu aplikacji, podczas uruchamiania, debugowania i przeglądanie zdarzenia diagnostyczne w dzienniku IntelliTrace. [Skonfiguruj kompilacje](../debugger/diagnose-problems-after-deployment.md) tak, aby program Visual Studio, mogą automatycznie znaleźć i otworzyć pasujące źródło do wdrożonego kodu.  
  
1.  [Krok 1: Konfigurowanie programu Microsoft Monitoring Agent](#SetUpMonitoring)  
  
2.  [Krok 2. Rozpoczynanie monitorowania aplikacji](#MonitorEvents)  
  
3.  [Krok 3: Zapisz zarejestrowane zdarzenia](#SaveEvents)  
  
##  <a name="SetUpMonitoring"></a> Krok 1: Konfigurowanie programu Microsoft Monitoring Agent  
 Skonfiguruj agenta autonomiczny, na serwerze sieci web, do przeprowadzenia monitorowania lokalnego bez konieczności zmieniania aplikacji. Jeśli używasz programu System Center 2012, zobacz [instalacji programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465156.aspx).  
  
###  <a name="SetUpStandaloneMMA"></a> Konfigurowanie agenta autonomiczny  
  
1.  Upewnij się, że:  
  
    -   Na serwerze sieci web jest uruchomiona [obsługiwane wersje programu Internetowe usługi informacyjne (IIS)](http://technet.microsoft.com/library/dn465154.aspx).  
  
    -   Serwer sieci web ma .NET Framework 3.5, 4 lub 4.5.  
  
    -   Serwer sieci web jest uruchomiony program Windows PowerShell 3.0 lub nowszej. [P: co jeśli mam Windows PowerShell 2.0?](#PowerShell2)  
  
    -   Należy mieć uprawnienia administratora na serwerze sieci web, aby uruchamiać polecenia programu PowerShell i Odtwórz pulę aplikacji, po uruchomieniu monitorowania.  
  
    -   Po odinstalowaniu wszystkie wcześniejsze wersje programu Microsoft Monitoring Agent.  
  
2.  [Pobierz bezpłatnie agenta monitorowania Microsoft](http://go.microsoft.com/fwlink/?LinkId=320384), wersji 32-bitowej **MMASetup-i386.exe** lub 64-bitowej wersji **MMASetup-AMD64.exe**, z Microsoft Download Center, aby usługi sieci web serwer.  
  
3.  Uruchom pobrany plik wykonywalny, aby uruchomić Kreatora instalacji.  
  
4.  Utwórz bezpieczny katalog na serwerze sieci web, aby przechowywać dzienniki IntelliTrace, na przykład **C:\IntelliTraceLogs**.  
  
     Upewnij się, utworzyć ten katalog, przed rozpoczęciem monitorowania. Aby nie spowalniać pracy swojej aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo obciążony.  
  
    > [!IMPORTANT]
    >  Dzienniki IntelliTrace może zawierać dane osobowe i wrażliwe. Dostęp do tego katalogu do tych tożsamości, które muszą pracować z plikami. Sprawdź zasady zachowania poufności informacji firmy.  
  
5.  Uruchom szczegółowy poziom funkcji monitorowania lub do monitorowania aplikacji programu SharePoint, należy udzielić tej puli aplikacji, który jest hostem sieci web aplikacji lub aplikacji SharePoint uprawnienia odczytu i zapisu do katalogu dziennika funkcji IntelliTrace. [Pytanie: jak skonfigurować uprawnienia dla puli aplikacji](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Pytania i odpowiedzi  
  
####  <a name="PowerShell2"></a> P: co jeśli mam Windows PowerShell 2.0?  
 **Odp.:** zdecydowanie zalecane jest użycie PowerShell 3.0. W przeciwnym wypadku musisz zaimportować poleceń cmdlet programu Microsoft Monitoring Agent PowerShell z każdym razem, gdy uruchamiasz program PowerShell. Nie masz też dostęp do zawartości pomocy do pobrania.  
  
1.  Otwórz **programu Windows PowerShell** lub **środowiska Windows PowerShell ISE** okna wiersza polecenia jako administrator.  
  
2.  Zaimportuj moduł Microsoft Monitoring Agent PowerShell z domyślnej lokalizacji instalacji:  
  
     **PS C: > Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3.  [Odwiedź TechNet](http://technet.microsoft.com/systemcenter/default) można pobrać najnowszej zawartości pomocy.  
  
####  <a name="FullPermissionsITLog"></a> Pytanie: jak skonfigurować uprawnienia dla puli aplikacji  
 **Odp.:** używać Windows **icacls** polecenia lub za pomocą Eksploratora Windows (lub Eksploratora plików). Na przykład:  
  
- Aby skonfigurować uprawnienia za pomocą Windows **icacls** polecenia:  
  
  - Dla aplikacji sieci web **DefaultAppPool** puli aplikacji:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
  - Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
    —lub—  
  
- Aby skonfigurować uprawnienia za pomocą Eksploratora Windows (lub Eksploratora plików):  
  
  1.  Otwórz **właściwości** dla katalogu dziennika funkcji IntelliTrace.  
  
  2.  Na **zabezpieczeń** kartę, wybrać **Edytuj**, **Dodaj**.  
  
  3.  Upewnij się, że **wbudowane zabezpieczenia główne** pojawia się w **wybierz ten typ obiektu** pole. Jeśli nie ma tam, wybierz **wybierane** ją dodać.  
  
  4.  Upewnij się, że komputer lokalny pojawi się w **z tej lokalizacji** pole. Jeśli nie ma tam, wybierz **lokalizacje** go zmienić.  
  
  5.  W **wprowadź nazwy obiektów do wybrania** Dodaj pulę aplikacji dla aplikacji sieci web lub aplikacji programu SharePoint.  
  
  6.  Wybierz **Sprawdź nazwy** do rozpoznania nazwy. Wybierz **OK**.  
  
  7.  Upewnij się, że pula aplikacji ma **odczytu & wykonać** uprawnienia.  
  
##  <a name="MonitorEvents"></a> Krok 2. Rozpoczynanie monitorowania aplikacji  
 Za pomocą programu Windows PowerShell [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) polecenie, aby rozpocząć monitorowanie aplikacji. Jeśli używasz programu System Center 2012, zobacz [monitorowanie aplikacji sieci Web za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
1.  Na serwerze sieci web Otwórz **programu Windows PowerShell** lub **środowiska Windows PowerShell ISE** okna wiersza polecenia jako administrator.  
  
     ![Otwórz program Windows PowerShell jako administrator](../debugger/media/ffr-powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2.  Uruchom [Start-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) polecenie, aby rozpocząć monitorowanie aplikacji. To spowoduje ponowne uruchomienie wszystkich aplikacji sieci web na serwerze sieci web.  
  
     Oto skróconej składni:  
  
     **Start-WebApplicationMonitoring** *"\<nazwa_aplikacji >"*  *\<monitoringMode >* *"\<outputPath >"*  *\<UInt32 >* *"\<collectionPlanPathAndFileName >"*  
  
     Oto przykład pokazujący, po prostu nazwę aplikacji sieci web i uproszczone **Monitor** trybu:  
  
     **PS C: > Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" Monitorowanie "C:IntelliTraceLogs"**  
  
     Oto przykład pokazujący, ścieżka programu IIS i uproszczone **Monitor** trybu:  
  
     **PS C: > Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" Monitorowanie "C:IntelliTraceLogs"**  
  
     Po rozpoczęciu monitorowania, możesz zobaczyć Wstrzymaj program Microsoft Monitoring Agent podczas ponownego uruchomienia aplikacji.  
  
     ![Rozpocznij monitorowanie za pomocą potwierdzenia MMA](../debugger/media/ffr-powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\<nazwa_aplikacji >"*|Określ ścieżkę do nazwy aplikacji sieci web i witryny sieci web w usługach IIS. Można także dodać ścieżkę usług IIS, jeśli użytkownik sobie tego życzy.<br /><br /> *"\<IISWebsiteName >\\< IISWebAppName\>"*<br /><br /> —lub—<br /><br /> **"IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*<br /><br /> Tę ścieżkę można znaleźć w Menedżerze usług IIS. Na przykład:<br /><br /> ![Ścieżka do witryny sieci web usług IIS i aplikacji sieci web](../debugger/media/ffr-iismanager.png "FFR_IISManager")<br /><br /> Można również użyć [Get-WebSite](http://technet.microsoft.com/library/ee807832.aspx) i [uzyskać WebApplication](http://technet.microsoft.com/library/ee790554.aspx) poleceń.|  
    |*\<monitoringMode >*|Określ tryb monitorowania:<br /><br /> <ul><li>**Monitor**: Rejestrowanie minimalne szczegółowe informacje na temat zdarzeń dotyczących wyjątków i zdarzeń dotyczących wydajności. W tym trybie wykorzystuje domyślny plan kolekcji.</li><li>**Śledzenie**: Zarejestruj szczegóły na poziomie funkcji lub monitorowanie aplikacji SharePoint 2010 i SharePoint 2013 przy użyciu planu w określonej kolekcji. Ten tryb może uniemożliwić aplikacji wykonywania wolniej.<br /><br /> <ul><li>[Pytanie: jak skonfigurować uprawnienia dla puli aplikacji](#FullPermissionsITLog)</li><li>[P: jak uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing)</li></ul><br />     Przykład ten rejestruje zdarzenia dla aplikacji programu SharePoint hostowany w witrynie programu SharePoint:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" śledzenia "C:\Program Files\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Niestandardowe**: rejestrowanie szczegółów niestandardowego przy użyciu określonego dostosowanego planu kolekcji. Musisz ponownie uruchomić monitorowanie edycji planu kolekcji po monitorowania został już uruchomiony.</li></ul>|  
    |*"\<outputPath >"*|Określ pełną ścieżką do przechowywania dzienników IntelliTrace. Upewnij się, utworzyć ten katalog, przed rozpoczęciem monitorowania.|  
    |*\<UInt32 >*|Określ maksymalny rozmiar dziennika IntelliTrace. Domyślny maksymalny rozmiar dziennika IntelliTrace to 250 MB.<br /><br /> Gdy osiągnie ten limit, agent zastępuje najwcześniej wpisy, aby zrobić miejsce na więcej wpisów. Aby zmienić ten limit, użyj **— wartość właściwości MaximumFileSizeInMegabytes** opcji lub edytować `MaximumLogFileSize` atrybutu w planie kolekcji.|  
    |*"\<collectionPlanPathAndFileName >"*|Określ pełną ścieżkę lub względną ścieżkę i nazwę pliku w planie kolekcji. Ten plan jest plikiem .xml, który konfiguruje ustawienia dla agenta.<br /><br /> Te plany są uwzględnione w agencie i Praca z aplikacjami sieci web i aplikacji programu SharePoint:<br /><br /> -   **ASP.NET.default.XML**<br />     Zbiera tylko zdarzenia, takie jak wyjątki, zdarzenia wydajności, wywołaniami bazy danych i żądaniami serwera sieci Web.<br />-   **collection_plan.asp.NET.trace.XML**<br />     Wywołania funkcji na poziomie zbiera oraz wszystkie dane w domyślny plan kolekcji. Ten plan jest dobry szczegółową analizę, ale może spowolnić aplikację.<br /><br /> Zlokalizowane wersje tych planów można znaleźć w podfolderach agenta. Możesz również [Dostosuj te plany lub utworzyć własne plany](http://go.microsoft.com/fwlink/?LinkId=227871) aby nie spowalniać pracy swojej aplikacji. Umieścić plany kolekcji niestandardowej w tym samym bezpiecznym miejscu na agenta.<br /><br /> [P: jak uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing)|  
  
     Aby uzyskać więcej informacji o pełnej składni i inne przykłady, uruchom **get-help Start-WebApplicationMonitoring — szczegółowe** polecenia lub **get-help Start-WebApplicationMonitoring — przykłady** polecenie.  
  
3.  Aby sprawdzić stan wszystkich monitorowanych aplikacji sieci web, uruchom [Get-WebApplicationMonitoringStatus](http://go.microsoft.com/fwlink/?LinkID=313685) polecenia.  
  
### <a name="q--a"></a>Pytania i odpowiedzi  
  
####  <a name="Minimizing"></a> P: jak uzyskać większość danych bez spowalniania mojej aplikacji?  
 **Odp.:** Microsoft Monitoring Agent może zbierać dużą ilość danych i ma wpływ na wydajność aplikacji, w zależności od zbierania danych i jak je zebrać. Oto kilka sposobów na zdobycie większości danych bez spowalniania aplikacji:  
  
- Dla aplikacji sieci web i aplikacji programu SharePoint agent rejestruje dane dla każdej aplikacji, która udostępnia określona pula aplikacji. Może to spowolnić każdej aplikacji, która udostępnia tej samej puli aplikacji, mimo że można ograniczyć kolekcji do modułów, w ramach jednej aplikacji. Aby nie spowalniać inne aplikacje, Hostuj każdą aplikację we własnej puli aplikacji.  
  
- Przejrzyj zdarzenia, dla których agent zbiera dane w planie kolekcji. Edytuj plan kolekcji, aby wyłączyć zdarzenia, które nie są odpowiednie ani interesujące. Może to poprawić wydajność uruchamiania i wydajność środowiska uruchomieniowego.  
  
   Aby wyłączyć zdarzenie, ustaw `enabled` atrybutu dla `<DiagnosticEventSpecification>` elementu `false`:  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   Jeśli `enabled` atrybut nie istnieje, zdarzenie jest włączone.  
  
   Na przykład:  
  
  -   Wyłącz zdarzenia Windows Workflow dla aplikacji, które nie używają Windows Workflow.  
  
  -   Wyłącz zdarzenia rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie wyświetlają problemów z ustawieniami rejestru.  
  
- Przegląd moduły, dla których agent zbiera dane w planie kolekcji. Edytuj plan kolekcji, aby uwzględnić tylko moduły, które Cię interesują.  
  
   Zmniejsza to ilość informacji wywołania metody oraz innych danych instrumentacji, które agent zbiera, gdy aplikacja jest uruchomiona i. Te dane ułatwiają przejść przez kod podczas debugowania i przeglądając wartości przekazywane do i zwrócony z wywołania funkcji.  
  
  1. Otwórz plan kolekcji. Znajdź `<ModuleList>` elementu.  
  
  2. W `<ModuleList>`ustaw `isExclusionList` atrybutu `false`.  
  
  3. Użyj `<Name>` elementu, aby określić każdy moduł przy użyciu jednego z następujących czynności: Nazwa pliku wartość ciągu, aby uwzględnić dowolny moduł, którego nazwa zawiera dany ciąg lub klucz publiczny.  
  
     W tym przykładzie tworzy listę, która gromadzi dane tylko z głównego modułu aplikacji sieci web Fabrikam Fiber:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>FabrikamFiber.Web.dll</Name>  
  </ModuleList>  
  
  ```  
  
   Aby zebrać dane z każdego modułu, którego nazwa zawiera "Fabrikam", Utwórz listę podobny do poniższego:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>Fabrikam</Name>  
  </ModuleList>  
  
  ```  
  
   Aby zebrać dane z modułów, określając tokeny klucza publicznego, Utwórz listę podobny do poniższego:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>PublicKeyToken:B77A5C561934E089</Name>  
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
     <Name>PublicKeyToken:31BF3856AD364E35</Name>  
     <Name>PublicKeyToken:89845DCD8080CC91</Name>  
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
  </ModuleList>  
  
  ```  
  
   **P: Dlaczego nie po prostu wykluczyć modułów?**  
  
   **Odp.:** plany kolekcji domyślnie wykluczają moduły przez ustawienie `isExclusionList` atrybutu `true`. Jednak to może nadal zbierać dane z modułów, które nie spełniają kryteriów listy lub które mogą nie być interesujące, takie jak moduły strony trzeciej lub typu open source.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>Pytanie: jakie wartości jest zbieranie agenta?  
 **Odp.:** Aby zmniejszyć wpływ na wydajność, agent zbiera tylko następujące wartości:  
  
- Pierwotne typy danych, które są przekazywane do metod oraz zwracanych przez  
  
- Typy danych pierwotnych w polach obiektów najwyższego poziomu przekazywane do metod oraz zwracanych przez  
  
  Załóżmy, że masz `AlterEmployee` podpis metody, która akceptuje liczbę całkowitą `id` i `Employee` obiektu `oldemployee`:  
  
  `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
  `Employee` Typ ma następujące atrybuty: `Id`, `Name`, i `HomeAddress`. Istnieje relacja skojarzenia między `Employee` i `Address` typu.  
  
  ![Relacja między pracowników i adres](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
  Agent zapisuje wartości dla `id`, `Employee.Id`, `Employee.Name` i `Employee` obiekt zwracany z `AlterEmployee` metody. Jednak agent nie zapisuje informacje o `Address` innych obiektów niż posiadającym wartość zerową lub nie. Agent nie zapisuje również dane dotyczące zmiennych lokalnych w `AlterEmployee` metody, chyba że inne metody używają tych zmiennych lokalnych jako parametrów w tym momencie są zapisywane jako parametry metody.  
  
##  <a name="SaveEvents"></a> Krok 3: Zapisz zarejestrowane zdarzenia  
 Po znalezieniu błędu lub problemu z wydajnością, Zapisz zarejestrowane zdarzenia w dzienniku IntelliTrace. Agent tworzy dziennik tylko wtedy, gdy zarejestrował zdarzenia. Jeśli używasz programu System Center 2012, zobacz [monitorowanie aplikacji sieci Web za pomocą programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Zapisz zarejestrowane zdarzenia, ale Kontunuuj monitorowanie  
 Wykonaj następujące kroki, gdy chcesz utworzyć dziennik IntelliTrace, ale nie chcesz ponownie uruchomić aplikacji lub zatrzymywania monitorowania. Agent kontynuuje monitorowanie, nawet jeśli ponowne uruchomienie serwera lub aplikacji.  
  
1. Na serwerze sieci web Otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.  
  
2. Uruchom [Checkpoint-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313684) polecenie, aby zapisać migawkę dziennika IntelliTrace:  
  
    **CheckPoint-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- lub —  
  
    **CheckPoint-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Na przykład:  
  
    **PS C:\\> Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
    —lub—  
  
    **PS C: > Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**  
  
    Aby uzyskać więcej informacji, uruchom **get-help Checkpoint-WebApplicationMonitoring — szczegółowe** polecenia lub **get-help Checkpoint-WebApplicationMonitoring — przykłady** polecenia.  
  
3. Kopiuj dziennik do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, który ma Visual Studio Enterprise (ale nie w wersji Professional lub Community).  
  
   > [!IMPORTANT]
   >  Należy zachować ostrożność podczas udostępniania dzienników IntelliTrace, ponieważ mogą one zawierać dane osobowe i wrażliwe. Upewnij się, kto mogą uzyskiwać dostęp do tych dzienników ma uprawnienia do wzięcia pod tych danych. Sprawdź zasady zachowania poufności informacji firmy.  
  
   **Następnie:** [diagnozowanie rejestrowane zdarzenia w programie Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Zapisz zarejestrowane zdarzenia i zatrzymać monitorowanie  
 Jeśli po prostu chcesz uzyskać informacje diagnostyczne podczas odtwarzania konkretnego problemu, wykonaj następujące kroki. To spowoduje ponowne uruchomienie wszystkich aplikacji sieci web na serwerze sieci web.  
  
1. Na serwerze sieci web Otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.  
  
2. Uruchom [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) polecenie, aby utworzyć dziennik IntelliTrace i zatrzymać monitorowanie aplikacji internetowej:  
  
    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*  
  
    \- lub —  
  
    **Stop-WebApplicationMonitoring "IIS:\sites**  *\\< IISWebsiteName\>\\< IISWebAppName\>"*  
  
    Lub aby zatrzymać monitorowanie wszystkich aplikacji sieci web:  
  
    **Stop-WebApplicationMonitoring - wszystkie**  
  
    Na przykład:  
  
    **PS C:\\> Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
    \- lub —  
  
    **PS C:\\> Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**  
  
    Aby uzyskać więcej informacji, uruchom **get-help Stop-WebApplicationMonitoring — szczegółowe** polecenia lub **get-help Stop-WebApplicationMonitoring — przykłady** polecenia.  
  
3. Kopiuj dziennik do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, który ma Visual Studio Enterprise.  
  
   **Następnie:** [diagnozowanie rejestrowane zdarzenia w programie Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-where-can-i-get-more-information"></a>P: gdzie można uzyskać więcej informacji?  
  
#### <a name="blogs"></a>Blogi  
 [Wprowadzenie do programu Microsoft Monitoring Agent](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/introducing-microsoft-monitoring-agent.aspx)  
  
 [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
#### <a name="forums"></a>Fora  
 [Diagnostyka programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)










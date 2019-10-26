---
title: Korzystanie z Microsoft Monitoring Agent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2489ae06e3ff5ffc362599018e4e95d58f92b2ad
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911282"
---
# <a name="using-the-microsoft-monitoring-agent-c-visual-basic"></a>Korzystanie z Microsoft Monitoring Agent (C#, Visual Basic)

Można monitorować lokalnie aplikacje sieci Web ASP.NET hostowane przez usługi IIS oraz aplikacje programu SharePoint 2010 lub 2013 pod kątem błędów, problemów z wydajnością lub innych problemów przy użyciu **Microsoft Monitoring Agent**. Zdarzenia diagnostyczne z agenta można zapisać do pliku dziennika IntelliTrace (. iTrace). Następnie można otworzyć Visual Studio Enterprise logowania (ale nie wersji Professional lub Community), aby debugować problemy ze wszystkimi narzędziami diagnostycznymi programu Visual Studio. Możesz również zbierać dane diagnostyczne IntelliTrace i dane metod, uruchamiając agenta w trybie **śledzenia** . Microsoft Monitoring Agent można zintegrować z usługami [Application Insights](/azure/application-insights/) i [System Center Operations Manager](/previous-versions/system-center/system-center-2012-R2/hh205987(v=sc.12)). Microsoft Monitoring Agent zmienia środowisko systemu docelowego podczas instalacji.

> [!NOTE]
> Możesz również zbierać IntelliTrace dane diagnostyczne i metody dla aplikacji sieci Web, SharePoint, WPF i Windows form na maszynach zdalnych bez zmiany środowiska docelowego przy użyciu **modułu zbierającego autonomicznego IntelliTrace**. Moduł zbierający autonomiczny ma większy wpływ na wydajność niż uruchamianie Microsoft Monitoring Agent w trybie **monitora** . Zobacz [Używanie autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

 Jeśli używasz programu System Center 2012, użyj Microsoft Monitoring Agent z Operations Manager, aby otrzymywać alerty o problemach i tworzyć Team Foundation Server elementy robocze z linkami do zapisanych dzienników IntelliTrace. Następnie można przypisać te elementy robocze do innych celów debugowania. Zobacz [integrowanie Operations Manager z procesami deweloperskimi](/previous-versions/system-center/system-center-2012-R2/jj614609(v=sc.12)) i [monitorowaniem przy użyciu Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).

 Przed rozpoczęciem upewnij się, że masz pasujące źródło i symbole dla skompilowanego i wdrożonego kodu. Dzięki temu możesz przejść bezpośrednio do kodu aplikacji po rozpoczęciu debugowania i przeglądania zdarzeń diagnostycznych w dzienniku IntelliTrace. [Skonfiguruj kompilacje](../debugger/diagnose-problems-after-deployment.md) tak, aby program Visual Studio mógł automatycznie znaleźć i otworzyć pasujące Źródło dla wdrożonego kodu.

1. [Krok 1. Konfigurowanie Microsoft Monitoring Agent](#SetUpMonitoring)

2. [Krok 2. rozpoczęcie monitorowania aplikacji](#MonitorEvents)

3. [Krok 3. zapisywanie zarejestrowanych zdarzeń](#SaveEvents)

## <a name="SetUpMonitoring"></a>Krok 1. Konfigurowanie Microsoft Monitoring Agent

 Skonfiguruj autonomiczny Agent na serwerze sieci Web, aby przeprowadzić monitorowanie lokalne bez zmiany aplikacji. Jeśli używasz programu System Center 2012, zobacz [instalowanie Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465156(v=sc.12)).

### <a name="SetUpStandaloneMMA"></a>Konfigurowanie agenta autonomicznego

1. Upewnij się, że:

    - Na serwerze sieci Web działa [obsługiwana wersja programu Internet Information Services (IIS)](/previous-versions/system-center/system-center-2012-R2/dn465154(v=sc.12)).

    - Serwer sieci Web ma .NET Framework 3,5, 4 lub 4,5.

    - Na serwerze sieci Web jest uruchomiony program Windows PowerShell 3,0 lub nowszy. [P: co w przypadku, gdy mam program Windows PowerShell 2,0?](#PowerShell2)

    - Masz uprawnienia administratora na serwerze sieci Web, aby uruchomić polecenia programu PowerShell i odtworzyć pulę aplikacji po rozpoczęciu monitorowania.

    - Wszystkie wcześniejsze wersje Microsoft Monitoring Agent zostały odinstalowane.

2. [Pobierz bezpłatną Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316), czyli 32-bitową wersję **MMASetup-i386. exe** lub 64-bitową w wersji **MMASetup-AMD64. exe**, z centrum pobierania firmy Microsoft do serwera sieci Web.

3. Uruchom pobrany plik wykonywalny, aby uruchomić Kreatora instalacji.

4. Utwórz bezpieczny katalog na serwerze sieci Web, aby przechowywać dzienniki IntelliTrace, na przykład **C:\IntelliTraceLogs**.

     Przed rozpoczęciem monitorowania upewnij się, że ten katalog został utworzony. Aby uniknąć spowolnienia działania aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo aktywny.

    > [!IMPORTANT]
    > Dzienniki IntelliTrace mogą zawierać dane osobowe i poufne. Ogranicz ten katalog tylko do tożsamości, które muszą współpracować z plikami. Sprawdź zasady zachowania poufności informacji firmy.

5. Aby uruchomić szczegółowe monitorowanie poziomu funkcji lub monitorować aplikacje programu SharePoint, nadaj puli aplikacji, która hostuje aplikację sieci Web lub uprawnienia do odczytu i zapisu w katalogu dziennika IntelliTrace. [P: Jak mogę skonfigurować uprawnienia dla puli aplikacji?](#FullPermissionsITLog)

### <a name="q--a"></a>p & A

#### <a name="PowerShell2"></a>P: co w przypadku, gdy mam program Windows PowerShell 2,0?
 Odp **.:** Zdecydowanie zalecamy użycie programu PowerShell 3,0. W przeciwnym razie konieczne będzie zaimportowanie Microsoft Monitoring Agent poleceń cmdlet programu PowerShell przy każdym uruchomieniu programu PowerShell. Nie będzie też można uzyskać dostępu do zawartości pomocy do pobrania.

1. Otwórz program **Windows PowerShell** lub **Windows PowerShell ISE** okno wiersza polecenia jako administrator.

2. Zaimportuj moduł Microsoft Monitoring Agent PowerShell z domyślnej lokalizacji instalacji:

     **PS C: > Import-Module "C:\Program Files\Microsoft monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**

3. [Odwiedź witrynę TechNet](https://technet.microsoft.com/systemcenter/default) , aby uzyskać najnowszą zawartość pomocy.

#### <a name="FullPermissionsITLog"></a>P: Jak mogę skonfigurować uprawnienia dla puli aplikacji?
 Odp **.:** Użyj polecenia **icacls** systemu Windows lub Eksploratora Windows (lub Eksploratora plików). Na przykład:

- Aby skonfigurować uprawnienia za pomocą polecenia **icacls** systemu Windows:

  - W przypadku aplikacji sieci Web w **puli aplikacji z** identyfikatorem usługi

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`

  - W przypadku aplikacji SharePoint w puli aplikacji **programu SharePoint-80** :

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`

    —lub—

- Aby skonfigurować uprawnienia za pomocą Eksploratora Windows (lub Eksploratora plików):

  1. Otwórz **Właściwości** katalogu dziennika IntelliTrace.

  2. Na karcie **zabezpieczenia** wybierz pozycję **Edytuj**, a następnie pozycję **Dodaj**.

  3. Upewnij się, że **wbudowane podmioty zabezpieczeń** są wyświetlane w polu **Wybierz ten typ obiektu** . Jeśli tak nie jest, wybierz **typy obiektów** , aby je dodać.

  4. Upewnij się, że komputer lokalny jest wyświetlany w polu **z tej lokalizacji** . Jeśli tak nie jest, wybierz **lokalizacje** , aby je zmienić.

  5. W polu **Wprowadź nazwy obiektów do wybrania** Dodaj pulę aplikacji aplikacji sieci Web lub aplikacji programu SharePoint.

  6. Wybierz **Sprawdź nazwy** , aby rozpoznać nazwę. Wybierz **przycisk OK**.

  7. Upewnij się, że Pula aplikacji ma uprawnienia do **wykonywania &** .

## <a name="MonitorEvents"></a>Krok 2. rozpoczęcie monitorowania aplikacji
 Aby rozpocząć monitorowanie aplikacji, użyj polecenia [Start-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) środowiska Windows PowerShell. W przypadku korzystania z programu System Center 2012 zobacz [monitorowanie aplikacji sieci Web za pomocą Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465157.aspx).

1. Na serwerze sieci Web otwórz okno **programu Windows PowerShell** lub **Windows PowerShell ISE** oknie wiersza polecenia jako administrator.

     ![Otwórz program Windows PowerShell jako administrator](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin")

2. Uruchom polecenie [Start-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) , aby rozpocząć monitorowanie aplikacji. Spowoduje to ponowne uruchomienie wszystkich aplikacji sieci Web na serwerze sieci Web.

     Oto krótka Składnia:

     **Start-WebApplicationMonitoring** *"\<nazwa_aplikacji >"* *\<monitorowaniamode >* *"\<outputPath >"* *\<UInt32 >* *"\<collectionPlanPathAndFileName >"*

     Oto przykład, który używa samej nazwy aplikacji sieci Web i uproszczonego **monitora** :

     **PS C: > Start-WebApplicationMonitoring "FabrikamFabrikamFiber. Web" Monitor "C:IntelliTraceLogs"**

     Oto przykład korzystający ze ścieżki usług IIS i uproszczonego **monitora** :

     **PS C: > Start-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web" Monitor "C:IntelliTraceLogs"**

     Po rozpoczęciu monitorowania podczas ponownego uruchamiania aplikacji może zostać wyświetlony Microsoft Monitoring Agent wstrzymanie.

     ![Rozpocznij monitorowanie z potwierdzeniem MMA](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")

    |||
    |-|-|
    |*"\<nazwa_aplikacji >"*|Określ ścieżkę do witryny sieci Web i nazwy aplikacji sieci Web w usługach IIS. Jeśli wolisz, możesz również uwzględnić ścieżkę IIS.<br /><br /> *"\<IISWebsiteName >\\< IISWebAppName\>"*<br /><br /> —lub—<br /><br /> **"IIS: \ lokacje** *\\< IISWebsiteName\>\\< IISWebAppName\>"*<br /><br /> Tę ścieżkę można znaleźć w Menedżerze usług IIS. Na przykład:<br /><br /> ![Ścieżka do witryny sieci Web i aplikacji sieci Web usług IIS](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> Możesz również użyć poleceń [Get-Web](https://technet.microsoft.com/library/ee807832.aspx) i [Get WebApplication](https://technet.microsoft.com/library/ee790554.aspx) .|
    |*\<> monitorowania*|Określ tryb monitorowania:<br /><br /> <ul><li>**Monitoruj**: rejestruje minimalne szczegóły dotyczące zdarzeń wyjątków i zdarzeń wydajności. Ten tryb używa domyślnego planu kolekcji.</li><li>**Śledzenie**: rejestrowanie szczegółów poziomu funkcji lub monitorowanie aplikacji SharePoint 2010 i SharePoint 2013 przy użyciu określonego planu kolekcji. Ten tryb może sprawiać, że aplikacja będzie działać wolniej.<br /><br /> <ul><li>[P: Jak mogę skonfigurować uprawnienia dla puli aplikacji?](#FullPermissionsITLog)</li><li>[P: Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?](#Minimizing)</li></ul><br />     Ten przykład rejestruje zdarzenia dla aplikacji programu SharePoint hostowanej w witrynie programu SharePoint:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp", śledzenie "C:\Program Files\Microsoft monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Niestandardowe**: rejestruje szczegóły niestandardowe przy użyciu określonego niestandardowego planu kolekcji. Należy ponownie uruchomić monitorowanie, jeśli po zakończeniu monitorowania już zostanie przeprowadzone Edytowanie planu zbierania danych.</li></ul>|
    |*"\<outputPath >"*|Określ pełną ścieżkę katalogu do przechowywania dzienników IntelliTrace. Przed rozpoczęciem monitorowania upewnij się, że ten katalog został utworzony.|
    |*\<UInt32 >*|Określ maksymalny rozmiar dziennika IntelliTrace. Domyślny maksymalny rozmiar dziennika IntelliTrace to 250 MB.<br /><br /> Gdy dziennik osiągnie ten limit, Agent zastępuje najwcześniejsze wpisy, aby miejsce na więcej wpisów. Aby zmienić ten limit, należy użyć opcji **-wartość właściwości maximumfilesizeinmegabytes** lub edytować atrybut `MaximumLogFileSize` w planie kolekcji.|
    |*"\<collectionPlanPathAndFileName >"*|Określ pełną ścieżkę lub ścieżkę względną oraz nazwę pliku planu kolekcji. Ten plan jest plikiem XML, który konfiguruje ustawienia dla agenta.<br /><br /> Te plany są dołączone do agenta i działają z aplikacjami sieci Web i aplikacjami programu SharePoint:<br /><br /> -   **collection_plan. ASP. NET. default. XML**<br />     Zbiera tylko zdarzenia, takie jak wyjątki, zdarzenia wydajności, wywołania bazy danych i żądania serwera sieci Web.<br />-   **collection_plan. ASP. NET. Trace. XML**<br />     Zbiera wywołania na poziomie funkcji i wszystkie dane z domyślnego planu kolekcji. Ten plan jest dobry dla szczegółowej analizy, ale może spowolnić aplikację.<br /><br /> Zlokalizowane wersje tych planów można znaleźć w podfolderach agenta. Możesz również [dostosować te plany lub utworzyć własne plany](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) , aby uniknąć spowolnienia działania aplikacji. Wszystkie plany niestandardowe należy umieścić w tej samej bezpiecznej lokalizacji co Agent.<br /><br /> [P: Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?](#Minimizing)|

     Aby uzyskać więcej informacji na temat pełnej składni i innych przykładów, uruchom polecenie **Get-Help Start-WebApplicationMonitoring-detailed** lub polecenie **Get-Help Start-WebApplicationMonitoring-** example.

3. Aby sprawdzić stan wszystkich monitorowanych aplikacji sieci Web, uruchom polecenie [Get-WebApplicationMonitoringStatus](/previous-versions/system-center/powershell/system-center-2012-r2/dn472751(v=sc.20)) .

### <a name="q--a"></a>p & A

#### <a name="Minimizing"></a>P: Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?
 Odp **.:** Microsoft Monitoring Agent może zbierać wiele danych i wpływać na wydajność aplikacji w zależności od wybranych danych do zebrania i sposobu ich zbierania. Oto kilka sposobów na uzyskanie większości danych bez spowalniania aplikacji:

- W przypadku aplikacji sieci Web i aplikacji programu SharePoint Agent rejestruje dane dla każdej aplikacji, która współużytkuje określoną pulę aplikacji. Może to spowolnić każdą aplikację, która współużytkuje tę samą pulę aplikacji, nawet jeśli można ograniczyć kolekcję do modułów dla jednej aplikacji. Aby uniknąć spowolnienia innych aplikacji, należy hostować każdą aplikację we własnej puli aplikacji.

- Przejrzyj zdarzenia, dla których Agent zbiera dane w planie kolekcji. Edytuj plan kolekcji, aby wyłączyć zdarzenia, które nie są odpowiednie lub nie są interesujące. Może to poprawić wydajność uruchamiania i wydajność w czasie wykonywania.

   Aby wyłączyć zdarzenie, ustaw atrybut `enabled` dla elementu `<DiagnosticEventSpecification>` na `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Jeśli atrybut `enabled` nie istnieje, zdarzenie jest włączone.

   Na przykład:

  - Wyłącz zdarzenia Windows Workflow dla aplikacji, które nie używają przepływu pracy systemu Windows.

  - Wyłącz zdarzenia rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie wyświetlaj problemów z ustawieniami rejestru.

- Przejrzyj moduły, dla których Agent zbiera dane w planie kolekcji. Edytuj plan kolekcji w celu uwzględnienia tylko interesujących Cię modułów.

   Zmniejsza to ilość informacji o wywołaniu metody i innych danych Instrumentacji zbieranych przez agenta podczas uruchamiania i uruchamiania aplikacji. Te dane ułatwiają przechodzenie przez kod podczas debugowania i przeglądania wartości, które są przenoszone i zwracane przez wywołania funkcji.

  1. Otwórz plan zbierania danych. Znajdź element `<ModuleList>`.

  2. W `<ModuleList>`ustaw atrybut `isExclusionList` na `false`.

  3. Użyj elementu `<Name>`, aby określić każdy moduł z jedną z następujących: nazwą pliku, wartością ciągu do uwzględnienia dowolnego modułu, którego nazwa zawiera ten ciąg lub klucz publiczny.

     Ten przykład tworzy listę, która zbiera dane tylko z głównego modułu aplikacji sieci Web firmy Fabrikam Fiber:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>

  ```

   Aby zebrać dane z dowolnego modułu, którego nazwa zawiera "Fabrikam", Utwórz listę taką jak:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>

  ```

   Aby zebrać dane z modułów przez określenie ich tokenów kluczy publicznych, Utwórz listę taką jak:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>

  ```

   **P: Dlaczego nie wykluczają się tylko moduły?**

   Odp **.:** Domyślnie plany kolekcji wykluczają moduły, ustawiając atrybut `isExclusionList` na `true`. Może jednak nadal zbierać dane z modułów, które nie spełniają kryteriów listy lub które mogą nie być interesujące, takie jak moduły innych firm lub typu open-source.

#### <a name="q-what-values-does-the-agent-collect"></a>P: jakie wartości zbiera Agent?

Odp **.:** Aby zmniejszyć wpływ na wydajność, Agent zbiera tylko te wartości:

- Typy danych pierwotnych, które są przesyłane do i zwracane z metod

- Typy danych pierwotnych w polach dla obiektów najwyższego poziomu przekazana do i zwróconych z metod

Załóżmy na przykład, że masz sygnaturę metody `AlterEmployee`, która akceptuje liczbę całkowitą `id` i `Employee` obiektu `oldemployee`:

`public Employee AlterEmployee(int id, Employee oldemployee)`

Typ `Employee` ma następujące atrybuty: `Id`, `Name`i `HomeAddress`. Między `Employee` i typem `Address` istnieje relacja skojarzenia.

![Relacja między pracownikiem a adresem](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

Agent rejestruje wartości `id`, `Employee.Id`, `Employee.Name` i `Employee` obiektu zwróconego z metody `AlterEmployee`. Jednak Agent nie rejestruje informacji o obiekcie `Address` innym niż to, czy ma on wartość null, czy nie. Agent nie rejestruje również danych o zmiennych lokalnych w metodzie `AlterEmployee`, chyba że inne metody używają tych zmiennych lokalnych jako parametrów, w których są one rejestrowane jako parametry metody.

## <a name="SaveEvents"></a>Krok 3. zapisywanie zarejestrowanych zdarzeń
 Po znalezieniu błędu lub problemu z wydajnością Zapisz zarejestrowane zdarzenia w dzienniku IntelliTrace. Agent tworzy dziennik tylko wtedy, gdy zarejestrował zdarzenia. W przypadku korzystania z programu System Center 2012 zobacz [monitorowanie aplikacji sieci Web za pomocą Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465157.aspx).

### <a name="save-recorded-events-but-continue-monitoring"></a>Zapisuj zarejestrowane zdarzenia, ale Kontynuuj monitorowanie
 Wykonaj następujące kroki, aby utworzyć dziennik IntelliTrace, ale nie chcesz ponownie uruchamiać aplikacji ani zatrzymać monitorowania. Agent kontynuuje monitorowanie nawet w przypadku ponownego uruchomienia serwera lub aplikacji.

1. Na serwerze sieci Web otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.

2. Uruchom polecenie [Checkpoint-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472750(v=sc.20)) , aby zapisać migawkę dziennika IntelliTrace:

    **Checkpoint-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*

    \- lub-

    **Checkpoint-WebApplicationMonitoring "IIS: \ lokacje** *\\< IISWebsiteName\>\\< IISWebAppName\>"*

    Na przykład:

    **PS C:\\> Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**

    —lub—

    **PS C: > Checkpoint-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web"**

    Aby uzyskać więcej informacji, uruchom polecenie **Get-Help Checkpoint-WebApplicationMonitoring-Details** lub Command **Get-Help Checkpoint-WebApplicationMonitoring-przykłady** .

3. Skopiuj dziennik do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, który ma Visual Studio Enterprise (ale nie wersje Professional lub Community).

   > [!IMPORTANT]
   > Należy zachować ostrożność podczas udostępniania dzienników IntelliTrace, ponieważ mogą one zawierać dane osobowe i poufne. Upewnij się, że osoba mająca dostęp do tych dzienników ma uprawnienia do przeglądania tych danych. Sprawdź zasady zachowania poufności informacji firmy.

   **Dalej:** [Diagnozuj zarejestrowane zdarzenia w Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

### <a name="save-recorded-events-and-stop-monitoring"></a>Zapisuj zarejestrowane zdarzenia i Zatrzymaj monitorowanie
 Wykonaj następujące kroki, aby uzyskać informacje diagnostyczne po odtworzeniu określonego problemu. Spowoduje to ponowne uruchomienie wszystkich aplikacji sieci Web na serwerze sieci Web.

1. Na serwerze sieci Web otwórz okno wiersza polecenia programu Windows PowerShell jako administrator.

2. Uruchom polecenie [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) , aby utworzyć dziennik IntelliTrace i zatrzymać monitorowanie określonej aplikacji sieci Web:

    **Stop-WebApplicationMonitoring** *"\<IISWebsiteName >\\< IISWebAppName\>"*

    \- lub-

    **Stop-WebApplicationMonitoring "IIS: \ lokacje** *\\< IISWebsiteName\>\\< IISWebAppName\>"*

    Lub aby zatrzymać monitorowanie wszystkich aplikacji sieci Web:

    **Stop-WebApplicationMonitoring — wszystko**

    Na przykład:

    **PS C:\\> Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**

    \- lub-

    **PS C:\\> Stop-WebApplicationMonitoring "IIS: \ sites\Fabrikam\FabrikamFiber.Web"**

    Aby uzyskać więcej informacji, uruchom polecenie **get-help Stop-WebApplicationMonitoring-detail** lub polecenie **get-help Stop-WebApplicationMonitoring-** example.

3. Skopiuj dziennik do bezpiecznego folderu udostępnionego, a następnie otwórz dziennik z komputera, który ma Visual Studio Enterprise.

   **Dalej:** [Diagnozuj zarejestrowane zdarzenia w Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

## <a name="q--a"></a>p & A

### <a name="q-where-can-i-get-more-information"></a>P: gdzie można uzyskać więcej informacji?

#### <a name="blogs"></a>Blogi
 [Wprowadzenie Microsoft Monitoring Agent](https://devblogs.microsoft.com/devops/introducing-microsoft-monitoring-agent/)

 [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

#### <a name="forums"></a>Fora
 [Diagnostyka programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

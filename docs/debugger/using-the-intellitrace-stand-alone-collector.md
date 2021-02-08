---
title: Korzystanie z autonomicznego modułu zbierającego IntelliTrace | Microsoft Docs
description: Użyj autonomicznego modułu zbierającego IntelliTrace, aby zbierać dane bez instalowania programu Visual Studio i bez zmiany środowiska systemu docelowego.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 251b15edc838a1231e017d8f23b04f8bbb773692
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840876"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Korzystanie z autonomicznego modułu zbierającego IntelliTrace (C#, Visual Basic)

Autonomiczny **moduł zbierający IntelliTrace** umożliwia zbieranie danych diagnostycznych IntelliTrace dla aplikacji na serwerach produkcyjnych lub w innych środowiskach bez konieczności instalowania programu Visual Studio na maszynie docelowej i bez zmiany środowiska systemu docelowego. Autonomiczny moduł zbierający IntelliTrace działa w aplikacjach sieci Web, SharePoint, WPF i Windows Forms. Po zakończeniu zbierania danych po prostu usuń moduł zbierający, aby go odinstalować.

 Obejrzyj IntelliTrace w działaniu: [zbieranie i analizowanie danych IntelliTrace w środowisku produkcyjnym w celu debugowania (wideo Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

> [!NOTE]
> Możesz również zbierać te same dane IntelliTrace dla aplikacji sieci Web i programu SharePoint działających na komputerach zdalnych przy użyciu **Microsoft Monitoring Agent** w trybie **śledzenia** .
>
> Zdarzenia związane z wydajnością można zbierać w danych IntelliTrace, uruchamiając agenta w trybie **monitora** . Tryb **monitora** ma mniej wpływu na wydajność niż tryb **śledzenia** lub autonomiczny **moduł zbierający IntelliTrace**. Microsoft Monitoring Agent zmienia środowisko systemu docelowego podczas instalacji. Zobacz [używanie Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).
> Autonomiczny moduł zbierający IntelliTrace nie obsługuje migawek procesów.

 **Wymagania**

- .NET Framework 3,5 lub nowszy

- Visual Studio Enterprise (ale nie wersje Professional lub Community) na komputerze deweloperskim lub innym komputerze, aby otworzyć pliki. iTrace

  > [!NOTE]
  > Pamiętaj, aby zapisać pliki symboli (. pdb). Aby debugować przy użyciu IntelliTrace i przechodzenia przez kod, musisz mieć pasujące pliki źródłowe i pliki symboli. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

  **Często zadawane pytania**

- [Jakie aplikacje współpracują z modułem zbierającym?](#WhatApps)

- [Jak rozpocząć?](#GetStarted)

- [Jak mogę uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing)

- [Gdzie można uzyskać dane IntelliTrace?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> Jakie aplikacje współpracują z modułem zbierającym?

- ASP.NET aplikacje sieci Web hostowane w Internet Information Services (IIS) w wersji 7,0, 7,5, 8,0, 12,0 i 16,0

- Aplikacje SharePoint 2010 i SharePoint 2013

- Windows Presentation Foundation (WPF) i aplikacje Windows Forms.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> Jak mogę rozpocząć?

1. [Instalowanie modułu zbierającego](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Skonfiguruj uprawnienia dla katalogu modułu zbierającego](#ConfigurePermissionsRunningCollector)

3. [Instalowanie poleceń cmdlet programu IntelliTrace PowerShell w celu zbierania danych dla aplikacji sieci Web lub aplikacji programu SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [Skonfiguruj uprawnienia dla katalogu plików. iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -lub-

     [Zbieranie danych z aplikacji zarządzanej](#BKMK_Collect_Data_from_Executables)

6. [Otwórz plik. iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Instalowanie modułu zbierającego

1. Na serwerze swojej aplikacji Utwórz katalog modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

2. Pobierz moduł zbierający z [Centrum pobierania Microsoft](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019), [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)lub z folderu instalacji Visual Studio 2013 Update 3. [IntelliTrace Collector for Visual Studio 2013 Update 4](https://www.microsoft.com/download/details.aspx?id=44909):

   - **Microsoft Download Center** lub **My.VisualStudio.com**:

     1. Obok pozycji **IntelliTraceCollector.exe** wybierz pozycję **Pobierz**.

     2. Zapisz IntelliTraceCollector.exe w katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

     3. Uruchom IntelliTraceCollector.exe. Spowoduje to wyodrębnienie pliku IntelliTraceCollection.cab.

        \- oraz

   - **Folder instalacyjny programu Visual Studio**:

     1. Skopiuj IntelliTraceCollection.cab z folderu, w którym zainstalowano moduł zbierający, na przykład:

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          lub w przypadku poprzednich wersji programu Visual Studio:

          **.. \Microsoft Visual Studio 12 \ Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Umieść IntelliTraceCollection.cab w katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

3. Rozwiń IntelliTraceCollection.cab:

   1. Na serwerze aplikacji otwórz okno wiersza polecenia jako administrator.

   2. Przejdź do katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

   3. Użyj polecenia **expand** , łącznie z kropką (**.**) na końcu, aby rozwinąć IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Kropka (**.**) zachowuje podfoldery, które zawierają zlokalizowane plany kolekcji.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> Skonfiguruj uprawnienia dla katalogu modułu zbierającego

1. Na serwerze aplikacji otwórz okno wiersza polecenia jako administrator.

2. Użyj polecenia **icacls** systemu Windows, aby nadać administratorowi serwera pełne uprawnienia do katalogu modułu zbierającego. Na przykład:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Aby zbierać dane dla aplikacji sieci Web lub aplikacji programu SharePoint:

    1. Nadaj osobie korzystającej z poleceń cmdlet programu IntelliTrace PowerShell pełne uprawnienia do katalogu modułu zbierającego.

         Na przykład:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Nadaj puli aplikacji aplikacji sieci Web lub aplikacji programu SharePoint uprawnienia do odczytu i wykonania do katalogu modułu zbierającego.

         Na przykład:

        - W przypadku aplikacji sieci Web w **puli aplikacji z** identyfikatorem usługi

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - W przypadku aplikacji SharePoint w puli aplikacji **programu SharePoint-80** :

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Instalowanie poleceń cmdlet programu IntelliTrace PowerShell w celu zbierania danych dla aplikacji sieci Web lub aplikacji programu SharePoint

1. Na serwerze swojej aplikacji upewnij się, że program PowerShell jest włączony. W większości wersji systemu Windows Server można dodać tę funkcję za pomocą narzędzia administracyjnego **Menedżer serwera** .

     ![Dodawanie programu PowerShell przy użyciu Menedżer serwera](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. Zainstaluj IntelliTrace polecenia cmdlet programu PowerShell.

    1. Otwórz okno polecenia programu PowerShell jako administrator.

        1. Wybierz **Start**, **Wszystkie programy**, **akcesoria**, **Windows PowerShell**.

        2. Wybierz jeden z następujących kroków:

            - W 64-bitowych systemach operacyjnych Otwórz menu skrótów dla **programu Windows PowerShell**. Wybierz **Uruchom jako administrator**.

            - W 32-bitowych systemach operacyjnych Otwórz menu skrótów dla **programu Windows PowerShell (x86)**. Wybierz **Uruchom jako administrator**.

    2. W oknie wiersza polecenia programu PowerShell Użyj polecenia **Import-Module** , aby zaimportować **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Na przykład:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Skonfiguruj uprawnienia dla katalogu plików. iTrace

1. Na serwerze swojej aplikacji Utwórz katalog plików. iTrace, na przykład: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Aby uniknąć spowolnienia działania aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo aktywny.
   >   - Pliki. iTrace i pliki modułu zbierającego można umieścić w tym samym miejscu. Jeśli jednak masz aplikację sieci Web lub aplikację programu SharePoint, upewnij się, że to miejsce znajduje się poza katalogiem, który obsługuje aplikację.
   >
   > [!IMPORTANT]
   > - Ogranicz katalog plików. iTrace tylko do tych tożsamości, które muszą współpracować z modułem zbierającym. Plik. iTrace może zawierać informacje poufne, takie jak dane od użytkowników, bazy danych, inne lokalizacje źródłowe i parametry połączenia, ponieważ IntelliTrace może rejestrować wszystkie dane, które są przekazywane do parametrów metody lub jako wartości zwracane.
   >   - Upewnij się, że osoby, które mogą otwierać pliki. iTrace, mają uprawnienia do wyświetlania poufnych danych. Podczas udostępniania plików iTrace należy zachować ostrożność. Jeśli inne osoby muszą mieć dostęp, skopiuj pliki do bezpiecznej lokalizacji udostępnionej.

2. W przypadku aplikacji sieci Web lub aplikacji programu SharePoint nadaj jej pulę aplikacji pełne uprawnienia do katalogu plików. iTrace. Można użyć polecenia **icacls** systemu Windows lub Eksploratora Windows (lub Eksploratora plików).

    Na przykład:

   - Aby skonfigurować uprawnienia za pomocą polecenia **icacls** systemu Windows:

     - W przypadku aplikacji sieci Web w **puli aplikacji z** identyfikatorem usługi

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - W przypadku aplikacji SharePoint w puli aplikacji **programu SharePoint-80** :

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -lub-

   - Aby skonfigurować uprawnienia za pomocą Eksploratora Windows (lub Eksploratora plików):

     1. Otwórz **Właściwości** dla katalogu plików. iTrace.

     2. Na karcie **zabezpieczenia** wybierz pozycję **Edytuj**, a następnie pozycję **Dodaj**.

     3. Upewnij się, że **wbudowane podmioty zabezpieczeń** są wyświetlane w polu **Wybierz ten typ obiektu** . Jeśli tak nie jest, wybierz **typy obiektów** , aby je dodać.

     4. Upewnij się, że komputer lokalny jest wyświetlany w polu **z tej lokalizacji** . Jeśli tak nie jest, wybierz **lokalizacje** , aby je zmienić.

     5. W polu **Wprowadź nazwy obiektów do wybrania** Dodaj pulę aplikacji aplikacji sieci Web lub aplikacji programu SharePoint.

     6. Wybierz **Sprawdź nazwy** , aby rozpoznać nazwę. Wybierz przycisk **OK**.

     7. Upewnij się, że Pula aplikacji ma **pełną kontrolę**.

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint

1. Aby rozpocząć zbieranie danych, Otwórz okno polecenia programu PowerShell jako administrator, a następnie uruchom następujące polecenie:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Po uruchomieniu tego polecenia, wpisz **Y** , aby potwierdzić, że chcesz rozpocząć zbieranie danych.

     Na przykład, aby zbierać dane z aplikacji SharePoint w puli aplikacji **programu SharePoint-80** :

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Nazwa|Opis|
    |-|-|
    |*ApplicationPool*|Nazwa puli aplikacji, w której działa aplikacja|
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik. XML, który konfiguruje ustawienia modułu zbierającego.<br /><br /> Możesz określić plan dostarczany z modułem zbierającym. Następujące plany działają w przypadku aplikacji sieci Web i aplikacji programu SharePoint:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Zbiera tylko zdarzenia IntelliTrace i zdarzenia programu SharePoint, w tym wyjątki, wywołania bazy danych i żądania serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Zbiera wywołania funkcji i wszystkie dane w collection_plan.ASP.NET.default.xml. Ten plan jest dobry dla szczegółowej analizy, ale może spowolnić działanie aplikacji więcej niż collection_plan.ASP.NET.default.xml.<br /><br /> Aby uniknąć spowolnienia działania aplikacji, Dostosuj te plany lub Utwórz własny plan. W celu zapewnienia bezpieczeństwa należy umieścić dowolne plany niestandardowe w tej samej bezpiecznej lokalizacji co pliki modułu zbierającego. Zobacz [Tworzenie i dostosowywanie planów zbierania IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) oraz [Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?](#Minimizing) **Uwaga:**  Domyślnie maksymalny rozmiar pliku. iTrace to 100 MB. Gdy plik. iTrace osiągnie ten limit, moduł zbierający usuwa najstarsze wpisy pliku, aby miejsce na nowsze wpisy. Aby zmienić ten limit, Edytuj atrybut planu kolekcji `MaximumLogFileSize` . <br /><br /> *Gdzie mogę znaleźć zlokalizowane wersje tych planów kolekcji?*<br /><br /> Zlokalizowane plany można znaleźć w podfolderach modułu zbierającego.|
    |*FullPathToITraceFileDirectory*|Pełna ścieżka do katalogu plików. iTrace. **Uwaga dotycząca zabezpieczeń:**  Podaj pełną ścieżkę, a nie ścieżkę względną.|

     Moduł zbierający dołącza do puli aplikacji i zaczyna zbierać dane.

     *Czy mogę otworzyć plik. iTrace w tej chwili?* Nie, plik jest zablokowany podczas zbierania danych.

2. Odtwórz problem.

3. Aby utworzyć punkt kontrolny pliku. iTrace, użyj następującej składni:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Aby sprawdzić stan kolekcji, użyj następującej składni:

     `Get-IntelliTraceCollectionStatus`

5. Aby zatrzymać zbieranie danych, należy użyć następującej składni:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Po uruchomieniu tego polecenia, wpisz **Y** , aby potwierdzić, że chcesz zatrzymać zbieranie danych. W przeciwnym razie moduł zbierający może kontynuować zbieranie danych, plik iTrace pozostanie zablokowany lub plik może nie zawierać żadnych użytecznych danych.

6. [Otwórz plik. iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> Zbieranie danych z aplikacji zarządzanej

1. Aby uruchomić aplikację i zebrać dane w tym samym czasie, użyj następującej składni:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Na przykład, aby zbierać dane z aplikacji o nazwie **MojaApl**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Nazwa|Opis|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Pełna ścieżka do pliku wykonywalnego modułu zbierającego, IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik. XML, który konfiguruje ustawienia modułu zbierającego.<br /><br /> Możesz określić plan dostarczany z modułem zbierającym. Następujące plany działają w przypadku zarządzanych aplikacji:<br /><br /> -collection_plan.ASP.NET.default.xml<br />     Zbiera tylko zdarzenia IntelliTrace, w tym wyjątki, wywołania bazy danych i żądania serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Zbiera wywołania funkcji i wszystkie dane w collection_plan.ASP.NET.default.xml. Ten plan jest dobry dla szczegółowej analizy, ale może spowolnić działanie aplikacji więcej niż collection_plan.ASP.NET.default.xml.<br /><br /> Aby uniknąć spowolnienia działania aplikacji, Dostosuj te plany lub Utwórz własny plan. W celu zapewnienia bezpieczeństwa należy umieścić dowolne plany niestandardowe w tej samej bezpiecznej lokalizacji co pliki modułu zbierającego. Zobacz [Tworzenie i dostosowywanie planów zbierania IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) oraz [Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?](#Minimizing) **Uwaga:**  Domyślnie maksymalny rozmiar pliku. iTrace to 100 MB. Gdy plik. iTrace osiągnie ten limit, moduł zbierający usuwa najstarsze wpisy pliku, aby miejsce na nowsze wpisy. Aby zmienić ten limit, Edytuj atrybut planu kolekcji `MaximumLogFileSize` . <br /><br /> *Gdzie mogę znaleźć zlokalizowane wersje tych planów kolekcji?*<br /><br /> Zlokalizowane plany można znaleźć w podfolderach modułu zbierającego.|
    |*FullPathToITraceFileDirectoryAndFileName*|Pełna ścieżka do katalogu plików. iTrace i nazwa pliku. iTrace z rozszerzeniem **. iTrace** . **Uwaga dotycząca zabezpieczeń:**  Podaj pełną ścieżkę, a nie ścieżkę względną.|
    |*PathToAppExecutableFileAndFileName*|Ścieżka i nazwa pliku aplikacji zarządzanej|

2. Zatrzymaj zbieranie danych przez wyjście z aplikacji.

3. [Otwórz plik. iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a> Otwórz plik. iTrace w Visual Studio Enterprise

> [!NOTE]
> Aby debugować przy użyciu IntelliTrace i przechodzenia przez kod, musisz mieć pasujące pliki źródłowe i pliki symboli. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

1. Przenieś plik. iTrace lub skopiuj go na komputer z Visual Studio Enterprise (ale nie wersji Professional lub Community).

2. Kliknij dwukrotnie plik. iTrace poza programem Visual Studio lub Otwórz plik w programie Visual Studio.

     Program Visual Studio wyświetla stronę **podsumowania IntelliTrace** . W większości sekcji można przejrzeć zdarzenia lub inne elementy, wybrać element i rozpocząć debugowanie za pomocą IntelliTrace w punkcie, w którym wystąpił zdarzenie. Zobacz [Używanie zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > Aby debugować przy użyciu IntelliTrace i przechodzenia przez kod, musisz mieć pasujące pliki źródłowe i pliki symboli na komputerze deweloperskim. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Jak mogę uzyskać najwięcej danych bez spowalniania mojej aplikacji?
 IntelliTrace może zbierać wiele danych, dzięki czemu wpływ na wydajność aplikacji zależy od danych, które IntelliTrace zbiera, i rodzaju kodu, który analizuje. Zobacz [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/).

 Oto kilka sposobów na uzyskanie większości danych bez spowalniania aplikacji:

- Uruchom moduł zbierający tylko wtedy, gdy sądzisz, że wystąpił problem, lub jeśli możesz odtworzyć problem.

   Rozpocznij zbieranie danych, Odtwórz problem, a następnie Zatrzymaj zbieranie. Otwórz plik. iTrace w Visual Studio Enterprise i Przeanalizuj dane. Zobacz [Otwórz plik. iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- W przypadku aplikacji sieci Web i aplikacji programu SharePoint moduł zbierający rejestruje dane dla każdej aplikacji, która współużytkuje określoną pulę aplikacji. Może to spowolnić każdą aplikację, która współużytkuje tę samą pulę aplikacji, mimo że można określić tylko moduły dla jednej aplikacji w planie kolekcji.

   Aby zapobiec spowolnieniu innych aplikacji przez moduł zbierający, należy hostować każdą aplikację we własnej puli aplikacji.

- Przejrzyj zdarzenia w planie kolekcji, dla którego IntelliTrace zbiera dane. Edytuj plan kolekcji, aby wyłączyć zdarzenia, które nie są odpowiednie lub nie są interesujące.

   Aby wyłączyć zdarzenie, ustaw `enabled` atrybut dla `<DiagnosticEventSpecification>` elementu na `false` :

   `<DiagnosticEventSpecification enabled="false">`

   Jeśli `enabled` atrybut nie istnieje, zdarzenie jest włączone.

   *Jak zwiększa to wydajność?*

  - Można skrócić czas uruchamiania, wyłączając zdarzenia, które nie są istotne dla aplikacji. Na przykład Wyłącz zdarzenia Windows Workflow dla aplikacji, które nie używają przepływu pracy systemu Windows.

  - Można poprawić wydajność uruchamiania i uruchamiania, wyłączając zdarzenia rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie wykazują problemów z ustawieniami rejestru.

- Przejrzyj moduły w planie kolekcji, dla którego IntelliTrace zbiera dane. Edytuj plan kolekcji w celu uwzględnienia tylko interesujących Cię modułów:

  1. Otwórz plan zbierania danych. Znajdź `<ModuleList>` element.

  2. W `<ModuleList>` , ustaw `isExclusionList` atrybut na `false` .

  3. Użyj `<Name>` elementu, aby określić każdy moduł z jedną z następujących: nazwą pliku, wartością ciągu do uwzględnienia dowolnego modułu, którego nazwa zawiera ten ciąg lub klucz publiczny.

     Na przykład, aby zbierać dane tylko z głównego modułu sieci Web aplikacji sieci Web firmy Fabrikam Fiber, Utwórz listę taką jak:

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

   *Jak zwiększa to wydajność?*

   Zmniejsza to ilość informacji o wywołaniu metody i innych danych instrumentacji, które IntelliTrace zbiera, gdy aplikacja zostanie uruchomiona i uruchomiona. Te dane umożliwiają:

  - Przechodzenie przez kod po zebraniu danych.

  - Badaj wartości przesyłane do i zwracane z wywołań funkcji.

    *Dlaczego zamiast tego nie wykluczać modułów?*

    Domyślnie plany kolekcji wykluczają moduły przez ustawienie `isExclusionList` atrybutu na `true` . Jednak wykluczenie modułów może nadal powodować zbieranie danych z modułów, które nie spełniają kryteriów listy i mogą nie być interesujące, takie jak moduły innych firm lub typu open-source.

- *Czy istnieją jakieś dane, które nie są zbierane przez IntelliTrace?*

   Tak, aby zmniejszyć wpływ na wydajność, IntelliTrace ogranicza zbieranie danych do wartości typów danych pierwotnych przekazana do i zwracanych z metod oraz do wartości typów danych pierwotnych w polach obiektów najwyższego poziomu przekazana do i zwróconych z metod.

   Załóżmy na przykład, `AlterEmployee` że masz sygnaturę metody akceptującą liczbę całkowitą `id` i `Employee` obiekt `oldemployee` :

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee`Typ ma następujące atrybuty: `Id` , `Name` , i `HomeAddress` . Między i typem istnieje relacja skojarzenia `Employee` `Address` .

   ![Relacja między pracownikiem a adresem](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Moduł zbierający rejestruje wartości `id` dla `Employee.Id` , `Employee.Name` i `Employee` obiekt zwrócony z `AlterEmployee` metody. Moduł zbierający nie rejestruje jednak informacji o `Address` obiekcie innym niż to, czy ma on wartość null, czy nie. Moduł zbierający nie rejestruje również danych o zmiennych lokalnych w `AlterEmployee` metodzie, chyba że inne metody używają tych zmiennych lokalnych jako parametrów, w których są one rejestrowane jako parametry metody.

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> Gdzie można uzyskać dane IntelliTrace?

Możesz uzyskać dane IntelliTrace z sesji debugowania IntelliTrace w Visual Studio Enterprise. Zobacz [Funkcje IntelliTrace](../debugger/intellitrace-features.md).

## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?
 [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blogi
 [Zdalne korzystanie z autonomicznego modułu zbierającego IntelliTrace](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [Tworzenie i dostosowywanie planów kolekcji IntelliTrace](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [DevOps firmy Microsoft](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Fora
 [Visual Studio Debugger](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Filmy wideo
 [Wideo Channel 9: zbieranie i analizowanie danych IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)

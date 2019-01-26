---
title: Przy użyciu autonomicznego modułu zbierającego IntelliTrace | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96a7fe0e46420a2469271219aa44ee76c9a49774
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986816"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>Przy użyciu autonomicznego modułu zbierającego IntelliTrace (C#, Visual Basic)

**Autonomiczny moduł zbierający IntelliTrace** umożliwia zbieranie danych diagnostycznych IntelliTrace dla aplikacji na serwerach produkcyjnych lub innych środowiskach bez instalowania programu Visual Studio na maszynie docelowej i bez wprowadzania zmian docelowe środowiska systemu. Autonomiczny moduł zbierający IntelliTrace działa w sieci web programu SharePoint, aplikacje WPF i Windows Forms. Po zakończeniu zbierania danych, po prostu usuń moduł zbierający aby go odinstalować.

 Obejrzyj działanie IntelliTrace: [Zbieranie i analizowanie danych IntelliTrace w produkcji do debugowania (wideo Channel 9)](http://go.microsoft.com/fwlink/?LinkID=251851)

> [!NOTE]
>  Może również zbierać te same dane funkcji IntelliTrace dla sieci web i aplikacje programu SharePoint uruchomionych na komputerach zdalnych przy użyciu **Microsoft Monitoring Agent** w **śledzenia** trybu.
>
>  Zdarzenia związane z wydajnością w danych funkcji IntelliTrace można zbierać, uruchamiając agenta w **Monitor** trybu. **Monitor** tryb ma mniejszy wpływ na wydajność niż **śledzenia** tryb lub **autonomiczny moduł zbierający IntelliTrace**. Program Microsoft Monitoring Agent zmienić środowiska systemu docelowego, po jej zainstalowaniu. Zobacz [przy użyciu programu Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).
>  Autonomiczny moduł zbierający IntelliTrace nie obsługuje przetwarzania migawek.

 **Wymagania**

- .NET framework 3.5, 4 lub 4.5

- Visual Studio Enterprise (ale nie Professional lub Community Edition) na komputerze deweloperskim lub innym komputerze, aby otworzyć pliki .iTrace

  > [!NOTE]
  >  Upewnij się, że zapisano symbole plików (.pdb). Aby debugować za pomocą IntelliTrace i przejść przez kod, musisz mieć pasujące pliki źródłowe i pliki symboli. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

  **FAQ**

- [Jakie aplikacje działają z modułem zbierającym?](#WhatApps)

- [Jak rozpocząć pracę?](#GetStarted)

- [Jak uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing)

- [Gdzie indziej można uzyskać dane IntelliTrace?](#WhereElse)

##  <a name="WhatApps"></a> Jakie aplikacje działają z modułem zbierającym?

-   Aplikacje ASP.NET sieci Web hostowanych na Internet Information Services (IIS) w wersji 7.0, 7.5 i 8.0

-   Aplikacje programu SharePoint 2010 i SharePoint 2013

-   Windows Presentation Foundation (WPF) i Windows Forms aplikacji.

##  <a name="GetStarted"></a> Jak rozpocząć pracę?

1.  [Zainstaluj moduł zbierający](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2.  [Skonfiguruj uprawnienia dla katalogu kolektora](#ConfigurePermissionsRunningCollector)

3.  [Zainstaluj polecenia cmdlet programu PowerShell funkcji IntelliTrace, zbieranie danych dla aplikacji sieci Web lub aplikacji programu SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4.  [Skonfiguruj uprawnienia dla katalogu plików .iTrace](#BKMK_Create_and_Configure_a_Log_File_Directory)

5.  [Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)

     —lub—

     [Zbieranie danych z zarządzanej aplikacji](#BKMK_Collect_Data_from_Executables)

6.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Zainstaluj moduł zbierający

1. Na serwerze swojej aplikacji Utwórz katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

2. Pobierz moduł zbierający, z Microsoft Download Center lub z folderu instalacyjnego programu Visual Studio 2013 Update 3. [IntelliTrace Collector for Visual Studio 2013 Update 4](https://www.microsoft.com/en-us/download/details.aspx?id=44909)::

   - **Centrum pobierania Microsoft**:

     1. Obok pozycji **IntelliTraceCollector.exe**, wybierz **Pobierz**.

     2. Zapisz IntelliTraceCollector.exe w katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

     3. Run IntelliTraceCollector.exe. Wyodrębnia plik IntelliTraceCollection.cab.

        \- lub —

   - **Folder instalacyjny Visual Studio**:

     1.  Skopiuj IntelliTraceCollection.cab z następującego folderu:

          **..\Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2.  Umieścić IntelliTraceCollection.cab w katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

3. Rozwiń IntelliTraceCollection.cab:

   1.  Na serwerze swojej aplikacji Otwórz okno wiersza polecenia jako administrator.

   2.  Przejdź do katalogu modułu zbierającego, na przykład: **C:\IntelliTraceCollector**

   3.  Użyj **rozwiń** polecenia, w tym okresie (**.**) na końcu, aby rozwinąć IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       >  Okres (**.**) zachowuje podfoldery, które zawierają zlokalizowane plany kolekcji.

##  <a name="ConfigurePermissionsRunningCollector"></a> Skonfiguruj uprawnienia dla katalogu kolektora

1.  Na serwerze swojej aplikacji Otwórz okno wiersza polecenia jako administrator.

2.  Użyj Windows **icacls** polecenie, aby nadać serwerowi pełne uprawnienia administratora do katalogu modułu zbierającego. Na przykład:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID >* `":F`

3.  Zbieranie danych dla aplikacji sieci Web lub aplikacji programu SharePoint:

    1.  Udziel osobom, które będą uruchamiane polecenia cmdlet programu IntelliTrace PowerShell pełnych uprawnień do katalogu modułu zbierającego.

         Na przykład:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2.  Udzielić tej puli aplikacji dla aplikacji sieci Web lub aplikacji SharePoint uprawnienia odczytu i wykonania do katalogu modułu zbierającego.

         Na przykład:

        -   Dla aplikacji sieci Web **DefaultAppPool** puli aplikacji:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        -   Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

##  <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Zainstaluj polecenia cmdlet programu PowerShell funkcji IntelliTrace, zbieranie danych dla aplikacji sieci Web lub aplikacji programu SharePoint

1.  Na serwerze swojej aplikacji upewnij się, że program PowerShell jest włączona. W większości wersji systemu Windows Server, można dodać tę funkcję w **Menedżera serwera** narzędzie administracyjne.

     ![Dodawanie programu PowerShell przy użyciu Menedżera serwera](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2.  Zainstaluj polecenia cmdlet programu PowerShell funkcji IntelliTrace.

    1.  Otwórz okno poleceń programu PowerShell jako administrator.

        1.  Wybierz **Start**, **wszystkie programy**, **Akcesoria**, **programu Windows PowerShell**.

        2.  Wybierz jedną z następujących czynności:

            -   W 64-bitowych systemach operacyjnych, otwórz menu skrótów dla **programu Windows PowerShell**. Wybierz **Uruchom jako administrator**.

            -   W 32-bitowych systemach operacyjnych, otwórz menu skrótów dla **programu Windows PowerShell (x86)**. Wybierz **Uruchom jako administrator**.

    2.  W oknie wiersza polecenia programu PowerShell użyj **Import-Module** polecenie, aby zaimportować **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.

         Na przykład:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

##  <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Skonfiguruj uprawnienia dla katalogu plików .iTrace

1. Na serwerze swojej aplikacji Utwórz katalog plików .iTrace, na przykład: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Aby nie spowalniać pracy swojej aplikacji, wybierz lokalizację na lokalnym dysku o dużej szybkości, który nie jest bardzo obciążony.
   >   -   Pliki .iTrace i pliki modułów zbierających można umieścić w tym samym miejscu. Jednak jeśli masz aplikację sieci Web lub aplikacji programu SharePoint, upewnij się, że to miejsce jest poza katalogiem, który obsługuje aplikacja.
   > 
   > [!IMPORTANT]
   > - Ogranicz katalogu plików .iTrace tylko do tych tożsamości, które należy skontaktować się z modułem zbierającym. Plik .iTrace może zawierać informacje poufne, takie jak dane od użytkowników, bazy danych, inne lokalizacje źródłowe i parametry połączenia, ponieważ IntelliTrace może rejestrować wszelkie dane, które przekazuje parametrami metody lub wartościami zwrotnymi.
   >   -   Upewnij się, że tych, którzy mogą otwierać pliki .iTrace mają uprawnienia do danych poufnych. Należy zachować ostrożność podczas udostępniania plików .iTrace. Jeśli inne osoby muszą mieć dostęp, skopiuj pliki do bezpiecznej lokalizacji udostępnionej.

2. Dla aplikacji sieci Web lub aplikacji programu SharePoint należy nadać jej puli aplikacji pełne uprawnienia do katalogu plików .iTrace. Możesz użyć Windows **icacls** polecenia lub za pomocą Eksploratora Windows (lub Eksploratora plików).

    Na przykład:

   - Aby skonfigurować uprawnienia za pomocą Windows **icacls** polecenia:

     - Dla aplikacji sieci Web **DefaultAppPool** puli aplikacji:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - Dla aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       —lub—

   - Aby skonfigurować uprawnienia za pomocą Eksploratora Windows (lub Eksploratora plików):

     1.  Otwórz **właściwości** dla katalogu plików .iTrace.

     2.  Na **zabezpieczeń** kartę, wybrać **Edytuj**, **Dodaj**.

     3.  Upewnij się, że **wbudowane zabezpieczenia główne** pojawia się w **wybierz ten typ obiektu** pole. Jeśli nie ma tam, wybierz **wybierane** ją dodać.

     4.  Upewnij się, że komputer lokalny pojawi się w **z tej lokalizacji** pole. Jeśli nie ma tam, wybierz **lokalizacje** go zmienić.

     5.  W **wprowadź nazwy obiektów do wybrania** Dodaj pulę aplikacji dla aplikacji sieci Web lub aplikacji programu SharePoint.

     6.  Wybierz **Sprawdź nazwy** do rozpoznania nazwy. Wybierz **OK**.

     7.  Upewnij się, że pula aplikacji ma **Pełna kontrola**.

##  <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Zbieranie danych z aplikacji sieci Web lub aplikacji programu SharePoint

1.  Aby rozpocząć zbieranie danych, Otwórz okno poleceń programu PowerShell jako administrator, a następnie uruchom następujące polecenie:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    >  Po uruchomieniu tego polecenia, wpisz **Y** aby upewnić się, że chcesz rozpocząć zbieranie danych.

     Na przykład, aby zbierać dane z aplikacji programu SharePoint w **SharePoint — 80** puli aplikacji:

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |||
    |-|-|
    |*Puli aplikacji*|Nazwa puli aplikacji, w której działa Twoja aplikacja|
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik .xml, który konfiguruje ustawienia dla modułu zbierającego.<br /><br /> Można określić plan, który jest dostarczany z modułem zbierającym. Następujące plany działają w przypadku aplikacji sieci Web i aplikacji programu SharePoint:<br /><br /> -ASP.NET.default.XML<br />     Zbiera tylko zdarzenia IntelliTrace i zdarzenia programu SharePoint, łącznie z wyjątkami, wywołaniami bazy danych i żądaniami serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Wywołania funkcji gromadzenia i wszystkie dane w ASP.NET.default.XML. Ten plan jest dobry szczegółową analizę, ale może spowolnić działanie Twojej aplikacji bardziej niż collection_plan.ASP.NET.default.xml.<br /><br /> Aby nie spowalniać pracy swojej aplikacji, Dostosuj te plany lub Utwórz własny plan. Względów bezpieczeństwa należy umieścić plany kolekcji niestandardowej w tym samym bezpiecznym miejscu, co pliki modułów zbierających. Zobacz [tworzenie i dostosowywanie planów zbierania IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) i [jak uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing) **Uwaga:**  Domyślnie maksymalny rozmiar pliku .iTrace wynosi 100 MB. W przypadku pliku.itrace osiągnie ten limit, moduł zbierający usuwa najwcześniej wpisy pliku, aby miejsce na nowsze wpisy. Aby zmienić ten limit, Edytuj plan kolekcji `MaximumLogFileSize` atrybutu. <br /><br /> *Gdzie można znaleźć zlokalizowane wersje tych planów kolekcji?*<br /><br /> Zlokalizowane plany można znaleźć w podfolderach modułu zbierającego.|
    |*FullPathToITraceFileDirectory*|Pełna ścieżka do katalogu plików .iTrace. **Uwaga dotycząca zabezpieczeń:**  Podaj pełną ścieżkę, nie ścieżkę względną.|

     Moduł zbierający dołącza do puli aplikacji i rozpoczyna zbieranie danych.

     *W tym momencie można otworzyć plik .iTrace?* Nie, plik jest zablokowany podczas zbierania danych.

2.  Odtwórz problem.

3.  Aby utworzyć punkt kontrolny plik .iTrace, użyj następującej składni:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4.  Aby sprawdzić stan procesu kolekcji, użyj następującej składni:

     `Get-IntelliTraceCollectionStatus`

5.  Aby zatrzymać zbieranie danych, użyj następującej składni:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    >  Po uruchomieniu tego polecenia, wpisz **Y** aby upewnić się, że chcesz zatrzymać zbieranie danych. W przeciwnym razie moduł zbierający może nadal zbierać dane, w pliku iTrace plik pozostanie zablokowany lub plik nie może zawierać żadnych użytecznych danych.

6.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_Collect_Data_from_Executables"></a> Zbieranie danych z zarządzanej aplikacji

1.  Aby uruchomić aplikację i zbierać dane, w tym samym czasie, użyj następującej składni:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Na przykład, aby zbierać dane z aplikacji o nazwie **MyApp**:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |||
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Pełna ścieżka do pliku wykonywalnego modułu zbierającego IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Ścieżka do planu kolekcji, plik .xml, który konfiguruje ustawienia dla modułu zbierającego.<br /><br /> Można określić plan, który jest dostarczany z modułem zbierającym. Następujące plany działają w przypadku zarządzanych aplikacji:<br /><br /> -ASP.NET.default.XML<br />     Zbiera tylko zdarzenia IntelliTrace, łącznie z wyjątkami, wywołaniami bazy danych i żądaniami serwera sieci Web.<br />-collection_plan.ASP.NET.trace.xml<br />     Wywołania funkcji gromadzenia i wszystkie dane w ASP.NET.default.XML. Ten plan jest dobry szczegółową analizę, ale może spowolnić działanie Twojej aplikacji bardziej niż collection_plan.ASP.NET.default.xml.<br /><br /> Aby nie spowalniać pracy swojej aplikacji, Dostosuj te plany lub Utwórz własny plan. Względów bezpieczeństwa należy umieścić plany kolekcji niestandardowej w tym samym bezpiecznym miejscu, co pliki modułów zbierających. Zobacz [tworzenie i dostosowywanie planów zbierania IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) i [jak uzyskać większość danych bez spowalniania mojej aplikacji?](#Minimizing) **Uwaga:**  Domyślnie maksymalny rozmiar pliku .iTrace wynosi 100 MB. W przypadku pliku.itrace osiągnie ten limit, moduł zbierający usuwa najwcześniej wpisy pliku, aby miejsce na nowsze wpisy. Aby zmienić ten limit, Edytuj plan kolekcji `MaximumLogFileSize` atrybutu. <br /><br /> *Gdzie można znaleźć zlokalizowane wersje tych planów kolekcji?*<br /><br /> Zlokalizowane plany można znaleźć w podfolderach modułu zbierającego.|
    |*FullPathToITraceFileDirectoryAndFileName*|Pełna ścieżka do katalogu plików .iTrace i nazwa pliku .iTrace z **.itrace** rozszerzenia. **Uwaga dotycząca zabezpieczeń:**  Podaj pełną ścieżkę, nie ścieżkę względną.|
    |*PathToAppExecutableFileAndFileName*|Ścieżka i nazwa pliku Twojej aplikacji zarządzanej|

2.  Zatrzymaj zbieranie danych podczas zamknięcie aplikacji.

3.  [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

##  <a name="BKMK_View_IntelliTrace_Log_Files"></a> Otwórz plik .iTrace w Visual Studio Enterprise

> [!NOTE]
>  Aby debugować za pomocą IntelliTrace i przejść przez kod, musisz mieć pasujące pliki źródłowe i pliki symboli. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

1.  Przenieś plik .iTrace lub skopiuj go do komputera za pomocą programu Visual Studio Enterprise (ale nie Professional lub Community).

2.  Kliknij dwukrotnie plik .iTrace, poza Visual Studio lub Otwórz plik z poziomu programu Visual Studio.

     Visual Studio Wyświetla **krótki opis IntelliTrace** strony. W większości sekcji, można przejrzeć zdarzenia lub inne elementy, wybierz element i Rozpocznij debugowanie z IntelliTrace w punkcie gdzie i kiedy miało miejsce zdarzenie. Zobacz [używanie zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    >  Aby debugować za pomocą IntelliTrace i przejść przez kod, musisz mieć pasujące pliki źródłowe i pliki na komputerze deweloperskim z symbolami. Zobacz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

##  <a name="Minimizing"></a> Jak uzyskać większość danych bez spowalniania mojej aplikacji?
 IntelliTrace może zbierać dużą ilość danych, więc wpływ na wydajność aplikacji zależy od IntelliTrace zbiera dane i rodzaju kodu, który analizuje. Zobacz [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233).

 Oto kilka sposobów na zdobycie większości danych bez spowalniania aplikacji:

- Uruchom moduł zbierający, tylko wtedy, gdy uważasz, że występuje problem lub można odtworzyć problem.

   Rozpocznij zbieranie danych, odtworzenie problemu, a następnie Zatrzymaj kolekcję. Otwórz plik .iTrace w Visual Studio Enterprise i zbadaj dane. Zobacz [Otwórz plik .iTrace w Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).

- Dla aplikacji sieci Web i aplikacji SharePoint moduł gromadzący zapisuje dane dla każdej aplikacji, która udostępnia określona pula aplikacji. Może to spowolnić każdej aplikacji, która udostępnia tej samej puli aplikacji, mimo że można określić tylko moduły dla pojedynczej aplikacji planu kolekcji.

   Aby zapobiec sytuacji, w której moduł zbierający spowalniania innych aplikacji, Hostuj każdą aplikację we własnej puli aplikacji.

- Przejrzyj zdarzenia w planie kolekcji, dla którego IntelliTrace zbiera dane. Edytuj plan kolekcji, aby wyłączyć zdarzenia, które nie są odpowiednie ani interesujące.

   Aby wyłączyć zdarzenie, ustaw `enabled` atrybutu dla `<DiagnosticEventSpecification>` elementu `false`:

   `<DiagnosticEventSpecification enabled="false">`

   Jeśli `enabled` atrybut nie istnieje, zdarzenie jest włączone.

   *Jak zwiększa to wydajność?*

  -   Aby ograniczyć czas uruchamiania, wyłączając zdarzenia, które nie są odpowiednie dla aplikacji. Na przykład wyłącz zdarzenia Windows Workflow dla aplikacji, które nie używają Windows Workflow.

  -   Może poprawić wydajność uruchamiania i wykonywania, wyłączając zdarzenia rejestru dla aplikacji, które uzyskują dostęp do rejestru, ale nie wyświetlają problemów z ustawieniami rejestru.

- Przeanalizuj moduły w planie kolekcji, dla którego IntelliTrace zbiera dane. Edytuj plan kolekcji, aby uwzględnić tylko interesujące Cię moduły:

  1. Otwórz plan kolekcji. Znajdź `<ModuleList>` elementu.

  2. W `<ModuleList>`ustaw `isExclusionList` atrybutu `false`.

  3. Użyj `<Name>` elementu, aby określić każdy moduł przy użyciu jednego z następujących czynności: Nazwa pliku wartość ciągu, aby uwzględnić dowolny moduł, którego nazwa zawiera dany ciąg lub klucz publiczny.

     Na przykład aby zebrać dane po prostu głównego modułu sieci Web aplikacji sieci Web Fabrikam Fiber, Utwórz listę podobny do poniższego:

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

   *Jak zwiększa to wydajność?*

   Zmniejsza to ilość informacji wywołania metody oraz innych danych instrumentacji, gromadzi IntelliTrace, gdy aplikacja jest uruchomiona i. Dane te umożliwiają:

  - Przejść przez kod po zebraniu danych.

  - Sprawdzić wartości przekazane do i zwrócony z wywołania funkcji.

    *Dlaczego nie wykluczyć modułów?*

    Plany kolekcji domyślnie wykluczają moduły przez ustawienie `isExclusionList` atrybutu `true`. Jednak wyłączenie modułów może nadal prowadzić do zbierania danych z modułów, które nie spełniają kryteriów listy i może nie być interesujące, takie jak moduły strony trzeciej lub typu open source.

- *Czy są jakieś dane, które IntelliTrace nie zbiera?*

   Tak, aby zmniejszyć wpływ na wydajność, IntelliTrace ogranicza zbieranie danych do wartości pierwotnych typów danych przekazany do i zwrócony z metody i wartości typów danych pierwotnych w polach obiektów najwyższego poziomu, przekazywane do metod oraz zwracanych przez.

   Załóżmy, że masz `AlterEmployee` podpis metody, która akceptuje liczbę całkowitą `id` i `Employee` obiektu `oldemployee`:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee` Typ ma następujące atrybuty: `Id`, `Name`, i `HomeAddress`. Istnieje relacja skojarzenia między `Employee` i `Address` typu.

   ![Relacja między pracowników i adres](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Moduł zbierający zapisuje wartości `id`, `Employee.Id`, `Employee.Name` i `Employee` obiekt zwracany z `AlterEmployee` metody. Jednak moduł zbierający nie zapisuje informacje o `Address` innych obiektów niż posiadającym wartość zerową lub nie. Moduł zbierający nie zapisuje również dane dotyczące zmiennych lokalnych w `AlterEmployee` metody, chyba że inne metody używają tych zmiennych lokalnych jako parametrów w tym momencie są zapisywane jako parametry metody.

##  <a name="WhereElse"></a> Gdzie indziej można uzyskać dane IntelliTrace?

-   W programie Visual Studio Enterprise sesję debugowania funkcji IntelliTrace, zobacz temat [funkcji IntelliTrace](../debugger/intellitrace-features.md).

-   W sesji testowej w programie Microsoft Test Manager, zobacz [jak: Zbieranie danych IntelliTrace aby pomóc w debugowaniu trudnych problemów](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?
 [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Blogi
 [Za pomocą IntelliTrace Standalone Collector zdalnie](http://go.microsoft.com/fwlink/?LinkId=262277)

 [Tworzenie i dostosowywanie planów kolekcji IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871)

 [Optymalizacja kolekcji IntelliTrace na serwerach produkcyjnych](http://go.microsoft.com/fwlink/?LinkId=255233)

 [Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)

### <a name="forums"></a>Fora
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)

### <a name="videos"></a>Wideo
 [Wideo Channel 9: Zbieranie i analizowanie danych IntelliTrace](http://go.microsoft.com/fwlink/?LinkID=251851)

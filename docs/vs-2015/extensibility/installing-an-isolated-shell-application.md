---
title: Instalowanie aplikacji Isolated Shell | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 55c4ebc96d93d9b068c29d24727d40975518b1ef
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062831"
---
# <a name="installing-an-isolated-shell-application"></a>Instalowanie aplikacji Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zainstalować aplikację powłoki należy wykonać następujące czynności.  
  
- Przygotuj swoje rozwiązanie.  
  
- Tworzenie pakietu Instalatora Windows (MSI) dla aplikacji.  
  
- Utwórz program inicjujący Instalatora.  
  
  Cały kod przykładowy w tym dokumencie pochodzą z [Przykładowe wdrożenie powłoki](http://go.microsoft.com/fwlink/?LinkId=262245), który można pobrać z galerii kodów w witrynie MSDN. Przykład przedstawiono wyniki wykonania każdy z tych kroków.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać procedury, które w tym temacie opisano, następujące narzędzia musi zainstalowany na tym komputerze.  
  
- Visual Studio SDK  
  
- [Zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=82720) wersji 3.6  
  
  Przykład wymaga także Microsoft Visualization i Modeling SDK, które wymagają powłoki nie wszystkie.  
  
## <a name="preparing-your-solution"></a>Trwa przygotowywanie rozwiązania  
 Domyślnie szablony powłoki kompilacja — przejście do pakietów VSIX, ale to zachowanie jest przeznaczony głównie do celów debugowania. Podczas wdrażania aplikacji powłoki, aby zezwolić na dostęp do rejestru i ponownego uruchomienia podczas instalacji należy użyć pakiety MSI dla. Aby przygotować aplikację do wdrożenia MSI, wykonaj następujące czynności.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Aby przygotować aplikację powłoki dla wdrożenia MSI  
  
1. Edytuj każdego pliku .vsixmanifest w rozwiązaniu.  
  
     W `Identifier` elementu Dodawanie `InstalledByMSI` elementu i `SystemComponent` elementu, a następnie ustaw ich wartości `true`.  
  
     Te elementy uniemożliwić Instalator VSIX do zainstalowania składników i użytkownika z je odinstalować za pomocą **rozszerzenia i aktualizacje** okno dialogowe.  
  
2. Dla każdego projektu, który zawiera VSIX manifest należy edytować zadania kompilacji, aby wyprowadzić zawartość do lokalizacji, z której zostanie zainstalowany z pliku MSI. Dołączenie manifestu VSIX w danych wyjściowych kompilacji, ale nie tworzy plik .vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Tworzenie pliku MSI dla powłoki  
 Do utworzenia pakietu MSI, firma Microsoft zaleca użycie [zestaw narzędzi XML Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=82720) ponieważ daje większą elastyczność niż standardowy projekt Instalatora.  
  
 W pliku Product.wxs Ustaw bloki wykrywania i układu elementów powłoki.  
  
 Następnie należy utworzyć wpisy rejestru, zarówno w pliku reg dla rozwiązania i ApplicationRegistry.wxs.  
  
### <a name="detection-blocks"></a>Bloki wykrywania  
 Blok wykrywania składa się z `Property` element, który określa warunek wstępny do wykrywania i `Condition` element, który określa wiadomości do zwrócenia, jeśli wstępnie wymaganego składnika nie jest obecny na komputerze. Na przykład aplikacji powłoki wymaga programu Microsoft Visual Studio Shell do dystrybucji i blok wykrywanie będzie przypominać następujące znaczniki.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Układ powłoki składników  
 Należy dodać elementy do identyfikowania strukturę katalogu docelowego i składniki do zainstalowania.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Aby ustawić układ powłoki składników  
  
1. Tworzenie hierarchii `Directory` elementu do reprezentowania wszystkich katalogów na tworzenie w systemie plików na komputerze docelowym, jak w poniższym przykładzie pokazano.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Te katalogi są określane przez `Id` gdy są określone pliki, które muszą zostać zainstalowane.  
  
2. Zidentyfikuj składniki, które wymagają powłoka i aplikacji powłoki, co ilustruje poniższy przykład.  
  
    > [!NOTE]
    >  Niektóre elementy mogą odwoływać się do definicji w innych plikach .wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. `ComponentRef` Element odwołuje się do innego pliku .wxs identyfikujący pliki, które wymaga bieżącego składnika. Na przykład GeneralProfile ma następującą definicję w HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` Element określa, gdzie te pliki na komputerze użytkownika. `Directory` Element określa, że zostanie ona zainstalowana w podkatalogu, a każdy `File` element reprezentuje pliku utworzonego lub istnieje jako część rozwiązania i określa, gdzie ten plik można znaleźć po utworzeniu pliku MSI.  
  
    2. `ComponentGroupRef` Element odwołuje się do grupy innych składników (lub składniki i grup składników). Na przykład `ComponentGroupRef` w grupie ApplicationGroup jest zdefiniowana w następujący sposób w Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Dostępne są następujące zależności wymagane dla aplikacji, Shell (Isolated): DebuggerProxy, MasterPkgDef, zasoby (szczególnie plik .winprf), aplikacji i PkgDefs.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Szablon projektu Shell (Isolated) zawiera *ProjectName*plik reg dla kluczy rejestru w celu scalenia w instalacji. Te wpisy rejestru musi być częścią pliku MSI dla instalacji i czyszczenia celów. Należy także utworzyć pasującego bloki rejestru w ApplicationRegistry.wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Aby zintegrować wpisy rejestru do pliku MSI  
  
1. W **dostosowania powłoki** folder, otwórz *ProjectName*. reg.  
  
2. Zastąp wszystkie wystąpienia zmiennej $RootFolder$ token ze ścieżką do katalogu instalacyjnego programu docelowego.  
  
3. Dodaj inne wpisy rejestru, których wymaga aplikacja.  
  
4. Otwórz ApplicationRegistry.wxs.  
  
5. Dla każdego wpisu rejestru w *ProjectName*.reg, Dodaj odpowiedni blok rejestru, jak w poniższych przykładach pokazano.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @="PhotoStudio DTE Object"|\<RegistryKey Id='DteClsidRegKey' Root='HKCR' Key='$(var.DteClsidRegKey)' Action='createAndRemoveOnUninstall'><br /><br /> \<Typ RegistryValue = "string" Name = "@" wartość = "$(var.) Obiekt ShortProductName) DTE "/ ><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<Typ RegistryValue = "string" Name = "@" wartość = "[INSTALLDIR] $(var.) ShortProductName) .exe "/ ><br /><br /> \</RegistryKey>|  
  
     W tym przykładzie Var.DteClsidRegKey jest rozpoznawany jako klucz rejestru w górnym wierszu. Var.ShortProductName jest rozpoznawana jako `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Tworzenie programu inicjującego Instalatora  
 Twoje ukończone MSI zainstaluje tylko wtedy, gdy wszystkie wstępnie wymagane składniki są najpierw instalowane. Aby ułatwić środowisko użytkownika końcowego, Utwórz program instalacyjny, który zbiera i instaluje wszystkie wymagania wstępne, przed instalacją aplikacji. Aby zapewnić pomyślną instalację, wykonaj następujące akcje:  
  
- Wymuszaj instalację przez administratora.  
  
- Wykryj, czy jest zainstalowany program Visual Studio Shell (Isolated).  
  
- Jeden lub oba instalatory powłoki są uruchamiane w kolejności.  
  
- Obsługuje żądania ponownego uruchomienia.  
  
- Uruchom usługi MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Wymuszanie instalacji przez administratora  
 Ta procedura jest wymagany do włączenia programu instalacyjnego do uzyskania dostępu wymagane katalogi, takich jak \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Aby wymusić instalację przez administratora  
  
1. Otwórz menu skrótów dla projektu Instalatora, a następnie wybierz **właściwości**.  
  
2. W obszarze **plik konsolidatora/właściwości/Manifest konfiguracji**ustaw **poziom wykonywania UAC** do **requireAdministrator**.  
  
     Ta właściwość umieszcza atrybut, który wymaga program można uruchomić jako Administrator w pliku manifestu osadzonego.  
  
### <a name="detecting-shell-installations"></a>Wykrywanie instalacji powłoki  
 Aby ustalić, czy Visual Studio Shell (izolowany) musi być zainstalowany, należy najpierw określić, czy jest już zainstalowany, sprawdzając wartość rejestru HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
>  Te wartości również są odczytywane przez blok wykrywania powłoki w Product.wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Określa lokalizację, w którym został zainstalowany program Visual Studio Shell i możesz sprawdzić, czy dla plików istnieje.  
  
 Na przykład wykrywanie instalacji powłoki zobacz `GetProductDirFromReg` funkcja Utilities.cpp w przykładowym wdrożeniu powłoki.  
  
 Jeśli jeden lub oba z programu Visual Studio powłoki, który wymaga pakietu nie jest zainstalowany na komputerze, należy je dodać do listy składników do zainstalowania. Aby uzyskać przykład, zobacz `ComponentsPage::OnInitDialog` funkcja ComponentsPage.cpp w przykładowym wdrożeniu powłoki.  
  
### <a name="running-the-shell-installers"></a>Uruchamianie powłoki pliki instalacyjne  
 Aby uruchomić instalatory powłoki, należy wywołać pakiety redystrybucyjne programu Visual Studio Shell przy użyciu poprawne argumenty wiersza polecenia. Jako minimum, należy użyć argumenty wiersza polecenia **/q/norestart /** , zwracając uwagę na kod powrotny ustalić, co należy zrobić dalej. W poniższym przykładzie uruchamiane Shell (Isolated) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Uruchamianie powłoki instalatory pakiet języka  
 Jeśli okaże się zamiast tego, czy powłoki lub powłoki zostały zainstalowane, i po prostu potrzebujesz pakietu językowego, można zainstalować pakiety językowe, jak w poniższym przykładzie pokazano.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Odszyfrowanie zwracanych wartości  
 W niektórych systemach operacyjnych instalacja programu Visual Studio Shell (Isolated) będzie wymagać ponownego uruchomienia. Ten problem można ustalić przez kod powrotny wywołania `ExecCmd`.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalacja została zakończona. Można teraz zainstalować aplikację.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalacja została zakończona. Aplikację można zainstalować po ponownym uruchomieniu komputera.|  
|3015|Instalacja jest w toku. W celu kontynuowania instalacji jest wymagane ponowne uruchomienie komputera.|  
  
### <a name="handling-restarts"></a>Obsługa ponownego uruchomienia  
 Po uruchomieniu Instalatora Shell przy użyciu **/norestart /** , możesz określić argument w takich sytuacjach przydałaby jego ponownego uruchomienia komputera lub poproś o ponowne uruchomienie komputera. Jednak może być wymagane ponowne uruchomienie i należy upewnić się, że swój Instalatora, ma kontynuować działanie po ponownym uruchomieniu komputera.  
  
 Aby prawidłowo obsłużyć ponowne uruchomienie, upewnij się, że tylko jeden program instalacyjny jest ustawiony, aby wznowić poprawnie obsługiwane wznowienie procesu.  
  
 ERROR_SUCCESS_REBOOT_REQUIRED lub 3015 zostaną zwrócone, Twój kod należy ponownie uruchomić komputer przed kontynuacją instalacji.  
  
 Aby obsłużyć ponowne uruchomienie, wykonaj następujące akcje:  
  
- Ustaw rejestru, aby wznowić instalację, podczas uruchamiania Windows.  
  
- Program inicjujący double ponownego uruchomienia komputera.  
  
- Usuń klucz ResumeData Instalatora powłoki.  
  
- Uruchom ponownie Windows.  
  
- Resetowanie początku ścieżki pliku MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Ustawienie rejestru, aby wznowić instalację, podczas uruchamiania Windows  
 Klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ wykonuje podczas uruchamiania systemu z uprawnieniami administracyjnymi i następnie są usuwane. HKEY_CURRENT_USER zawiera klucz podobne, ale działa jako zwykły użytkownik i nie jest odpowiednie dla instalacji. Instalację można wznowić, ustawiając wartość ciągu w kluczu RunOnce, który wywołuje Instalatora. Firma Microsoft zaleca jednak wywołać Instalatora przy użyciu **/ponowne uruchomienie** lub podobny parametr, by powiadomić aplikację, która jest wznawiana zamiast uruchamiania. Może również obejmować parametry, aby wskazać, gdzie jesteś w procesie instalacji, co jest szczególnie przydatne w przypadku instalacji, które mogą wymagać ponownego uruchomienia wielu.  
  
 Poniższy przykład pokazuje wartość klucza rejestru RunOnce wznawiania instalacji.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalowanie Double ponowne uruchomienie programu inicjującego  
 Jeśli ustawienia są używane bezpośrednio z RunOnce, pulpitu nie będzie można całkowicie załadować. Aby udostępnić pełny interfejs użytkownika, możesz utworzyć inne uruchomienie Instalatora i zakończyć wystąpienia jednorazowego uruchomienia.  
  
 Program instalacyjny musi wykonaj ponownie, dzięki czemu uzyskuje odpowiednie uprawnienia i należy nadać mu wystarczająco dużo informacji, aby wiedzieć, gdzie zatrzymana przed ponownym uruchomieniem, co ilustruje poniższy przykład.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Usuwanie klucza ResumeData Instalatora powłoki  
 Instalator powłoki Ustawia klucz rejestru HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData z danymi, aby wznowić instalację po ponownym uruchomieniu. Ponieważ wznawia działanie Twojej aplikacji, a nie Instalator powłoki, należy usunąć tego klucza rejestru, jak w poniższym przykładzie pokazano.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Ponowne uruchamianie Windows  
 Po ustawieniu wymagane klucze rejestru, można ponownie uruchomić Windows. Poniższy przykład przedstawia wywoływanie polecenia ponownego uruchomienia dla różnych systemów operacyjnych Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Resetowanie Start ścieżka pliku msi  
 Przed ponownym uruchomieniem bieżący katalog to lokalizacji programu instalacyjnego, ale po ponownym uruchomieniu, lokalizacja staje się w katalogu system32. Program instalacyjny, należy resetować bieżącego katalogu przed każdym wywołaniem MSI, co ilustruje poniższy przykład.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Uruchomienie aplikacji MSI  
 Po powrocie z Instalatora programu Visual Studio Shell ERROR_SUCCESS możesz uruchomić plik MSI dla swojej aplikacji. Ponieważ program instalacyjny, dostarcza interfejs użytkownika, należy uruchomić usługi MSI w trybie cichym (**/q**) i za pomocą funkcji rejestrowania (**/l**), jak pokazano w poniższym przykładzie.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie podstawowej aplikacji Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

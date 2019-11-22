---
title: Instalowanie aplikacji izolowanej powłoki | Microsoft Docs
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
ms.openlocfilehash: a077173a0d095ee10cc1fa16da3db1f3744dafa8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301155"
---
# <a name="installing-an-isolated-shell-application"></a>Instalowanie aplikacji w programie Shell (izolowanym)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zainstalować aplikację powłoki, należy wykonać następujące czynności.  
  
- Przygotuj rozwiązanie.  
  
- Utwórz pakiet Instalator Windows (MSI) dla aplikacji.  
  
- Utwórz program inicjujący Instalatora.  
  
  Cały przykładowy kod w tym dokumencie pochodzi z [przykładu wdrożenia powłoki](https://go.microsoft.com/fwlink/?LinkId=262245), który można pobrać z galerii kodu w witrynie MSDN. Przykład pokazuje wyniki wykonywania każdego z tych kroków.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać procedury opisane w tym temacie, należy zainstalować na komputerze następujące narzędzia.  
  
- Zestaw Visual Studio SDK  
  
- Zestaw [narzędzi Instalator Windows XML](https://go.microsoft.com/fwlink/?LinkId=82720) w wersji 3,6  
  
  Przykład wymaga również wizualizacji i modelowania zestawu SDK firmy Microsoft, które nie są wymagane przez wszystkie powłoki.  
  
## <a name="preparing-your-solution"></a>Przygotowywanie rozwiązania  
 Domyślnie szablony powłoki kompilują pakiety VSIX, ale takie zachowanie jest przeznaczone głównie do celów debugowania. Podczas wdrażania aplikacji powłoki należy używać pakietów MSI do zezwalania na dostęp do rejestru i ponownego uruchamiania podczas instalacji. Aby przygotować aplikację do wdrożenia MSI, wykonaj następujące czynności.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Aby przygotować aplikację powłoki do wdrożenia MSI  
  
1. Edytuj każdy plik. vsixmanifest w rozwiązaniu.  
  
     W `Identifier` elementu Dodaj element `InstalledByMSI` i element `SystemComponent`, a następnie ustaw ich wartości na `true`.  
  
     Te elementy uniemożliwiają Instalatorowi VSIX próbę zainstalowania składników i odinstalowanie ich przez użytkownika przy użyciu okna dialogowego **rozszerzenia i aktualizacje** .  
  
2. Dla każdego projektu, który zawiera manifest VSIX, Edytuj zadania kompilacji w celu wygenerowania zawartości do lokalizacji, z której zostanie zainstalowany plik MSI. Uwzględnij manifest VSIX w danych wyjściowych kompilacji, ale nie Kompiluj pliku. VSIX.  
  
## <a name="creating-an-msi-for-your-shell"></a>Tworzenie pliku MSI dla powłoki  
 Aby skompilować pakiet MSI, zalecamy użycie zestawu [narzędzi Instalator Windows XML](https://go.microsoft.com/fwlink/?LinkId=82720) , ponieważ zapewnia większą elastyczność niż standardowy projekt konfiguracji.  
  
 W pliku Product. WXS Ustaw bloki wykrywania i układ składników powłoki.  
  
 Następnie utwórz wpisy rejestru, zarówno w pliku reg dla Twojego rozwiązania, jak i w ApplicationRegistry. WXS.  
  
### <a name="detection-blocks"></a>Bloki wykrywania  
 Blok wykrywania składa się z `Property` elementu, który określa warunek wstępny do wykrycia i `Condition` elementu, który określa komunikat, który ma zostać zwrócony, jeśli na komputerze nie ma wymagań wstępnych. Na przykład aplikacja powłoki będzie wymagała redystrybucyjnej powłoki Microsoft Visual Studio, a blok wykrywania będzie wyglądać następująco.  
  
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
  
### <a name="layout-of-shell-components"></a>Układ składników powłoki  
 Należy dodać elementy, aby określić docelową strukturę katalogów i składniki do zainstalowania.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Aby ustawić układ składników powłoki  
  
1. Utwórz hierarchię elementów `Directory`, aby reprezentować wszystkie katalogi do utworzenia w systemie plików na komputerze docelowym, jak pokazano w poniższym przykładzie.  
  
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
  
     Te katalogi są określane przez `Id`, gdy należy określić pliki, które muszą być zainstalowane.  
  
2. Zidentyfikuj składniki wymagane przez powłokę i aplikację powłoki, jak pokazano w poniższym przykładzie.  
  
    > [!NOTE]
    > Niektóre elementy mogą odwoływać się do definicji w innych plikach. WXS.  
  
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
  
    1. Element `ComponentRef` odwołuje się do innego pliku. WXS, który identyfikuje pliki wymagane przez bieżący składnik. Na przykład GeneralProfile ma następującą definicję w HelpAbout. WXS.  
  
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
  
         Element `DirectoryRef` określa, gdzie te pliki są przekazywane na komputerze użytkownika. `Directory` element określa, że zostanie on zainstalowany w podkatalogu, a każdy element `File` reprezentuje plik, który jest skompilowany lub który istnieje jako część rozwiązania i identyfikuje, gdzie można znaleźć ten plik podczas tworzenia pliku MSI.  
  
    2. `ComponentGroupRef` element odnosi się do grupy innych składników (lub składników i grup składników). Na przykład `ComponentGroupRef` w obszarze aplikacja jest zdefiniowana w następujący sposób w Application. WXS.  
  
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
    > Wymagane zależności aplikacji powłoki (izolowanych) to: DebuggerProxy, MasterPkgDef, zasoby (zwłaszcza plik. winprf), aplikacja i PkgDefs.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Szablon projektu Shell (izolowany) zawiera plik *ProjectName*. reg dla kluczy rejestru do scalenia podczas instalacji. Te wpisy rejestru muszą być częścią pliku MSI na potrzeby instalacji i czyszczenia. Należy również utworzyć pasujące bloki rejestru w ApplicationRegistry. WXS.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Aby zintegrować wpisy rejestru z MSI  
  
1. W folderze **Dostosowywanie powłoki** Otwórz *ProjectName*. reg.  
  
2. Zastąp wszystkie wystąpienia $RootFolder $ tokenem ścieżką docelowego katalogu instalacyjnego.  
  
3. Dodaj inne wpisy rejestru wymagane przez aplikację.  
  
4. Otwórz ApplicationRegistry. WXS.  
  
5. Dla każdego wpisu rejestru w *ProjectName*. reg Dodaj odpowiedni blok rejestru, jak pokazano w poniższych przykładach.  
  
    |*ProjectName*. reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "PhotoStudio DTE"|\<RegistryKey ID = "DteClsidRegKey" root = "HKCR" Key = "$ (var. DteClsidRegKey) "Action =" createAndRemoveOnUninstall "><br /><br /> \<RegistryValue Type = "String" name = "@" value = "$ (var. ShortProductName) obiekt DTE "/><br /><br /> \</RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @ = "$RootFolder $ \PhotoStudio.exe"|\<RegistryKey Id='DteLocSrv32RegKey' Root='HKCR' Key='$(var.DteClsidRegKey)\LocalServer32' Action='createAndRemoveOnUninstall'><br /><br /> \<RegistryValue Type = "String" name = "@" value = "[INSTALLDIR] $ (var. ShortProductName). exe "/><br /><br /> \</RegistryKey >|  
  
     W tym przykładzie var. DteClsidRegKey jest rozpoznawany jako klucz rejestru w górnym wierszu. Var. ShortProductName jest rozpoznawana jako `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Tworzenie programu inicjującego Instalatora  
 Ukończony plik MSI zostanie zainstalowany tylko wtedy, gdy najpierw zostaną zainstalowane wszystkie wymagania wstępne. Aby uprościć środowisko użytkownika końcowego, należy utworzyć program instalacyjny, który zbiera i instaluje wszystkie wymagania wstępne przed zainstalowaniem aplikacji. Aby zapewnić pomyślną instalację, wykonaj następujące czynności:  
  
- Wymuś instalację przez administratora.  
  
- Wykryj, czy program Visual Studio Shell (izolowany) jest zainstalowany.  
  
- Uruchom jedną lub obie Instalatory powłoki w podanej kolejności.  
  
- Obsługa żądań ponownego uruchomienia.  
  
- Uruchom plik MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Wymuszanie instalacji przez administratora  
 Ta procedura jest wymagana, aby umożliwić programowi Instalatora dostęp do wymaganych katalogów, takich jak \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Aby wymusić instalację przez administratora  
  
1. Otwórz menu skrótów dla projektu instalacji, a następnie wybierz polecenie **Właściwości**.  
  
2. W obszarze **Właściwości konfiguracji/konsolidator/plik manifestu**Ustaw **poziom wykonywania kontroli konta użytkownika** na **wymaga administratora**.  
  
     Ta właściwość umieszcza atrybut, który wymaga uruchomienia programu jako administrator w osadzonym pliku manifestu.  
  
### <a name="detecting-shell-installations"></a>Wykrywanie instalacji powłoki  
 Aby określić, czy program Visual Studio Shell (izolowany) musi być zainstalowany, należy najpierw określić, czy jest już zainstalowany, sprawdzając wartość rejestru HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Te wartości są również odczytywane przez blok wykrywania powłoki w Product. WXS.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder Określa lokalizację, w której zainstalowano powłokę programu Visual Studio, i można tam sprawdzić pliki.  
  
 Aby zapoznać się z przykładem wykrywania instalacji powłoki, zobacz funkcję `GetProductDirFromReg` narzędzi. cpp w przykładowym wdrożeniu powłoki.  
  
 Jeśli na komputerze nie zainstalowano jednej lub obu powłok programu Visual Studio, których wymaga pakiet, należy dodać je do listy składników do zainstalowania. Aby zapoznać się z przykładem, zapoznaj się z funkcją `ComponentsPage::OnInitDialog` ComponentsPage. cpp w przykładowym wdrożeniu powłoki.  
  
### <a name="running-the-shell-installers"></a>Uruchamianie instalatorów powłoki  
 Aby uruchomić instalatorów powłoki, wywołaj pakiet redystrybucyjny programu Visual Studio Shell przy użyciu prawidłowych argumentów wiersza polecenia. Aby określić, co należy wykonać, należy użyć argumentów wiersza polecenia **/norestart/q** i obserwować Kod powrotu. W poniższym przykładzie zostanie uruchomiony pakiet redystrybucyjny programu Shell (izolowany).  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Uruchamianie instalatorów pakietu językowego powłoki  
 Jeśli zamiast tego okaże się, że powłoka lub powłoki zostały zainstalowane i wystarczy pakiet językowy, można zainstalować pakiety językowe, jak pokazano w poniższym przykładzie.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Deszyfrowanie wartości zwracanych  
 W niektórych systemach operacyjnych instalacja programu Visual Studio Shell (izolowana) będzie wymagała ponownego uruchomienia. Ten stan może być określony przez kod powrotu wywołania do `ExecCmd`.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalacja została ukończona. Teraz można zainstalować aplikację.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalacja została ukończona. Po ponownym uruchomieniu komputera można zainstalować aplikację.|  
|3015|Instalacja jest w toku. W celu kontynuowania instalacji wymagane jest ponowne uruchomienie komputera.|  
  
### <a name="handling-restarts"></a>Obsługa ponownych uruchomień  
 Po uruchomieniu Instalatora powłoki przy użyciu argumentu **/norestart** określono, że nie będzie on ponownie uruchamiał komputera lub poprosił o ponowne uruchomienie komputera. Może być jednak wymagane ponowne uruchomienie komputera i należy upewnić się, że Instalator będzie kontynuował działanie po ponownym uruchomieniu.  
  
 Aby prawidłowo obsłużyć ponowne uruchamianie, upewnij się, że tylko jeden program instalacyjny jest ustawiony do wznowienia i że proces wznawiania będzie obsłużony prawidłowo.  
  
 Jeśli zostanie zwrócona wartość ERROR_SUCCESS_REBOOT_REQUIRED lub 3015, kod powinien ponownie uruchomić komputer przed kontynuowaniem instalacji.  
  
 Aby obsłużyć ponowne uruchomienia, wykonaj następujące czynności:  
  
- Ustaw rejestr w celu wznowienia instalacji po uruchomieniu systemu Windows.  
  
- Wykonaj podwójne ponowne uruchomienie programu inicjującego.  
  
- Usuń klucz ResumeData Instalatora powłoki.  
  
- Uruchom ponownie system Windows.  
  
- Zresetuj ścieżkę początkową pliku MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Ustawianie rejestru w celu wznowienia instalacji po uruchomieniu systemu Windows  
 Klucz rejestru HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ jest wykonywany podczas uruchamiania systemu z uprawnieniami administracyjnymi, a następnie jest usuwany. HKEY_CURRENT_USER zawiera podobny klucz, ale jest uruchamiany jako zwykły użytkownik i nie jest odpowiedni dla instalacji. Instalację można wznowić przez umieszczenie w kluczu RunOnce wartości ciągu, która wywołuje Instalatora. Zaleca się jednak, aby wywoływać Instalatora przy użyciu **/restart** lub podobnego parametru w celu powiadomienia aplikacji, która jest wznawiana zamiast uruchamiania. Możesz również dołączyć parametry, aby wskazać, gdzie jesteś w procesie instalacji, co jest szczególnie przydatne w przypadku instalacji, które mogą wymagać wielu ponownych uruchomień.  
  
 Poniższy przykład przedstawia wartość klucza rejestru RunOnce dla wznawiania instalacji.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalowanie podwójnego ponownego uruchomienia programu inicjującego  
 Jeśli Instalator jest używany bezpośrednio z programu RunOnce, pulpit nie będzie mógł zostać załadowany w całości. Aby zapewnić pełen dostęp do interfejsu użytkownika, należy utworzyć inne wykonanie instalacji i zakończyć wystąpienie RunOnce.  
  
 Należy ponownie uruchomić program instalacyjny, aby uzyskał odpowiednie uprawnienia, i należy przekazać mu wystarczającą ilość informacji, aby dowiedzieć się, gdzie zostało zatrzymane przed ponownym uruchomieniem, jak pokazano w poniższym przykładzie.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Usuwanie klucza ResumeData Instalatora powłoki  
 Instalator powłoki ustawia klucz rejestru HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData z danymi w celu wznowienia instalacji po ponownym uruchomieniu. Ponieważ aplikacja, a nie Instalator powłoki, wznawia działanie, Usuń ten klucz rejestru, jak pokazano w poniższym przykładzie.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Ponowne uruchamianie systemu Windows  
 Po ustawieniu wymaganych kluczy rejestru możesz ponownie uruchomić system Windows. Poniższy przykład wywołuje polecenia restart dla różnych systemów operacyjnych Windows.  
  
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
  
### <a name="resetting-the-start-path-of-msi"></a>Resetowanie ścieżki początkowej MSI  
 Przed ponownym uruchomieniem, bieżący katalog jest lokalizacją programu instalacyjnego, ale po ponownym uruchomieniu, lokalizacja zmieni się na katalog system32. Program instalacyjny powinien zresetować bieżący katalog przed każdym wywołaniem MSI, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="running-the-application-msi"></a>Uruchamianie aplikacji MSI  
 Po powrocie Instalatora powłoki programu Visual Studio ERROR_SUCCESS można uruchomić plik MSI dla swojej aplikacji. Ponieważ Twój program instalacyjny udostępnia interfejs użytkownika, uruchom plik MSI w trybie cichym ( **/q**) i z funkcją rejestrowania ( **/l**), jak pokazano w poniższym przykładzie.  
  
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

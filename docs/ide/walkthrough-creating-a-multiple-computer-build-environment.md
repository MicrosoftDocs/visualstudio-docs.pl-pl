---
title: 'Przewodnik: tworzenie środowiska kompilowania na wielu komputerach'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11b158854a0026de28cb2fb0a582bbaf764eeaa4
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461536"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Przewodnik: tworzenie środowiska kompilowania na wielu komputerach

Środowisko kompilacji można utworzyć w organizacji, instalując program Visual Studio na komputerze hosta, a następnie kopiując różne pliki i ustawienia na inny komputer, aby mógł uczestniczyć w kompilacjach. Nie trzeba instalować programu Visual Studio na innym komputerze.

Ten dokument nie przyznaje praw do samodzielnego rozpowszechniania oprogramowania lub dostarczania środowisk kompilacji do stron trzecich.

> Zastrzeżenie<br /><br /> Ten dokument jest dostarczany z uwzględnieniem "AS-IS". Po przetestowaniu opisanych czynności firma Microsoft nie może wyczerpująco testować każdej konfiguracji. Będziemy próbować zachować bieżący dokument z dowolnymi dodatkowymi informacjami. Informacje i poglądy wyrażone w tym dokumencie, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do informacji podanych w tym miejscu. Użytkownik ponosi ryzyko związane z korzystaniem z niego.<br /><br /> Niniejszy dokument nie udostępnia żadnych praw do jakiejkolwiek własności intelektualnej w jakimkolwiek produkcie firmy Microsoft. Licencjobiorca może kopiować i używać tego dokumentu do wewnętrznych celów referencyjnych.<br /><br /> Nie masz obowiązku udzielenia firmie Microsoft żadnych sugestii, komentarzy ani innych informacji zwrotnych ("opinia") związanych z tym dokumentem. Jednak wszelkie zaoferowane dobrowolnie informacje mogą być używane w produktach firmy Microsoft i związanych z nimi specyfikacjach lub w innych dokumentach (zbiorczo "oferty firmy Microsoft"), które z kolei mogą polegać na innych stronach trzecich do opracowania własnych produktów. W związku z tym, Jeśli przekażesz opinię firmy Microsoft dotyczącą dowolnej wersji tego dokumentu lub ofert firmy Microsoft, do których mają zastosowanie, zgadzasz się: (a) firma Microsoft może swobodnie używać, reprodukowania, licencjonować, rozpowszechniać i w inny sposób wprowadzać swoją opinię w firmie Microsoft Oferty (b) przyznano również podmiotom trzecim bez opłat, tylko te prawa patentowe, które są niezbędne do umożliwienia innym produktom korzystania z określonych części produktu firmy Microsoft, które obejmują swoją opinię; i (c) nie otrzymasz opinii firmy Microsoft o tym, że masz powód, aby podejrzewać, że podlegają one jakimkolwiek patentom, prawom autorskim lub innym podmiotom własności intelektualnej; lub (II) z zastrzeżeniem postanowień licencyjnych, które poszukują złożenia oferty firmy Microsoft lub jej podania na podstawie opinii lub innych własności intelektualnej firmy Microsoft, które mają być licencjonowane lub udostępniane innym podmiotom trzecim.

Ten Instruktaż został sprawdzony pod kątem następujących systemów operacyjnych:

- Windows 8 (x86 i x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Po wykonaniu kroków opisanych w tym instruktażu można użyć środowiska wielu komputerów do kompilowania tych rodzajów aplikacji:

- C++aplikacje klasyczne korzystające z zestawu SDK systemu Windows 8
- Visual Basic lub C# aplikacje klasyczne, które są przeznaczone dla .NET Framework 4,5

Nie można używać środowiska wielu komputerów do kompilowania tych rodzajów aplikacji:

- Aplikacje platformy UWP. Aby tworzyć aplikacje platformy UWP, należy zainstalować program Visual Studio na komputerze kompilacji.
- Aplikacje klasyczne, które są przeznaczone dla .NET Framework 4 lub starszych. Aby kompilować te rodzaje aplikacji, należy zainstalować program Visual Studio lub zestawy odniesienia i narzędzia platformy .NET (z zestawu SDK systemu Windows 7,1) na komputerze kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

Program Visual Studio z zainstalowanym obciążeniem **deweloperskim programu .NET Desktop** .

## <a name="install-software-on-the-computers"></a>Zainstaluj oprogramowanie na komputerach

Najpierw skonfiguruj komputer hosta, a następnie skonfiguruj komputer kompilacji.

Instalując program Visual Studio na komputerze hosta, należy utworzyć pliki i ustawienia, które zostaną później skopiowane do komputera kompilacji. Program Visual Studio można zainstalować na komputerze z procesorem x86 lub x64, ale architektura komputera kompilacji musi być zgodna z architekturą komputera hosta.

1. Na komputerze-hoście Zainstaluj program Visual Studio.

2. Na komputerze kompilacji Zainstaluj .NET Framework 4,5 lub nowszy. Aby sprawdzić, czy jest zainstalowana, sprawdź, czy wpis **wersji** w podkluczu rejestru **rejestrze Framework Setup\NDP\v4\Full** ma wartość **4,5** lub wyższą.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Kopiuj pliki z komputera hosta do komputera kompilacji

Ta sekcja dotyczy kopiowania określonych plików, kompilatorów, narzędzi kompilacji, zasobów programu MSBuild i ustawień rejestru z komputera hosta do komputera kompilacji. W tych instrukcjach przyjęto założenie, że program Visual Studio został zainstalowany w domyślnej lokalizacji na komputerze-hoście; Jeśli zainstalowano w innej lokalizacji, Dostosuj odpowiednie kroki.

- Na komputerze z procesorem x86 lokalizacja domyślna to *C:\Program Files\Microsoft Visual Studio*
- Na komputerze z procesorem x64 domyślna lokalizacja to *C:\Program Files (x86) \Microsoft Visual Studio*

Należy zauważyć, że nazwa folderu *Program Files* jest zależna od zainstalowanego systemu operacyjnego. Na komputerze z procesorem x86 nazwa to *Program Files*; na komputerze z procesorem x64 nazwa to *Program Files (x86)* . Niezależnie od architektury systemu, ten Instruktaż dotyczy folderu *Program Files* jako *% ProgramFiles%* .

> [!NOTE]
> Na komputerze kompilacji wszystkie odpowiednie pliki muszą znajdować się na tym samym dysku. Literę dysku dla tego dysku mogą jednak różnić się od litery dysku dysku, na którym program Visual Studio jest zainstalowany na komputerze hosta. W każdym przypadku należy uwzględnić lokalizację plików podczas tworzenia wpisów rejestru zgodnie z opisem w dalszej części tego dokumentu.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Kopiowanie plików Windows SDK na komputer kompilacji

1. Jeśli masz tylko Windows SDK dla systemu Windows 8, skopiuj te foldery rekurencyjnie z komputera hosta do komputera kompilacji:

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

   Jeśli istnieją także inne zestawy Windows 8...

   - Zestaw do oceny i wdrażania systemu Microsoft Windows

   - Zestaw sterowników systemu Microsoft Windows

   - Zestaw certyfikacji sprzętu systemu Microsoft Windows

   ... mogą mieć zainstalowane pliki w folderach *%PROGRAMFILES%\Windows Kits\8.0* , które są wymienione w poprzednim kroku, a ich postanowienia licencyjne mogą nie zezwalać na prawa serwera kompilacji dla tych plików. Zapoznaj się z postanowieniami licencyjnymi dotyczącymi każdego zainstalowanego zestawu Windows Kit, aby sprawdzić, czy pliki mogą być kopiowane do komputera kompilacji. Jeśli postanowienia licencyjne nie zezwalają na prawa serwera kompilacji, Usuń pliki z komputera kompilacji.

2. Skopiuj następujące foldery cyklicznie z komputera hosta do komputera kompilacji:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Merge Modules\

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\VC\

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. Skopiuj te pliki z komputera hosta do komputera kompilacji:

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\Tools\vsvars32.bat

4. Następujące biblioteki środowiska C++ uruchomieniowego języka Visual są wymagane tylko wtedy, gdy uruchamiasz dane wyjściowe kompilacji na komputerze kompilacji — na przykład w ramach zautomatyzowanego testowania. Pliki zwykle znajdują się w podfolderach *%ProgramFiles%\Microsoft Visual Studio\\\<version >\\\<Edition > \VC\redist\x86* lub *%ProgramFiles%\Microsoft Visual Studio\\wwersji\\>Edition>\VC\redist\x64,wzależnościodarchitekturysystemu\<.\<* W systemach x86 Skopiuj pliki binarne x86 do folderu *Windows\System32* . W systemach x64 Skopiuj pliki binarne x86 do folderu *Windows\SysWOW64* oraz pliki binarne x64 do folderu *Windows\System32* .

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Skopiuj tylko następujące pliki z folderu *Debug_NonRedist\x86* lub *Debug_NonRedist\x64* do komputera kompilacji, zgodnie z opisem w artykule [przygotowywanie maszyny testowej do uruchamiania pliku wykonywalnego debugowania](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Nie można kopiować innych plików.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Utwórz ustawienia rejestru

Aby skonfigurować ustawienia dla programu MSBuild, należy utworzyć wpisy rejestru.

1. Zidentyfikuj folder nadrzędny dla wpisów rejestru. Wszystkie wpisy rejestru są tworzone pod tym samym kluczem nadrzędnym. Na komputerze z procesorem x86 kluczem nadrzędnym jest **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. Na komputerze z procesorem x64 klucz nadrzędny to **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Niezależnie od architektury systemu, ten Instruktaż odwołuje się do klucza nadrzędnego jako% RegistryRoot%.

    > [!NOTE]
    > Jeśli architektura komputera hosta różni się od wersji komputera kompilacji, upewnij się, że na każdym komputerze użyto odpowiedniego klucza nadrzędnego. Jest to szczególnie ważne w przypadku automatyzowania procesu eksportu.
    >
    > Ponadto, jeśli używasz innej litery dysku na komputerze kompilacji niż ta, która jest używana na komputerze hosta, pamiętaj, aby zmienić wartości wpisów rejestru.

2. Utwórz następujące wpisy rejestru na komputerze kompilacji. Wszystkie te wpisy są ciągami (Type = = "REG_SZ") w rejestrze. Ustaw wartości tych wpisów tak samo jak wartości porównywalnych wpisów na komputerze hosta.

   - **% RegistryRoot%\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild zestawy publiczne @ (domyślnie)**

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **% RegistryRoot%\VisualStudio\11.0@Source katalogów**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\InstalledRoots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   Na komputerze kompilacji x64 Utwórz również następujący wpis rejestru i zapoznaj się z komputerem hosta, aby określić, jak go ustawić.

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Jeśli komputer kompilacji to x64 i chcesz użyć 64-bitowej wersji programu MSBuild lub jeśli używasz usługi Team Foundation Server Build na komputerze z procesorem x64, Utwórz następujące wpisy rejestru w natywnym rejestrze 64-bitowym. Zapoznaj się z komputerem hosta, aby określić, jak ustawić te wpisy.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Ustawianie zmiennych środowiskowych na komputerze kompilacji

Aby użyć programu MSBuild na komputerze kompilacji, należy ustawić zmienne środowiskowe PATH. Można użyć *vcvarsall. bat* , aby ustawić zmienne, lub można je skonfigurować ręcznie.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Użyj vcvarsall. bat do ustawiania zmiennych środowiskowych

Otwórz okno **wiersza polecenia** na komputerze kompilacji i uruchom *Program% Files%\Microsoft programu\\Visual Studio\<w wersji >\\\<Edition > \VC\vcvarsall.bat*. Można użyć argumentu wiersza polecenia, aby określić zestaw narzędzi, który ma być używany — x86, natywny x64 lub x64 cross-kompilator. Jeśli nie określisz argumentu wiersza polecenia, zostanie użyty zestaw narzędzi x86.

W tej tabeli opisano obsługiwane argumenty dla *vcvarsall. bat*:

|Vcvarsall. bat — argument|Compiler|Architektura komputera kompilacji|Architektura danych wyjściowych kompilacji|
| - |--------------| - | - |
|x86 (wartość domyślna)|32 — bit natywny|x86, x64|x86|
|x86_amd64|64 krzyżowe|x86, x64|X64|
|amd64|Procesor x64|X64|X64|

Jeśli *vcvarsall. bat* zostanie uruchomiony pomyślnie — to znaczy, że żaden komunikat o błędzie nie jest wyświetlany — można pominąć następny krok i kontynuować [instalację zestawów MSBuild w globalnej pamięci podręcznej zestawów (GAC) w sekcji Kompilacja komputera](#install-msbuild-to-gac) tego dokumentu.

### <a name="manually-set-environment-variables"></a>Ręcznie Ustaw zmienne środowiskowe

1. Aby ręcznie skonfigurować środowisko wiersza polecenia, należy dodać tę ścieżkę do zmiennej środowiskowej PATH:

    - % Program Files%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE

2. Opcjonalnie można również dodać następujące ścieżki do zmiennej PATH, aby ułatwić korzystanie z programu MSBuild do kompilowania rozwiązań.

   Jeśli chcesz użyć natywnego 32-bitowego programu MSBuild, Dodaj te ścieżki do zmiennej PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Jeśli chcesz użyć natywnego 64-bitowego programu MSBuild, Dodaj te ścieżki do zmiennej PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="a-nameinstall-msbuild-to-gac--install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" />Instalowanie zestawów programu MSBuild w globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji

Program MSBuild wymaga zainstalowania dodatkowych zestawów w pamięci GAC na komputerze kompilacji.

1. Skopiuj następujące zestawy z komputera hosta do komputera kompilacji. Ponieważ zostaną one zainstalowane w pamięci podręcznej GAC, nie ma znaczenia, gdzie są umieszczane na komputerze kompilacji.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio\\\<w wersji\\>\<Edition > \Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Aby zainstalować zestawy w pamięci podręcznej GAC, zlokalizuj *Gacutil. exe* na komputerze kompilacji — zwykle jest to narzędzie%programfiles%\microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools\\. Jeśli nie możesz znaleźć tego folderu, powtórz czynności opisane w sekcji [Kopiuj pliki z komputera hosta do komputera kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) w tym instruktażu.

     Otwórz okno **wiersza polecenia** z uprawnieniami administracyjnymi i Uruchom to polecenie dla każdego pliku:

     **plik Gacutil- \<i >**

    > [!NOTE]
    > Może być wymagany ponowny rozruch zestawu, aby można było w pełni zainstalować do pamięci GAC.

## <a name="build-projects"></a>Kompiluj projekty

Za pomocą Azure Pipelines można tworzyć projekty i rozwiązania programu Visual Studio lub tworzyć je w wierszu polecenia. W przypadku używania Azure Pipelines do kompilowania projektów program wywołuje plik wykonywalny MSBuild, który odpowiada architekturze systemu. W wierszu polecenia można użyć 32-bitowej wersji programu MSBuild lub 64-bitowego programu MSBuild i można wybrać architekturę MSBuild, ustawiając zmienną środowiskową PATH lub bezpośrednio wywołując plik wykonywalny specyficzny dla architektury.

Aby użyć programu *MSBuild. exe* w wierszu polecenia, uruchom następujące polecenie, w którym *rozwiązanie. sln* jest symbolem zastępczym dla nazwy rozwiązania.

**msbuild** *solution.sln*

Aby uzyskać więcej informacji o sposobach korzystania z programu MSBuild w wierszu polecenia, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Utwórz środowisko kompilacji, aby można było je zaewidencjonować w kontroli źródła

Można utworzyć środowisko kompilacji, które można wdrożyć na różnych komputerach i nie wymaga plików "GAC"-lub modyfikowania ustawień rejestru. Poniższe kroki są tylko jednym ze sposobów, aby to zrobić. Dostosuj te kroki do unikatowych cech środowiska kompilacji.

> [!NOTE]
> Należy wyłączyć Kompilowanie przyrostowe, aby program *śledząc. exe* nie zgłosi błędu podczas kompilacji. Aby wyłączyć Kompilowanie przyrostowe, ustaw ten parametr kompilacji:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Utwórz katalog *magazynu* na komputerze-hoście.

     Te kroki odnoszą się do katalogu jako% magazyn%.

2. Skopiuj katalogi i pliki zgodnie z opisem w sekcji [Kopiuj pliki z komputera hosta do komputera kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) w tym instruktażu, z tą różnicą, że wklej je w katalogu *% Magazyn%* , który został właśnie utworzony. Na przykład skopiuj z *katalogu%PROGRAMFILES%\Windows Kits\8.0\bin* do *%Depot%\Windows Kits\8.0\bin*.

3. Po wklejeniu plików w *% magazynie%* wprowadź następujące zmiany:

    - W%Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.cpp.targets, \Microsoft.cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\i \Microsoft.CppCommon.targets\\, Zmień każde wystąpienie z

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Poprzednie nazewnictwo polega na GAC'ed zestawu.

    - W magazynie% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets Zmień każde wystąpienie elementu

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Utwórz plik *. props* — na przykład *partner. AutoImports. props*— i umieść go w katalogu głównym folderu, który zawiera projekty. Ten plik służy do ustawiania zmiennych, które są używane przez program MSBuild do znajdowania różnych zasobów. Jeśli zmienne nie są ustawiane przez ten plik, są ustawiane przez inne *.* elementy props i pliki *. targets* , które opierają się na wartościach rejestru. Ponieważ nie ustawiamy żadnych wartości rejestru, te zmienne byłyby puste i kompilacja nie powiedzie się. Zamiast tego należy dodać ten program do *partnera. AutoImports. props*:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio\2017\Enterprise\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. W każdym z plików projektu, należy dodać następujący wiersz u góry, po `<Project Default Targets...>` wierszu.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Zmień środowisko wiersza polecenia w następujący sposób:

    - Set magazynu =*Lokalizacja katalogu magazynu utworzonego w kroku 1*

    - Ustaw ścieżkę =% Path%; *Lokalizacja programu MSBuild na komputerze*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 15.0 \ Common7\IDE\

       W przypadku natywnego kompilowania 64-bitowego wskaż 64-bitową wersję programu MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Zmień środowisko wiersza polecenia w następujący sposób:

    - Set magazynu =*Lokalizacja katalogu magazynu utworzonego w kroku 1*

    - Ustaw ścieżkę =% Path%; *Lokalizacja programu MSBuild na komputerze*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 16.0 \ Common7\IDE\

       W przypadku natywnego kompilowania 64-bitowego wskaż 64-bitową wersję programu MSBuild.

::: moniker-end

## <a name="see-also"></a>Zobacz także

- [Przygotuj maszynę testową do uruchomienia pliku wykonywalnego debugowania](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
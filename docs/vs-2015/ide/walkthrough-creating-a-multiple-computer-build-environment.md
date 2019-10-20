---
title: 'Przewodnik: Tworzenie środowiska kompilacji z wieloma komputerami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d0fccb5694e538cdf71844d2cc18640114ec735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672309"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Wskazówki: tworzenie środowiska kompilacji na wielu komputerach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Środowisko kompilacji można utworzyć w organizacji, instalując program Visual Studio na komputerze hosta, a następnie kopiując różne pliki i ustawienia na inny komputer, aby mógł uczestniczyć w kompilacjach. Nie trzeba instalować programu Visual Studio na innym komputerze.

 Ten dokument nie przyznaje praw do samodzielnego rozpowszechniania oprogramowania lub dostarczania środowisk kompilacji do stron trzecich.

||
|-|
|Zastrzeżenie<br /><br /> Ten dokument jest dostarczany z uwzględnieniem "AS-IS". Po przetestowaniu opisanych czynności firma Microsoft nie może wyczerpująco testować każdej konfiguracji. Będziemy próbować zachować bieżący dokument z dowolnymi dodatkowymi informacjami. Informacje i poglądy wyrażone w tym dokumencie, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do informacji podanych w tym miejscu. Użytkownik ponosi ryzyko związane z korzystaniem z niego.<br /><br /> Niniejszy dokument nie udostępnia żadnych praw do jakiejkolwiek własności intelektualnej w jakimkolwiek produkcie firmy Microsoft. Licencjobiorca może kopiować i używać tego dokumentu do wewnętrznych celów referencyjnych.<br /><br /> Nie masz obowiązku udzielenia firmie Microsoft żadnych sugestii, komentarzy ani innych informacji zwrotnych ("opinia") związanych z tym dokumentem. Jednak wszelkie zaoferowane dobrowolnie informacje mogą być używane w produktach firmy Microsoft i związanych z nimi specyfikacjach lub w innych dokumentach (zbiorczo "oferty firmy Microsoft"), które z kolei mogą polegać na innych stronach trzecich do opracowania własnych produktów. W związku z tym, Jeśli przekażesz opinię firmy Microsoft dotyczącą dowolnej wersji tego dokumentu lub ofert firmy Microsoft, do których mają zastosowanie, zgadzasz się: (a) firma Microsoft może swobodnie używać, reprodukowania, licencjonować, rozpowszechniać i w inny sposób wprowadzać swoją opinię w firmie Microsoft Oferty (b) przyznano również podmiotom trzecim bez opłat, tylko te prawa patentowe, które są niezbędne do umożliwienia innym produktom korzystania z określonych części produktu firmy Microsoft, które obejmują swoją opinię; i (c) nie otrzymasz opinii firmy Microsoft o tym, że masz powód, aby podejrzewać, że podlegają one jakimkolwiek patentom, prawom autorskim lub innym podmiotom własności intelektualnej; lub (II) z zastrzeżeniem postanowień licencyjnych, które poszukują złożenia oferty firmy Microsoft lub jej podania na podstawie opinii lub innych własności intelektualnej firmy Microsoft, które mają być licencjonowane lub udostępniane innym podmiotom trzecim.|

 Ten Instruktaż został sprawdzony pod kątem następujących systemów operacyjnych przez wykonanie MSBuild w wierszu polecenia i za pomocą Team Foundation Build.

- Windows 8 (x86 i x64)

- Windows 7 Ultimate

- Windows Server 2008 R2 Standard

  Po wykonaniu kroków opisanych w tym instruktażu można użyć środowiska wielu komputerów do kompilowania tych rodzajów aplikacji:

- C++aplikacje klasyczne korzystające z zestawu SDK systemu Windows 8

- Visual Basic lub C# aplikacje klasyczne, które są przeznaczone dla .NET Framework 4,5

  Nie można używać środowiska wielu komputerów do kompilowania tych rodzajów aplikacji:

- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji. Aby tworzyć aplikacje [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], należy zainstalować program Visual Studio na komputerze kompilacji.

- Aplikacje klasyczne, które są przeznaczone dla .NET Framework 4 lub starszych. Aby kompilować te rodzaje aplikacji, należy zainstalować program Visual Studio lub zestawy odniesienia i narzędzia platformy .NET (z zestawu SDK systemu Windows 7,1) na komputerze kompilacji.

  Ten Instruktaż jest podzielony na następujące części:

- [Instalowanie oprogramowania na komputerach](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)

- [Kopiowanie plików z komputera hosta do komputera kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)

- [Tworzenie ustawień rejestru](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)

- [Ustawianie zmiennych środowiskowych na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)

- [Instalowanie zestawów MSBuild w globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)

- [Kompilowanie projektów](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)

- [Tworzenie środowiska kompilacji tak, aby można je było zaewidencjonować do kontroli źródła](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)

## <a name="prerequisites"></a>Wymagania wstępne

- Licencjonowana kopia Visual Studio Ultimate, Visual Studio Premium lub Visual Studio Professional

- Kopia .NET Framework 4.5.1, którą można pobrać z witryny sieci Web [firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=40779) .

## <a name="InstallingSoftware"></a>Instalowanie oprogramowania na komputerach
 Najpierw skonfiguruj komputer hosta, a następnie skonfiguruj komputer kompilacji.

 Instalując program Visual Studio na komputerze hosta, należy utworzyć pliki i ustawienia, które zostaną później skopiowane do komputera kompilacji. Program Visual Studio można zainstalować na komputerze z procesorem x86 lub x64, ale architektura komputera kompilacji musi być zgodna z architekturą komputera hosta.

#### <a name="to-install-software-on-the-computers"></a>Aby zainstalować oprogramowanie na komputerach

1. Na komputerze-hoście Zainstaluj program Visual Studio.

2. Na komputerze kompilacji Zainstaluj .NET Framework 4,5. Aby sprawdzić, czy jest zainstalowana, upewnij się, że wartość klucza rejestru rejestrze Framework Setup\NDP\v4\Full@Version rozpoczyna się od "4,5".

## <a name="CopyingFiles"></a>Kopiowanie plików z komputera hosta do komputera kompilacji
 Ta sekcja dotyczy kopiowania określonych plików, kompilatorów, narzędzi kompilacji, zasobów programu MSBuild i ustawień rejestru z komputera hosta do komputera kompilacji. W tych instrukcjach przyjęto założenie, że program Visual Studio został zainstalowany w domyślnej lokalizacji na komputerze-hoście; Jeśli zainstalowano w innej lokalizacji, Dostosuj odpowiednie kroki.

- Na komputerze z procesorem x86 domyślna lokalizacja to C:\Program Files\Microsoft Visual Studio 11,0 \

- Na komputerze z procesorem x64 domyślna lokalizacja to C:\Program Files (x86) \Microsoft Visual Studio 11,0 \

  Należy zauważyć, że nazwa folderu Program Files jest zależna od zainstalowanego systemu operacyjnego. Na komputerze z procesorem x86 nazwa to \Program Files \\; na komputerze z procesorem x64 nazwa to \Program Files (x86) \\. Niezależnie od architektury systemu, ten Instruktaż dotyczy folderu Program Files jako% ProgramFiles%.

> [!NOTE]
> Na komputerze kompilacji wszystkie odpowiednie pliki muszą znajdować się na tym samym dysku; literę dysku dla tego dysku mogą jednak różnić się od litery dysku dysku, na którym program Visual Studio jest zainstalowany na komputerze hosta. W każdym przypadku należy uwzględnić lokalizację plików podczas tworzenia wpisów rejestru zgodnie z opisem w dalszej części tego dokumentu.

#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Aby skopiować pliki Windows SDK do komputera kompilacji

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

     ... mogą mieć zainstalowane pliki w folderach%ProgramFiles%\Windows Kits\8.0\, które są wymienione w poprzednim kroku, a ich postanowienia licencyjne mogą nie zezwalać na prawa serwera kompilacji dla tych plików. Zapoznaj się z postanowieniami licencyjnymi dotyczącymi każdego zainstalowanego zestawu Windows Kit, aby sprawdzić, czy pliki mogą być kopiowane do komputera kompilacji. Jeśli postanowienia licencyjne nie zezwalają na prawa serwera kompilacji, Usuń pliki z komputera kompilacji.

2. Skopiuj następujące foldery cyklicznie z komputera hosta do komputera kompilacji:

   - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools \

   - %ProgramFiles%\Common Files\Merge — moduły \

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ VC \

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\ProjectComponents\

   - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework \\. NETCore\v4.5\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework \\. NETFramework\v4.5\

3. Skopiuj te pliki z komputera hosta do komputera kompilacji:

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\msobj110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdb110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdbcore.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\mspdbsrv.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\msvcdis110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\makehm.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\VCVarsQueryRegistry.bat

   - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\Tools\vsvars32.bat

4. Następujące biblioteki środowiska C++ uruchomieniowego języka Visual są wymagane tylko wtedy, gdy uruchamiasz dane wyjściowe kompilacji na komputerze kompilacji — na przykład w ramach zautomatyzowanego testowania. Pliki zwykle znajdują się w podfolderach%ProgramFiles%\Microsoft Visual Studio 11.0 \ VC\redist\x86\ lub%ProgramFiles%\Microsoft Visual Studio 11.0 \ VC\redist\x64\, w zależności od architektury systemu. W systemach x86 Skopiuj pliki binarne x86 do folderu \Windows\system32\.. W systemach x64 Skopiuj pliki binarne x86 do folderu Windows\SysWOW64\ oraz pliki binarne x64 do folderu Windows\System32\.

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

5. Skopiuj tylko następujące pliki z folderu \Debug_NonRedist\x86\ lub \Debug_NonRedist\x64\ do komputera kompilacji, zgodnie z opisem w artykule [przygotowywanie maszyny testowej do uruchomienia pliku wykonywalnego debugowania](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Nie można kopiować innych plików.

   - \Microsoft.VC110.DebugCRT\msvcp110d.dll

   - \Microsoft.VC110.DebugCRT\msvcr110d.dll

   - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110ud.dll

   - \Microsoft.VC110.DebugMFC\mfcm110d.dll

   - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

   - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="CreatingRegistry"></a>Tworzenie ustawień rejestru
 Aby skonfigurować ustawienia dla programu MSBuild, należy utworzyć wpisy rejestru.

#### <a name="to-create-registry-settings"></a>Aby utworzyć ustawienia rejestru

1. Zidentyfikuj folder nadrzędny dla wpisów rejestru. Wszystkie wpisy rejestru są tworzone pod tym samym kluczem nadrzędnym. Na komputerze z procesorem x86 klucz nadrzędny to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft \\. Na komputerze z procesorem x64 klucz nadrzędny to HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft \\. Niezależnie od architektury systemu, ten Instruktaż odwołuje się do klucza nadrzędnego jako% RegistryRoot%.

   > [!NOTE]
   > Jeśli architektura komputera hosta różni się od wersji komputera kompilacji, upewnij się, że na każdym komputerze użyto odpowiedniego klucza nadrzędnego. Jest to szczególnie ważne w przypadku automatyzowania procesu eksportu.
   >
   >  Ponadto, jeśli używasz innej litery dysku na komputerze kompilacji niż ta, która jest używana na komputerze hosta, pamiętaj, aby zmienić wartości wpisów rejestru.

2. Utwórz następujące wpisy rejestru na komputerze kompilacji. Wszystkie te wpisy są ciągami (Type = = "REG_SZ") w rejestrze. Ustaw wartości tych wpisów tak samo jak wartości porównywalnych wpisów na komputerze hosta.

   - % RegistryRoot% \\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild publiczne zestawy @ (domyślnie)

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder

   - % RegistryRoot% \VisualStudio\11.0@Source katalogi

   - % RegistryRoot% \VisualStudio\11.0\Setup\VC@ProductDir

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkDir32

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkDir64

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkVer32

   - % RegistryRoot% \VisualStudio\SxS\VC7@FrameworkVer64

   - % RegistryRoot% \VisualStudio\SxS\VC7@11.0

   - % RegistryRoot% \VisualStudio\SxS\VS7@11.0

   - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - % RegistryRoot% \MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

     Na komputerze kompilacji x64 Utwórz również następujący wpis rejestru i zapoznaj się z komputerem hosta, aby określić, jak go ustawić.

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder

     Jeśli komputer kompilacji to x64 i chcesz użyć 64-bitowej wersji programu MSBuild lub jeśli używasz usługi Team Foundation Server Build na komputerze z procesorem x64, musisz utworzyć następujące wpisy rejestru w macierzystym rejestrze 64-bitowym. Zapoznaj się z komputerem hosta, aby określić, jak ustawić te wpisy.

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

## <a name="SettingEnvVariables"></a>Ustawianie zmiennych środowiskowych na komputerze kompilacji
 Aby użyć programu MSBuild na komputerze kompilacji, należy ustawić zmienne środowiskowe PATH. Można użyć vcvarsall. bat, aby ustawić zmienne, lub można je skonfigurować ręcznie.

#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Aby użyć vcvarsall. bat do ustawiania zmiennych środowiskowych

- Otwórz okno wiersza polecenia na komputerze kompilacji i uruchom program% Files%\Microsoft programu Visual Studio 11.0 \ VC\vcvarsall.bat. Można użyć argumentu wiersza polecenia, aby określić zestaw narzędzi, który ma być używany — x86, natywny x64 lub x64 cross-kompilator. Jeśli nie określisz argumentu wiersza polecenia, zostanie użyty zestaw narzędzi x86.

     W tej tabeli opisano obsługiwane argumenty dla vcvarsall. bat:

    |Vcvarsall. bat — argument|Compiler|Architektura komputera kompilacji|Architektura danych wyjściowych kompilacji|
    |----------------------------|--------------|---------------------------------|-------------------------------|
    |x86 (wartość domyślna)|32 — bit natywny|x86, x64|x86|
    |x86_amd64|64 krzyżowe|x86, x64|X64|
    |amd64|Procesor x64|X64|X64|

     Jeśli vcvarsall. bat zostanie uruchomiony pomyślnie — to znaczy, że żaden komunikat o błędzie nie jest wyświetlany — można pominąć następny krok i kontynuować [instalację zestawów MSBuild w globalnej pamięci podręcznej zestawów (GAC) w sekcji Kompilacja komputera](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) tego dokumentu.

#### <a name="to-manually-set-environment-variables"></a>Aby ręcznie ustawić zmienne środowiskowe

1. Aby ręcznie skonfigurować środowisko wiersza polecenia, należy dodać tę ścieżkę do zmiennej środowiskowej PATH:

   - % Program Files%\Microsoft Visual Studio 11.0 \ Common7\IDE

2. Opcjonalnie można również dodać następujące ścieżki do zmiennej PATH, aby ułatwić korzystanie z programu MSBuild do kompilowania rozwiązań.

    Jeśli chcesz użyć natywnego 32-bitowego programu MSBuild, Dodaj te ścieżki do zmiennej PATH:

   - Narzędzia% Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0

   - %windir%\Microsoft.NET\Framework\v4.0.30319

     Jeśli chcesz użyć natywnego 64-bitowego programu MSBuild, Dodaj te ścieżki do zmiennej PATH:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="InstallingMSBuildToGAC"></a>Instalowanie zestawów MSBuild w globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji
 Program MSBuild wymaga zainstalowania dodatkowych zestawów w pamięci GAC na komputerze kompilacji.

#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Aby skopiować zestawy z komputera hosta i zainstalować je na komputerze kompilacji

1. Skopiuj następujące zestawy z komputera hosta do komputera kompilacji. Ponieważ zostaną one zainstalowane w pamięci podręcznej GAC, nie ma znaczenia, gdzie są umieszczane na komputerze kompilacji.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0 \ Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Aby zainstalować zestawy w pamięci podręcznej GAC, zlokalizuj Gacutil. exe na komputerze kompilacji — zwykle znajduje się w folderze%ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4,0 Tools \\. Jeśli nie możesz znaleźć tego folderu, powtórz czynności opisane w sekcji [Kopiowanie plików z komputera hosta do komputera kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) w tym instruktażu.

     Otwórz okno wiersza polecenia z uprawnieniami administracyjnymi i Uruchom to polecenie dla każdego pliku:

     **Gacutil-i \<file >**

    > [!NOTE]
    > Może być wymagany ponowny rozruch zestawu, aby można było w pełni zainstalować do pamięci GAC.

## <a name="BuildingProjects"></a>Kompilowanie projektów
 Możesz użyć Team Foundation Build, aby skompilować [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projekty i rozwiązania, lub możesz skompilować je w wierszu polecenia. Gdy używasz Team Foundation Build do kompilowania projektów, wywoła plik wykonywalny MSBuild, który odpowiada architekturze systemu.  W wierszu polecenia można użyć 32-bitowej wersji programu MSBuild lub 64-bitowego programu MSBuild i można wybrać architekturę MSBuild, ustawiając zmienną środowiskową PATH lub bezpośrednio wywołując plik wykonywalny specyficzny dla architektury.

 Aby użyć programu MSBuild. exe w wierszu polecenia, uruchom następujące polecenie, w którym *rozwiązanie. sln* jest symbolem zastępczym dla nazwy rozwiązania.

 Rozwiązanie **MSBuild** *. sln*

 Aby uzyskać więcej informacji o sposobach korzystania z programu MSBuild w wierszu polecenia, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Aby tworzyć projekty [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], należy użyć zestawu narzędzi platformy "v110". Jeśli nie chcesz edytować plików projektu [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], możesz ustawić zestaw narzędzi platformy przy użyciu tego argumentu wiersza polecenia:
>
> *rozwiązanie MSBuild. sln* **/p: PlatformToolset = v110**

## <a name="CreatingForSourceControl"></a>Tworzenie środowiska kompilacji tak, aby można je było zaewidencjonować do kontroli źródła
 Można utworzyć środowisko kompilacji, które można wdrożyć na różnych komputerach i nie wymaga plików GAC'ing ani modyfikować ustawień rejestru. Poniższe kroki są tylko jednym ze sposobów, aby to zrobić. Dostosuj te kroki do unikatowych cech środowiska kompilacji.

> [!NOTE]
> Należy wyłączyć Kompilowanie przyrostowe, aby program śledząc. exe nie zgłosi błędu podczas kompilacji. Aby wyłączyć Kompilowanie przyrostowe, ustaw ten parametr kompilacji:
>
> *rozwiązanie MSBuild. sln* **/p: TrackFileAccess = false**

#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Aby utworzyć środowisko kompilacji, które można sprawdzić w kontroli źródła

1. Utwórz katalog "magazyn" na komputerze-hoście.

     Te kroki odnoszą się do katalogu jako% magazyn%.

2. Skopiuj katalogi i pliki zgodnie z opisem w sekcji [Kopiowanie plików z komputera hosta do komputera kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) w tym instruktażu, z tą różnicą, że wklej je w katalogu% magazyn%, który został właśnie utworzony. Na przykład skopiuj z katalogu%ProgramFiles%\Windows Kits\8.0\bin\ do%Depot%\Windows Kits\8.0\bin \\.

3. Po wklejeniu plików w% magazynie% wprowadź następujące zmiany:

    - W%Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets \\, \Microsoft.cppbuild.targets \\ i \Microsoft.CppCommon.targets \\ Zmień każde wystąpienie elementu

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         na

         AssemblyFile = "$ (VCTargetsPath11) Microsoft. Build. CppTasks. Common. v110. dll".

         Poprzednie nazewnictwo polega na GAC'ed zestawu.

    - W magazynie% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets Zmień każde wystąpienie elementu

         AssemblyName = "Microsoft. Build. CppTasks. Common. v110, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a"

         na

         AssemblyFile = "$ (VCTargetsPath11) Microsoft. Build. CppTasks. Common. v110. dll".

4. Utwórz plik. props — na przykład partner. AutoImports. props — i umieść go w katalogu głównym folderu, który zawiera projekty. Ten plik służy do ustawiania zmiennych, które są używane przez program MSBuild do znajdowania różnych zasobów. Jeśli zmienne nie są ustawiane przez ten plik, są ustawiane przez inne. elementy props i pliki. targets, które opierają się na wartościach rejestru. Ponieważ nie ustawiamy żadnych wartości rejestru, te zmienne byłyby puste i kompilacja nie powiedzie się. Zamiast tego należy dodać ten program do partnera. AutoImports. props:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. W każdym z plików projektu, należy dodać następujący wiersz u góry, po wierszu `<Project Default Targets…>`.

    ```
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Zmień środowisko wiersza polecenia w następujący sposób:

    - Set magazynu =*Lokalizacja katalogu magazynu utworzonego w kroku 1*

    - Ustaw ścieżkę =% Path%; *Lokalizacja programu MSBuild na komputerze*;% D epot%\Windows\System32;% D epot%\Windows\SysWOW64;% D epot%\Microsoft Visual Studio 11.0 \ Common7\IDE\

         W przypadku natywnego kompilowania 64-bitowego wskaż 64-bitowy program MSBuild.

## <a name="see-also"></a>Zobacz też
 [Przygotowywanie maszyny testowej do uruchamiania debugowania wykonywalnego](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable) [wiersza polecenia](../msbuild/msbuild-command-line-reference.md)

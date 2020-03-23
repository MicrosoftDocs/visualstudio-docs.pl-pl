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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461536"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>Przewodnik: tworzenie środowiska kompilowania na wielu komputerach

Środowisko kompilacji w organizacji można utworzyć, instalując program Visual Studio na komputerze-hoście, a następnie kopiując różne pliki i ustawienia na inny komputer, aby mógł uczestniczyć w kompilacjach. Nie trzeba instalować programu Visual Studio na innym komputerze.

Niniejszy dokument nie przyznaje praw do redystrybucji oprogramowania na zewnątrz ani do dostarczania środowisk kompilacji osobom trzecim.

> Disclaimer<br /><br /> Niniejszy dokument jest dostarczany na zasadzie "tak, jak jest". Chociaż przetestowaliśmy opisane kroki, nie jesteśmy w stanie wyczerpująco przetestować każdej konfiguracji. Postaramy się, aby dokument był aktualny, a wszelkie dodatkowe informacje zostały wyciągnięte. Informacje i poglądy wyrażone w tym dokumencie, w tym adresy URL i inne odniesienia do stron internetowych, mogą ulec zmianie bez powiadomienia. Firma Microsoft nie udziela żadnych gwarancji, jawnych lub domniemanych, w odniesieniu do informacji podanych w tym miejscu. Użytkownik ponosi ryzyko związane z ich użyciem.<br /><br /> Ten dokument nie zapewnia żadnych praw do własności intelektualnej w jakimkolwiek produkcie firmy Microsoft. Możesz skopiować ten dokument i używać go do wewnętrznych celów referencyjnych.<br /><br /> Użytkownik nie ma obowiązku przekazywania firmie Microsoft żadnych sugestii, komentarzy lub innych opinii ("Opinie") dotyczących tego dokumentu. Wszelkie dobrowolnie przekazane opinie mogą być jednak wykorzystywane w Produktach firmy Microsoft i powiązanych specyfikacjach lub innej dokumentacji (łącznie "Oferty Microsoft"), na które z kolei mogą polegać inne strony trzecie w celu opracowywania własnych produktów. W związku z tym, jeśli użytkownik przekaże firmie Microsoft opinię na temat jakiejkolwiek wersji niniejszego dokumentu lub Ofert Microsoft, do których mają one zastosowanie, użytkownik wyraża zgodę na: (a) Firma Microsoft może swobodnie wykorzystywać, reprodukować, licencjonować, rozpowszechniać i w inny sposób komercjalizować opinie użytkownika w dowolnej firmie Microsoft Ofiarowanie; (b) Użytkownik udziela również osobom trzecim, bez opłat, tylko tych praw patentowych niezbędnych do umożliwienia innym produktom korzystania z określonych części Produktu Microsoft lub interfejsu z określonymi częściami Produktu Microsoft, które zawierają Opinie użytkownika; oraz (c) Użytkownik nie będzie udzielał firmie Microsoft żadnych opinii (i), że ma powody sądzić, że podlega wszelkim patentom, prawom autorskim lub innym roszczeniu własności intelektualnej lub praw osobom trzecim; lub (ii) z zastrzeżeniem postanowień licencyjnych, które mają na celu wymaganie, aby jakakolwiek Oferta Microsoft zawierająca lub uzyskana z takich Opinii lub innej własności intelektualnej firmy Microsoft była licencjonowana lub w inny sposób udostępniana osobom trzecim.

Ten instruktaż został zweryfikowany w następujących systemach operacyjnych:

- Windows 8 (x86 i x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Po wykonaniu kroków w tym instruktażu można użyć środowiska wielokomputerowego do tworzenia tego rodzaju aplikacji:

- Aplikacje klasyczne języka C++ korzystające z pakietu Windows 8 SDK
- Aplikacje klasyczne języka Visual Basic lub C#przeznaczone dla programu .NET Framework 4.5

Środowiska wielokomputerowego nie można używać do tworzenia tego rodzaju aplikacji:

- aplikacje platformy uniwersalnej systemu Windows. Aby utworzyć aplikacje platformy uniwersalnej systemu Windows, należy zainstalować program Visual Studio na komputerze kompilacji.
- Aplikacje klasyczne przeznaczone dla platformy .NET Framework 4 lub wcześniejszych. Aby utworzyć tego rodzaju aplikacje, należy zainstalować visual studio lub .NET reference assemblies and Tools (z zestawu Windows 7.1 SDK) na komputerze kompilacji.

## <a name="prerequisites"></a>Wymagania wstępne

Visual Studio z zainstalowanym obciążeniem **dewelopera pulpitu .NET.**

## <a name="install-software-on-the-computers"></a>Instalowanie oprogramowania na komputerach

Najpierw skonfiguruj komputer-host, a następnie skonfiguruj komputer kompilacji.

Instalując program Visual Studio na komputerze-hoście, można utworzyć pliki i ustawienia, które zostaną skopiowane do komputera kompilacji później. Program Visual Studio można zainstalować na komputerze x86 lub x64, ale architektura komputera kompilacji musi być zgodna z architekturą komputera-hosta.

1. Na komputerze-hoście zainstaluj program Visual Studio.

2. Na komputerze kompilacji zainstaluj program .NET Framework 4.5 lub nowszy. Aby sprawdzić, czy jest zainstalowany, sprawdź, czy wpis **Wersja** w podkluczu rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** ma wartość **4,5** lub wyższą.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Kopiowanie plików z komputera-hosta na komputer kompilacji

Ta sekcja obejmuje kopiowanie określonych plików, kompilatorów, narzędzi kompilacji, zasobów MSBuild i ustawień rejestru z komputera-hosta do komputera kompilacji. Te instrukcje zakładają, że program Visual Studio został zainstalowany w lokalizacji domyślnej na komputerze-hoście; jeśli zainstalowano w innej lokalizacji, dostosuj odpowiednie kroki.

- Na komputerze x86 domyślną lokalizacją jest *C:\Program Files\Microsoft Visual Studio*
- Na komputerze x64 domyślną lokalizacją jest *C:\Program Files (x86)\Microsoft Visual Studio*

Należy zauważyć, że nazwa folderu *Pliki programu* zależy od zainstalowanego systemu operacyjnego. Na komputerze x86 nazwa to *Program Files*; na komputerze x64, nazwa to *Program Files (x86)*. Niezależnie od architektury systemu niniejszy przewodnik odnosi się do folderu *Pliki programu* jako *%ProgramFiles%*.

> [!NOTE]
> Na komputerze kompilacji wszystkie odpowiednie pliki muszą znajdować się na tym samym dysku. Jednak litera dysku dla tego dysku może być inna niż litera dysku dla dysku, na którym jest zainstalowany program Visual Studio na komputerze-hoście. W każdym przypadku podczas tworzenia wpisów rejestru należy uwzględnić lokalizację plików, zgodnie z opisem w dalszej części tego dokumentu.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Kopiowanie plików SDK systemu Windows na komputer kompilacji

1. Jeśli masz zainstalowany tylko pakiet Windows SDK dla systemu Windows 8, skopiuj te foldery rekursywnie z komputera-hosta na komputer kompilacji:

   - %ProgramFiles%\Zestawy systemu Windows\8.0\bin\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\Katalogi\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\DesignTime\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\include\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\Lib\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\Redist\

   - %ProgramFiles%\Zestawy systemu Windows\8.0\Odwołania\

   Jeśli masz również te inne zestawy Windows 8 ...

   - Zestaw do oceny i wdrażania systemu Microsoft Windows

   - Zestaw sterowników systemu Microsoft Windows

   - Zestaw certyfikacji sprzętu systemu Microsoft Windows

   ... mogły mieć zainstalowane pliki w *folderach %ProgramFiles%\Windows Kits\8.0* wymienionych w poprzednim kroku, a ich postanowienia licencyjne mogą nie zezwalać na prawa do budowania serwera dla tych plików. Sprawdź postanowienia licencyjne dla każdego zainstalowanego zestawu Windows, aby sprawdzić, czy pliki mogą być kopiowane na komputer kompilacji. Jeśli postanowienia licencyjne nie zezwalają na prawa do serwera kompilacji, usuń pliki z komputera kompilacji.

2. Skopiuj następujące foldery cyklicznie z komputera-hosta na komputer kompilacji:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Pliki wspólne\Moduły scalania\

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wersja>\VC\

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>edycji>\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\

    - %ProgramFiles%\Zestawy odwołań\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Zestawy odwołań\Microsoft\Framework\\. NETFramework\v4.5\

3. Skopiuj te pliki z komputera-hosta na komputer kompilacji:

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wersja>\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wersja>\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\Tools\makehm.exe

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Wersja programu\\\<Microsoft Visual \\ \<Studio>wydanie>\Common7\Tools\vsvars32.bat

4. Następujące biblioteki środowiska wykonawczego języka Visual C++ są wymagane tylko wtedy, gdy uruchamiasz dane wyjściowe kompilacji na komputerze kompilacji — na przykład w ramach automatycznych testów. Pliki zazwyczaj znajdują się w podfolderach w folderze *%ProgramFiles%\Microsoft\\\<Visual Studio \\ \<>edition>\VC\redist\x86* lub *%ProgramFiles%\Microsoft Visual\\\<Studio version>\\ \<edition>\VC\redist\x64,* w zależności od architektury systemu. W systemach x86 skopiuj pliki binarne x86 do folderu *Windows\System32.* W systemach x64 skopiuj pliki binarne x86 do folderu *Windows\SysWOW64,* a pliki binarne x64 do folderu *Windows\System32.*

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

5. Skopiuj tylko następujące pliki z folderu *Debug_NonRedist\x86* lub *Debug_NonRedist\x64* na komputer kompilacji, zgodnie z [opisem w polu Przygotowanie komputera testowego do uruchomienia pliku wykonywalnego debugowania](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). Żadne inne pliki nie mogą być kopiowane.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Tworzenie ustawień rejestru

Aby skonfigurować ustawienia dla systemu MSBuild, należy utworzyć wpisy rejestru.

1. Identyfikowanie folderu nadrzędnego dla wpisów rejestru. Wszystkie wpisy rejestru są tworzone przy tym samym kluczu nadrzędnym. Na komputerze x86 klucz nadrzędny jest **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. Na komputerze x64 klucz nadrzędny jest **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Niezależnie od architektury systemu, ten przewodnik odnosi się do klucza nadrzędnego jako %RegistryRoot%.

    > [!NOTE]
    > Jeśli architektura komputera-hosta różni się od architektury komputera kompilacji, upewnij się, że na każdym komputerze jest używany odpowiedni klucz nadrzędny. Jest to szczególnie ważne w przypadku automatyzacji procesu eksportowania.
    >
    > Ponadto jeśli używasz innej litery dysku na komputerze kompilacji niż ta, której używasz na komputerze-hoście, upewnij się, że wartości wpisów rejestru są zgodne.

2. Utwórz następujące wpisy rejestru na komputerze kompilacji. Wszystkie te wpisy są ciągami (Type == "REG_SZ" w rejestrze). Ustaw wartości tych wpisów takie same jak wartości porównywalnych wpisów na komputerze-hoście.

   - **%RegistryRoot%\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Domyślnie)**

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **Katalogi %RegistryRoot%\VisualStudio\11.0@Source**

   - <strong>%RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>%RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **%RegistryRoot%\VisualStudio\SxS\VC7@11.0**

   - **%RegistryRoot%\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Zestawy systemu Windows\ZainstalowaneRoots@KitsRoot</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>%RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   Na komputerze kompilacji x64 należy również utworzyć następujący wpis rejestru i odwołać się do komputera-hosta, aby określić sposób jego ustawienia.

   - <strong>%RegistryRoot%\MicrosoftSDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Jeśli komputer kompilacji jest x64 i chcesz użyć 64-bitowej wersji msbuild, lub jeśli używasz Team Foundation Server Build Service na komputerze x64, należy utworzyć następujące wpisy rejestru w natywnym 64-bitowym rejestrze. Zapoznaj się z komputerem-hostem, aby ustalić sposób ustawiania tych wpisów.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Ustawianie zmiennych środowiskowych na komputerze kompilacji

Aby użyć MSBuild na komputerze kompilacji, należy ustawić zmienne środowiskowe PATH. Można użyć *vcvarsall.bat,* aby ustawić zmienne, lub można ręcznie je skonfigurować.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Użyj vcvarsall.bat, aby ustawić zmienne środowiskowe

Otwórz okno **wiersza polecenia** na komputerze kompilacji i uruchom *wersję programu %Program Files%\Microsoft Visual Studio\\\<>\\ \<edycji>\VC\vcvarsall.bat*. Za pomocą argumentu wiersza polecenia można określić zestaw narzędzi, którego chcesz użyć — x86, natywny x64 lub x64 cross-compiler. Jeśli argument wiersza polecenia nie zostanie określony, zostanie użyty zestaw narzędzi x86.

W tej tabeli opisano obsługiwane argumenty *dla vcvarsall.bat*:

|Argument Vcvarsall.bat|Kompilator|Tworzenie architektury komputera|Tworzenie architektury danych wyjściowych|
| - |--------------| - | - |
|x86 (domyślnie)|32-bitowy natywny|x86, x64|x86|
|x86_amd64|x64 Krzyż|x86, x64|x64|
|amd64|X64 Natywne|x64|x64|

Jeśli *plik vcvarsall.bat* działa pomyślnie — oznacza to, że nie jest wyświetlany żaden komunikat o błędzie — można pominąć następny krok i kontynuować w [zestawach Install MSBuild do globalnej pamięci podręcznej zestawów (GAC) w](#install-msbuild-to-gac) sekcji komputer kompilacji tego dokumentu.

### <a name="manually-set-environment-variables"></a>Ręczne ustawianie zmiennych środowiskowych

1. Aby ręcznie skonfigurować środowisko wiersza polecenia, dodaj tę ścieżkę do zmiennej środowiskowej PATH:

    - %Program Files%\Microsoft\\\<Visual Studio version \\ \<>edition>\Common7\IDE

2. Opcjonalnie można również dodać następujące ścieżki do zmiennej PATH, aby ułatwić korzystanie z usługi MSBuild do tworzenia rozwiązań.

   Jeśli chcesz użyć macierzystego 32-bitowego MSBuild, dodaj te ścieżki do zmiennej PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Jeśli chcesz użyć natywnego 64-bitowego MSBuild, dodaj te ścieżki do zmiennej PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a><a name="install-msbuild-to-gac" />Instalowanie zestawów MSBuild w globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji

MSBuild wymaga niektórych dodatkowych zestawów, które mają być zainstalowane w pliku GAC na komputerze kompilacji.

1. Skopiuj następujące zestawy z komputera-hosta na komputer kompilacji. Ponieważ zostaną one zainstalowane w pliku GAC, nie ma znaczenia, gdzie można umieścić je na komputerze kompilacji.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio wersja \\ \<>wydanie>\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual\\\<Studio wersja \\ \<>wydanie>\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Aby zainstalować zestawy w pliku GAC, zlokalizuj *plik gacutil.exe* na komputerze kompilacji — zazwyczaj jest on w %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\. Jeśli nie możesz zlokalizować tego folderu, powtórz kroki opisane w sekcji [Kopiuj pliki z komputera-hosta do](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) sekcji komputer kompilacji w tym instruktażu.

     Otwórz okno **wiersza polecenia** z prawami administracyjnymi i uruchom to polecenie dla każdego pliku:

     **gacutil -i \<plik>**

    > [!NOTE]
    > Ponowne uruchomienie może być wymagane dla zestawu, aby w pełni zainstalować w pliku GAC.

## <a name="build-projects"></a>Tworzenie projektów

Za pomocą usługi Azure Pipelines można tworzyć projekty i rozwiązania programu Visual Studio lub można utworzyć je w wierszu polecenia. Korzystając z usługi Azure Pipelines do tworzenia projektów, wywołuje plik wykonywalny MSBuild, który odpowiada architekturze systemu. W wierszu polecenia można użyć 32-bitowego msbuild lub 64-bitowego msbuildu i wybrać architekturę msbuild, ustawiając zmienną środowiskową PATH lub bezpośrednio wywołując plik wykonywalny MSBuild specyficzny dla architektury.

Aby użyć *msbuild.exe* w wierszu polecenia, uruchom następujące polecenie, w którym *solution.sln* jest symbolem zastępczym dla nazwy rozwiązania.

**msbuild** *solution.sln*

Aby uzyskać więcej informacji na temat używania msbuild w wierszu polecenia, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Tworzenie środowiska kompilacji, tak aby można było je zaewidencjonować w formancie źródła

Można utworzyć środowisko kompilacji, które można wdrożyć na różnych komputerach i nie wymaga plików "GAC" lub modyfikowania ustawień rejestru. Poniższe kroki są tylko jednym ze sposobów, aby to osiągnąć. Dostosuj te kroki do unikatowych cech środowiska kompilacji.

> [!NOTE]
> Należy wyłączyć tworzenie przyrostowe, aby *tracker.exe* nie zgłaszał błędu podczas kompilacji. Aby wyłączyć tworzenie przyrostowe, ustaw ten parametr kompilacji:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Utwórz katalog *magazynu* na komputerze-hoście.

     Te kroki odnoszą się do katalogu jako %Depot%.

2. Skopiuj katalogi i pliki zgodnie z opisem w sekcji [Kopiuj pliki z komputera-hosta do](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#copy-files-from-the-host-computer-to-the-build-computer) sekcji komputer kompilacji tego przewodnika, z wyjątkiem wklejenia ich w katalogu *%Depot%,* który został właśnie utworzony. Na przykład skopiuj z *%ProgramFiles%\Windows Kits\8.0\bin* do *%Depot%\Windows Kits\8.0\bin*.

3. Po wklejeniu plików w *%Depot%* należy wprowadzić następujące zmiany:

    - W obszarze %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\, i\\\Microsoft.CppCommon.targets , zmień każde wystąpienie

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Poprzednie nazewnictwo opiera się na zgromadzeniu jest GAC'ed.

    - W obszarze %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets zmień każde wystąpienie

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Utwórz plik *.props* — na przykład *Partner.AutoImports.props*— i umieść go w katalogu głównym folderu zawierającego projekty. Ten plik służy do ustawiania zmiennych, które są używane przez MSBuild do znajdowania różnych zasobów. Jeśli zmienne nie są ustawiane przez ten plik, są one ustawiane przez inne pliki *.props* i *pliki .targets,* które opierają się na wartościach rejestru. Ponieważ nie ustawiamy żadnych wartości rejestru, te zmienne będą puste, a kompilacja zakończy się niepowodzeniem. Zamiast tego dodaj to do *strony Partner.AutoImports.props:*

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

5. W każdym z plików projektu dodaj następujący wiersz u `<Project Default Targets...>` góry, za wierszem.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

::: moniker range="vs-2017"

6. Zmień środowisko wiersza polecenia w następujący sposób:

    - Ustaw magazyn =*lokalizację katalogu magazynu utworzonego w kroku 1*

    - Ustaw ścieżkę=%ścieżkę%; *lokalizacja MSBuild na komputerze*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 15.0\Common7\IDE\

       W przypadku natywnego 64-bitowego budowania wskaż 64-bitową wersję programu MSBuild.

::: moniker-end

::: moniker range=">=vs-2019"

6. Zmień środowisko wiersza polecenia w następujący sposób:

    - Ustaw magazyn =*lokalizację katalogu magazynu utworzonego w kroku 1*

    - Ustaw ścieżkę=%ścieżkę%; *lokalizacja MSBuild na komputerze*;%D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft Visual Studio 16.0\Common7\IDE\

       W przypadku natywnego 64-bitowego budowania wskaż 64-bitową wersję programu MSBuild.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Przygotowanie maszyny testowej do uruchomienia debugowania pliku wykonywalnego](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable)
- [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md)
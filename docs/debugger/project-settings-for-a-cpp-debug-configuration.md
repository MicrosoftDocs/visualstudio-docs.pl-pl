---
title: Ustawienia projektu dla konfiguracji debugowania w języku C++
description: Skonfiguruj debugowanie języków C i C++ na stronach właściwości. W tym artykule opisano ustawienia i przedstawiono ich kategorię.
ms.custom: SEO-VS-2020
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 34dd9b82a642c9e9ec32dde383a8c2e02ac57aa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385191"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w języku C++
Ustawienia projektu dla konfiguracji debugowania w języku  C lub C++ można zmienić w oknie dialogowym Strony właściwości, zgodnie z omówieniem w artykule Jak ustawić konfiguracje [debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **oknie dialogowym Strony** właściwości.

> [!NOTE]
> Ustawienia projektu debugowania w kategorii **Właściwości konfiguracji/Debugowanie** są różne dla aplikacji platformy UWP i składników napisanych w języku C++. Zobacz [Uruchamianie sesji debugowania (VB, C#, C++ i XAML).](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

 Każde ustawienie właściwości debugowania jest automatycznie zapisywane w pliku "na użytkownika" (.vcxproj.user) rozwiązania podczas zapisywania rozwiązania.

 Określ debuger, który ma być w **debugerze** do uruchamiania pola listy, zgodnie z opisem w poniższej tabeli. Wybór będzie miał wpływ na właściwości, które są widoczne.

## <a name="configuration-properties-folder-debugging-category"></a>Folder Właściwości konfiguracji (kategoria debugowania)

| **Ustawienie** | **Opis** |
| - | - |
| **Debuger do uruchomienia** | Określa debuger do uruchomienia, z następującymi opcjami:<br /><br /> -   **Lokalny debuger systemu Windows**<br />-   **Zdalny debuger systemu Windows**<br />-   **Debuger przeglądarki internetowej**<br />-   **Debuger usługi internetowej** |
| **Polecenie** (lokalny debuger systemu Windows) | Określa polecenie uruchamiania programu, który jest debugowania na komputerze lokalnym. |
| **Zdalne polecenie** (zdalny debuger systemu Windows) | Ścieżka do .exe na komputerze zdalnym. Wprowadź ścieżkę tak samo jak na maszynie zdalnej. |
| **Argumenty polecenia** (lokalny debuger systemu Windows)<br /><br /> **Argumenty polecenia zdalnego** (zdalny debuger systemu Windows) | -Określa argumenty dla polecenia określonego wcześniej.<br /><br /> W tym polu można użyć następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje stdout do pliku.<br /><br /> >> `file`<br /> Dołącza stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe stderr (2) do tej samej lokalizacji co stdout (1).<br /><br /> 1> &2<br /> Wysyła dane wyjściowe stdout (1) do tej samej lokalizacji co stderr (2).<br /><br /> W większości przypadków te operatory mają zastosowanie tylko do aplikacji konsolowych. |
| **Katalog roboczy** | Określa katalog roboczy debugowany program względem katalogu projektu, w którym znajduje się plik EXE. Jeśli pozostawisz to pole puste, katalog roboczy będzie katalogiem projektu. W przypadku debugowania zdalnego katalog projektu znajduje się na serwerze zdalnym. |
| **Dołączanie** (lokalny debuger systemu Windows i zdalny debuger systemu Windows) | Określa, czy aplikacja ma być uruchamiana, czy dołączana. Ustawieniem domyślnym jest Nie. |
| **Nazwa serwera zdalnego** (zdalny debuger systemu Windows) | Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makro kompilacji RemoteMachine jest ustawione na wartość tej właściwości; Aby uzyskać więcej informacji, zobacz [Makra dla poleceń kompilacji i właściwości](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Połączenie** (zdalny debuger systemu Windows) | Umożliwia przełączanie między typami połączeń standardowych i bez uwierzytelniania na potrzeby debugowania zdalnego. Określ nazwę komputera zdalnego w **nazwa serwera zdalnego** pole. Typy połączeń są następujące:<br /><br /> -   **Zdalne z uwierzytelnianiem systemu Windows**<br />-   **Zdalne bez uwierzytelniania**<br /><br /> **Uwaga** Zdalne debugowanie bez uwierzytelniania może spowodować, że komputer zdalny będzie narażony na naruszenia zabezpieczeń. Tryb uwierzytelniania systemu Windows jest bezpieczniejszy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Zdalne konfigurowanie debugowania](../debugger/remote-debugging.md). |
| **Adres URL PROTOKOŁU HTTP** (debuger usługi internetowej i debuger przeglądarki internetowej) | Określa adres URL, pod którym znajduje się debugowanie projektu. |
| **Typ debugera** | Określa typ debugera, który ma być **używany:** Tylko natywne, Tylko zarządzane, Tylko procesor **GPU,** **Mieszany,** **Automatyczny** (domyślny) lub **Skrypt**.<br /><br /> -   **Tylko natywna** dotyczy niezabędnego kodu C++.<br />-   **Tylko zarządzane dotyczy** kodu uruchamianego w środowisku uruchomieniowym języka wspólnego (kod zarządzany).<br />-   **Mieszany** wywołuje debuger zarówno dla kodu zarządzanego, jak i nieza zarządzania.<br />-   **Automatycznie** określa typ debugera na podstawie informacji o kompilatorze i pliku EXE.<br />-   **Skrypt** wywołuje debuger dla skryptów.<br />-   **Tylko procesor GPU** jest C++ AMP uruchamiany na urządzeniu GPU lub w rasteryzatorze referencyjnym DirectX. Zobacz [Debugowanie kodu procesora GPU](../debugger/debugging-gpu-code.md). |
| **Środowisko** (lokalny debuger systemu Windows i zdalny debuger systemu Windows) | Określa zmienne środowiskowe dla debugego programu. Użyj standardowej składni zmiennej środowiskowej (na przykład `PATH="%SystemRoot%\..."` ). Te zmienne zastępują środowisko systemowe lub są scalane ze środowiskiem systemowym, w zależności od ustawienia **Scal środowisko.** Po kliknięciu lewym przyciskiem myszy w kolumnie ustawień zostanie wyświetlony komunikat "Edytuj...". Wybierz ten link, aby edytować zmienne środowiskowe. |
| **Środowisko scalania** (lokalny debuger systemu Windows) | Określa, czy zmienne, które są określone w **środowisku** pole zostaną scalone ze środowiskiem zdefiniowanym przez system operacyjny. Ustawieniem domyślnym jest Tak. |
| **Debugowanie SQL** (wszystkie oprócz debugera klastra MPI) | Umożliwia debugowanie procedur SQL z [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji. Ustawieniem domyślnym jest Nie. |
| **Typ akceleratora debugowania** (tylko debugowanie procesora GPU) | Określa urządzenie procesora GPU do użycia na potrzeby debugowania. Zainstalowanie sterowników urządzeń dla zgodnych urządzeń GPU spowoduje dodanie dodatkowych opcji. Ustawieniem domyślnym jest **procesor GPU — emulator oprogramowania**. |
| **Domyślne zachowanie punktu przerwania procesora GPU** (tylko debugowanie procesora GPU) | Określa, czy zdarzenie punktu przerwania powinno być wywoływane dla każdego wątku w warp SIMD. Ustawieniem domyślnym jest tylko raz podnieść zdarzenie punktu przerwania dla każdego warp. |
| **Domyślny akcelerator Amp** | Określa domyślny akcelerator AMP podczas debugowania kodu gpu. Wybierz **akcelerator oprogramowania WARP,** aby zbadać, czy problem jest spowodowany przez sprzęt, czy sterownik zamiast kodu. |
| **Katalog wdrożenia** (zdalny debuger systemu Windows) | Określa ścieżkę na komputerze zdalnym, gdzie dane wyjściowe projektu zostaną skopiowane przed uruchomieniem. Ścieżka może być udziału sieciowego na komputerze zdalnym lub ścieżka do folderu na komputerze zdalnym. Ustawienie domyślne jest puste, co oznacza, że dane wyjściowe projektu nie są kopiowane do udziału sieciowego. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru Wd **wdrażaj** w Menedżer konfiguracji dialogowym. Aby uzyskać więcej informacji, [zobacz Tworzyć i edytować konfiguracje.](../ide/how-to-create-and-edit-configurations.md) |
| **Dodatkowe pliki do wdrożenia** (zdalny debuger systemu Windows) | Jeśli właściwość Katalog wdrażania jest ustawiona, jest to rozdzielana średnikami lista dodatkowych plików do skopiowania do katalogu wdrożenia. Ustawienie domyślne jest puste, co oznacza, że żadne dodatkowe pliki nie są kopiowane do katalogu wdrożenia. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru Wd **wdrażaj** w Menedżer konfiguracji dialogowym. Aby uzyskać więcej informacji, [zobacz Tworzyć i edytować konfiguracje.](../ide/how-to-create-and-edit-configurations.md) |
| **Wdrażanie Visual C++ środowiska uruchomieniowego debugowania** (zdalny debuger systemu Windows) | Jeśli właściwość Deployment Directory jest ustawiona, określa, czy Visual C++ środowiska uruchomieniowego debugowania dla bieżącej platformy powinny być kopiowane do udziału sieciowego. Ustawieniem domyślnym jest Tak. |

## <a name="cc-folder-general-category"></a>Folder C/C++ (kategoria ogólna)

|Ustawienie|Opis|
|-------------|-----------------|
|**Format informacji debugowania** ([/Z7, /Zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Określa typ informacji debugowania, które mają zostać utworzone dla projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym z funkcją Edytuj i kontynuuj. Aby uzyskać więcej informacji, zobacz [/Z7, /Zd, /Zi, /ZI (Format informacji debugowania).](/cpp/build/reference/z7-zi-zi-debug-information-format)|

## <a name="cc-folder-optimization-category"></a>Folder C/C++ (kategoria optymalizacji)

|Ustawienie|Opis|
|-------------|-----------------|
|**Optymalizacja**|Określa, czy kompilator powinien zoptymalizować kod, który tworzy. Optymalizacja zmienia wykonywany kod. Zoptymalizowany kod nie pasuje już do kodu źródłowego, co utrudnia debugowanie.<br /><br /> Opcja domyślna (**Wyłączone (/0d)**) pomija optymalizację. Możesz programować z pominięciem optymalizacji, a następnie włączyć ją podczas tworzenia produkcyjnej wersji kodu.|

## <a name="linker-folder-debugging-category"></a>Folder linkera (kategoria debugowania)

|Ustawienie|Opis|
|-------------|-----------------|
|**Generowanie informacji o debugowaniu** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Informuje program do dołączania informacji debugowania, który będzie miał format określony przez [/Z7, /Zd, Zi lub /ZI.](/cpp/build/reference/z7-zi-zi-debug-information-format)|
|**Generowanie pliku bazy danych programu** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|W tym polu określ nazwę pliku bazy danych programu (PDB). Należy wybrać opcję ZI lub /Zi w formacie informacji debugowania.|
|**Strip Private Symbols** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|Określ nazwę pliku PDB w tym polu, jeśli nie chcesz uwzględniać symboli prywatnych w pliku PDB. Ta opcja tworzy drugi plik PDB podczas kompilowania obrazu programu przy użyciu dowolnej opcji kompilatora lub linkera, które generują plik PDB, takich jak /DEBUG, /Z7, /Zd. Lub /Zi. Ten drugi plik PDB pomija symbole, których nie chcesz dostarczać klientom. Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (Usuwania symboli prywatnych)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Generowanie pliku mapy** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Nakazuje programowi linkerowi wygenerowanie pliku mapy podczas łączenia. Ustawieniem domyślnym jest Nie. Aby uzyskać więcej informacji, zobacz [/MAP (Generuj plik Mapfile).](/cpp/build/reference/map-generate-mapfile)|
|**Mapowanie nazwy pliku** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*name*)|Jeśli wybierzesz opcję Generuj plik mapy, w tym polu możesz określić plik mapy. Aby uzyskać więcej informacji, zobacz [/MAP (Generuj plik Mapfile).](/cpp/build/reference/map-generate-mapfile)|
|**Map Exports** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Zawiera wyeksportowane funkcje w pliku mapy. Ustawieniem domyślnym jest Nie. Aby uzyskać więcej informacji, zobacz [/MAPINFO (Dołącz informacje do Mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Zestaw debugowalny** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Określa ustawienia dla opcji Linker /ASSEMBLYDEBUG. Możliwe wartości:<br /><br /> -   **Brak atrybutu, który można debugować, nie został emitowany.**<br />-   **Śledzenie środowiska uruchomieniowego i wyłączanie optymalizacji (/ASSEMBLYDEBUG)**. Jest to ustawienie domyślne.<br />-   **Brak śledzenia środowiska uruchomieniowego i włączanie optymalizacji (/ASSEMBLYDEBUG:DISABLE)**.<br />-   **\<inherit from parent or project defaults>**.<br />- Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute).](/cpp/build/reference/assemblydebug-add-debuggableattribute)|

 Te ustawienia można zmienić w folderze Właściwości konfiguracji (kategoria debugowania) programowo przy użyciu interfejsu Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Inne ustawienia projektu

Aby można było debugować typy projektów, takie jak biblioteki statyczne i biblioteki DLL, Visual Studio projektu musi być w stanie znaleźć poprawne pliki. Gdy kod źródłowy jest dostępny, możesz dodać biblioteki statyczne i biblioteki DLL jako oddzielne projekty do tego samego rozwiązania, aby ułatwić debugowanie. Aby uzyskać informacje na temat tworzenia tych typów projektów, zobacz [Creating and using a Dynamic Link Library (DLL) (Tworzenie](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) i używanie biblioteki DLL) i Creating a using a static library (Tworzenie [biblioteki statycznej).](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp) Przy dostępnym kodzie źródłowym można również utworzyć nowy projekt Visual Studio wybierając pozycję **File** New Project From Existing Code (Nowy projekt pliku  >    >  **z istniejącego kodu).**

Aby debugować biblioteki DLL, które znajdują się poza projektem, zobacz [Debugowanie projektów DLL.](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal) Jeśli musisz debugować własny projekt DLL, ale nie masz dostępu do projektu dla aplikacji wywołującej, zobacz How to debug from a DLL project (Jak debugować z [projektu DLL).](../debugger/how-to-debug-from-a-dll-project.md)

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Tworzenie projektów w języku C++ i zarządzanie nimi](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Typowe makra dla właściwości i poleceń kompilacji](/cpp/ide/common-macros-for-build-commands-and-properties)
---
title: Ustawienia projektu dla konfiguracji debugowania języka C++
description: Skonfiguruj debugowanie C i C++ na stronach właściwości. W tym artykule opisano ustawienia i podano ich kategorię.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6130b49beecb3411c275fc5d2005b7aabee262fd
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975293"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w języku C++
Ustawienia projektu dla konfiguracji debugowania C lub C++ można zmienić w oknie dialogowym **strony właściwości** , zgodnie z opisem w temacie [How to: Set Debug and Release](../debugger/how-to-set-debug-and-release-configurations.md)Configurations. W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie dialogowym **strony właściwości** .

> [!NOTE]
> Ustawienia projektu debugowania w kategorii **Właściwości/debugowanie** są różne dla aplikacji platformy UWP oraz dla składników, które są zapisywane w języku C++. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

 Każde ustawienie właściwości debugowania jest automatycznie zapisywane i zapisywane w pliku "użytkownika" (. vcxproj. user) dla rozwiązania podczas zapisywania rozwiązania.

 Określ, który debuger ma być używany w polu listy **debuger do uruchomienia** , zgodnie z opisem w poniższej tabeli. Wybór będzie mieć wpływ na to, które właściwości są widoczne.

## <a name="configuration-properties-folder-debugging-category"></a>Folder właściwości konfiguracji (kategoria debugowania)

| **Ustawienie** | **Opis** |
| - | - |
| **Debuger do uruchomienia** | Określa debuger do uruchomienia z następującymi opcjami:<br /><br /> -   **Lokalny debuger systemu Windows**<br />-   **Zdalny debuger systemu Windows**<br />-   **Debuger przeglądarki sieci Web**<br />-   **Debuger usługi sieci Web** |
| **Polecenie** (lokalny debuger systemu Windows) | Określa polecenie uruchamiania programu, który jest debugowany na komputerze lokalnym. |
| **Polecenie zdalne** (Zdalny debuger systemu Windows) | Ścieżka pliku exe na komputerze zdalnym. Wprowadź ścieżkę tak samo jak na maszynie zdalnej. |
| **Argumenty polecenia** (lokalny debuger systemu Windows)<br /><br /> **Argumenty polecenia zdalnego** (Zdalny debuger systemu Windows) | -Określa argumenty dla polecenia określonego wcześniej.<br /><br /> W tym polu można użyć następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje stdout do pliku.<br /><br /> >> `file`<br /> Dołącza stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe stderr (2) do tej samej lokalizacji co stdout (1).<br /><br /> 1> &2<br /> Wysyła dane wyjściowe stdout (1) do tej samej lokalizacji co stderr (2).<br /><br /> W większości przypadków te operatory mają zastosowanie tylko do aplikacji konsoli. |
| **Katalog roboczy** | Określa katalog roboczy debugowanego programu, względem katalogu projektu, w którym znajduje się plik EXE. Jeśli pozostawisz to pole puste, katalog roboczy jest katalogiem projektu. W przypadku zdalnego debugowania katalog projektu znajduje się na serwerze zdalnym. |
| **Dołącz** (lokalny debuger systemu Windows i zdalny debuger systemu Windows) | Określa, czy uruchomić lub dołączyć do aplikacji. Ustawienie domyślne to nie. |
| **Nazwa serwera zdalnego** (Zdalny debuger systemu Windows) | Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makro kompilacji RemoteMachine jest ustawione na wartość tej właściwości. Aby uzyskać więcej informacji, zobacz [makra dla poleceń i właściwości kompilacji](/cpp/build/reference/common-macros-for-build-commands-and-properties). |
| **Połączenie** (Zdalny debuger systemu Windows) | Pozwala na przełączanie się między typami połączeń standardowy i bez uwierzytelniania dla zdalnego debugowania. Określ nazwę komputera zdalnego w polu **Nazwa serwera zdalnego** . Dostępne są następujące typy połączeń:<br /><br /> -   **Zdalne z uwierzytelnianiem systemu Windows**<br />-   **Zdalne bez uwierzytelniania**<br /><br /> **Uwaga** Debugowanie zdalne bez uwierzytelniania może spowodować naruszenie zabezpieczeń komputera zdalnego. Tryb uwierzytelniania systemu Windows jest bezpieczniejszy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Instalator zdalnego debugowania](../debugger/remote-debugging.md). |
| **Adres URL http** (debuger usługi sieci Web i debuger przeglądarki sieci Web) | Określa adres URL, pod którym znajduje się debugowany projekt. |
| **Typ debugera** | Określa typ debugera do użycia: **tylko natywny**, tylko **zarządzany**, **tylko procesor GPU**, **mieszany**, **Auto(domyślny** ) lub **skrypt**.<br /><br /> -   **Tylko natywny** dla niezarządzanego kodu C++.<br />-   **Tylko zarządzany** jest dla kodu, który jest uruchamiany w środowisku uruchomieniowym języka wspólnego (kod zarządzany).<br />-   **Mieszane** wywołuje debugery dla kodu zarządzanego i niezarządzanego.<br />-   **Funkcja** autookreśla typ debugera na podstawie informacji kompilatora i exe.<br />-   **Skrypt** wywołuje debuger dla skryptów.<br />-   **Procesor GPU dotyczy tylko** kodu C++ amp, który jest uruchamiany na urządzeniu GPU lub w rasteryzatora referencyjnym DirectX. Zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md). |
| **Środowisko** (lokalny debuger systemu Windows i zdalny debuger systemu Windows) | Określa zmienne środowiskowe dla debugowanego programu. Użyj standardowej składni zmiennej środowiskowej (na przykład `PATH="%SystemRoot%\..."` ). Te zmienne zastępują środowisko systemowe lub są scalone ze środowiskiem systemowym, w zależności od ustawienia **środowisko scalone** . Po kliknięciu lewym przyciskiem myszy w kolumnie Ustawienia zostanie wyświetlony komunikat "Edytuj...". Wybierz ten link, aby edytować zmienne środowiskowe. |
| **Scal środowisko** (lokalny debuger systemu Windows) | Określa, czy zmienne określone w polu **środowisko** zostaną scalone ze środowiskiem zdefiniowanym przez system operacyjny. Ustawieniem domyślnym jest tak. |
| **Debugowanie SQL** (wszystkie oprócz debuger klastra MPI) | Umożliwia debugowanie procedur SQL z poziomu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji. Ustawienie domyślne to nie. |
| **Typ akceleratora debugowania** (tylko debugowanie GPU) | Określa urządzenie GPU do użycia na potrzeby debugowania. Zainstalowanie sterowników urządzeń zgodnych z urządzeniami GPU spowoduje dodanie dodatkowych opcji. Ustawieniem domyślnym jest **procesor GPU — emulator oprogramowania**. |
| **Domyślne zachowanie punktu przerwania procesora GPU** (tylko debugowanie GPU) | Określa, czy zdarzenie punktu przerwania powinno być wywoływane dla każdego wątku w wypaczeniu SIMD. Ustawieniem domyślnym jest podnoszenie zdarzenia punktu przerwania tylko raz na osnowę. |
| **Akcelerator domyślny amp** | Określa domyślny akcelerator AMP podczas debugowania kodu GPU. Wybierz pozycję **Wypaczanie akceleratora oprogramowania** , aby sprawdzić, czy problem jest spowodowany przez sprzęt, czy sterownik zamiast kodu. |
| **Katalog wdrożenia** (Zdalny debuger systemu Windows) | Określa ścieżkę na komputerze zdalnym, na którym zostaną skopiowane dane wyjściowe projektu przed uruchomieniem. Ścieżka może być udziałem sieciowym na komputerze zdalnym lub może być ścieżką do folderu na komputerze zdalnym. Ustawienie domyślne jest puste, co oznacza, że dane wyjściowe projektu nie są kopiowane do udziału sieciowego. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru **Wdróż** w oknie dialogowym Configuration Manager. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Dodatkowe pliki do wdrożenia** (Zdalny debuger systemu Windows) | Jeśli ustawiono właściwość katalogu wdrażania, jest to rozdzielana średnikami lista dodatkowych plików do skopiowania do katalogu wdrożenia. Ustawienie domyślne jest puste, co oznacza, że żadne dodatkowe pliki nie są kopiowane do katalogu wdrożenia. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru **Wdróż** w oknie dialogowym Configuration Manager. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md). |
| **Wdróż biblioteki środowiska uruchomieniowego debugowania Visual C++** (Zdalny debuger systemu Windows) | Jeśli ustawiono właściwość katalogu wdrażania, określa, czy Visual C++ biblioteki środowiska uruchomieniowego debugowania dla bieżącej platformy powinny zostać skopiowane do udziału sieciowego. Ustawieniem domyślnym jest tak. |

## <a name="cc-folder-general-category"></a>Folder C/C++ (kategoria ogólna)

|Ustawienie|Opis|
|-------------|-----------------|
|**Format informacji o debugowaniu** ([/Z7,/ZD, Zi,/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format))|Określa typ informacji o debugowaniu, które mają zostać utworzone dla projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym z opcją Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [/Z7,/ZD,/Zi,/ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format).|

## <a name="cc-folder-optimization-category"></a>Folder C/C++ (kategoria optymalizacji)

|Ustawienie|Opis|
|-------------|-----------------|
|**Optymalizacja**|Określa, czy kompilator powinien zoptymalizować tworzony przez niego kod. Optymalizacja zmienia kod, który jest wykonywany. Zoptymalizowany kod nie jest już zgodny z kodem źródłowym, co sprawia, że debugowanie jest trudniejsze.<br /><br /> Opcja domyślna (**wyłączona (/0D)**) pomija optymalizację. Można opracowywać z pominięciem optymalizacji, a następnie włączyć ją podczas tworzenia wersji produkcyjnej kodu.|

## <a name="linker-folder-debugging-category"></a>Folder konsolidatora (kategoria debugowania)

|Ustawienie|Opis|
|-------------|-----------------|
|**Generuj informacje o debugowaniu** ([/Debug](/cpp/build/reference/debug-generate-debug-info))|Nakazuje konsolidatorowi dołączenie informacji debugowania, które będą miały format określony przez [/Z7,/ZD, Zi lub/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format).|
|**Generuj plik bazy danych programu** ([/PDB: Nazwa](/cpp/build/reference/pdb-use-program-database))|W tym polu Określ nazwę pliku bazy danych programu (PDB). Dla formatu informacji debugowania należy wybrać ZI lub/Zi.|
|**Symbole prywatne z paskiem** ([/PDBSTRIPPED: filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|W tym polu Określ nazwę pliku PDB, jeśli nie chcesz umieszczać prywatnych symboli w pliku PDB. Ta opcja tworzy drugi plik PDB podczas kompilowania obrazu programu przy użyciu dowolnego z opcji kompilatora lub konsolidatora, które generują plik PDB, na przykład/DEBUG,/Z7,/ZD. Lub/Zi. Ten drugi plik PDB pomija symbole, które nie powinny być wysyłane do klientów. Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (symbole prywatne)](/cpp/build/reference/pdbstripped-strip-private-symbols).|
|**Generuj plik mapy** ([/map](/cpp/build/reference/map-generate-mapfile))|Nakazuje konsolidatorowi wygenerowanie pliku mapy podczas konsolidacji. Ustawienie domyślne to nie. Aby uzyskać więcej informacji, zobacz [/map (Generate Mapfile)](/cpp/build/reference/map-generate-mapfile).|
|**Nazwa pliku mapy** ([/map:](/cpp/build/reference/map-generate-mapfile)*Nazwa*)|Jeśli wybierzesz opcję Generuj plik mapy, możesz określić plik mapy w tym polu. Aby uzyskać więcej informacji, zobacz [/map (Generate Mapfile)](/cpp/build/reference/map-generate-mapfile).|
|**Eksporty mapy** ([/MapInfo: exports](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Zawiera wyeksportowane funkcje w pliku mapy. Ustawienie domyślne to nie. Aby uzyskać więcej informacji, zobacz [/MapInfo (Dołącz informacje w mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|
|**Zestaw możliwością debugowania** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Określa ustawienia dla opcji konsolidatora/ASSEMBLYDEBUG. Możliwe wartości:<br /><br /> -   **Nie wyemitowano atrybutu możliwością debugowania**.<br />-   **Śledzenie środowiska uruchomieniowego i wyłączanie optymalizacji (/ASSEMBLYDEBUG)**. Jest to ustawienie domyślne,<br />-   **Brak śledzenia środowiska uruchomieniowego i Włącz optymalizacje (/ASSEMBLYDEBUG: Disable)**.<br />-   **\<inherit from parent or project defaults>**.<br />-Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|

 Możesz zmienić te ustawienia w folderze właściwości konfiguracji (kategoria debugowania) programowo przy użyciu interfejsu Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Inne ustawienia projektu

Aby debugować typy projektów, takie jak biblioteki statyczne i biblioteki DLL, projekt programu Visual Studio musi być w stanie znaleźć odpowiednie pliki. Gdy kod źródłowy jest dostępny, można dodać biblioteki statyczne i biblioteki DLL jako oddzielne projekty do tego samego rozwiązania, aby ułatwić debugowanie. Aby uzyskać informacje na temat tworzenia tych typów projektów, zobacz [Tworzenie i używanie biblioteki dołączanej dynamicznie (dll)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) i [Tworzenie przy użyciu biblioteki statycznej](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Za pomocą dostępnego kodu źródłowego można również utworzyć nowy projekt programu Visual Studio, wybierając pozycję **plik**  >  **Nowy**  >  **projekt z istniejącego kodu**.

Aby debugować biblioteki DLL, które są zewnętrzne dla projektu, zobacz [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Jeśli musisz debugować własny projekt DLL, ale nie masz dostępu do projektu dla aplikacji wywołującej, zobacz [jak debugować z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)
- [Tworzenie projektów C++ i zarządzanie nimi](/cpp/ide/creating-and-managing-visual-cpp-projects)
- [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)
- [Typowe makra dla właściwości i poleceń kompilacji](/cpp/ide/common-macros-for-build-commands-and-properties)
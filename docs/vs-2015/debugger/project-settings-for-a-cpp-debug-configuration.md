---
title: Ustawienia projektu dla konfiguracji debugowania języka C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca9ff0678ba2c7abafa0d988efa09437ccd27dca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687560"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia projektu dla konfiguracji debugowania C lub Visual C++ można zmienić w oknie dialogowym **strony właściwości** , zgodnie z opisem w temacie [How to: Set Debug and Release](../debugger/how-to-set-debug-and-release-configurations.md)Configurations. W poniższych tabelach przedstawiono, gdzie znaleźć ustawienia związane z debugerem w oknie dialogowym **strony właściwości** .  
  
> [!WARNING]
> Ustawienia projektu debugowania w kategorii **Właściwości/debugowanie debugowania** dla aplikacji ze sklepu Windows i składników, które są zapisywane w języku C++, różnią się. Zobacz [Rozpoczynanie sesji debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) w centrum deweloperów systemu Windows.  
  
 Określ debuger do użycia w polu listy **debuger do uruchomienia** . Wybór będzie mieć wpływ na to, które właściwości są widoczne.  
  
 Każde ustawienie właściwości debugowania jest automatycznie zapisywane i zapisywane w pliku "użytkownika" (. vcxproj. user) dla rozwiązania przy każdym zapisaniu rozwiązania.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Folder właściwości konfiguracji (kategoria debugowania)  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Debuger do uruchomienia**|Określa debuger do uruchomienia z następującymi opcjami:<br /><br /> -   **Lokalny debuger systemu Windows**<br />-   **Zdalny debuger systemu Windows**<br />-   **Debuger przeglądarki sieci Web**<br />-   **Debuger usługi sieci Web**|  
|**Polecenie** (lokalny debuger systemu Windows)|Określa polecenie uruchamiania programu, który jest debugowany na komputerze lokalnym.|  
|**Polecenie zdalne** (Zdalny debuger systemu Windows)|Ścieżka pliku exe na komputerze zdalnym. Wprowadź ścieżkę tak samo jak na maszynie zdalnej.|  
|**Argumenty polecenia** (lokalny debuger systemu Windows i zdalny debuger systemu Windows)|-Określa argumenty dla polecenia określonego wcześniej.<br /><br /> W tym polu można użyć następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje stdout do pliku.<br /><br /> >> `file`<br /> Dołącza stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe stderr (2) do tej samej lokalizacji co stdout (1).<br /><br /> 1> &2<br /> Wysyła dane wyjściowe stdout (1) do tej samej lokalizacji co stderr (2).<br /><br /> W większości przypadków te operatory mają zastosowanie tylko do aplikacji konsoli.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu, względem katalogu projektu, w którym znajduje się plik EXE. Jeśli pozostawisz to pole puste, katalog roboczy jest katalogiem projektu. W przypadku zdalnego debugowania katalog projektu będzie na serwerze zdalnym.|  
|**Dołącz** (lokalny debuger systemu Windows i zdalny debuger systemu Windows)|Określa, czy uruchomić lub dołączyć do aplikacji. Ustawienie domyślne to nie.|  
|**Nazwa serwera zdalnego** (Zdalny debuger systemu Windows)|Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makro kompilacji RemoteMachine jest ustawione na wartość tej właściwości. Aby uzyskać więcej informacji, zobacz [makra dla poleceń i właściwości kompilacji](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Połączenie** (Zdalny debuger systemu Windows)|Pozwala na przełączanie się między typami połączeń standardowy i bez uwierzytelniania dla zdalnego debugowania. Określ nazwę komputera zdalnego w polu **Nazwa serwera zdalnego** . Dostępne są następujące typy połączeń:<br /><br /> -   **Zdalne z uwierzytelnianiem systemu Windows**<br />-   **Zdalne bez uwierzytelniania (tylko natywne)**<br /><br /> **Uwaga** Debugowanie zdalne bez uwierzytelniania może spowodować naruszenie zabezpieczeń komputera zdalnego. Tryb uwierzytelniania systemu Windows jest bezpieczniejszy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Instalator zdalnego debugowania](../debugger/remote-debugging.md).|  
|**Adres URL http** (debuger usługi sieci Web i debuger przeglądarki sieci Web)|Określa adres URL, pod którym znajduje się debugowany projekt.|  
|**Typ debugera**|Określa typ debugera do użycia: **tylko natywny**, tylko **zarządzany**, **tylko procesor GPU**, **mieszany**, **Auto(domyślny** ) lub **skrypt**.<br /><br /> -   **Tylko natywny** dla niezarządzanego kodu C++.<br />-   **Tylko zarządzany** jest dla kodu, który jest uruchamiany w środowisku uruchomieniowym języka wspólnego (kod zarządzany).<br />-   **Mieszane** wywołuje debugery dla kodu zarządzanego i niezarządzanego.<br />-   **Funkcja** autookreśla typ debugera na podstawie informacji kompilatora i exe.<br />-   **Skrypt** wywołuje debuger dla skryptów.<br />-   **Procesor GPU dotyczy tylko** kodu C++ amp, który jest uruchamiany na urządzeniu GPU lub w rasteryzatora referencyjnym DirectX. Zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md).|  
|**Środowisko** (lokalny debuger systemu Windows)|Określa zmienne środowiskowe dla debugowanego programu. Użyj standardowej składni zmiennej środowiskowej (na przykład `PATH="%SystemRoot%\..."` ). Te zmienne zastępują środowisko systemowe lub są scalone ze środowiskiem systemowym, w zależności od ustawienia **środowisko scalone** . Po kliknięciu w kolumnie Ustawienia zostanie wybrana wartość "Edytuj..." się. Kliknij ten link, aby edytować zmienne środowiskowe.|  
|**Scal środowisko** (lokalny debuger systemu Windows)|Określa, czy zmienne określone w polu **środowisko** zostaną scalone ze środowiskiem zdefiniowanym przez system operacyjny. Ustawieniem domyślnym jest tak.|  
|**Debugowanie SQL** (wszystkie oprócz debuger klastra MPI)|Umożliwia debugowanie procedur SQL z poziomu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikacji. Ustawienie domyślne to nie.|  
|**Typ akceleratora debugowania** (tylko debugowanie GPU)|Określa urządzenie GPU do użycia na potrzeby debugowania. Zainstalowanie sterowników urządzeń zgodnych z urządzeniami GPU spowoduje dodanie dodatkowych opcji. Ustawieniem domyślnym jest "GPU-emulator oprogramowania".|  
|**Domyślne zachowanie punktu przerwania procesora GPU** (tylko debugowanie GPU)|Określa, czy zdarzenie punktu przerwania powinno być wywoływane dla każdego wątku w wypaczeniu SIMD. Ustawieniem domyślnym jest podnoszenie zdarzenia punktu przerwania tylko raz na osnowę.|  
|**Akcelerator domyślny amp** (tylko debugowanie GPU)|Określa domyślny akcelerator AMP podczas debugowania kodu GPU. Wybierz pozycję **Wypaczanie akceleratora oprogramowania** , aby sprawdzić, czy problem jest spowodowany przez sprzęt, czy sterownik zamiast kodu.|  
|**Katalog wdrożenia** (Zdalny debuger systemu Windows)|Określa ścieżkę na komputerze zdalnym, na którym zostaną skopiowane dane wyjściowe projektu przed uruchomieniem. Ścieżka może być udziałem sieciowym na komputerze zdalnym lub może być ścieżką do folderu na komputerze zdalnym. Ustawienie domyślne jest puste, co oznacza, że dane wyjściowe projektu nie są kopiowane do udziału sieciowego. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru **Wdróż** w oknie dialogowym Configuration Manager. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Dodatkowe pliki do wdrożenia** (Zdalny debuger systemu Windows)|Jeśli ustawiono właściwość katalogu wdrażania, jest to rozdzielana średnikami lista dodatkowych plików do skopiowania do katalogu wdrożenia. Ustawienie domyślne jest puste, co oznacza, że żadne dodatkowe pliki nie są kopiowane do katalogu wdrożenia. Aby włączyć wdrażanie plików, należy również zaznaczyć pole wyboru **Wdróż** w oknie dialogowym Configuration Manager. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md).|  
|**Wdróż biblioteki środowiska uruchomieniowego debugowania Visual C++** (Zdalny debuger systemu Windows)|Jeśli ustawiono właściwość katalogu wdrażania, określa, czy Visual C++ biblioteki środowiska uruchomieniowego debugowania dla bieżącej platformy powinny zostać skopiowane do udziału sieciowego. Ustawieniem domyślnym jest tak.|  
  
### <a name="cc-folder-general-category"></a>Folder C/C++ (kategoria ogólna)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Format informacji o debugowaniu** ([/Z7,/ZD, Zi,/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Określa typ informacji o debugowaniu, które mają zostać utworzone dla projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym z opcją Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [/Z7,/ZD,/Zi,/ZI (format informacji o debugowaniu)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Folder C/C++ (kategoria optymalizacji)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Optymalizacja**|Określa, czy kompilator powinien zoptymalizować tworzony przez niego kod. Optymalizacja zmienia kod, który jest wykonywany. Zoptymalizowany kod nie jest już zgodny z kodem źródłowym. W związku z tym debugowanie jest trudne.<br /><br /> Opcja domyślna (**Disabled (/0D**) pomija optymalizację. Można opracowywać z pominięciem optymalizacji, a następnie włączyć ją podczas tworzenia wersji produkcyjnej kodu.|  
  
### <a name="linker-folder-debugging-category"></a>Folder konsolidatora (kategoria debugowania)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Generuj informacje o debugowaniu** ([/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Nakazuje konsolidatorowi dołączenie informacji debugowania, które będą miały format określony przez/Z7,/ZD, Zi lub/ZI.|  
|**Generuj plik bazy danych programu** ([/PDB: Nazwa](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|W tym polu Określ nazwę pliku PDB. Dla formatu informacji debugowania należy wybrać ZI lub/Zi.|  
|**Symbole prywatne z paskiem** ([/PDBSTRIPPED: filename](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|W tym polu Określ nazwę pliku PDB, jeśli nie chcesz umieszczać prywatnych symboli w pliku PDB. Ta opcja tworzy drugi plik bazy danych programu (PDB) podczas kompilowania obrazu programu przy użyciu dowolnego z opcji kompilatora lub konsolidatora, które generują plik PDB, na przykład/DEBUG,/Z7,/ZD. Lub/Zi. Ten drugi plik PDB pomija symbole, które nie powinny być wysyłane do klientów. Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (symbole prywatne)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Generuj plik mapy** ([/map](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Nakazuje konsolidatorowi wygenerowanie pliku mapy podczas konsolidacji. Ustawienie domyślne to nie. Aby uzyskać więcej informacji, zobacz [/map (Generate Mapfile)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Nazwa pliku mapy** ([/map:](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*Nazwa*)|Jeśli wybierzesz opcję Generuj plik mapy, możesz określić plik mapy w tym polu. Aby uzyskać więcej informacji, zobacz [/map (Generate Mapfile)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eksporty mapy** ([/MapInfo: exports](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Zawiera wyeksportowane funkcje w pliku mapy. Ustawienie domyślne to nie. Aby uzyskać więcej informacji, zobacz [/MapInfo (Dołącz informacje w mapfile)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Zestaw możliwością debugowania** ([/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Określa ustawienia dla opcji konsolidatora/ASSEMBLYDEBUG. Dopuszczalne są następujące wartości:<br /><br /> -   **Nie wyemitowano atrybutu możliwością debugowania**.<br />-   **Śledzenie środowiska uruchomieniowego i wyłączanie optymalizacji (/ASSEMBLYDEBUG)**. Jest to ustawienie domyślne,<br />-   **Brak śledzenia środowiska uruchomieniowego i Włącz optymalizacje (/ASSEMBLYDEBUG: Disable)**.<br />-   **\<inherit from parent or project defaults>**.<br />-Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Add DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Możesz zmienić te ustawienia w folderze właściwości konfiguracji (kategoria debugowania) programowo przy użyciu interfejsu Microsoft. VisualStudio. VCProjectEngine. VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Tworzenie projektów Visual C++ i zarządzanie nimi](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Typowe makra dla poleceń i właściwości kompilacji](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)

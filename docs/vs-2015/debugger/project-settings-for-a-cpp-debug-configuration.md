---
title: Ustawienia konfiguracji debugowania języka C++ projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 87b8913a95203d082a76e8b18a92d2f509cace16
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446174"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zmienić ustawienia projektu dla konfiguracji debugowania języka Visual C++ lub C w **stron właściwości** okno dialogowe, zgodnie z opisem w [jak: Ustaw wartość Debug i Release konfiguracje](../debugger/how-to-set-debug-and-release-configurations.md). W poniższej tabeli przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **stron właściwości** okno dialogowe.  
  
> [!WARNING]
> Ustawienia projektu debugowania w **właściwości konfiguracji/debugowanie** kategorii dla aplikacji Windows Store i składników napisanych w języku C++ są różne. Zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) w Centrum deweloperów Windows.  
  
 Określ, który debuger do użycia w **debuger do uruchomienia** pola listy. Wybór ten wpłynie właściwości, które są widoczne.  
  
 Każde ustawienie właściwości debugowania jest automatycznie zapisywane i zapisywane w pliku "wg użytkownika" (. vcxproj.user) dla rozwiązania przy każdym zapisywaniu rozwiązania.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Folder właściwości konfiguracji (kategoria debugowanie)  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Debuger do uruchomienia**|Określa debugera do uruchomienia z następującymi opcjami:<br /><br /> -   **Debuger lokalny Windows**<br />-   **Debuger zdalny Windows**<br />-   **Debuger przeglądarki sieci Web**<br />-   **Debuger usługi sieci Web**|  
|**Polecenie** (debuger Windows lokalnego)|Określa polecenie uruchamiające program debugowany na komputerze lokalnym.|  
|**Polecenie zdalne** (debuger zdalny Windows)|Ścieżka .exe na komputerze zdalnym. Wprowadź ścieżkę, tak samo, jak byłaby wprowadzana na komputerze zdalnym.|  
|**Argumenty polecenia** (debuger Windows lokalnego i debugera zdalnego Windows)|-Określa argumenty określonego wcześniej polecenia.<br /><br /> W tym polu, można użyć następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje plik stdout do pliku.<br /><br /> >> `file`<br /> Dołącza plik stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje plik stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza plik stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe obiektu stderr (2) do tej samej lokalizacji co obiekt stdout (1).<br /><br /> 1> &2<br /> Wysyła stdout (1) dane wyjściowe do tej samej lokalizacji co obiekt stderr (2).<br /><br /> W większości przypadków te operatory mają zastosowanie tylko do aplikacji konsoli.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu względem katalogu projektu, w którym znajduje się Twój plik EXE. Jeśli zostawisz puste, katalogiem roboczym jest katalogu projektu. Dla zdalnego debugowania katalogu projektu będzie na serwerze zdalnym.|  
|**Dołącz** (debuger Windows lokalnego i debugera zdalnego Windows)|Określa, czy należy uruchomić lub dołączyć do aplikacji. Domyślne ustawienie to nie.|  
|**Nazwa serwera zdalnego** (debuger zdalny Windows)|Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makro kompilacji RemoteMachine jest ustawiona na wartość tej właściwości; Aby uzyskać więcej informacji, zobacz [makra dla poleceń i właściwości kompilacji](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Połączenie** (debuger zdalny Windows)|Umożliwia przełączanie między typami połączeń standardowych i nieuwierzytelnionymi dla debugowania zdalnego. Określ nazwę komputera zdalnego, w **nazwa serwera zdalnego** pole. Typy połączeń obejmują następujące czynności:<br /><br /> -   **Zdalny z uwierzytelnianiem Windows**<br />-   **Zdalny bez bez uwierzytelnienia (tylko natywne)**<br /><br /> **Uwaga** zdalne debugowanie bez uwierzytelniania może opuścić narażony na naruszenia zabezpieczeń komputera zdalnego. Tryb uwierzytelniania Windows jest bezpieczniejszy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Konfiguracja zdalnego debugowania](../debugger/remote-debugging.md).|  
|**Adres URL HTTP** (sieci Web usługi debugera i debuger przeglądarki sieci Web)|Określa adres URL, w którym znajduje się projekt, który debugujesz.|  
|**Typ debugera**|Określa typ debugera, który ma być używany: **Tylko w trybie macierzystym**, **tylko zarządzane**, **tylko GPU**, **mieszany**, **automatycznie** (ustawienie domyślne) lub **skryptu**.<br /><br /> -   **Tylko w trybie macierzystym** jest dla niezarządzanego kodu C++.<br />-   **Tylko zarządzany** jest dla kodu, który jest uruchamiany w ramach środowiska uruchomieniowego języka wspólnego (kod zarządzany).<br />-   **Mieszane** wywołuje debugery dla obu kodu zarządzanego i niezarządzanego.<br />-   **Automatyczne** Określa typ debugera na podstawie kompilatora i informacji EXE.<br />-   **Skrypt** wywołuje debugera skryptów.<br />-   **Tylko GPU** jest dla kodu C++ AMP, który jest uruchamiany na urządzeniu GPU lub na rasteryzatorze referencyjnym. Zobacz [debugowania kodu GPU](../debugger/debugging-gpu-code.md).|  
|**Środowisko** (debuger Windows lokalnego)|Określa zmienne środowiskowe dla debugowanego programu. Użyj składni zmiennych standardowego środowiska (na przykład `PATH="%SystemRoot%\..."`). Te zmienne zastępują środowisko systemu lub są scalane w środowisku systemu, w zależności od **Scal środowisko** ustawienie. Po kliknięciu w kolumnie ustawień "Edytuj" pojawia się. Kliknij łącze, aby edytować zmienne środowiskowe.|  
|**Scal środowisko** (debuger Windows lokalnego)|Określa, czy zmienne, które są określone w **środowiska** pola zostaną scalone ze środowiskiem, która jest zdefiniowana przez system operacyjny. Ustawienie domyślne to Yes.|  
|**Debugowanie SQL** (wszystko oprócz debugera klastra MPI)|Włącza debugowanie procedur SQL z Twojej [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikacji. Domyślne ustawienie to nie.|  
|**Typ akceleratora debugera** (tylko debugowanie GPU)|Określa urządzenie GPU używane do debugowania. Instalowanie sterowników urządzeń w przypadku kompatybilnych urządzeń GPU spowoduje dodanie dodatkowych opcji. Ustawieniem domyślnym jest "GPU — Emulator oprogramowania."|  
|**Domyślne zachowanie punktu przerwania GPU** (tylko debugowanie GPU)|Określa, czy dla każdego wątku w otoce SIMD powinno być generowane zdarzenie punktu przerwania. Ustawieniem domyślnym jest generowanie zdarzenia przerwania tylko raz na wiązkę.|  
|**Akcelerator domyślny amp** (tylko debugowanie GPU)|Określa domyślny akcelerator AMP podczas debugowania kodu GPU. Wybierz **akcelerator oprogramowania WARP** Zbadaj, czy problem jest spowodowany przez sprzęt lub sterownik zamiast kodu.|  
|**Katalog wdrożenia** (debuger zdalny Windows)|Określa ścieżkę na komputerze zdalnym, w której projekt wyjściowy będzie skopiowany przed uruchomieniem. Ścieżka może być udziałem sieciowym na komputerze zdalnym lub może być ścieżką do folderu na komputerze zdalnym. Ustawieniem domyślnym jest pusty, co oznacza, że dane wyjściowe projektu nie jest kopiowany do udziału sieciowego. Aby włączyć wdrażanie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md).|  
|**Dodatkowe pliki do wdrożenia** (debuger zdalny Windows)|Jeśli ustawiono właściwość katalogu wdrażania, to rozdzielana średnikami lista dodatkowych plików do skopiowania do katalogu wdrażania. Ustawieniem domyślnym jest pusty, oznacza to, że żadne dodatkowe pliki są kopiowane do katalogu wdrażania. Aby włączyć wdrażanie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md).|  
|**Wdrażanie bibliotek środowiska uruchomieniowego Visual C++ Debug** (debuger zdalny Windows)|Jeśli ustawiono właściwość katalogu wdrażania, określa czy biblioteki wykonawcze debugowania Visual C++ dla bieżącej platformy powinny zostać skopiowane do udziału sieciowego. Ustawienie domyślne to Yes.|  
  
### <a name="cc-folder-general-category"></a>Folder C/C++ (Kategoria Ogólne)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Format informacji o debugowaniu** ([/z7, / zd, Zi, /ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Określa typ informacji debugowania do utworzenia projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [/z7, / zd, / zi, /ZI (Format informacji debugowania)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>Folder C/C++ (kategoria Optymalizacja)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Optymalizacja**|Określa, czy kompilator powinien optymalizować generowany kod, który tworzy. Optymalizacja zmienia kod, który jest wykonywany. Zoptymalizowany kod nie zgadza się z kodu źródłowego. Dlatego debugowanie jest trudne.<br /><br /> Opcja domyślna (**wyłączony (/ 0d**) powoduje pominięcie optymalizacji. Można opracować z zahamowaniem optymalizacji, a następnie włącz go po utworzeniu wersję produkcyjną kodu.|  
  
### <a name="linker-folder-debugging-category"></a>Folder łączący (kategoria debugowanie)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Generuj informacje o debugowaniu** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|Nakazuje programowi łączącemu uwzględnienie informacji debugowania, które będą miały format określony przez/z7, / zd, Zi lub/zi.|  
|**Generuj plik bazy danych programu** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|W tym polu Określ nazwę pliku PDB. Dla formatu informacji debugowania, należy wybrać ZI lub/zi.|  
|**Usuń symbole prywatne** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|W tym polu należy określić nazwę pliku PDB, jeśli nie chcesz uwzględniać symboli prywatnych w pliku PDB. Ta opcja tworzy drugi plik bazy danych (PDB) programu podczas tworzenia obrazu programu za pomocą kompilatora lub konsolidatora, opcje, które generują plik PDB, takich jak/Debug, / z7, / zd. Lub/zi. Ten drugi plik PDB pomija symbole, których nie chcesz wysłać do klientów. Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symbole prywatne)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Generuj plik mapy** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Informuje konsolidator, aby wygenerowanie pliku mapy podczas konsolidacji. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Nazwa pliku mapy** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*nazwa*)|Jeśli wybierzesz opcję Generuj plik mapy, w tym polu można określić plik mapy. Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eksporty mapy** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Zawiera eksportowane funkcje w pliku mapy. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/MapInfo (zawierają informacje o mapfile)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Zestaw do debugowania** ([/assemblydebug](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Określa ustawienia dla konsolidatora opcję/assemblydebug. Dopuszczalne są następujące wartości:<br /><br /> -   **Nie emitowania debugowalnych atrybutów**.<br />-   **Środowisko uruchomieniowe śledzenie i wyłączone optymalizacje (/ ASSEMBLYDEBUG)**. To ustawienie domyślne<br />-   **Nie optimizations(/ASSEMBLYDEBUG:DISABLE) śledzenia i Włącz środowisko uruchomieniowe**.<br />-   **\<Dziedzicz z nadrzędnych bądź projektowych wartości domyślnych >**.<br />-Aby uzyskać więcej informacji, zobacz [/assemblydebug (Dodaj DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Te ustawienia w folderze właściwości konfigurowania (kategoria debugowania) można zmienić programowo za pomocą interfejsu Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Tworzenie i zarządzanie projektami Visual C++](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Typowe makra dla właściwości i poleceń kompilacji](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)

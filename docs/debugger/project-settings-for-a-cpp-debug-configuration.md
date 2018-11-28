---
title: Ustawienia dla konfiguracji debugowania w języku C++ projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/26/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: b333dca8f717cbd8e1172ed00b4a044aafeed857
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389659"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w języku C++
Możesz zmienić ustawienia projektu dla konfiguracji debugowania języka Visual C++ lub C w **stron właściwości** okno dialogowe, zgodnie z opisem w [porady: zestaw debugowania i zwalniania konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md). W poniższej tabeli przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **stron właściwości** okno dialogowe.  
  
> [!NOTE]
>  Ustawienia projektu debugowania w **właściwości konfiguracji/debugowanie** kategorii różnią się dla aplikacji platformy uniwersalnej systemu Windows i składników napisanych w języku C++. Zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Każde ustawienie właściwości debugowania jest automatycznie zapisywane i zapisywane w pliku "wg użytkownika" (. vcxproj.user) dla rozwiązania, gdy zapisujesz rozwiązania.  

 Określ, który debuger do użycia w **debuger do uruchomienia** pola listy, zgodnie z opisem w poniższej tabeli. Wybór ten wpłynie właściwości, które są widoczne.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Folder właściwości konfiguracji (kategoria debugowanie)  
  
| **Ustawienie** | **Opis** |
| - | - |
| **Debuger do uruchomienia** | Określa debugera do uruchomienia z następującymi opcjami:<br /><br /> -   **Debuger lokalny Windows**<br />-   **Debuger zdalny Windows**<br />-   **Debuger przeglądarki sieci Web**<br />-   **Debuger usługi sieci Web** |
| **Polecenie** (debuger Windows lokalnego) | Określa polecenie uruchamiające program debugowany na komputerze lokalnym. |
| **Polecenie zdalne** (debuger zdalny Windows) | Ścieżka .exe na komputerze zdalnym. Wprowadź ścieżkę, tak samo, jak byłaby wprowadzana na komputerze zdalnym. |
| **Argumenty polecenia** (debuger Windows lokalnego)<br /><br /> **Argumenty polecenia zdalnego** (debuger zdalny Windows) | -Określa argumenty określonego wcześniej polecenia.<br /><br /> W tym polu, można użyć następujących operatorów przekierowania:<br /><br /> < `file`<br /> Odczytuje stdin z pliku.<br /><br /> > `file`<br /> Zapisuje plik stdout do pliku.<br /><br /> >> `file`<br /> Dołącza plik stdout do pliku.<br /><br /> 2> `file`<br /> Zapisuje plik stderr do pliku.<br /><br /> 2>> `file`<br /> Dołącza plik stderr do pliku.<br /><br /> 2> &1<br /> Wysyła dane wyjściowe obiektu stderr (2) do tej samej lokalizacji co obiekt stdout (1).<br /><br /> 1> &2<br /> Wysyła stdout (1) dane wyjściowe do tej samej lokalizacji co obiekt stderr (2).<br /><br /> W większości przypadków te operatory mają zastosowanie tylko do aplikacji konsoli. |
| **Katalog roboczy** | Określa katalog roboczy debugowanego programu względem katalogu projektu, w którym znajduje się Twój plik EXE. Jeśli zostawisz puste, katalogiem roboczym jest katalogu projektu. Katalog projektu dla zdalnego debugowania, znajduje się na serwerze zdalnym. |
| **Dołącz** (debuger Windows lokalnego i debugera zdalnego Windows) | Określa, czy należy uruchomić lub dołączyć do aplikacji. Domyślne ustawienie to nie. |
| **Nazwa serwera zdalnego** (debuger zdalny Windows) | Określa nazwę komputera (innego niż Twój), na którym chcesz debugować aplikację.<br /><br /> Makro kompilacji RemoteMachine jest ustawiona na wartość tej właściwości; Aby uzyskać więcej informacji, zobacz [makra dla kompilacji polecenia i właściwości](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Połączenie** (debuger zdalny Windows) | Umożliwia przełączanie między typami połączeń standardowych i nieuwierzytelnionymi dla debugowania zdalnego. Określ nazwę komputera zdalnego, w **nazwa serwera zdalnego** pole. Typy połączeń obejmują następujące czynności:<br /><br /> -   **Zdalny z uwierzytelnianiem Windows**<br />-   **Zdalny bez bez uwierzytelnienia**<br /><br /> **Uwaga** zdalne debugowanie bez uwierzytelniania może opuścić narażony na naruszenia zabezpieczeń komputera zdalnego. Tryb uwierzytelniania Windows jest bezpieczniejszy.<br /><br /> Aby uzyskać więcej informacji, zobacz [zdalnego debugowania konfiguracji](../debugger/remote-debugging.md). |
| **Adres URL HTTP** (sieci Web usługi debugera i debuger przeglądarki sieci Web) | Określa adres URL, w którym znajduje się projekt, który debugujesz. |
| **Typ debugera** | Określa typ debugera, który ma być używany: **tylko natywny**, **tylko zarządzane**, **tylko GPU**, **mieszany**, **automatycznie**(ustawienie domyślne) lub **skryptu**.<br /><br /> -   **Tylko w trybie macierzystym** jest dla niezarządzanego kodu C++.<br />-   **Tylko zarządzany** jest dla kodu, który jest uruchamiany w ramach środowiska uruchomieniowego języka wspólnego (kod zarządzany).<br />-   **Mieszane** wywołuje debugery dla obu kodu zarządzanego i niezarządzanego.<br />-   **Automatyczne** Określa typ debugera na podstawie kompilatora i informacji EXE.<br />-   **Skrypt** wywołuje debugera skryptów.<br />-   **Tylko GPU** jest dla kodu C++ AMP, który jest uruchamiany na urządzeniu GPU lub na rasteryzatorze referencyjnym. Zobacz [kodu debugowania GPU](../debugger/debugging-gpu-code.md). |
| **Środowisko** (debuger Windows lokalnego i debugera zdalnego Windows) | Określa zmienne środowiskowe dla debugowanego programu. Użyj składni zmiennych standardowego środowiska (na przykład `PATH="%SystemRoot%\..."`). Te zmienne zastępują środowisko systemu lub są scalane w środowisku systemu, w zależności od **Scal środowisko** ustawienie. Po kliknięciu lewym przyciskiem myszy w kolumnie ustawień "Edytuj" pojawia się. Wybierz łącze, aby edytować zmienne środowiskowe. |
| **Scal środowisko** (debuger Windows lokalnego) | Określa, czy zmienne, które są określone w **środowiska** pola zostaną scalone ze środowiskiem, która jest zdefiniowana przez system operacyjny. Ustawienie domyślne to Yes. |
| **Debugowanie SQL** (wszystko oprócz debugera klastra MPI) | Włącza debugowanie procedur SQL z Twojej [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji. Domyślne ustawienie to nie. |
| **Typ akceleratora debugera** (tylko debugowanie GPU) | Określa urządzenie GPU używane do debugowania. Instalowanie sterowników urządzeń w przypadku kompatybilnych urządzeń GPU spowoduje dodanie dodatkowych opcji. Ustawieniem domyślnym jest **GPU — Emulator programowy**. |
| **Domyślne zachowanie punktu przerwania GPU** (tylko debugowanie GPU) | Określa, czy dla każdego wątku w otoce SIMD powinno być generowane zdarzenie punktu przerwania. Ustawieniem domyślnym jest generowanie zdarzenia przerwania tylko raz na wiązkę. |
| **Akcelerator domyślny amp** | Określa domyślny akcelerator AMP podczas debugowania kodu GPU. Wybierz **akcelerator oprogramowania WARP** Zbadaj, czy problem jest spowodowany przez sprzęt lub sterownik zamiast kodu. |
| **Katalog wdrożenia** (debuger zdalny Windows) | Określa ścieżkę na komputerze zdalnym, w której projekt wyjściowy będzie skopiowany przed uruchomieniem. Ścieżka może być udziałem sieciowym na komputerze zdalnym lub może być ścieżką do folderu na komputerze zdalnym. Ustawieniem domyślnym jest pusty, co oznacza, że dane wyjściowe projektu nie jest kopiowany do udziału sieciowego. Aby włączyć wdrażanie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md). |
| **Dodatkowe pliki do wdrożenia** (debuger zdalny Windows) | Jeśli ustawiono właściwość katalogu wdrażania, to rozdzielana średnikami lista dodatkowych plików do skopiowania do katalogu wdrażania. Ustawieniem domyślnym jest pusty, oznacza to, że żadne dodatkowe pliki są kopiowane do katalogu wdrażania. Aby włączyć wdrażanie plików, należy również wybrać **Wdróż** pole wyboru w oknie dialogowym programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [porady: tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md). |
| **Wdrażanie bibliotek środowiska uruchomieniowego Visual C++ Debug** (debuger zdalny Windows) | Jeśli ustawiono właściwość katalogu wdrażania, określa czy biblioteki wykonawcze debugowania Visual C++ dla bieżącej platformy powinny zostać skopiowane do udziału sieciowego. Ustawienie domyślne to Yes. |
  
## <a name="cc-folder-general-category"></a>Folder C/C++ (Kategoria Ogólne)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Format informacji o debugowaniu** ([/z7, / zd, Zi, /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|Określa typ informacji debugowania do utworzenia projektu.<br /><br /> Opcja domyślna (/ZI) tworzy bazę danych programu (PDB) w formacie zgodnym Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [/z7, / zd, / zi, /ZI (format informacji o debugowaniu)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>Folder C/C++ (kategoria Optymalizacja)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Optymalizacja**|Określa, czy kompilator powinien optymalizować generowany kod, który tworzy. Optymalizacja zmienia kod, który jest wykonywany. Zoptymalizowany kod nie zgadza się z kodu źródłowego, co sprawia, że debugowanie trudniejsze.<br /><br /> Opcja domyślna (**wyłączony (/ 0d)**) powoduje pominięcie optymalizacji. Można opracować z zahamowaniem optymalizacji, a następnie włącz go po utworzeniu wersję produkcyjną kodu.|  
  
## <a name="linker-folder-debugging-category"></a>Folder łączący (kategoria debugowanie)  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Generuj informacje o debugowaniu** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Nakazuje programowi łączącemu uwzględnienie informacji debugowania, które będą miały format określony przez [/z7, / zd, Zi lub/zi](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
|**Generuj plik bazy danych programu** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|W tym polu Określ nazwę pliku bazy danych (PDB) programu. Dla formatu informacji debugowania, należy wybrać ZI lub/zi.|  
|**Usuń symbole prywatne** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|W tym polu należy określić nazwę pliku PDB, jeśli nie chcesz uwzględniać symboli prywatnych w pliku PDB. Ta opcja tworzy drugi plik PDB podczas kompilowania obrazu programu za pomocą kompilatora lub konsolidatora, opcje, które generują plik PDB, takich jak/Debug, / z7, / zd. Lub/zi. Ten drugi plik PDB pomija symbole, których nie chcesz wysłać do klientów. Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symboli prywatnych)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Generuj plik mapy** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Informuje konsolidator, aby wygenerowanie pliku mapy podczas konsolidacji. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](/cpp/build/reference/map-generate-mapfile).|  
|**Nazwa pliku mapy** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*nazwa*)|Jeśli wybierzesz opcję Generuj plik mapy, w tym polu można określić plik mapy. Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](/cpp/build/reference/map-generate-mapfile).|  
|**Eksporty mapy** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Zawiera eksportowane funkcje w pliku mapy. Domyślne ustawienie to nie. Aby uzyskać więcej informacji, zobacz [/MapInfo (zawierają informacje o mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Zestaw do debugowania** ([/assemblydebug](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Określa ustawienia dla konsolidatora opcję/assemblydebug. Możliwe wartości to:<br /><br /> -   **Nie emitowania debugowalnych atrybutów**.<br />-   **Środowisko uruchomieniowe śledzenie i wyłączone optymalizacje (/ ASSEMBLYDEBUG)**. To ustawienie domyślne<br />-   **Nie optimizations(/ASSEMBLYDEBUG:DISABLE) śledzenia i Włącz środowisko uruchomieniowe**.<br />-   **\<Dziedzicz z nadrzędnych bądź projektowych wartości domyślnych >**.<br />-Aby uzyskać więcej informacji, zobacz [/assemblydebug (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Te ustawienia w folderze właściwości konfigurowania (kategoria debugowania) można zmienić programowo za pomocą interfejsu Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Inne ustawienia projektu

Aby debugować typów projektów, takich jak biblioteki statyczne i bibliotek DLL, projektu programu Visual Studio musi być może znaleźć odpowiednie pliki. Jeśli kod źródłowy jest dostępny, możesz dodać osobne projekty bibliotek statycznych i bibliotek DLL na tym samym rozwiązaniu, ułatwia debugowanie. Aby uzyskać informacje na temat tworzenia tych typów projektów, zobacz [tworzenie i używanie biblioteki łączy dynamicznych (DLL)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) i [tworzenie, używanie biblioteki statycznej](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Za pomocą dostępnego kodu źródłowego, można utworzyć nowy projekt programu Visual Studio, wybierając **pliku** > **New** > **projekt z istniejącego kodu**.

Aby debugować bibliotek DLL, które są zewnętrzne w stosunku do projektu, zobacz [projektów DLL debugowania](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Jeśli musisz utworzyć własny projekt DLL debugowania, ale nie ma dostępu do projektu aplikacji wywołującej, zobacz [debugowanie z projektu DLL](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Zobacz także  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Tworzenie i zarządzanie projektami Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Typowe makra dla poleceń kompilacji oraz właściwości](/cpp/ide/common-macros-for-build-commands-and-properties)
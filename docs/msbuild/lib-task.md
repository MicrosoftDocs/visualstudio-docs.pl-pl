---
title: Lib — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), LIB task
- LIB task (MSBuild (Visual C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51534979a96e0fb924d164dd1cc8d2fcc7bab04a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642821"
---
# <a name="lib-task"></a>LIB — Zadanie
Opakowuje narzędzie Microsoft 32-bitowy Library Manager *lib.exe*. Menedżer biblioteki tworzy i zarządza Biblioteka plików obiektów Common Object File Format (COFF). Menedżer biblioteki można tworzyć pliki eksportu i Importuj biblioteki do definicji odwołanie, eksportowane. Aby uzyskać więcej informacji, zobacz [odwołanie do biblioteki LIB](/cpp/build/reference/lib-reference) i [uruchamianie LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry **LIB** zadania. Większość parametrów zadania odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalDependencies**|Opcjonalnie **String []** parametru.<br /><br /> Określa dodatkowe elementy do dodania do wiersza polecenia.|
|**AdditionalLibraryDirectories**|Opcjonalnie **String []** parametru.<br /><br /> Zastępuje ścieżki biblioteki środowiska. Określ nazwę katalogu.<br /><br /> Aby uzyskać więcej informacji, zobacz [/libpath — (dodatkowa Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.<br /><br /> Lista *lib.exe* opcje określone w wierszu polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru do określenia *lib.exe* opcje, które nie są reprezentowane przez inne **LIB** parametru zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz [uruchamianie LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Opcjonalnie **ciąg** parametru.<br /><br /> Wyświetla informacje o bibliotece wyjściowej. Określ nazwę pliku, aby przekierować dane do pliku. Określ "CON" lub nie rób przekierować dane do konsoli.<br /><br /> Ten parametr odnosi się do **/LIST** opcji *lib.exe*.|
|**ErrorReporting**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa, jak wysyłać informacje o wewnętrznych błędach do firmy Microsoft, jeśli *lib.exe* zakończy się niepowodzeniem w czasie wykonywania.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **NoErrorReport** -   **/errorreport: Brak**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Aby uzyskać więcej informacji, zobacz **/errorreport** opcji wiersza polecenia w [uruchamianie LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Opcjonalnie **String []** parametru.<br /><br /> Określa jedną lub więcej funkcji do wyeksportowania.<br /><br /> Ten parametr odnosi się do **/EXPORT:** opcji *lib.exe*.|
|**ForceSymbolReferences**|Opcjonalnie **ciąg** parametru.<br /><br /> Wymusza *lib.exe* obejmujący odwołaniem do określonego symbolu.<br /><br /> Ten parametr odnosi się do **/INCLUDE:** opcji *lib.exe*.|
|**IgnoreAllDefaultLibraries**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, usuwa wszystkie domyślne biblioteki z listy bibliotek, *lib.exe* wyszukuje podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odnosi się do postaci bezparametrowego **/nodefaultlib** opcji *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Opcjonalnie **String []** parametru.<br /><br /> Usuwa określony bibliotek z listy bibliotek, *lib.exe* wyszukuje podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odnosi się do **/nodefaultlib** opcji *lib.exe* przyjmującej `library` argumentu.|
|**LinkLibraryDependencies**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, czy biblioteka wyników z odwoływanych projektów jest automatycznie konsolidowana.|
|**LinkTimeCodeGeneration**|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa generowanie łączonych kodów czasowych.<br /><br /> Ten parametr odnosi się do **/LCTG** opcji *lib.exe*.|
|**MinimumRequiredVersion**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa minimalną wymaganą wersję podsystemu. Określ rozdzielaną przecinkami listę liczb dziesiętnych z zakresu od 0 do 65 535.|
|**ModuleDefinitionFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa nazwę pliku definicji modułu (*.def*).<br /><br /> Ten parametr odnosi się do **/DEF** opcji *lib.exe* przyjmującej `filename` argumentu.|
|**Nazwa**|Opcjonalnie **ciąg** parametru.<br /><br /> Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki dll, dla których jest ona kompilowana biblioteki importu.<br /><br /> Ten parametr odnosi się do **/NAME** opcji *lib.exe* przyjmującej `filename` argumentu.|
|**OutputFile**|Opcjonalnie **ciąg** parametru.<br /><br /> Przesłania domyślną nazwę i lokalizację programu, który *lib.exe* tworzy.<br /><br /> Ten parametr odnosi się do **/OUT** opcji *lib.exe* przyjmującej `filename` argumentu.|
|**RemoveObjects**|Opcjonalnie **String []** parametru.<br /><br /> Pomija określony obiekt z biblioteki wyjściowej. *Lib.exe* tworzy bibliotekę wyjściową, łącząc wszystkie obiekty (w plikach obiektu lub biblioteki), a następnie usuwając wszystkie obiekty, które są określone przez tę opcję.<br /><br /> Ten parametr odnosi się do **/usunąć** opcji *lib.exe* przyjmującej `membername` argumentu.|
|**Źródła**|Wymagane `ITaskItem[]` parametru.<br /><br /> Określa listę plików źródłowych, rozdzielone spacjami.|
|**SubSystem**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa środowisko dla pliku wykonywalnego. Wybór podsystemu wpływa na symbol punktu wejścia lub funkcję punktu wejścia.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **Konsola** - **opcji**<br />-   **Windows** - **/SUBSYSTEM:WINDOWS**<br />-   **Native** - **/SUBSYSTEM:NATIVE**<br />-   **EFI Application** - **/SUBSYSTEM:EFI_APPLICATION**<br />-   **Sterownik usługi rozruchu interfejsu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/SUBSYSTEM:POSIX**<br /><br /> Aby uzyskać więcej informacji, zobacz [/Subsystem (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcji na [uruchamianie LIB](/cpp/build/reference/running-lib).|
|**TargetMachine**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa platformę docelową dla tego programu lub DLL.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa katalog dziennika śledzenia.|
|**TreatLibWarningAsErrors**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, powoduje, że **LIB** zadania, aby wygenerować plik wyjściowy nie, jeśli *lib.exe* generuje ostrzeżenie. Jeśli `false`, generowany jest plik danych wyjściowych.<br /><br /> Aby uzyskać więcej informacji, zobacz **/WX** opcji na [uruchamianie LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, system projektu ma generować pliki odpowiedzi w kodowaniu UNICODE, gdy zduplikowaniu bibliotekarza. Określ `true` gdy pliki w projekcie mają ścieżki UNICODE.|
|**pełne**|Opcjonalnie **logiczna** parametru.<br /><br /> Jeśli `true`, są wyświetlane szczegółowe informacje o postępie sesji; obejmuje to nazwy *.obj* plików dodawanych. Informacje są wysyłane do wyjścia standardowego i mogą zostać przekierowane do pliku.<br /><br /> Aby uzyskać więcej informacji, zobacz **/VERBOSE** opcji [uruchamianie LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
---
title: Zadanie LIB | Dokumenty firmy Microsoft
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
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633593"
---
# <a name="lib-task"></a>LIB — Zadanie

Zawija narzędzie 32-bitowy Menedżer bibliotek firmy Microsoft, *lib.exe*. Menedżer bibliotek tworzy bibliotekę plików obiektów common object file format (COFF) i zarządza nimi. Menedżer bibliotek może również tworzyć pliki eksportu i importować biblioteki w celu odwoływania się do eksportowanych definicji. Aby uzyskać więcej informacji, zobacz [odwołanie do lib](/cpp/build/reference/lib-reference) i [uruchamianie LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **LIB.** Większość parametrów zadania odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**DodatkoweZależności**|Parametr **Opcjonalny ciąg[].**<br /><br /> Określa dodatkowe elementy, które mają być dodane do wiersza polecenia.|
|**AdditionalLibraryDirectory**|Parametr **Opcjonalny ciąg[].**<br /><br /> Zastępuje ścieżkę biblioteki środowiska. Określ nazwę katalogu.<br /><br /> Aby uzyskać więcej informacji, zobacz [/LIBPATH (Additional Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**Dodatkoweopcje**|Opcjonalny parametr **String.**<br /><br /> Lista opcji *lib.exe* określona w wierszu polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji *lib.exe,* które nie są reprezentowane przez żaden inny parametr zadania **LIB.**<br /><br /> Aby uzyskać więcej informacji, zobacz [Uruchamianie LIB](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Opcjonalny parametr **String.**<br /><br /> Wyświetla informacje o bibliotece danych wyjściowych. Określ nazwę pliku, aby przekierować informacje do pliku. Określ "CON" lub nic, aby przekierować informacje do konsoli.<br /><br /> Ten parametr odpowiada opcji **/LIST** *lib.exe*.|
|**Raportowanie błędów**|Opcjonalny parametr **String.**<br /><br /> Określa sposób wysyłania wewnętrznych informacji o błędzie do firmy Microsoft, jeśli *program lib.exe* nie powiedzie się w czasie wykonywania.<br /><br /> Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:BRAK**<br />-   **PromptImmediately** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:WYŚLIJ**<br /><br /> Aby uzyskać więcej informacji, zobacz **/ERRORREPORT** command-line option at [Running LIB](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions (Funkcje eksportowe)**|Parametr **Opcjonalny ciąg[].**<br /><br /> Określa jedną lub więcej funkcji do wyeksportowania.<br /><br /> Ten parametr odpowiada opcji **/EXPORT:** *lib.exe*.|
|**ForceSymbolReferences (Wymbole)**|Opcjonalny parametr **String.**<br /><br /> Wymusza, aby *lib.exe* zawierał odwołanie do określonego symbolu.<br /><br /> Ten parametr odpowiada opcji **/INCLUDE:** *lib.exe*.|
|**IgnoreAllDefaultBraries**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program ,usuwa wszystkie biblioteki domyślne z listy bibliotek przeszukiwanych przez *lib.exe* po usunięciu odwołań zewnętrznych.<br /><br /> Ten parametr odpowiada bezparametryjnej formie opcji **/NODEFAULTLIB** *lib.exe*.|
|**IgnoreSpecificDefaultLibraries**|Parametr **Opcjonalny ciąg[].**<br /><br /> Usuwa określone biblioteki z listy bibliotek, które *lib.exe* wyszukuje po usunięciu odwołań zewnętrznych.<br /><br /> Ten parametr odpowiada opcji **/NODEFAULTLIB** *lib.exe,* `library` która przyjmuje argument.|
|**LinkLibraryZależności**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa, że dane wyjściowe biblioteki z zależności projektu są automatycznie połączone w.|
|**Pouczanie łącza timecode**|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa generowanie kodu w czasie łącza.<br /><br /> Ten parametr odpowiada opcji **/LCTG** *lib.exe*.|
|**Minimalna wymaganaweryjda**|Opcjonalny parametr **String.**<br /><br /> Określa minimalną wymaganą wersję podsystemu. Określ rozdzielaną przecinkami listę liczb dziesiętnych w zakresie od 0 do 65535.|
|**Plik zdefiniowanie modułu**|Opcjonalny parametr **String.**<br /><br /> Określa nazwę pliku definicji modułu (*.def*).<br /><br /> Ten parametr odpowiada opcji **/DEF** *lib.exe,* `filename` która przyjmuje argument.|
|**Nazwa**|Opcjonalny parametr **String.**<br /><br /> Podczas przygotowywania biblioteki importu określa nazwę biblioteki DLL, dla której jest budowana biblioteka importu.<br /><br /> Ten parametr odpowiada opcji **/NAME** *lib.exe,* `filename` która przyjmuje argument.|
|**Outputfile**|Opcjonalny parametr **String.**<br /><br /> Zastępuje domyślną nazwę i lokalizację programu tworzonego przez *lib.exe.*<br /><br /> Ten parametr odpowiada opcji **/OUT** *lib.exe,* `filename` która przyjmuje argument.|
|**Usuńobiekty**|Parametr **Opcjonalny ciąg[].**<br /><br /> Pomija określony obiekt z biblioteki danych wyjściowych. *Program Lib.exe* tworzy bibliotekę danych wyjściowych, łącząc wszystkie obiekty (w plikach obiektów lub bibliotekach), a następnie usuwając wszystkie obiekty określone przez tę opcję.<br /><br /> Ten parametr odpowiada **opcji /REMOVE** *lib.exe,* `membername` która przyjmuje argument.|
|**Źródeł**|Wymagany parametr interfejsu `ITaskItem[]`.<br /><br /> Określa listę plików źródłowych oddzielonych spacjami.|
|**Podsystemu**|Opcjonalny parametr **String.**<br /><br /> Określa środowisko dla pliku wykonywalnego. Wybór podsystemu wpływa na symbol punktu wejścia lub funkcję punktu wejścia.<br /><br /> Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.<br /><br /> -   **Konsola** - **/SUBSYSTEM:KONSOLA**<br />-   **Windows** - **/PODSYSTEM:WINDOWS**<br />-   **Natywne** - **/PODSYSTEM:NATYWNE**<br />-   **Aplikacja EFI** - **/PODSYSTEM:EFI_APPLICATION**<br />-   **Sterownik usługi rozruchu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/SUBSYSTEM:EFI_ROM**<br />-   **Środowisko wykonawcze** - EFI **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/PODSYSTEM:WINDOWSCE**<br />-   **POSIX** - **/PODSYSTEM:POSIX**<br /><br /> Aby uzyskać więcej informacji, zobacz [/SUBSYSTEM (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner (SuppressStartupBanner)**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.<br /><br /> Aby uzyskać więcej informacji, zobacz **/NOLOGO** opcja w [Running LIB](/cpp/build/reference/running-lib).|
|**Grupa docelowa**|Opcjonalny parametr **String.**<br /><br /> Określa platformę docelową programu lub biblioteki DLL.<br /><br /> Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.<br /><br /> -   **MACHINEARM** - **/MASZYNA:ARM**<br />-   **MachineEBC** - **/MASZYNA:EBC**<br />-   **MachineIA64** - **/MASZYNA:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MASZYNA:MIPS16**<br />-   **MachineMIPSFPU** -**/MASZYNA:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MASZYNA:MIPSFPU16**<br />-   **MachineSH4** - **/MASZYNA:SH4**<br />-   **MACHINETHUMB** - **/MASZYNA:KCIUK**<br />-   **MachineX64** - **/MASZYNA:X64**<br />-   **MachineX86** - **/MASZYNA:X86**<br /><br /> Aby uzyskać więcej informacji, zobacz [/MACHINE (Określ platformę docelową).](/cpp/build/reference/machine-specify-target-platform)|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **String.**<br /><br /> Określa katalog dziennika modułu śledzącego.|
|**TreatLibWarningAsErrors**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`zadanie **LIB** powoduje, że zadanie LIB nie generuje pliku wyjściowego, jeśli *lib.exe* generuje ostrzeżenie. Jeśli `false`zostanie wygenerowany plik wyjściowy.<br /><br /> Aby uzyskać więcej informacji, zobacz **/WX** opcja w [Running LIB](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`, nakazuje systemowi projektu generowanie plików odpowiedzi UNICODE po zduplikowanym bibliotekarzu. Określ, `true` kiedy pliki w projekcie mają ścieżki UNICODE.|
|**Pełne**|Opcjonalny parametr **logiczny.**<br /><br /> Jeśli `true`program , wyświetla szczegółowe informacje o postępie sesji; obejmuje to nazwy dodawanych plików *obj.* Informacje są wysyłane do standardowego wyjścia i mogą być przekierowywane do pliku.<br /><br /> Aby uzyskać więcej informacji, zobacz opcję **/VERBOSE** w [działaniu LIB](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
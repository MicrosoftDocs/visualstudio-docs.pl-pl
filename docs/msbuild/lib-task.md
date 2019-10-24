---
title: LIB — zadanie | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa43cef2176d9b2197e16b46a50e153da135502e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748093"
---
# <a name="lib-task"></a>LIB — Zadanie
Zawija narzędzie Microsoft 32-bitowego Menedżera bibliotek, *lib. exe*. Menedżer biblioteki tworzy i zarządza biblioteką plików obiektów Common File Format (COFF). Menedżer biblioteki może również tworzyć pliki eksportu i importować biblioteki w celu odwoływania się do wyeksportowanych definicji. Aby uzyskać więcej informacji, zobacz [Dokumentacja biblioteki lib](/cpp/build/reference/lib-reference) i [uruchomienie biblioteki lib](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **lib** . Większość parametrów zadań odpowiada opcji wiersza polecenia.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalDependencies**|Opcjonalny parametr **String []** .<br /><br /> Określa dodatkowe elementy do dodania do wiersza polecenia.|
|**AdditionalLibraryDirectories**|Opcjonalny parametr **String []** .<br /><br /> Zastępuje ścieżkę biblioteki środowiska. Określ nazwę katalogu.<br /><br /> Aby uzyskać więcej informacji, zobacz [/LIBPATH (dodatkowa LIBPATH)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .<br /><br /> Lista opcji *lib. exe* określona w wierszu polecenia. Na przykład/\<option1 >/\<option2 >/\<option # >. Użyj tego parametru, aby określić opcje *lib. exe* , które nie są reprezentowane przez żaden inny parametr zadania **lib** .<br /><br /> Aby uzyskać więcej informacji, zobacz [Uruchamianie lib](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|Opcjonalny parametr **ciągu** .<br /><br /> Wyświetla informacje o bibliotece wyjściowej. Określ nazwę pliku, aby przekierować informacje do pliku. Podaj wartość "CON" lub nie Przekieruj informacji do konsoli.<br /><br /> Ten parametr odpowiada opcji **/list** pliku *lib. exe*.|
|**ErrorReporting**|Opcjonalny parametr **ciągu** .<br /><br /> Określa, jak wysyłać wewnętrzne informacje o błędzie do firmy Microsoft, jeśli *lib. exe* kończy się niepowodzeniem w czasie wykonywania.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **NoErrorReport** -  **/errorReport: brak**<br />-   **monituj bezzwłocznie** -  **/errorReport: Prompt**<br />-   **QueueForNextLogin** -  **/errorReport: Queue**<br />-   **SendErrorReport** -  **/errorReport: Send**<br /><br /> Aby uzyskać więcej informacji, zobacz **/errorreport** opcji wiersza polecenia w [uruchomionej lib](/cpp/build/reference/running-lib).|
|**ExportNamedFunctions**|Opcjonalny parametr **String []** .<br /><br /> Określa co najmniej jedną funkcję, która ma zostać wyeksportowana.<br /><br /> Ten parametr odnosi się do **/Export:** opcji *lib. exe*.|
|**ForceSymbolReferences**|Opcjonalny parametr **ciągu** .<br /><br /> Wymusza, aby *lib. exe* zawierał odwołanie do określonego symbolu.<br /><br /> Ten parametr odpowiada opcji **/include:** *lib. exe*.|
|**IgnoreAllDefaultLibraries**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program usunie wszystkie biblioteki domyślne z listy bibliotek, które są przeszukiwane przez *lib. exe* podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odnosi się do formy opcji **/NODEFAULTLIB** *biblioteki lib. exe*, która jest bez parametrów.|
|**IgnoreSpecificDefaultLibraries**|Opcjonalny parametr **String []** .<br /><br /> Usuwa określone biblioteki z listy bibliotek, które są przeszukiwane przez *lib. exe* podczas rozpoznawania odwołań zewnętrznych.<br /><br /> Ten parametr odpowiada opcji **/NODEFAULTLIB** *biblioteki lib. exe* , która przyjmuje `library` argument.|
|**LinkLibraryDependencies**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa, że dane wyjściowe biblioteki z zależności projektu są automatycznie dołączane.|
|**LinkTimeCodeGeneration**|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa generowanie kodu w czasie konsolidacji.<br /><br /> Ten parametr odpowiada opcji **/LCTG** *biblioteki lib. exe*.|
|**MinimumRequiredVersion**|Opcjonalny parametr **ciągu** .<br /><br /> Określa minimalną wymaganą wersję podsystemu. Określ rozdzielaną przecinkami listę liczb dziesiętnych z zakresu od 0 do 65535.|
|**ModuleDefinitionFile**|Opcjonalny parametr **ciągu** .<br /><br /> Określa nazwę pliku definicji modułu ( *. def*).<br /><br /> Ten parametr odpowiada opcji **/def** *biblioteki lib. exe* , która przyjmuje `filename` argument.|
|**Nazwa**|Opcjonalny parametr **ciągu** .<br /><br /> Gdy biblioteka importowana jest skompilowana, określa nazwę biblioteki DLL, dla której jest tworzona biblioteka importowana.<br /><br /> Ten parametr odpowiada opcji **/name** pliku *lib. exe* , który przyjmuje `filename` argument.|
|**Plik_wyjściowy**|Opcjonalny parametr **ciągu** .<br /><br /> Zastępuje domyślną nazwę i lokalizację programu tworzonego przez *lib. exe* .<br /><br /> Ten parametr odpowiada opcji **/out** pliku *lib. exe* , który przyjmuje `filename` argument.|
|**RemoveObjects**|Opcjonalny parametr **String []** .<br /><br /> Pomija określony obiekt z biblioteki wyjściowej. *Lib. exe* tworzy bibliotekę wyjściową, łącząc wszystkie obiekty (w plikach lub bibliotekach obiektów), a następnie usuwa wszystkie obiekty, które są określone przez tę opcję.<br /><br /> Ten parametr odpowiada opcji **/Remove** pliku *lib. exe* , który przyjmuje `membername` argument.|
|**Źródeł**|Wymagany `ITaskItem[]` parametr.<br /><br /> Określa listę plików źródłowych rozdzielonych spacjami.|
|**Wykonawc**|Opcjonalny parametr **ciągu** .<br /><br /> Określa środowisko dla pliku wykonywalnego. Wybór podsystemu wpływa na symbol punktu wejścia lub funkcję punktu wejścia.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **konsoli** -  **/SUBSYSTEM: Konsola**<br />-   **windows** -  **/SUBSYSTEM: Windows**<br />-   **natywny** -  **/SUBSYSTEM: natywny**<br />**aplikacja -   EFI** -  **/SUBSYSTEM: EFI_APPLICATION**<br />**sterownik usługi rozruchu -   EFI** -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** -  **/SUBSYSTEM: EFI_ROM**<br />**środowisko uruchomieniowe -   EFI** -  **/SUBSYSTEM: EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** -  **/SUBSYSTEM: WindowsCE**<br />-   **posix** -  **/SUBSYSTEM: POSIX**<br /><br /> Aby uzyskać więcej informacji, zobacz [/subsystem (Określanie podsystemu)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.<br /><br /> Aby uzyskać więcej informacji, zobacz **/nologo** opcję w [uruchomionej lib](/cpp/build/reference/running-lib).|
|**TargetMachine**|Opcjonalny parametr **ciągu** .<br /><br /> Określa platformę docelową dla programu lub biblioteki DLL.<br /><br /> Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.<br /><br /> -   **MachineARM** -  **/Machine: ARM**<br />-   **MachineEBC** -  **/Machine: EBC**<br />-   **MachineIA64** -  **/Machine: IA64**<br />-   **MachineMIPS** -  **/Machine: MIPS**<br />-   **MachineMIPS16** -  **/Machine: MIPS16**<br />-   **MachineMIPSFPU** - **/Machine: MIPSFPU**<br />-   **MachineMIPSFPU16** -  **/Machine: MIPSFPU16**<br />-   **MachineSH4** -  **/Machine: sh4**<br />-   **MachineTHUMB** -  **/Machine: kciuk**<br />-   **MachineX64** -  **/Machine: x64**<br />-   **MachineX86** -  **/Machine: x86**<br /><br /> Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](/cpp/build/reference/machine-specify-target-platform).|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .<br /><br /> Określa katalog dziennika śledzenia.|
|**TreatLibWarningAsErrors**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, powoduje, że zadanie **lib** nie generuje pliku wyjściowego, jeśli *lib. exe* generuje ostrzeżenie. Jeśli `false`, generowany jest plik wyjściowy.<br /><br /> Aby uzyskać więcej informacji, zobacz **/WX** opcję w [uruchomionej lib](/cpp/build/reference/running-lib).|
|**UseUnicodeResponseFiles**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, nakazuje systemowi projektu generowanie plików odpowiedzi UNICODE podczas duplikowania bibliotekarza. Określ `true`, gdy pliki w projekcie mają ścieżki UNICODE.|
|**Pełne**|Opcjonalny parametr **logiczny** .<br /><br /> Jeśli `true`, wyświetla szczegółowe informacje o postępie sesji; dotyczy to również nazw dodawanych plików. *obj* . Informacje są wysyłane do wyjścia standardowego i mogą być przekierowywane do pliku.<br /><br /> Aby uzyskać więcej informacji, zobacz opcja **/verbose** w [uruchomionej lib](/cpp/build/reference/running-lib).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
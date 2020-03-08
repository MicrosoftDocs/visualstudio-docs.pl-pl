---
title: Połącz zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01105e3fd4c86d57077df7804e66592e32ebae07
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865352"
---
# <a name="link-task"></a>Link — Zadanie

Zawija narzędzia konsolidatora C++ firmy Microsoft, *link. exe*. Narzędzie konsolidatora łączy pliki i biblioteki obiektów Common Object Format (COFF), aby utworzyć plik wykonywalny (*exe*) lub bibliotekę dołączaną dynamicznie (dll). Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](/cpp/build/reference/linker-options) i [Użyj MSBuild z wiersza polecenia](/cpp/build/msbuild-visual-cpp) i [Użyj zestawu C++ narzędzi firmy Microsoft z wiersza polecenia](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Poniżej opisano parametry zadania **linku** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.

- **AdditionalDependencies**

  Opcjonalny parametr **String []** .

  Określa listę plików wejściowych do dodania do polecenia.

  Aby uzyskać więcej informacji, zobacz [łączenie plików wejściowych](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectories**

  Opcjonalny parametr **String []** .

  Zastępuje ścieżkę biblioteki środowiska. Określ nazwę katalogu.

  Aby uzyskać więcej informacji, zobacz [/LIBPATH (dodatkowa LIBPATH)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Opcjonalny parametr **String []** .

  Określa atrybuty, które zostaną umieszczone w sekcji `dependency` pliku manifestu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Zobacz również [pliki konfiguracji wydawcy](/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  Opcjonalny parametr **ciągu** .

  Lista opcji konsolidatora określona w wierszu polecenia. Na przykład/\<opcja1 >/\<opcja2 >/\<opcji # >. Użyj tego parametru, aby określić Opcje konsolidatora, które nie są reprezentowane przez żaden inny parametr zadania **linku** .

  Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Opcjonalny parametr **String []** .

  Dodaje odwołanie do modułu do zestawu.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **AllowIsolation**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, powoduje, że system operacyjny przeszukiwanie i ładowanie manifestu. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było manifestu.

  Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (odnośnik manifestu)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, emituje atrybut **DebuggableAttribute** wraz ze śledzeniem informacji debugowania i wyłącza optymalizacje JIT. Jeśli `false`, emituje atrybut **DebuggableAttribute** , ale wyłącza śledzenie informacji debugowania i włącza optymalizacje JIT.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Opcjonalny parametr **String []** .

  Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Określ nazwę zasobu.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYLINKRESOURCE (link do zasobów .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Niejawny parametr **logiczny** .

  Umożliwia dokładniejsze śledzenie plików, aby przechwycić zachowanie przyrostu łącza. Zawsze zwraca wartość `true`.

- **BaseAddress**

  Opcjonalny parametr **ciągu** .

  Ustawia adres podstawowy dla kompilowanego programu lub biblioteki DLL. Podaj wartość `{address[,size] | @filename,key}`.

  Aby uzyskać więcej informacji, zobacz [/Base (adres podstawowy)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  Opcjonalny parametr **logiczny** .

  Jeśli wartość jest równa true, wskazuje, że MSBuild jest wywoływany z IDE. W przeciwnym razie wskazuje, że MSBuild jest wywoływany z wiersza polecenia.

  Ten parametr nie ma równoważnej opcji konsolidatora.

- **CLRImageType**

  Opcjonalny parametr **ciągu** .

  Ustawia typ obrazu środowiska uruchomieniowego języka wspólnego (CLR).

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **Domyślne** -  *\<brak >*

  - **ForceIJWImage** -  **/CLRIMAGETYPE: IJW**

  - **ForcePureILImage** -  **/CLRIMAGETYPE: czysty**

  - **ForceSafeILImage** -  **/CLRIMAGETYPE: Safe**

  Aby uzyskać więcej informacji, zobacz [/CLRIMAGETYPE (Określ typ obrazu CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  Opcjonalny parametr **ciągu** .

  Zachowuje kod ostatniego błędu funkcji wywoływanych za pomocą mechanizmu P/Invoke.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **Włączone** -  **/CLRSupportLastError**

  - **Wyłączone** -  **/CLRSupportLastError: nie**

  - **SystemDlls** -  **/CLRSupportLastError: SYSTEMDLL**

  Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRThreadAttribute**

  Opcjonalny parametr **ciągu** .

  Jawnie określa atrybut wątkowości dla punktu wejścia programu CLR.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE: brak**

  - **MTAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: MTA**

  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: sta**

  Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (ustaw atrybut wątku CLR)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Opcjonalny parametr **logiczny** .

  Określa, czy konsolidator będzie stosował **SuppressUnmanagedCodeSecurityAttribute** do wygenerowanych przez konsolidatora wywołań P/Invoke z kodu zarządzanego do natywnych bibliotek DLL.

  Aby uzyskać więcej informacji, zobacz [/CLRUNMANAGEDCODECHECK (Add SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Opcjonalny parametr **ciągu** .

  Przygotowuje obraz do stosowania poprawek na gorąco.

  Określ jedną z następujących wartości, która odnosi się do opcji konsolidatora.

  - **Włączone** -  **/functionpadmin**

  - **X86Image** -  **/functionpadmin: 5**

  - **X64Image** -  **/functionpadmin: 6**

  - **ItaniumImage** -  **/functionpadmin: 16**

  Aby uzyskać więcej informacji, zobacz [/functionpadmin (Create możliwy do poprawiania Image)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, wskazuje, że plik wykonywalny został przetestowany pod kątem zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows.

  Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  Opcjonalny parametr **String []** .

  Ten parametr powoduje *opóźnione ładowanie* bibliotek DLL. Określ nazwę pliku DLL, aby opóźnić ładowanie.

  Aby uzyskać więcej informacji, zobacz [/DELAYLOAD (opóźnienie importowania ładowania)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, częściowo podpisuje zestaw. Domyślna wartość to `false`.

  Aby uzyskać więcej informacji, zobacz [/delaysign (częściowo podpisz zestaw)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Kierowc**

  Opcjonalny parametr **ciągu** .

  Określ ten parametr, aby skompilować sterownik trybu jądra systemu Windows NT.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - Wartość **NotSet** - *nie\<brak >*

  - ** - ** **sterownika sterowników**

  - **Tylko** - object **: tylko** do

  - **Wdm** -  **: WDM**

  Aby uzyskać więcej informacji, zobacz [Sterownik systemu Windows NT — sterowniki trybu jądra](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  Opcjonalny parametr **String []** .

  Osadza plik zasobów w zestawie. Określ wymaganą nazwę pliku zasobu. Opcjonalnie można określić nazwę logiczną, która jest używana do ładowania zasobu, oraz opcję **prywatną** wskazującą w manifeście zestawu, że plik zasobów jest prywatny.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYRESOURCE (osadzanie zarządzanego zasobu)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, włącza identyczne składanie COMDAT.

  Aby uzyskać więcej informacji, zobacz `ICF[= iterations]` argument [/opt (optymalizacje)](/cpp/build/reference/opt-optimizations).

- **EnableUAC**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa, że informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (osadzanie informacji UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Opcjonalny parametr **ciągu** .

  Określa funkcję punktu wejścia jako adres początkowy dla pliku *. exe* lub dll. Określ nazwę funkcji jako wartość parametru.

  Aby uzyskać więcej informacji, zobacz [/entry (symbol punktu wejścia)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  Opcjonalny parametr **logiczny** .

  W przypadku `true`tworzy program lub plik DLL, który można załadować tylko przy użyciu preferowanego adresu podstawowego.

  Aby uzyskać więcej informacji, zobacz [/FIXED (stały adres podstawowy)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  Opcjonalny parametr **ciągu** .

  Nakazuje konsolidatorowi utworzenie prawidłowego pliku *. exe* lub dll, nawet jeśli istnieje odwołanie do symbolu, ale nie zdefiniowane lub jest zdefiniowane wielokrotnie.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Włączono** -  **/Force**

  - **MultiplyDefinedSymbolOnly** -  **/Force: wiele**

  - **UndefinedSymbolOnly** -  **/Force: nierozwiązane**

  Aby uzyskać więcej informacji, zobacz [/Force (Wymuś dane wyjściowe pliku)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  Opcjonalny parametr **String []** .

  Ten parametr nakazuje konsolidatorowi dodanie określonego symbolu do tabeli symboli.

  Aby uzyskać więcej informacji, zobacz [/include (Wymuszaj odwołania do symboli)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  Opcjonalny parametr **ciągu** .

  Ten parametr optymalizuje program przez umieszczenie określonych spakowanych funkcji (COMDAT) w obrazie w ustalonej kolejności.

  Aby uzyskać więcej informacji, zobacz [/Order (Put funkcje w kolejności)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program tworzy informacje debugowania dla pliku *exe* lub dll.

  Aby uzyskać więcej informacji, zobacz [/debug (generowanie informacji o debugowaniu)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program tworzy plik manifestu obok siebie.

  Aby uzyskać więcej informacji, zobacz [/manifest (Create Side-by-Side manifest zestawu)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program tworzy *plik mapy*. Rozszerzenie nazwy pliku mapy to *. map*.

  Aby uzyskać więcej informacji, zobacz [/map (Generate Mapfile)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  Opcjonalny parametr **ciągu** .

  Określa ilość pamięci fizycznej na stercie do przydzielenia w danym momencie.

  Aby uzyskać więcej informacji, zobacz argument `commit` w [/Heap (Ustawianie rozmiaru sterty)](/cpp/build/reference/heap-set-heap-size). Zobacz również parametr **HeapReserveSize** .

- **HeapReserveSize**

  Opcjonalny parametr **ciągu** .

  Określa całkowitą alokację sterty w pamięci wirtualnej.

  Aby uzyskać więcej informacji, zobacz argument `reserve` w [/Heap (Ustawianie rozmiaru sterty)](/cpp/build/reference/heap-set-heap-size). Zobacz również parametr **HeapCommitSize** w tej tabeli.

- **IgnoreAllDefaultLibraries**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, nakazuje konsolidatorowi usunięcie co najmniej jednej biblioteki domyślnej z listy bibliotek, które przeszukuje, gdy rozwiązuje odwołania zewnętrzne.

  Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa, że żadne atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane do pliku *. idl* .

  Aby uzyskać więcej informacji, zobacz [/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa, że biblioteka importowana, generowana przez tę konfigurację, nie powinna być importowana do projektów zależnych.

  Ten parametr nie odpowiada opcji konsolidatora.

- **IgnoreSpecificDefaultLibraries**

  Opcjonalny parametr **String []** .

  Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania. Oddziel wiele bibliotek przy użyciu średników.

  Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, konsolidator tworzy obraz tylko wtedy, gdy może również generować tabelę obsługi wyjątków bezpiecznego obrazu.

  Aby uzyskać więcej informacji, zobacz [/SAFESEH (obraz ma bezpieczne procedury obsługi wyjątków)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Nazwa biblioteki importu określona przez użytkownika, która zastępuje domyślną nazwę biblioteki.

  Aby uzyskać więcej informacji, zobacz [/IMPLIB (Name import Library)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  Opcjonalny parametr **ciągu** .

  Kontener, który zawiera klucz dla podpisanego zestawu.

  Aby uzyskać więcej informacji, zobacz [/KEYCONTAINER (Określ kontener klucza do podpisania zestawu)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Zobacz również parametr **KeyFile** w tej tabeli.

- **KeyFile**

  Opcjonalny parametr **ciągu** .

  Określa plik, który zawiera klucz dla podpisanego zestawu.

  Aby uzyskać więcej informacji, zobacz [/keyfile (Określ klucz lub parę kluczy, aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Należy również zapoznać się z parametrem **kontenera** .

- **LargeAddressAware**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, aplikacja może obsłużyć adresy większe niż 2 gigabajty.

  Aby uzyskać więcej informacji, zobacz [/LARGEADDRESSAWARE (obsługa dużych adresów)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program kompiluje bibliotekę DLL jako główny plik wyjściowy.

  Aby uzyskać więcej informacji, zobacz [/dll (Kompilowanie biblioteki dll)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Opcjonalny parametr **ciągu** .

  Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do firmy Microsoft.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NoErrorReport** -  **/errorReport: brak**

  - **Monituj bezzwłocznie** -  **/errorReport: Prompt**

  - **QueueForNextLogin** -  **/errorReport: Queue**

  - **SendErrorReport** -  **/errorReport: Send**

  Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy konsolidatora)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, włącza łączenie przyrostowe.

  Aby uzyskać więcej informacji, zobacz [/Incremental (łączenie przyrostowe)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa, że dane wyjściowe biblioteki z zależności projektu są automatycznie dołączane.

  Ten parametr nie odpowiada opcji konsolidatora.

- **LinkStatus**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa, że konsolidator ma wyświetlać wskaźnik postępu, który pokazuje, jaki procent łącza zostało zakończone.

  Aby uzyskać więcej informacji, zobacz argument `STATUS` [/LTCG (generowanie kodu w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation).

- **LinkTimeCodeGeneration**

  Opcjonalny parametr **ciągu** .

  Określa opcje optymalizacji profilowanej.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Domyślne** -  *\<brak >*

  - **UseLinkTimeCodeGeneration** -  **/LTCG**

  - **PGInstrument** -  **/LTCG: PGInstrument**

  - **PGOptimization** -  **/LTCG: PGOptimize**

  - **PGUpdate**

    \- **/LTCG: PGUpdate**

  Aby uzyskać więcej informacji, zobacz [/LTCG (generowanie kodu w czasie konsolidacji)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  Opcjonalny parametr **ciągu** .

  Zmienia domyślną nazwę pliku manifestu na określoną nazwę pliku.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (Nazwij plik manifestu)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, nakazuje konsolidatorowi uwzględnienie wyeksportowanych funkcji w pliku mapy.

  Aby uzyskać więcej informacji, zobacz argument `EXPORTS` [/MapInfo (Dołącz informacje w mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  Opcjonalny parametr **ciągu** .

  Zmienia domyślną nazwę pliku mapy na określoną nazwę pliku.

- **MergedIDLBaseFileName**

  Opcjonalny parametr **ciągu** .

  Określa nazwę pliku i rozszerzenie nazwy pliku *IDL* .

  Aby uzyskać więcej informacji, zobacz [/IDLOUT (Name MIDL Output Files)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  Opcjonalny parametr **ciągu** .

  Łączy sekcje w obrazie. Podaj wartość `from-section=to-section`.

  Aby uzyskać więcej informacji, zobacz [/merge (łączenie sekcji)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  Opcjonalny parametr **ciągu** .

  Określ nazwę pliku, który zawiera opcje wiersza polecenia MIDL.

  Aby uzyskać więcej informacji, zobacz [/MIDL (Określ opcje wiersza polecenia MIDL)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **MinimumRequiredVersion**

  Opcjonalny parametr **ciągu** .

  Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65535.

- **ModuleDefinitionFile**

  Opcjonalny parametr **ciągu** .

  Określa nazwę [pliku definicji modułu](/cpp/build/reference/module-definition-dot-def-files).

  Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  Opcjonalny parametr **ciągu** .

  Dołącza określony program zastępczy systemu MS-DOS do programu systemu Win32.

  Aby uzyskać więcej informacji, zobacz [/stub (nazwa pliku szczątkowego systemu MS-DOS)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **Noentrypoint**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, określa plik DLL z tylko zasobami.

  Aby uzyskać więcej informacji, zobacz [/NOENTRY (brak punktu wejścia)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Parametr niejawnego **ciągu []** .

  Określa pliki obiektów, które są połączone.

- **OptimizeReferences**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, eliminuje funkcje i/lub dane, które nigdy nie są przywoływane.

  Aby uzyskać więcej informacji, zobacz argument `REF` w [/opt (optymalizacje)](/cpp/build/reference/opt-optimizations).

- **Plik_wyjściowy**

  Opcjonalny parametr **ciągu** .

  Zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.

  Aby uzyskać więcej informacji, zobacz [/out (nazwa pliku wyjściowego)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  Opcjonalny parametr **logiczny** .

  Jeśli `true` i rejestrowanie danych wyjściowych jest włączone, wymusza, aby zapisy rejestru **HKEY_CLASSES_ROOT** przekierowywać do **HKEY_CURRENT_USER**.

- **PreprocessOutput**

  Opcjonalny parametr `ITaskItem[]`.

  Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.

- **PreventDllBinding**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, wskazuje, że program *bind. exe* nie powinien być powiązany z połączonym obrazem.

  Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (Zapobiegaj powiązaniu biblioteki dll)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, tworzy plik wyjściowy, który może być używany z profilerem **narzędzi do oceny wydajności** .

  Aby uzyskać więcej informacji, zobacz [/Profile (Profiler narzędzi do oceny wydajności)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  Opcjonalny parametr **ciągu** .

  Określa nazwę pliku *. PGD* , który będzie używany do przechowywania informacji o działającym programie

  Aby uzyskać więcej informacji, zobacz [/PGD (Określ bazę danych dla optymalizacji](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations)profilowanej).

- **ProgramDatabaseFile**

  Opcjonalny parametr **ciągu** .

  Określa nazwę bazy danych programu (PDB), którą tworzy konsolidator.

  Aby uzyskać więcej informacji, zobacz [/PDB (Korzystanie z bazy danych programu)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program generuje obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji *losowego układu przestrzeni adresowej* (ASLR) systemu Windows.

  Aby uzyskać więcej informacji, zobacz [/DYNAMICBASE (Użyj losowości układu przestrzeni adresowej)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, rejestruje podstawowe dane wyjściowe tej kompilacji.

- **Wyrównanie sekcji**

  Opcjonalny parametr **liczby całkowitej** .

  Określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Wartość parametru jest liczbą jednostek bajtów i jest potęgą liczby 2.

  Aby uzyskać więcej informacji, zobacz [/align (wyrównanie sekcji)](/cpp/build/reference/align-section-alignment).

- **SetCheckSum —**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, ustawia sumę kontrolną w nagłówku pliku *. exe* .

  Aby uzyskać więcej informacji, zobacz [/Release (Ustaw sumę kontrolną)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  Opcjonalny parametr **ciągu** .

  Określa szczegółowość raportów postępu dla operacji łączenia.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - Wartość **NotSet** - *nie\<brak >*

  - **LinkVerbose** -  **/verbose**

  - **LinkVerboseLib** -  **/verbose: lib**

  - **LinkVerboseICF** -  **/verbose: ICF**

  - **LinkVerboseREF** -  **/verbose: ref**

  - **LinkVerboseSAFESEH** -  **/verbose: SAFESEH**

  - **LinkVerboseCLR** -  **/verbose: CLR**

  Aby uzyskać więcej informacji, zobacz [/verbose (drukowanie komunikatów o postępie)](/cpp/build/reference/verbose-print-progress-messages).

- **Źródeł**

  Wymagany `ITaskItem[]` parametr.

  Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.

- **SpecifySectionAttributes**

  Opcjonalny parametr **ciągu** .

  Określa atrybuty sekcji. Zastępuje to atrybuty, które zostały ustawione, gdy plik *. obj* sekcji został skompilowany.

  Aby uzyskać więcej informacji, zobacz [/Section (Określ atrybuty sekcji)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  Opcjonalny parametr **ciągu** .

  Określa ilość pamięci fizycznej w każdej alokacji po przydzieleniu dodatkowej pamięci.

  Aby uzyskać więcej informacji, zobacz argument `commit` [/Stack (alokacje stosu)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Opcjonalny parametr **ciągu** .

  Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.

  Aby uzyskać więcej informacji, zobacz argument `reserve` [/Stack (alokacje stosu)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Opcjonalny parametr **ciągu** .

  Tworzy drugi plik bazy danych programu (PDB), który pomija symbole, które nie mają być rozpowszechniane do klientów. Określ nazwę drugiego pliku PDB.

  Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (symbole prywatne)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Wykonawc**

  Opcjonalny parametr **ciągu** .

  Określa środowisko dla pliku wykonywalnego.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - Wartość **NotSet** - *nie\<brak >*

  - **Konsola** -  **/SUBSYSTEM: Konsola**

  - **Windows** -  **/SUBSYSTEM: Windows**

  - **Natywne** -  **/SUBSYSTEM: natywne**

  - **Aplikacja EFI** -  **/SUBSYSTEM: EFI_APPLICATION**

  - **Sterownik usługi rozruchu EFI** -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**

  - **Interfejs EFI ROM** -  **/SUBSYSTEM: EFI_ROM**

  - **Środowisko uruchomieniowe EFI** -  **/SUBSYSTEM: EFI_RUNTIME_DRIVER**

  - **WindowsCE** -  **/SUBSYSTEM: WindowsCE**

  - **Posix** -  **/SUBSYSTEM: POSIX**

  Aby uzyskać więcej informacji, zobacz [/subsystem (Określanie podsystemu)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, nakazuje konsolidatorowi nieuwzględnienie tabeli adresów importu (IAT) w końcowym obrazie.

  Aby uzyskać więcej informacji, zobacz argument `NOBIND` [/Delay (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, nakazuje funkcji pomocnika ładowania opóźnień, aby obsługiwała jawne wyładowywanie biblioteki DLL.

  Aby uzyskać więcej informacji, zobacz argument `UNLOAD` [/Delay (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

  Aby uzyskać więcej informacji, zobacz [/nologo (Pomijanie transparentu startowego) (Konsolidator)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Opcjonalny parametr **logiczny** .

  W przypadku `true`program instruuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd.

  Aby uzyskać więcej informacji, zobacz argument `CD` [/SWAPRUN (ładowanie danych wyjściowych konsolidatora do pliku wymiany)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz również parametr **SwapRunFromNET** .

- **SwapRunFromNET**

  Opcjonalny parametr **logiczny** .

  W przypadku `true`program instruuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd.

  Aby uzyskać więcej informacji, zobacz argument `NET` [/SWAPRUN (ładowanie danych wyjściowych konsolidatora do pliku wymiany)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz również parametr **SwapRunFromCD** w tej tabeli.

- **TargetMachine**

  Opcjonalny parametr **ciągu** .

  Określa platformę docelową dla programu lub biblioteki DLL.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - Wartość **NotSet** - *nie\<brak >*

  - **MachineARM** -  **/Machine: ARM**

  - **MachineEBC** -  **/Machine: EBC**

  - **MachineIA64** -  **/Machine: IA64**

  - **MachineMIPS** -  **/Machine: MIPS**

  - **MachineMIPS16** -  **/Machine: MIPS16**

  - **MachineMIPSFPU** -  **/Machine: MIPSFPU**

  - **MachineMIPSFPU16** -  **/Machine: MIPSFPU16**

  - **MachineSH4** -  **/Machine: sh4**

  - **MachineTHUMB** -  **/Machine: kciuk**

  - **MachineX64** -  **/Machine: x64**

  - **MachineX86** -  **/Machine: x86**

  Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian do aplikacji.

  Aby uzyskać więcej informacji, zobacz [/TSAWARE (Tworzenie aplikacji z obsługą serwera terminali)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **Katalog trackerlogdirectory**

  Opcjonalny parametr **ciągu** .

  Określa katalog dziennika śledzenia.

- **TreatLinkerWarningAsErrors**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator generuje ostrzeżenie.

  Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, program tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.

  Aby uzyskać więcej informacji, zobacz [/NOASSEMBLY (Create a module MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  Opcjonalny parametr **ciągu** .

  Określa nazwę pliku i rozszerzenie nazwy pliku *. tlb* . Określ nazwę pliku lub ścieżkę i nazwę pliku.

  Aby uzyskać więcej informacji, zobacz [/TLBOUT (nazwa pliku. tlb)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  Opcjonalny parametr **liczby całkowitej** .

  Określa wartość określoną przez użytkownika dla biblioteki typów utworzonej przez konsolidator. Określ wartość od 1 do 65535.

  Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla biblioteki typów)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  Opcjonalny parametr **ciągu** .

  Określa żądany poziom wykonywania aplikacji, gdy jest uruchamiany w ramach kontroli konta użytkownika.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Jako źródło** - `level='asInvoker'`

  - **Najwyższe dostępne** - `level='highestAvailable'`

  - **Wymaga administratora** - `level='requireAdministrator'`

  Aby uzyskać więcej informacji, zobacz argument `level` [/MANIFESTUAC (osadza informacje funkcji kontroli konta użytkownika w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, aplikacja pomija poziomy ochrony interfejsu użytkownika i dyski wejściowe w oknach wyższych uprawnień na pulpicie; w przeciwnym razie `false`.

  Aby uzyskać więcej informacji, zobacz argument `uiAccess` [/MANIFESTUAC (osadza informacje funkcji kontroli konta użytkownika w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Opcjonalny parametr **logiczny** .

  Jeśli `true`, dane wejściowe narzędzia bibliotekarza są używane zamiast pliku biblioteki, gdy dane wyjściowe biblioteki są połączone w programie.

- **Wersja**

  Opcjonalny parametr **ciągu** .

  Umieść numer wersji w nagłówku pliku *. exe* lub *. dll* . Określ wartość "`major[.minor]`". Argumenty `major` i `minor` są liczbami dziesiętnymi od 0 do 65535.

  Aby uzyskać więcej informacji, zobacz [/Version (informacje o wersji)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

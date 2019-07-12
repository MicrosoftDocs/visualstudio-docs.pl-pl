---
title: Łączenie zadań | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), Link task
- Link task (MSBuild (Visual C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 432ef1231f551d265e06242e2ab4ddc58a0fe5ac
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825409"
---
# <a name="link-task"></a>Link — Zadanie
Narzędzia konsolidatora Visual C++, jest zawijany *link.exe*. Narzędzia konsolidatora łączy pliki obiektu Common Object File Format (COFF) i biblioteki, aby utworzyć plik wykonywalny ( *.exe*) pliku lub biblioteki dołączanej (dynamicznie DLL). Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](/cpp/build/reference/linker-options).

## <a name="parameters"></a>Parametry
 Poniżej opisano parametry **łącze** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.

- **AdditionalDependencies**

  Opcjonalnie **String []** parametru.

  Określa listę plików wejściowych, aby dodać do polecenia.

  Aby uzyskać więcej informacji, zobacz [pliki wejściowe LINK](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectories**

  Opcjonalnie **String []** parametru.

  Zastępuje ścieżki biblioteki środowiska. Określ nazwę katalogu.

  Aby uzyskać więcej informacji, zobacz [/libpath — (dodatkowa Libpath)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  Opcjonalnie **String []** parametru.

  Określa atrybuty, które zostaną umieszczone w `dependency` części pliku manifestu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Zobacz też [pliki konfiguracyjne wydawcy](https://docs.microsoft.com/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  Opcjonalnie **ciąg** parametru.

  Lista opcji konsolidatora, jak określono w wierszu polecenia. Na przykład /\<opcja1 > /\<opcja2 > /\<opcja #>. Użyj tego parametru, aby określić opcje konsolidatora, które nie są reprezentowane przez inne **łącze** parametru zadania.

  Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Opcjonalnie **String []** parametru.

  Dodaje odwołania modułu do zestawu.

  Aby uzyskać więcej informacji, zobacz [assemblymodule (Dodaj moduł MSIL do zestawu)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **AllowIsolation**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, powoduje, że system operacyjny do manifestu wyszukiwań i ładuje. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było żadnych manifestu.

  Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (wyszukiwania plików manifestu)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, emituje **DebuggableAttribute** atrybut wraz z debugowania informacji śledzenia i wyłącza optymalizacje JIT. Jeśli `false`, emituje **DebuggableAttribute** atrybut, ale powoduje wyłączenie śledzenia informacji o debugowaniu i włącza optymalizacje JIT.

  Aby uzyskać więcej informacji, zobacz [/assemblydebug (Dodaj DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Opcjonalnie **String []** parametru.

  Tworzy łącze do zasobów .NET Framework w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym. Określ nazwę zasobu.

  Aby uzyskać więcej informacji, zobacz [assemblylinkresource (Link do zasobów .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Niejawne **logiczna** parametru.

  Umożliwia bardziej plik śledzenia do przechwytywania zachowanie łącza przyrostowe firmy. Zawsze zwraca `true`.

- **BaseAddress**

  Opcjonalnie **ciąg** parametru.

  Ustawia adres bazowy programu lub biblioteka DLL jest kompilowana. Określ `{address[,size] | @filename,key}`.

  Aby uzyskać więcej informacji, zobacz [uwzględniają (adres podstawowy)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  Opcjonalnie **logiczna** parametru.

  W przypadku opcji true wskazuje, że program MSBuild jest wywoływana z poziomu środowiska IDE. W przeciwnym razie wskazuje, że program MSBuild jest wywoływana z poziomu wiersza polecenia.

  Ten parametr nie ma żadnej opcji równoważne konsolidatora.

- **CLRImageType**

  Opcjonalnie **ciąg** parametru.

  Ustawia typ wspólnej obrazu od języka wspólnego (CLR).

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **Domyślne** -  *\<Brak >*

  - **ForceIJWImage** -  **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** -  **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** -  **/CLRIMAGETYPE:SAFE**

  Aby uzyskać więcej informacji, zobacz [/clrimagetype (określenie typu obrazu CLR)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  Opcjonalnie **ciąg** parametru.

  Zachowuje kod ostatniego błędu funkcji wywołanych za pomocą mechanizmu P/Invoke.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **Włączone** -  **/CLRSupportLastError**

  - **Wyłączone** -  **/CLRSupportLastError:NO**

  - **SystemDlls** -  **/CLRSupportLastError:SYSTEMDLL**

  Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRThreadAttribute**

  Opcjonalnie **ciąg** parametru.

  Określa jawnie atrybut wątkowości dla punktu wejścia programu CLR.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE: Brak**

  - **MTAThreadingAttribute** -  **: MTA**

  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE:STA**

  Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (atrybut wątku CLR Ustaw)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Opcjonalnie **logiczna** parametru.

  Określa, czy konsolidator zastosuje **SuppressUnmanagedCodeSecurityAttribute** na generowanych przez konsolidator wywołania metody P/Invoke z kodu zarządzanego, do macierzystych bibliotek DLL.

  Aby uzyskać więcej informacji, zobacz [opcji/clrunmanagedcodecheck (Dodaj atrybut SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Opcjonalnie **ciąg** parametru.

  Przygotowuje obraz do poprawki.

  Określ jedną z następujących wartości, które odpowiada opcji konsolidatora.

  - **Enabled** -  **/FUNCTIONPADMIN**

  - **X86Image** -  **/FUNCTIONPADMIN:5**

  - **X64Image** -  **/FUNCTIONPADMIN:6**

  - **ItaniumImage** -  **/FUNCTIONPADMIN:16**

  Aby uzyskać więcej informacji, zobacz [/FUNCTIONPADMIN (Utwórz obraz hotpatchable)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, wskazuje, że plik wykonywalny został sprawdzony w celu uzyskania zgodności z funkcją zapobiegania wykonywaniu danych Windows.

  Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  Opcjonalnie **String []** parametru.

  Powoduje, że ten parametr *opóźnione ładowanie* bibliotek DLL. Określ nazwę biblioteki DLL w celu opóźnienia ładowania.

  Aby uzyskać więcej informacji, zobacz [/delayload (Opóźnij importowanie ładowania)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, częściowo podpisuje zestaw. Domyślna wartość to `false`.

  Aby uzyskać więcej informacji, zobacz [/DelaySign (częściowo podpisać zestaw)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sterownik**

  Opcjonalnie **ciąg** parametru.

  Określenia tego parametru, aby zbudować sterownik trybu jądra Windows NT.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.

  - **NotSet** -  *\<none>*

  - **Driver** -  **/Driver**

  - **UpOnly** -  **/DRIVER:UPONLY**

  - **WDM** -  **/DRIVER:WDM**

  Aby uzyskać więcej informacji, zobacz [Driver/Driver (sterownik trybu jądra Windows NT)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  Opcjonalnie **String []** parametru.

  Osadza plik zasobów w zestawie. Określ nazwę pliku wymaganego zasobu. Opcjonalnie można określić nazwy logicznej, która jest używana do ładowania zasobu, a **PRYWATNEJ** opcja, która wskazuje w manifeście zestawu, czy plik zasobów jest prywatny.

  Aby uzyskać więcej informacji, zobacz [linkowany (Osadź zarządzany zasób)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, umożliwia identyczne składanie COMDAT.

  Aby uzyskać więcej informacji, zobacz `ICF[= iterations]` argument [od (optymalizacje)](/cpp/build/reference/opt-optimizations).

- **EnableUAC**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa, czy informacje kontroli konta użytkownika (UAC) będą osadzone w manifeście programu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  Opcjonalnie **ciąg** parametru.

  Określa funkcję punktu wejścia jako adres początkowy *.exe* pliku lub biblioteki DLL. Określ nazwę funkcji jako wartość parametru.

  Aby uzyskać więcej informacji, zobacz [/Entry (symbol punktu wejścia)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy program lub biblioteki DLL, który może zostać załadowany tylko pod swoim preferowanym adresem bazowym.

  Aby uzyskać więcej informacji, zobacz [/Fixed (stały adres podstawowy)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  Opcjonalnie **ciąg** parametru.

  Informuje konsolidator, aby utworzyć prawidłowy *.exe* pliku DLL nawet wtedy, gdy symbolu występują odwołania, ale nie zdefiniowana lub został zdefiniowany wiele razy.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Włączone** -   **/FORCE**

  - **MultiplyDefinedSymbolOnly** -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly** -   **/FORCE: NIEROZPOZNANA**

  Aby uzyskać więcej informacji, zobacz [/Force (Wymuszaj produkt wyjściowy pliku)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  Opcjonalnie **String []** parametru.

  Ten parametr informuje konsolidator, aby dodał określony symbol do tabeli symboli.

  Aby uzyskać więcej informacji, zobacz [/include (Wymuszaj odwołania do symboli)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  Opcjonalnie **ciąg** parametru.

  Ten parametr optymalizuje program, umieszczając określonego funkcje pakowane (COMDATs) w obrazie w ustalonej kolejności.

  Aby uzyskać więcej informacji, zobacz [/order (Put funkcje w kolejności)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy informacji o debugowaniu dla *.exe* pliku lub biblioteki DLL.

  Aby uzyskać więcej informacji, zobacz [/Debug (generowanie informacji o debugowaniu)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy plik manifestu side-by-side.

  Aby uzyskać więcej informacji, zobacz [/MANIFEST (Tworzenie manifestu zestawu side-by-side)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy *pliku mapy*. Rozszerzenie nazwy pliku mapy jest *.map*.

  Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  Opcjonalnie **ciąg** parametru.

  Określa ilość fizycznej pamięci na stosie, można przydzielić w danym momencie.

  Aby uzyskać więcej informacji, zobacz `commit` argument [/HEAP (Ustaw rozmiar sterty)](/cpp/build/reference/heap-set-heap-size). Zobacz też **HeapReserveSize** parametru.

- **HeapReserveSize**

  Opcjonalnie **ciąg** parametru.

  Określa Alokacja sterty całkowitej pamięci wirtualnej.

  Aby uzyskać więcej informacji, zobacz `reserve` argument [/HEAP (Ustaw rozmiar sterty)](/cpp/build/reference/heap-set-heap-size). Zobacz też **HeapCommitSize** parametru w tej tabeli.

- **IgnoreAllDefaultLibraries**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje konsolidator, aby usunąć jedną lub więcej bibliotek domyślnych z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych.

  Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa, czy jakiekolwiek atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane w *.idl* pliku.

  Aby uzyskać więcej informacji, zobacz [/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa, że biblioteka importowana, generowana przez tą konfigurację nie będzie importowana do projektów zależnych.

  Ten parametr nie odpowiada — opcja konsolidatora.

- **IgnoreSpecificDefaultLibraries**

  Opcjonalnie **String []** parametru.

  Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. Rozdzielaj wielokrotne biblioteki przy użyciu średników.

  Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, konsolidator generuje obraz tylko wtedy, gdy może utworzyć również tabelę obsługi bezpiecznych wyjątków obrazu.

  Aby uzyskać więcej informacji, zobacz [opcja/SAFESEH (obraz ma obsługi bezpiecznych wyjątków)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Nazwa biblioteki importu określonych przez użytkownika, która zastępuje domyślną nazwę biblioteki.

  Aby uzyskać więcej informacji, zobacz [/IMPLIB (Nazwij bibliotekę importowaną)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  Opcjonalnie **ciąg** parametru.

  Kontener, który zawiera klucz dla zestawu podpisem.

  Aby uzyskać więcej informacji, zobacz [/KeyContainer (Określ kontener klucza do podpisywania zestawu)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Zobacz też **KeyFile** parametru w tej tabeli.

- **KeyFile**

  Opcjonalnie **ciąg** parametru.

  Określa plik, który zawiera klucz dla zestawu podpisanego za pomocą.

  Aby uzyskać więcej informacji, zobacz [/KeyFile (Określ klucz lub parę kluczy, aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Zobacz też **KeyContainer** parametru.

- **LargeAddressAware**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, aplikacja może obsługiwać adresy większe niż 2 gigabajty.

  Aby uzyskać więcej informacji, zobacz [/largeaddressaware (Obsługa dużych adresów)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, kompiluje bibliotekę DLL jako plik wyjściowy głównego.

  Aby uzyskać więcej informacji, zobacz [/dll (kompilowanie biblioteki DLL)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  Opcjonalnie **ciąg** parametru.

  Pozwala zapewnić wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NoErrorReport** -   **/errorreport: Brak**

  - **PromptImmediately** -  **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**

  - **SendErrorReport** -  **/ERRORREPORT:SEND**

  Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy konsolidatora)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, włącza konsolidację przyrostową.

  Aby uzyskać więcej informacji, zobacz [/INCREMENTAL (łącz stopniowo)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa, czy biblioteka wyników z odwoływanych projektów jest automatycznie konsolidowana.

  Ten parametr nie odpowiada — opcja konsolidatora.

- **LinkStatus**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa, że konsolidator jest wyświetlenie wskaźnika postępu, który pokazuje, jaki procent łącze zostało zakończone.

  Aby uzyskać więcej informacji, zobacz `STATUS` argument [opcję/LTCG (Generowanie kodu Link-time)](/cpp/build/reference/ltcg-link-time-code-generation).

- **LinkTimeCodeGeneration**

  Opcjonalnie **ciąg** parametru.

  Określa opcje optymalizacji sterowanej profilem.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **Domyślne** -  *\<Brak >*

  - **UseLinkTimeCodeGeneration** -  **/LTCG**

  - **PGInstrument** -  **/LTCG:PGInstrument**

  - **PGOptimization** -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu Link-time)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  Opcjonalnie **ciąg** parametru.

  Zmienia domyślna nazwa pliku manifestu do określonej nazwy pliku.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (nazwa pliku manifestu)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje konsolidator, aby dołączał eksportowane funkcje w pliku mapy.

  Aby uzyskać więcej informacji, zobacz `EXPORTS` argument [/MapInfo (Dołącz informacje mapfile)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  Opcjonalnie **ciąg** parametru.

  Zmienia domyślna nazwa pliku mapy z określoną nazwą pliku.

- **MergedIDLBaseFileName**

  Opcjonalnie **ciąg** parametru.

  Określa nazwę pliku i rozszerzenie nazwy pliku *.idl* pliku.

  Aby uzyskać więcej informacji, zobacz [/idlout (pliki wyjściowe Name MIDL)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  Opcjonalnie **ciąg** parametru.

  Łączy sekcje w obrazie. Określ `from-section=to-section`.

  Aby uzyskać więcej informacji, zobacz [/merge (Połącz sekcje)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  Opcjonalnie **ciąg** parametru.

  Określ nazwę pliku, który zawiera opcje wiersza polecenia MIDL.

  Aby uzyskać więcej informacji, zobacz [/MIDL (Opcje wiersza polecenia MIDL określić)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **MinimumRequiredVersion**

  Opcjonalnie **ciąg** parametru.

  Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65535.

- **ModuleDefinitionFile**

  Opcjonalnie **ciąg** parametru.

  Określa nazwę [plik definicji modułu](/cpp/build/reference/module-definition-dot-def-files).

  Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  Opcjonalnie **ciąg** parametru.

  Dołącza określony program szczątkowy systemu MS-DOS do programu systemu Win32.

  Aby uzyskać więcej informacji, zobacz [/stub (nazwa pliku klasy zastępczej MS-DOS)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **NoEntryPoint**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, określa bibliotekę DLL tylko do zasobów.

  Aby uzyskać więcej informacji, zobacz [/noentry (Brak punktu wejścia)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Niejawne **String []** parametru.

  Określa pliki obiektów, które są połączone.

- **OptimizeReferences**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, eliminuje funkcje i/lub dane, które nigdy nie są wywoływane.

  Aby uzyskać więcej informacji, zobacz `REF` argument [od (optymalizacje)](/cpp/build/reference/opt-optimizations).

- **OutputFile**

  Opcjonalnie **ciąg** parametru.

  Przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.

  Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true` i włączono rejestrowanie wyników rejestru wymusza zapisuje **HKEY_CLASSES_ROOT** do **HKEY_CURRENT_USER**.

- **PreprocessOutput**

  Opcjonalnie `ITaskItem[]` parametru.

  Określa tablicę elementów dane wyjściowe preprocesora, które może być używany i wyemitowane przez zadania.

- **PreventDllBinding**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, wskazuje *Bind.exe* która obraz połączony nie ma zostać powiązana.

  Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (Zapobiegaj powiązaniu biblioteki DLL)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy plik wyjściowy, który może być używany z **narzędzia do oceny wydajności** profilera.

  Aby uzyskać więcej informacji, zobacz [/profile (profiler narzędzi wydajności)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  Opcjonalnie **ciąg** parametru.

  Określa nazwę *.pgd* pliku, który będzie używany do przechowywania informacji na temat uruchomiony program

  Aby uzyskać więcej informacji, zobacz [/PGD (Określ bazę danych dla optymalizacji sterowanej profilem)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Opcjonalnie **ciąg** parametru.

  Określa nazwę bazy danych programu (PDB) tworzonego przez konsolidatora.

  Aby uzyskać więcej informacji, zobacz [/PDB (Użyj bazy danych programu)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, generuje obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu *randomizacji układu przestrzeni adresów* (ASLR) funkcja systemu Windows.

  Aby uzyskać więcej informacji, zobacz [opcja/DynamicBase (randomizacji układu przestrzeni adresowej Użyj)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, rejestruje główny wynik tej kompilacji.

- **SectionAlignment**

  Opcjonalnie **całkowitą** parametru.

  Określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Wartość tego parametru jest jednostka liczba bajtów i jest potęgą liczby dwa.

  Aby uzyskać więcej informacji, zobacz [/align (wyrównanie sekcji)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, ustawia sumę kontrolną w nagłówku *.exe* pliku.

  Aby uzyskać więcej informacji, zobacz [/Release (Ustaw sumę kontrolną)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  Opcjonalnie **ciąg** parametru.

  Określa poziom szczegółowości raportów postępu dla operacji łączenia.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NotSet** -  *\<none>*

  - **LinkVerbose** -  **/VERBOSE**

  - **LinkVerboseLib** -  **/VERBOSE:Lib**

  - **LinkVerboseICF** -  **/VERBOSE:ICF**

  - **LinkVerboseREF** -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** -  **/VERBOSE:CLR**

  Aby uzyskać więcej informacji, zobacz [opcjami/verbose (Drukuj komunikaty o postępie)](/cpp/build/reference/verbose-print-progress-messages).

- **Źródła**

  Wymagane `ITaskItem[]` parametru.

  Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.

- **SpecifySectionAttributes**

  Opcjonalnie **ciąg** parametru.

  Określa atrybuty sekcji. Zastępuje atrybuty, które zostały określone podczas *.obj* pliku sekcji został skompilowany.

  Aby uzyskać więcej informacji, zobacz [/Section (Określ atrybuty sekcji)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  Opcjonalnie **ciąg** parametru.

  Określa ilość pamięci fizycznej w każdej alokacji, gdy jest przydzielany dodatkowej pamięci.

  Aby uzyskać więcej informacji, zobacz `commit` argument [/STACK (twórz stos z alokacji)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  Opcjonalnie **ciąg** parametru.

  Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.

  Aby uzyskać więcej informacji, zobacz `reserve` argument [/STACK (twórz stos z alokacji)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Opcjonalnie **ciąg** parametru.

  Tworzy drugi plik bazy danych (PDB) programu, które pomija symbole, których nie chcesz dystrybuować swoim klientom. Określ nazwę drugiego pliku PDB.

  Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symboli prywatnych)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **SubSystem**

  Opcjonalnie **ciąg** parametru.

  Określa środowisko dla pliku wykonywalnego.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NotSet** -  *\<none>*

  - **Konsola** - **opcji**

  - **Windows** -  **/SUBSYSTEM:WINDOWS**

  - **Native** -  **/SUBSYSTEM:NATIVE**

  - **Aplikacja EFI** -  **/SUBSYSTEM:EFI_APPLICATION**

  - **Sterownik usługi rozruchu interfejsu EFI** -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** -  **/SUBSYSTEM:EFI_ROM**

  - **EFI Runtime** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**

  - **POSIX** -  **/SUBSYSTEM:POSIX**

  Aby uzyskać więcej informacji, zobacz [/Subsystem (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje konsolidator, nie można dołączyć powiązania tabeli adresów importowania (IAT) do obrazu końcowego.

  Aby uzyskać więcej informacji, zobacz `NOBIND` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje funkcję pomocnika obciążenia opóźnienia, aby wspierała jawne zwalnianie biblioteki DLL.

  Aby uzyskać więcej informacji, zobacz `UNLOAD` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.

  Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (konsolidator)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje system operacyjny, aby najpierw skopiować konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.

  Aby uzyskać więcej informacji, zobacz `CD` argument [swaprun (Załaduj dane wyjściowe konsolidatora do pliku swap)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz też **SwapRunFromNET** parametru.

- **SwapRunFromNET**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, informuje system operacyjny, aby najpierw skopiować konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.

  Aby uzyskać więcej informacji, zobacz `NET` argument [swaprun (Załaduj dane wyjściowe konsolidatora do pliku swap)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz też **SwapRunFromCD** parametru w tej tabeli.

- **TargetMachine**

  Opcjonalnie **ciąg** parametru.

  Określa platformę docelową dla tego programu lub DLL.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **NotSet** -  *\<none>*

  - **MachineARM** -  **/MACHINE:ARM**

  - **MachineEBC** -  **/MACHINE:EBC**

  - **MachineIA64** -  **/MACHINE:IA64**

  - **MachineMIPS** -  **/MACHINE:MIPS**

  - **MachineMIPS16** -  **/MACHINE:MIPS16**

  - **MachineMIPSFPU** -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**

  - **MachineSH4** -  **/MACHINE:SH4**

  - **MachineTHUMB** -  **/MACHINE:THUMB**

  - **MachineX64** -  **/MACHINE:X64**

  - **MachineX86** -  **/MACHINE:X86**

  Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER dllcharacteristics w opcjonalnym nagłówku obrazu programu. Gdy ta flaga jest ustawiona, serwera terminali nie wprowadzi pewnych zmian aplikacji.

  Aby uzyskać więcej informacji, zobacz [/tsaware (Utwórz serwer terminali pamiętać aplikacji)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  Opcjonalnie **ciąg** parametru.

  Określa katalog dziennika śledzenia.

- **TreatLinkerWarningAsErrors**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator wygeneruje ostrzeżenie.

  Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.

  Aby uzyskać więcej informacji, zobacz [/noassembly (Utwórz moduł MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  Opcjonalnie **ciąg** parametru.

  Określa nazwę pliku i rozszerzenie nazwy pliku *.tlb* pliku. Określ nazwę pliku lub ścieżkę i nazwę pliku.

  Aby uzyskać więcej informacji, zobacz [/tlbout (Nazywanie pliku .tlb)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  Opcjonalnie **całkowitą** parametru.

  Określa wartość określone przez użytkownika dla biblioteki typów, utworzone przez konsolidator. Określ wartość z zakresu od 1 do 65 535.

  Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla TypeLib)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  Opcjonalnie **ciąg** parametru.

  Określa wymagany poziom wykonywania dla aplikacji, gdy jest uruchamiana przy użyciu kontroli konta użytkownika.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Aby uzyskać więcej informacji, zobacz `level` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`, aplikacja pomija poziomów ochrony interfejsu użytkownika i dyski danych wejściowych do wyższych uprawnień okien na pulpicie; w przeciwnym razie `false`.

  Aby uzyskać więcej informacji, zobacz `uiAccess` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  Opcjonalnie **logiczna** parametru.

  Jeśli `true`i wejścia do narzędzia bibliotekarza są używane zamiast pliku biblioteki samego w sobie podczas produktów wyjściowych biblioteki zależności projektów są dołączane.

- **Wersja**

  Opcjonalnie **ciąg** parametru.

  Umieszczenie numeru wersji w nagłówku *.exe* lub *.dll* pliku. Określ "`major[.minor]`". `major` i `minor` argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535.

  Aby uzyskać więcej informacji, zobacz [/Version (informacje o wersji)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

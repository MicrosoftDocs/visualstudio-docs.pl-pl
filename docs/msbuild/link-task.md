---
title: Zadanie łącza | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865352"
---
# <a name="link-task"></a>Link — Zadanie

Zawija narzędzie konsolidatora Języka Microsoft C++, *link.exe*. Narzędzie konsolidator łączy pliki obiektów i biblioteki common object file format (COFF), aby utworzyć plik wykonywalny (*.exe*) lub bibliotekę dynamicznego łącza (DLL). Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](/cpp/build/reference/linker-options) i [Użyj msbuild z wiersza polecenia](/cpp/build/msbuild-visual-cpp) i Użyj zestawu narzędzi Microsoft [C++ z wiersza polecenia](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametry

 Poniżej opisano parametry zadania **Łącze.** Większość parametrów zadania i kilka zestawów parametrów odpowiada opcji wiersza polecenia.

- **DodatkoweZależności**

  Parametr **Opcjonalny ciąg[].**

  Określa listę plików wejściowych do dodania do polecenia.

  Aby uzyskać więcej informacji, zobacz [pliki wejściowe LINK](/cpp/build/reference/link-input-files).

- **AdditionalLibraryDirectory**

  Parametr **Opcjonalny ciąg[].**

  Zastępuje ścieżkę biblioteki środowiska. Określ nazwę katalogu.

  Aby uzyskać więcej informacji, zobacz [/LIBPATH (Additional Libpath)](/cpp/build/reference/libpath-additional-libpath).

- **DodatkoweZależności wyrządzania**

  Parametr **Opcjonalny ciąg[].**

  Określa atrybuty, które zostaną `dependency` umieszczone w sekcji pliku manifestu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu).](/cpp/build/reference/manifestdependency-specify-manifest-dependencies) Zobacz też [Pliki konfiguracyjne programu Publisher](/windows/desktop/SbsCs/publisher-configuration-files).

- **Dodatkoweopcje**

  Opcjonalny parametr **String.**

  Lista opcji konsolidatora określona w wierszu polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji konsolidatora, które nie są reprezentowane przez żaden inny parametr zadania **łącza.**

  Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  Parametr **Opcjonalny ciąg[].**

  Dodaje odwołanie do modułu do złożenia.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **Allowizolation (Nazwiązanie)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,powoduje, że system operacyjny wykonuje wyszukiwania manifestów i ładunki. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było manifestu.

  Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (Wyszukiwanie manifestu)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug (AssemblyDebug)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, emituje **DebuggableAttribute** atrybut wraz z debugowania informacji śledzenia i wyłącza optymalizacje JIT. Jeśli `false`, emituje **DebuggableAttribute** atrybut, ale wyłącza debugowania informacji śledzenia i umożliwia optymalizacje JIT.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Add DebuggableAttribute)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  Parametr **Opcjonalny ciąg[].**

  Tworzy łącze do zasobu programu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Określ nazwę zasobu.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYLINKRESOURCE (Link do zasobu .NET Framework)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **Śledzenie pliku atrybutów**

  Niejawny parametr **logiczny.**

  Umożliwia głębsze śledzenie plików w celu przechwytywania zachowania przyrostowego łącza. Zawsze zwraca wartość `true`.

- **Baseaddress**

  Opcjonalny parametr **String.**

  Ustawia adres podstawowy dla tworzonego programu lub biblioteki DLL. Podaj wartość `{address[,size] | @filename,key}`.

  Aby uzyskać więcej informacji, zobacz [/BASE (adres podstawowy)](/cpp/build/reference/base-base-address).

- **BuildingInIDE (BudynekInIDE)**

  Opcjonalny parametr **logiczny.**

  Jeśli true, wskazuje, że MSBuild jest wywoływany z IDE. W przeciwnym razie wskazuje, że MSBuild jest wywoływany z wiersza polecenia.

  Ten parametr nie ma równoważnej opcji konsolidatora.

- **Typ CLRImage**

  Opcjonalny parametr **String.**

  Ustawia typ obrazu środowiska uruchomieniowego języka wspólnego (CLR).

  Określ jedną z następujących wartości, z których każda odpowiada opcji konsolidatora.

  - **Domyślnie brak** - >*\<*

  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**

  Aby uzyskać więcej informacji, zobacz [/CLRIMAGETYPE (Określ typ obrazu CLR).](/cpp/build/reference/clrimagetype-specify-type-of-clr-image)

- **CLRSupportLastError**

  Opcjonalny parametr **String.**

  Zachowuje ostatni kod błędu funkcji wywoływanych za pośrednictwem mechanizmu P/Invoke.

  Określ jedną z następujących wartości, z których każda odpowiada opcji konsolidatora.

  - **Włączono** - **/CLRSupportLastError**

  - **Wyłączone** - **/CLRSupportLastError:NIE**

  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**

  Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj ostatni kod błędu dla wywołań PInvoke).](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)

- **CLRThreadAttribute**

  Opcjonalny parametr **String.**

  Jawnie określa atrybut wątków dla punktu wejścia programu CLR.

  Określ jedną z następujących wartości, z których każda odpowiada opcji konsolidatora.

  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingAttribute** - **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**

  Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (Set CLR thread attribute)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  Opcjonalny parametr **logiczny.**

  Określa, czy konsolidator **zastosuje suppressunmanagedCodeSecurityAttribute** do wywołań P/Invoke generowanych przez program konsolidatora z kodu zarządzanego do natywnych bibliotek DLL.

  Aby uzyskać więcej informacji, zobacz [/CLRUNMANAGEDCODECHECK (Add SuppressUnmanagedCodeSecurityAttribute)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  Opcjonalny parametr **String.**

  Przygotowuje obraz do gorących poprawek.

  Określ jedną z następujących wartości, która odpowiada opcji konsolidatora.

  - **Włączono** - **/FUNCTIONPADMIN**

  - **X86Image** - **/FUNCTIONPADMIN:5**

  - **X64Image** - **/FUNCTIONPADMIN:6**

  - **ItaniumImage** - **/FUNCTIONPADMIN:16**

  Aby uzyskać więcej informacji, zobacz [/FUNCTIONPADMIN (Tworzenie obrazu z funkcją hotpatchable)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataWykonańprevention**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, wskazuje, że plik wykonywalny został przetestowany jako zgodny z funkcją zapobiegania wykonywaniu danych systemu Windows.

  Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (Compatible with Data Execution Prevention)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **BibliotekiDLloadloadload delay**

  Parametr **Opcjonalny ciąg[].**

  Ten parametr powoduje *opóźnione ładowanie* bibliotek DLL. Określ nazwę biblioteki DLL, aby opóźnić ładowanie.

  Aby uzyskać więcej informacji, zobacz [/DELAYLOAD (Delay load import)](/cpp/build/reference/delayload-delay-load-import).

- **Delaysign**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, częściowo podpisze zespół. Domyślna wartość to `false`.

  Aby uzyskać więcej informacji, zobacz [/DELAYSIGN (Częściowo podpisz zespół)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sterownik**

  Opcjonalny parametr **String.**

  Określ ten parametr, aby utworzyć sterownik trybu jądra systemu Windows NT.

  Określ jedną z następujących wartości, z których każda odpowiada opcji konsolidatora.

  - **NotSet brak** - >*\<*

  - **Sterownik** - **/Sterownik**

  - **UpOnly** - **/DRIVER:UPONLY**

  - **WDM** - **/DRIVER:WDM**

  Aby uzyskać więcej informacji, zobacz [/DRIVER (sterownik trybu jądra systemu Windows NT).](/cpp/build/reference/driver-windows-nt-kernel-mode-driver)

- **Plik embedManagedResourceFile**

  Parametr **Opcjonalny ciąg[].**

  Osadza plik zasobów w zestawie. Określ wymaganą nazwę pliku zasobu. Opcjonalnie należy określić nazwę logiczną, która jest używana do ładowania zasobu, oraz opcję **PRIVATE,** która wskazuje w manifeście zestawu, że plik zasobu jest prywatny.

  Aby uzyskać więcej informacji, zobacz [/ASSEMBLYRESOURCE (Osadzić zarządzany zasób)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **WłączcomdatFolding**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, umożliwia identyczne składanie COMDAT.

  Aby uzyskać więcej `ICF[= iterations]` informacji, zobacz argument [/OPT (Optymalizacje)](/cpp/build/reference/opt-optimizations).

- **EnableUAC (Umożliwianieac)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa, że informacje kontroli konta użytkownika (Kontrola konta użytkownika) są osadzone w manifeście programu.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (Osadza informacje uac w manifeście)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol (Punkt wejścia)**

  Opcjonalny parametr **String.**

  Określa funkcję punktu wejścia jako adres początkowy pliku exe lub *biblioteki* DLL. Określ nazwę funkcji jako wartość parametru.

  Aby uzyskać więcej informacji, zobacz [/ENTRY (symbol punktu wejścia).](/cpp/build/reference/entry-entry-point-symbol)

- **Adres o stałej bazie**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,tworzy program lub bibliotekę DLL, które można załadować tylko pod preferowanym adresem podstawowym.

  Aby uzyskać więcej informacji, zobacz [/FIXED (Stały adres podstawowy)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput (ForceFileOutput)**

  Opcjonalny parametr **String.**

  Informuje konsolidatora, aby utworzył prawidłowy plik exe lub *bibliotekę* DLL, nawet jeśli symbol jest określany, ale nie jest zdefiniowany lub jest zdefiniowany jako mnożona.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Włączone** - **/ŻYCIE**

  - **MultiplyDefinedSymbolOnly /FORCE:MULTIPLE MultiplyDefinedSymbolOnly /FORCE:MULTIPLE MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE MultiplyDe**

  - **UndefinedSymbolOnly** - **/FORCE:UNRESOLVED**

  Aby uzyskać więcej informacji, zobacz [/FORCE (Force file output)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences (Wymbole)**

  Parametr **Opcjonalny ciąg[].**

  Ten parametr informuje konsolidatora o dodaniu określonego symbolu do tabeli symboli.

  Aby uzyskać więcej informacji, zobacz [/INCLUDE (Wymusz odwołania do symboli)](/cpp/build/reference/include-force-symbol-references).

- **Kolejność funkcji**

  Opcjonalny parametr **String.**

  Ten parametr optymalizuje program, umieszczając określone spakowane funkcje (COMDATs) w obrazie w określonej kolejności.

  Aby uzyskać więcej informacji, zobacz [/ORDER (Ugasić funkcje w kolejności)](/cpp/build/reference/order-put-functions-in-order).

- **Generowanie informacji o debuginformacji**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program , tworzy informacje debugowania dla pliku *.exe* lub biblioteki DLL.

  Aby uzyskać więcej informacji, zobacz [/DEBUG (Generowanie informacji debugowania)](/cpp/build/reference/debug-generate-debug-info).

- **Generowaniemanifest**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, tworzy plik manifestu obok siebie.

  Aby uzyskać więcej informacji, zobacz [/MANIFEST (Tworzenie manifestu zestawu obok siebie)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **Generowanie pliku mapy**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`plik *mapy*zostanie utwory . Rozszerzeniem nazwy pliku mapy jest *.map*.

  Aby uzyskać więcej informacji, zobacz [/MAP (Generowanie pliku map)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize (Rozmiar heapCommitSize)**

  Opcjonalny parametr **String.**

  Określa ilość pamięci fizycznej na stercie do przydzielenia w czasie.

  Aby uzyskać więcej `commit` informacji, zobacz argument w [/HEAP (Set heap size)](/cpp/build/reference/heap-set-heap-size). Zobacz też **parametr HeapReserveSize.**

- **Rozmiar stertyReserveSize**

  Opcjonalny parametr **String.**

  Określa całkowitą alokację sterty w pamięci wirtualnej.

  Aby uzyskać więcej `reserve` informacji, zobacz argument w [/HEAP (Set heap size)](/cpp/build/reference/heap-set-heap-size). Zobacz także **HeapCommitSize** parametr w tej tabeli.

- **IgnoreAllDefaultBraries**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,informuje konsolidatora o usunięciu jednej lub więcej bibliotek domyślnych z listy bibliotek, które wyszukuje po usunięciu odwołań zewnętrznych.

  Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa, że wszelkie atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane w pliku *.idl.*

  Aby uzyskać więcej informacji, zobacz [/IGNOREIDL (Nie przetwarzaj atrybutów w MIDL)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportBrary**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa, że biblioteka importu generowana przez tę konfigurację nie powinna być importowana do projektów zależnych.

  Ten parametr nie odpowiada opcji konsolidatora.

- **IgnoreSpecificDefaultLibraries**

  Parametr **Opcjonalny ciąg[].**

  Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. Oddziel wiele bibliotek przy użyciu średników.

  Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`konsolidator tworzy obraz tylko wtedy, gdy może również tworzyć tabelę programów obsługi wyjątków bezpiecznego obrazu.

  Aby uzyskać więcej informacji, zobacz [/SAFESEH (Obraz ma bezpieczne programy obsługi wyjątków)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Określona przez użytkownika nazwa biblioteki importu, która zastępuje domyślną nazwę biblioteki.

  Aby uzyskać więcej informacji, zobacz [/IMPLIB (Biblioteka importu nazw)](/cpp/build/reference/implib-name-import-library).

- **Klawiatura KeyContainer**

  Opcjonalny parametr **String.**

  Kontener, który zawiera klucz dla zestawu podpisanego.

  Aby uzyskać więcej informacji, zobacz [/KEYCONTAINER (Określ kontener kluczy do podpisania zestawu)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Zobacz też parametr **KeyFile** w tej tabeli.

- **Keyfile**

  Opcjonalny parametr **String.**

  Określa plik zawierający klucz dla podpisanego zestawu.

  Aby uzyskać więcej informacji, zobacz [/KEYFILE (Określ parę klawiszy lub klawiszy, aby podpisać zestaw)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Zobacz także **parametr KeyContainer.**

- **DużeAddressAware**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`aplikacja może obsługiwać adresy większe niż 2 gigabajty.

  Aby uzyskać więcej informacji, zobacz [/LARGEADDRESSAWARE (Obsługa dużych adresów)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL (linkDLL)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, buduje bibliotekę DLL jako główny plik wyjściowy.

  Aby uzyskać więcej informacji, zobacz [/DLL (Tworzenie biblioteki DLL)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting (Zgłaszanie)**

  Opcjonalny parametr **String.**

  Umożliwia podanie informacji o błędzie kompilatora wewnętrznego (ICE) bezpośrednio do firmy Microsoft.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NoErrorReport** - **/ERRORREPORT:BRAK**

  - **PromptImmediately** - **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**

  - **SendErrorReport** - **/ERRORREPORT:WYŚLIJ**

  Aby uzyskać więcej informacji, zobacz [/ERRORREPORT (Report internal linker errors)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **Łącze Przyrostowe**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program Umożliwia łączenie przyrostowe.

  Aby uzyskać więcej informacji, zobacz [/INCREMENTAL (Łącze przyrostowo)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryZależności**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa, że dane wyjściowe biblioteki z zależności projektu są automatycznie połączone w.

  Ten parametr nie odpowiada opcji konsolidatora.

- **Status łącza**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa, że konsolidator jest wyświetlanie wskaźnika postępu, który pokazuje, jaki procent łącza jest ukończony.

  Aby uzyskać więcej `STATUS` informacji, zobacz argument [/LTCG (Generowanie kodu czasu łącza).](/cpp/build/reference/ltcg-link-time-code-generation)

- **Pouczanie łącza timecode**

  Opcjonalny parametr **String.**

  Określa opcje optymalizacji z przewodnikiem po profilu.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Domyślnie brak** - >*\<*

  - **UseLinkTimeCodeGeneration** - **/LTCG**

  - **PGInstrument** - **/LTCG:PGInstrument**

  - **PGOptymizacja** - **/LTCG:PGOptimize**

  - **PGUpdate**

    \-**/LTCG:PGUpdate**

  Aby uzyskać więcej informacji, zobacz [/LTCG (Generowanie kodu czasu łącza)](/cpp/build/reference/ltcg-link-time-code-generation).

- **Plik manifestu**

  Opcjonalny parametr **String.**

  Zmienia domyślną nazwę pliku manifestu na określoną nazwę pliku.

  Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (Plik manifestu nazwa)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program informuje konsolidator o uwzględnienie wyeksportowanych funkcji w pliku mapy.

  Aby uzyskać więcej `EXPORTS` informacji, zobacz argument [/MAPINFO (Dołącz informacje w pliku map)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **Nazwa pliku mapy**

  Opcjonalny parametr **String.**

  Zmienia domyślną nazwę pliku mapy na określoną nazwę pliku.

- **Nazwa pliku scalania IDLBaseFileName**

  Opcjonalny parametr **String.**

  Określa nazwę pliku i rozszerzenie nazwy pliku *.idl.*

  Aby uzyskać więcej informacji, zobacz [/IDLOUT (Nazwa plików wyjściowych MIDL)](/cpp/build/reference/idlout-name-midl-output-files).

- **Scalaniesekcje**

  Opcjonalny parametr **String.**

  Łączy sekcje na obrazie. Podaj wartość `from-section=to-section`.

  Aby uzyskać więcej informacji, zobacz [/MERGE (Łączenie sekcji)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile (Plik MidlCommandFile)**

  Opcjonalny parametr **String.**

  Określ nazwę pliku zawierającego opcje wiersza polecenia MIDL.

  Aby uzyskać więcej informacji, zobacz [/MIDL (Określ opcje wiersza polecenia MIDL)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **Minimalna wymaganaweryjda**

  Opcjonalny parametr **String.**

  Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi w zakresie od 0 do 65535.

- **Plik zdefiniowanie modułu**

  Opcjonalny parametr **String.**

  Określa nazwę pliku [definicji modułu](/cpp/build/reference/module-definition-dot-def-files).

  Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu).](/cpp/build/reference/def-specify-module-definition-file)

- **Nazwa pliku MSDOSStubfileName**

  Opcjonalny parametr **String.**

  Dołącza określony program skrótowy MS-DOS do programu Win32.

  Aby uzyskać więcej informacji, zobacz [/STUB (nazwa pliku skrótowego SYSTEMU MS-DOS).](/cpp/build/reference/stub-ms-dos-stub-file-name)

- **NoEntryPunkt**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, określa dll tylko do zasobów.

  Aby uzyskać więcej informacji, zobacz [/NOENTRY (Brak punktu wejścia)](/cpp/build/reference/noentry-no-entry-point).

- **Pliki obiektów**

  Niejawny **ciąg[]** parametr.

  Określa połączone pliki obiektów.

- **Optymalizacjareferencje**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, eliminuje funkcje i/lub dane, które nigdy nie są przywoły, o których nie ma odniesienia.

  Aby uzyskać więcej `REF` informacji, zobacz argument w [/OPT (Optymalizacje)](/cpp/build/reference/opt-optimizations).

- **Outputfile**

  Opcjonalny parametr **String.**

  Zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidator.

  Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection (Kierunek peruserredirection)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true` i zarejestruj dane wyjściowe jest włączona, wymusza zapisy rejestru **do HKEY_CLASSES_ROOT,** które mają zostać przekierowane do **HKEY_CURRENT_USER**.

- **Przetwory wstępneOutput**

  Parametr `ITaskItem[]` opcjonalny.

  Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.

- **PreventDllBinding**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, wskazuje *Bind.exe,* że połączony obraz nie powinien być związany.

  Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (Prevent DLL binding)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,tworzy plik wyjściowy, który może być używany z profilera **narzędzi wydajności.**

  Aby uzyskać więcej informacji, zobacz [/PROFILE (Performance Tools profiler)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfilGuidedDatabase**

  Opcjonalny parametr **String.**

  Określa nazwę pliku *.pgd,* który będzie używany do przechowywania informacji o uruchomionym programie

  Aby uzyskać więcej informacji, zobacz [/PGD (Określanie bazy danych dla optymalizacji z przewodnikiem profilu)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  Opcjonalny parametr **String.**

  Określa nazwę bazy danych programu (PDB), którą tworzy konsolidator.

  Aby uzyskać więcej informacji, zobacz [/PDB (Użyj bazy danych programów)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program , generuje obraz wykonywalny, który może być losowo przesiąknięty w czasie ładowania przy użyciu funkcji *randomizacji układu przestrzeni adresowej* (ASLR) systemu Windows.

  Aby uzyskać więcej informacji, zobacz [/DYNAMICBASE (Użyj randomizacji układu przestrzeni adresowej)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RejestracjaOutput**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, rejestruje podstawowe dane wyjściowe tej kompilacji.

- **Wyrównanie sekcji**

  Opcjonalny parametr **Liczba Całkowita.**

  Określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Wartość parametru jest jednostkową liczbą bajtów i jest potęgą dwóch.

  Aby uzyskać więcej informacji, zobacz [/ALIGN (Wyrównanie przekroju)](/cpp/build/reference/align-section-alignment).

- **SetChecksum ( SetChecksum )**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,ustawia sumę kontrolną w nagłówku pliku *exe.*

  Aby uzyskać więcej informacji, zobacz [/RELEASE (Set the checksum)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress (Proces pokażeń)**

  Opcjonalny parametr **String.**

  Określa szczegółowość raportów postępu dla operacji łączenia.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NotSet brak** - >*\<*

  - **LinkVerbose** - **/VERBOSE**

  - **LinkVerboseLib** - **/VERBOSE:Lib**

  - **LinkVerboseICF** - **/VERBOSE:ICF**

  - **LinkVerboseREF** - **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** - **/VERBOSE:CLR**

  Aby uzyskać więcej informacji, zobacz [/VERBOSE (Drukuj komunikaty postępu)](/cpp/build/reference/verbose-print-progress-messages).

- **Źródeł**

  Wymagany parametr interfejsu `ITaskItem[]`.

  Definiuje tablicę elementów pliku źródłowego MSBuild, które mogą być używane i emitowane przez zadania.

- **SpecifySectionAttributes (Określanie atrybutów)**

  Opcjonalny parametr **String.**

  Określa atrybuty sekcji. Zastępuje to atrybuty, które zostały ustawione podczas kompilowania pliku *obj* dla sekcji.

  Aby uzyskać więcej informacji, zobacz [/SECTION (Określ atrybuty sekcji).](/cpp/build/reference/section-specify-section-attributes)

- **Rozmiar stosu**

  Opcjonalny parametr **String.**

  Określa ilość pamięci fizycznej w każdej alokacji po przydzieleniu dodatkowej pamięci.

  Aby uzyskać więcej `commit` informacji, zobacz argument [/STACK (Alokacje stosu)](/cpp/build/reference/stack-stack-allocations).

- **Rozmiar usługi StackReserveSize**

  Opcjonalny parametr **String.**

  Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.

  Aby uzyskać więcej `reserve` informacji, zobacz argument [/STACK (Alokacje stosu)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  Opcjonalny parametr **String.**

  Tworzy drugi plik bazy danych programu (PDB), który pomija symbole, których nie chcesz rozpowszechniać wśród klientów. Określ nazwę drugiego pliku PDB.

  Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (Strip private symbols)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Podsystemu**

  Opcjonalny parametr **String.**

  Określa środowisko dla pliku wykonywalnego.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NotSet brak** - >*\<*

  - **Konsola** - **/SUBSYSTEM:KONSOLA**

  - **Windows** - **/PODSYSTEM:WINDOWS**

  - **Natywne** - **/PODSYSTEM:NATYWNE**

  - **Aplikacja EFI** - **/PODSYSTEM:EFI_APPLICATION**

  - **Sterownik usługi rozruchu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**

  - **Środowisko wykonawcze** - EFI **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** - **/PODSYSTEM:WINDOWSCE**

  - **POSIX** - **/PODSYSTEM:POSIX**

  Aby uzyskać więcej informacji, zobacz [/SUBSYSTEM (Określ podsystem)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,informuje konsolidatora, aby nie dołączał do obrazu końcowego tabeli adresów importu (IAT) do wiązania.

  Aby uzyskać więcej `NOBIND` informacji, zobacz argument [/DELAY (Ustawienia importu obciążenia opóźnienia)](/cpp/build/reference/delay-delay-load-import-settings).

- **ObsługaUnloadOfDelayLoadedDLL**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, informuje funkcję pomocnika opóźnienia ładowania do obsługi jawnego zwalniania biblioteki DLL.

  Aby uzyskać więcej `UNLOAD` informacji, zobacz argument [/DELAY (Ustawienia importu obciążenia opóźnienia)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner (SuppressStartupBanner)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.

  Aby uzyskać więcej informacji, zobacz [/NOLOGO (Pomijanie banera startowego) (konsolidator)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program , nakazuje systemowi operacyjnemu najpierw skopiować dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomić obraz stamtąd.

  Aby uzyskać więcej `CD` informacji, zobacz argument [/SWAPRUN (Dane wyjściowe modułu ładowania do wymiany pliku)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz też **parametr SwapRunFromNET.**

- **SwapRunFromNET (SwapRunFromNET)**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program , nakazuje systemowi operacyjnemu najpierw skopiować dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomić obraz stamtąd.

  Aby uzyskać więcej `NET` informacji, zobacz argument [/SWAPRUN (Dane wyjściowe modułu ładowania do wymiany pliku)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file). Zobacz także **Parametr SwapRunFromCD** w tej tabeli.

- **Grupa docelowa**

  Opcjonalny parametr **String.**

  Określa platformę docelową programu lub biblioteki DLL.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **NotSet brak** - >*\<*

  - **MACHINEARM** - **/MASZYNA:ARM**

  - **MachineEBC** - **/MASZYNA:EBC**

  - **MachineIA64** - **/MASZYNA:IA64**

  - **MachineMIPS** - **/MACHINE:MIPS**

  - **MachineMIPS16** - **/MASZYNA:MIPS16**

  - **MachineMIPSFPU** - **/MASZYNA:MIPSFPU**

  - **MachineMIPSFPU16** - **/MASZYNA:MIPSFPU16**

  - **MachineSH4** - **/MASZYNA:SH4**

  - **MACHINETHUMB** - **/MASZYNA:KCIUK**

  - **MachineX64** - **/MASZYNA:X64**

  - **MachineX86** - **/MASZYNA:X86**

  Aby uzyskać więcej informacji, zobacz [/MACHINE (Określ platformę docelową).](/cpp/build/reference/machine-specify-target-platform)

- **TerminalServerAware**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian w aplikacji.

  Aby uzyskać więcej informacji, zobacz [/TSAWARE (Tworzenie aplikacji obsługującej serwer terminali).](/cpp/build/reference/tsaware-create-terminal-server-aware-application)

- **TrackerLogDirectory (TrackerLogDirectory)**

  Opcjonalny parametr **String.**

  Określa katalog dziennika modułu śledzącego.

- **TreatLinkerWarningAsErrors**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program ,powoduje, że nie ma wygenerowanego pliku wyjściowego, jeśli konsolidator generuje ostrzeżenie.

  Aby uzyskać więcej informacji, zobacz [/WX (Treat linker warnings as errors)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffassemblyGeneracja**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`program , tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.

  Aby uzyskać więcej informacji, zobacz [/NOASSEMBLY (Tworzenie modułu MSIL)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypLibraryFile**

  Opcjonalny parametr **String.**

  Określa nazwę pliku i rozszerzenie nazwy pliku *.tlb.* Określ nazwę pliku lub ścieżkę i nazwę pliku.

  Aby uzyskać więcej informacji, zobacz [/TLBOUT (Nazwa pliku .tlb)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **Wpis TypLibraryResourceID**

  Opcjonalny parametr **Liczba Całkowita.**

  Wyznacza wartość określoną przez użytkownika dla biblioteki typów utworzonej przez konsolidatora. Określ wartość od 1 do 65535.

  Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla TypeLib)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACWykonańLepoziom**

  Opcjonalny parametr **String.**

  Określa żądany poziom wykonania dla aplikacji, gdy jest uruchamiany w obszarze z kontrolą konta użytkownika.

  Określ jedną z następujących wartości, z których każda odpowiada opcji wiersza polecenia.

  - **Asinvoker** - `level='asInvoker'`

  - **NajwyższaDostępna** - `level='highestAvailable'`

  - **Requireadministrator** - `level='requireAdministrator'`

  Aby uzyskać więcej `level` informacji, zobacz argument [/MANIFESTUAC (Osadza informacje UAC w manifeście).](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)

- **UACUIAccess**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`aplikacja omija poziomy ochrony interfejsu użytkownika i kieruje dane wejściowe do okien o wyższych uprawnieniach na pulpicie; w `false`przeciwnym razie , .

  Aby uzyskać więcej `uiAccess` informacji, zobacz argument [/MANIFESTUAC (Osadza informacje UAC w manifeście).](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)

- **UseLibraryDependencyInputs**

  Opcjonalny parametr **logiczny.**

  Jeśli `true`dane wejściowe do narzędzia bibliotekarza są używane, a nie sam plik biblioteki, gdy dane wyjściowe biblioteki zależności projektu są połączone w.

- **Wersja**

  Opcjonalny parametr **String.**

  Umieść numer wersji w nagłówku pliku *.exe* lub *dll.* Określ`major[.minor]`" ". Argumenty `major` `minor` i są liczbami dziesiętnymi od 0 do 65535.

  Aby uzyskać więcej informacji, zobacz [/VERSION (Informacje o wersji)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

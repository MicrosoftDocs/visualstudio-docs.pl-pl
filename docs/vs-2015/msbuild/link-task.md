---
title: Łączenie zadań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efcdbb4f72d47a5044b287f1b40424f5611d6401
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703431"
---
# <a name="link-task"></a>Połącz — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opakowuje narzędzia konsolidatora Visual C++ link.exe. Narzędzia konsolidatora łączy pliki obiektu Common Object File Format (COFF) i biblioteki, aby utworzyć plik wykonywalny (.exe) lub biblioteki dołączanej (dynamicznie DLL). Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **łącze** zadania. Większość parametrów zadania oraz kilka zestawów parametrów, odpowiada opcji wiersza polecenia.  
  
- **AdditionalDependencies**  
  
   Opcjonalnie **String []** parametru.  
  
   Określa listę plików wejściowych, aby dodać do polecenia.  
  
   Aby uzyskać więcej informacji, zobacz [plików wejściowych łącze](https://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Opcjonalnie **String []** parametru.  
  
   Zastępuje ścieżki biblioteki środowiska. Określ nazwę katalogu.  
  
   Aby uzyskać więcej informacji, zobacz [/libpath — (dodatkowa Libpath)](https://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Opcjonalnie **String []** parametru.  
  
   Określa atrybuty, które zostaną umieszczone w `dependency` części pliku manifestu.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu)](https://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Zobacz też "Pliki konfiguracyjne wydawcy" na [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) witryny sieci Web.  
  
- **AdditionalOptions**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Lista opcji konsolidatora, jak określono w wierszu polecenia. Na przykład **"**_/option1 /option2 /option#_". Użyj tego parametru, aby określić opcje konsolidatora, które nie są reprezentowane przez inne **łącze** parametru zadania.  
  
   Aby uzyskać więcej informacji, zobacz [opcje konsolidatora](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Opcjonalnie **String []** parametru.  
  
   Dodaje odwołania modułu do zestawu.  
  
   Aby uzyskać więcej informacji, zobacz [assemblymodule (Dodaj moduł MSIL do zestawu)](https://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, powoduje, że system operacyjny do manifestu wyszukiwań i ładuje. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było żadnych manifestu.  
  
   Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (wyszukiwanie Manifest)](https://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, emituje **DebuggableAttribute** atrybut wraz z debugowania informacji śledzenia i wyłącza optymalizacje JIT. Jeśli `false`, emituje **DebuggableAttribute** atrybut, ale powoduje wyłączenie śledzenia informacji o debugowaniu i włącza optymalizacje JIT.  
  
   Aby uzyskać więcej informacji, zobacz [/assemblydebug (Dodaj DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Opcjonalnie **String []** parametru.  
  
   Tworzy łącze do zasobów .NET Framework w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym. Określ nazwę zasobu.  
  
   Aby uzyskać więcej informacji, zobacz [assemblylinkresource (Link do zasobów .NET Framework)](https://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Niejawne **logiczna** parametru.  
  
   Umożliwia bardziej plik śledzenia do przechwytywania zachowanie łącza przyrostowe firmy. Zawsze zwraca `true`.  
  
- **BaseAddress**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Ustawia adres bazowy programu lub biblioteka DLL jest kompilowana. Określ `{address[,size] | @filename,key}`.  
  
   Aby uzyskać więcej informacji, zobacz [uwzględniają (adres podstawowy)](https://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Opcjonalnie **logiczna** parametru.  
  
   W przypadku opcji true wskazuje, że program MSBuild jest wywoływana z poziomu środowiska IDE. W przeciwnym razie wskazuje, że program MSBuild jest wywoływana z poziomu wiersza polecenia.  
  
   Ten parametr nie ma żadnej opcji równoważne konsolidatora.  
  
- **CLRImageType**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Ustawia typ wspólnej obrazu od języka wspólnego (CLR).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **ForceIJWImage** - **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**  
  
  - **ForceSafeILImage** - **/CLRIMAGETYPE:SAFE**  
  
    Aby uzyskać więcej informacji, zobacz [/clrimagetype (określenie typu z obrazu CLR)](https://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Zachowuje kod ostatniego błędu funkcji wywołanych za pomocą mechanizmu P/Invoke.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **Włączone** - **/CLRSupportLastError**  
  
  - **Wyłączone** - **/CLRSupportLastError:NO**  
  
  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**  
  
    Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)](https://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa jawnie atrybut wątkowości dla punktu wejścia programu CLR.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE: Brak**  
  
  - **MTAThreadingAttribute** - **: MTA**  
  
  - **STAThreadingAttribute** - **/CLRTHREADATTRIBUTE:STA**  
  
    Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (Ustaw wątku atrybut CLR)](https://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Określa, czy konsolidator zastosuje **SuppressUnmanagedCodeSecurityAttribute** na generowanych przez konsolidator wywołania metody P/Invoke z kodu zarządzanego, do macierzystych bibliotek DLL.  
  
   Aby uzyskać więcej informacji, zobacz [opcji/clrunmanagedcodecheck (Dodaj atrybut SuppressUnmanagedCodeSecurityAttribute)](https://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Przygotowuje obraz do poprawki.  
  
   Określ jedną z następujących wartości, które odpowiada opcji konsolidatora.  
  
  - **Enabled** - **/FUNCTIONPADMIN**  
  
  - **X86Image** - **/FUNCTIONPADMIN:5**  
  
  - **X64Image** - **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** - **/FUNCTIONPADMIN:16**  
  
    Aby uzyskać więcej informacji, zobacz [/FUNCTIONPADMIN (Utwórz obraz Hotpatchable)](https://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, wskazuje, że plik wykonywalny został sprawdzony w celu uzyskania zgodności z funkcją zapobiegania wykonywaniu danych Windows.  
  
   Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](https://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Opcjonalnie **String []** parametru.  
  
   Powoduje, że ten parametr *opóźnione ładowanie* bibliotek DLL. Określ nazwę biblioteki DLL w celu opóźnienia ładowania.  
  
   Aby uzyskać więcej informacji, zobacz [/delayload (Opóźnij importowanie ładowania)](https://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, częściowo podpisuje zestaw. Domyślna wartość to `false`.  
  
   Aby uzyskać więcej informacji, zobacz [/DelaySign (częściowo podpisać zestaw)](https://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Sterownik**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określenia tego parametru, aby zbudować sterownik trybu jądra Windows NT.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **NotSet** - *\<none>*  
  
  - **Driver** - **/Driver**  
  
  - **UpOnly** - **/DRIVER:UPONLY**  
  
  - **WDM** - **/DRIVER:WDM**  
  
    Aby uzyskać więcej informacji, zobacz [Driver/Driver (sterownik trybu jądra Windows NT)](https://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Opcjonalnie **String []** parametru.  
  
   Osadza plik zasobów w zestawie. Określ nazwę pliku wymaganego zasobu. Opcjonalnie można określić nazwy logicznej, która jest używana do ładowania zasobu, a **PRYWATNEJ** opcja, która wskazuje w manifeście zestawu, czy plik zasobów jest prywatny.  
  
   Aby uzyskać więcej informacji, zobacz [linkowany (Osadź zarządzany zasób)](https://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, umożliwia identyczne składanie COMDAT.  
  
   Aby uzyskać więcej informacji, zobacz `ICF[= iterations]` argument [od (optymalizacje)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa, czy informacje kontroli konta użytkownika (UAC) będą osadzone w manifeście programu.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa funkcję punktu wejścia jako adres początkowy dla pliku .exe lub DLL. Określ nazwę funkcji jako wartość parametru.  
  
   Aby uzyskać więcej informacji, zobacz [/Entry (Symbol punktu wejścia)](https://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzy program lub biblioteki DLL, który może zostać załadowany tylko pod swoim preferowanym adresem bazowym.  
  
   Aby uzyskać więcej informacji, zobacz [/Fixed (stały adres podstawowy)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Informuje konsolidator, aby utworzyć plik .exe prawidłowe lub biblioteki DLL nawet wtedy, gdy symbolu występują odwołania, ale nie zdefiniowane, lub należy pomnożyć zdefiniowane.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Włączone** -   **/FORCE**  
  
  - **MultiplyDefinedSymbolOnly** - **/FORCE:MULTIPLE**  
  
  - **UndefinedSymbolOnly** -   **/FORCE: NIEROZPOZNANA**  
  
    Aby uzyskać więcej informacji, zobacz [/Force (Wymuszaj produkt wyjściowy pliku)](https://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Opcjonalnie **String []** parametru.  
  
   Ten parametr informuje konsolidator, aby dodał określony symbol do tabeli symboli.  
  
   Aby uzyskać więcej informacji, zobacz [/include (Wymuszaj odwołania do symboli)](https://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Ten parametr optymalizuje program, umieszczając określonego funkcje pakowane (COMDATs) w obrazie w ustalonej kolejności.  
  
   Aby uzyskać więcej informacji, zobacz [/order (umieścić funkcje w kolejności)](https://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzenie informacji debugowania dla pliku .exe lub DLL.  
  
   Aby uzyskać więcej informacji, zobacz [/Debug (generowanie informacji debugowania)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzy plik manifestu side-by-side.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFEST (Side-by-Side tworzenie manifestu dla aplikacji)](https://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzy *pliku mapy*. Rozszerzenie nazwy pliku mapy jest map.  
  
   Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa ilość fizycznej pamięci na stosie, można przydzielić w danym momencie.  
  
   Aby uzyskać więcej informacji, zobacz `commit` argument [/HEAP (Ustaw rozmiar sterty)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Zobacz też **HeapReserveSize** parametru.  
  
- **HeapReserveSize**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa Alokacja sterty całkowitej pamięci wirtualnej.  
  
   Aby uzyskać więcej informacji, zobacz `reserve` argument [/HEAP (Ustaw rozmiar sterty)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Zobacz też **HeapCommitSize** parametru w tej tabeli.  
  
- **IgnoreAllDefaultLibraries**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje konsolidator, aby usunąć jedną lub więcej bibliotek domyślnych z listy bibliotek wyszukiwania podczas rozpoznawania odwołań zewnętrznych.  
  
   Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa, że nie można przetworzyć jakiekolwiek atrybuty IDL w kodzie źródłowym do pliku .idl.  
  
   Aby uzyskać więcej informacji, zobacz [/IGNOREIDL (nie atrybutów procesu w MIDL)](https://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa, że biblioteka importowana, generowana przez tą konfigurację nie będzie importowana do projektów zależnych.  
  
   Ten parametr nie odpowiada — opcja konsolidatora.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Opcjonalnie **String []** parametru.  
  
   Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. Rozdzielaj wielokrotne biblioteki przy użyciu średników.  
  
   Aby uzyskać więcej informacji, zobacz [/nodefaultlib (Ignoruj biblioteki)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, konsolidator generuje obraz tylko wtedy, gdy może utworzyć również tabelę obsługi bezpiecznych wyjątków obrazu.  
  
   Aby uzyskać więcej informacji, zobacz [opcja/SAFESEH (obraz ma bezpieczną obsługę wyjątków)](https://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Nazwa biblioteki importu określonych przez użytkownika, która zastępuje domyślną nazwę biblioteki.  
  
   Aby uzyskać więcej informacji, zobacz [/IMPLIB (Nazwij bibliotekę importowaną)](https://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Kontener, który zawiera klucz dla zestawu podpisem.  
  
   Aby uzyskać więcej informacji, zobacz [/KeyContainer (Określ kontener klucza, aby podpisać zestaw)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Zobacz też **KeyFile** parametru w tej tabeli.  
  
- **KeyFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa plik, który zawiera klucz dla zestawu podpisanego za pomocą.  
  
   Aby uzyskać więcej informacji, zobacz [/KeyFile (Określ klucz lub parę klucz Aby podpisać zestaw)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Zobacz też **KeyContainer** parametru.  
  
- **LargeAddressAware**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, aplikacja może obsługiwać adresy większe niż 2 gigabajty.  
  
   Aby uzyskać więcej informacji, zobacz [/largeaddressaware (Obsługa dużych adresów)](https://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, kompiluje bibliotekę DLL jako plik wyjściowy głównego.  
  
   Aby uzyskać więcej informacji, zobacz [/dll (kompilowanie biblioteki DLL)](https://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Pozwala zapewnić wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NoErrorReport** -   **/errorreport: Brak**  
  
  - **PromptImmediately** - **/ERRORREPORT:PROMPT**  
  
  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** - **/ERRORREPORT:SEND**  
  
    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy konsolidatora)](https://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, włącza konsolidację przyrostową.  
  
   Aby uzyskać więcej informacji, zobacz [/incremental (Link przyrostowo)](https://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa, czy biblioteka wyników z odwoływanych projektów jest automatycznie konsolidowana.  
  
   Ten parametr nie odpowiada — opcja konsolidatora.  
  
- **LinkStatus**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa, że konsolidator jest wyświetlenie wskaźnika postępu, który pokazuje, jaki procent łącze zostało zakończone.  
  
   Aby uzyskać więcej informacji, zobacz `STATUS` argument [opcję/LTCG (Generowanie kodu Link-time)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa opcje optymalizacji sterowanej profilem.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** - *\<Brak >*  
  
  - **UseLinkTimeCodeGeneration** - **/LTCG**  
  
  - **PGInstrument** - **/LTCG:PGInstrument**  
  
  - **PGOptimization** - **/LTCG:PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG:PGUpdate**  
  
    Aby uzyskać więcej informacji, zobacz [opcję/LTCG (Generowanie kodu Link-time)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Zmienia domyślna nazwa pliku manifestu do określonej nazwy pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (nazwa pliku manifestu)](https://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje konsolidator, aby dołączał eksportowane funkcje w pliku mapy.  
  
   Aby uzyskać więcej informacji, zobacz `EXPORTS` argument [/MapInfo (zawierają informacje o mapfile)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Zmienia domyślna nazwa pliku mapy z określoną nazwą pliku.  
  
- **MergedIDLBaseFileName**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę pliku i rozszerzenie pliku .idl.  
  
   Aby uzyskać więcej informacji, zobacz [/idlout (nazwa wyjściowe pliki MIDL)](https://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Łączy sekcje w obrazie. Określ `from-section=to-section`.  
  
   Aby uzyskać więcej informacji, zobacz [/merge (Połącz sekcje)](https://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określ nazwę pliku, który zawiera opcje wiersza polecenia MIDL.  
  
   Aby uzyskać więcej informacji, zobacz [/MIDL (Określ opcje ze wiersza polecenia w MIDL)](https://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65535.  
  
- **ModuleDefinitionFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę [plik definicji modułu](https://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu)](https://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Dołącza określony program szczątkowy systemu MS-DOS do programu systemu Win32.  
  
   Aby uzyskać więcej informacji, zobacz [/stub (nazwa pliku klasy zastępczej MS-DOS)](https://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, określa bibliotekę DLL tylko do zasobów.  
  
   Aby uzyskać więcej informacji, zobacz [/noentry (Brak punktu wejścia)](https://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Niejawne **String []** parametru.  
  
   Określa pliki obiektów, które są połączone.  
  
- **OptimizeReferences**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, eliminuje funkcje i/lub dane, które nigdy nie są wywoływane.  
  
   Aby uzyskać więcej informacji, zobacz `REF` argument [od (optymalizacje)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.  
  
   Aby uzyskać więcej informacji, zobacz [/OUT (nazwa pliku wyjściowego)](https://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true` i włączono rejestrowanie wyników rejestru wymusza zapisuje **HKEY_CLASSES_ROOT** do **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Opcjonalnie `ITaskItem[]` parametru.  
  
   Określa tablicę elementów dane wyjściowe preprocesora, które może być używany i wyemitowane przez zadania.  
  
- **PreventDllBinding**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, wskazuje Bind.exe, obraz połączony nie powinny być powiązane.  
  
   Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (zapobieganie powiązanie biblioteki DLL)](https://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profil**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzy plik wyjściowy, który może być używany z **narzędzia do oceny wydajności** profilera.  
  
   Aby uzyskać więcej informacji, zobacz [/profile (Profiler narzędzi wydajności)](https://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę pliku .pgd, która będzie służyć do przechowywania informacji na temat uruchomiony program  
  
   Aby uzyskać więcej informacji, zobacz [/PGD (Określ bazę danych dla optymalizacji Profile-Guided)](https://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443).  
  
- **ProgramDatabaseFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę bazy danych programu (PDB) tworzonego przez konsolidatora.  
  
   Aby uzyskać więcej informacji, zobacz [/PDB (Użyj bazy danych programu)](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, generuje obraz wykonywalny, który może być losowo przebazowanych w czasie ładowania przy użyciu *randomizacji układu przestrzeni adresów* (ASLR) funkcja systemu Windows.  
  
   Aby uzyskać więcej informacji, zobacz [opcja/DynamicBase (randomizacji układu przestrzeni adresowej Użyj)](https://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, rejestruje główny wynik tej kompilacji.  
  
- **SectionAlignment**  
  
   Opcjonalnie **całkowitą** parametru.  
  
   Określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Wartość tego parametru jest jednostka liczba bajtów i jest potęgą liczby dwa.  
  
   Aby uzyskać więcej informacji, zobacz [/align (wyrównanie sekcji)](https://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, ustawia sumę kontrolną w nagłówku pliku .exe.  
  
   Aby uzyskać więcej informacji, zobacz [/Release (Ustaw sumę kontrolną)](https://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa poziom szczegółowości raportów postępu dla operacji łączenia.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** - *\<none>*  
  
  - **LinkVerbose** - **/VERBOSE**  
  
  - **LinkVerboseLib** - **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** - **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** - **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** - **/VERBOSE:CLR**  
  
    Aby uzyskać więcej informacji, zobacz [opcjami/verbose (Drukuj komunikaty o postępie)](https://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Źródła**  
  
   Wymagane `ITaskItem[]` parametru.  
  
   Określa tablicę elementów pliku źródłowego programu MSBuild, które mogą być używane i wyemitowane przez zadania.  
  
- **SpecifySectionAttributes**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa atrybuty sekcji. Ustawienie to zastępuje atrybuty, które zostały ustawione, gdy plik .obj sekcji został skompilowany.  
  
   Aby uzyskać więcej informacji, zobacz [/Section (Określ atrybuty sekcji)](https://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa ilość pamięci fizycznej w każdej alokacji, gdy jest przydzielany dodatkowej pamięci.  
  
   Aby uzyskać więcej informacji, zobacz `commit` argument [/STACK (twórz stos z alokacji)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.  
  
   Aby uzyskać więcej informacji, zobacz `reserve` argument [/STACK (twórz stos z alokacji)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Tworzy drugi plik bazy danych (PDB) programu, które pomija symbole, których nie chcesz dystrybuować swoim klientom. Określ nazwę drugiego pliku PDB.  
  
   Aby uzyskać więcej informacji, zobacz [/pdbstripped (Usuń symbole prywatne)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **SubSystem**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa środowisko dla pliku wykonywalnego.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** - *\<none>*  
  
  - **Konsola** - **opcji**  
  
  - **Windows** - **/SUBSYSTEM:WINDOWS**  
  
  - **Native** - **/SUBSYSTEM:NATIVE**  
  
  - **Aplikacja EFI** - **/SUBSYSTEM:EFI_APPLICATION**  
  
  - **Sterownik usługi rozruchu interfejsu EFI** - **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**  
  
  - **EFI ROM** - **/SUBSYSTEM:EFI_ROM**  
  
  - **EFI Runtime** - **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** - **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** - **/SUBSYSTEM:POSIX**  
  
    Aby uzyskać więcej informacji, zobacz [/Subsystem (Określ podsystem)](https://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje konsolidator, nie można dołączyć powiązania tabeli adresów importowania (IAT) do obrazu końcowego.  
  
   Aby uzyskać więcej informacji, zobacz `NOBIND` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje funkcję pomocnika obciążenia opóźnienia, aby wspierała jawne zwalnianie biblioteki DLL.  
  
   Aby uzyskać więcej informacji, zobacz `UNLOAD` argument [przełącznik/DELAY (ustawienia opóźnienia importowania ładowania)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, uniemożliwia wyświetlanie wiadomości praw autorskich i wersji, podczas uruchamiania zadania.  
  
   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijaj transparent startowy) (konsolidator)](https://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje system operacyjny, aby najpierw skopiować konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
   Aby uzyskać więcej informacji, zobacz `CD` argument [swaprun (Załaduj dane wyjściowe konsolidatora do pliku Swap)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Zobacz też **SwapRunFromNET** parametru.  
  
- **SwapRunFromNET**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, informuje system operacyjny, aby najpierw skopiować konsolidatora dane wyjściowe do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
   Aby uzyskać więcej informacji, zobacz `NET` argument [swaprun (Załaduj dane wyjściowe konsolidatora do pliku Swap)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Zobacz też **SwapRunFromCD** parametru w tej tabeli.  
  
- **TargetMachine**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa platformę docelową dla tego programu lub DLL.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** - *\<none>*  
  
  - **MachineARM** - **/MACHINE:ARM**  
  
  - **MachineEBC** - **/MACHINE:EBC**  
  
  - **MachineIA64** - **/MACHINE:IA64**  
  
  - **MachineMIPS** - **/MACHINE:MIPS**  
  
  - **MachineMIPS16** - **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** - **/MACHINE:SH4**  
  
  - **MachineTHUMB** - **/MACHINE:THUMB**  
  
  - **MachineX64** - **/MACHINE:X64**  
  
  - **MachineX86** - **/MACHINE:X86**  
  
    Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](https://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER dllcharacteristics w opcjonalnym nagłówku obrazu programu. Gdy ta flaga jest ustawiona, serwera terminali nie wprowadzi pewnych zmian aplikacji.  
  
   Aby uzyskać więcej informacji, zobacz [/tsaware (Utwórz terminalu aplikację świadomą serwera)](https://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **TrackerLogDirectory**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa katalog dziennika śledzenia.  
  
- **TreatLinkerWarningAsErrors**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator wygeneruje ostrzeżenie.  
  
   Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jak błędy)](https://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.  
  
   Aby uzyskać więcej informacji, zobacz [/noassembly (Utwórz moduł MSIL)](https://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa nazwę pliku i rozszerzenie pliku .tlb. Określ nazwę pliku lub ścieżkę i nazwę pliku.  
  
   Aby uzyskać więcej informacji, zobacz  [ /tlbout (nazwa. Plik TLB)](https://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Opcjonalnie **całkowitą** parametru.  
  
   Określa wartość określone przez użytkownika dla biblioteki typów, utworzone przez konsolidator. Określ wartość z zakresu od 1 do 65 535.  
  
   Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla TypeLib)](https://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Określa wymagany poziom wykonywania dla aplikacji, gdy jest uruchamiana przy użyciu kontroli konta użytkownika.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Aby uzyskać więcej informacji, zobacz `level` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`, aplikacja pomija poziomów ochrony interfejsu użytkownika i dyski danych wejściowych do wyższych uprawnień okien na pulpicie; w przeciwnym razie `false`.  
  
   Aby uzyskać więcej informacji, zobacz `uiAccess` argument [/MANIFESTUAC (osadza informacje UAC w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Opcjonalnie **logiczna** parametru.  
  
   Jeśli `true`i wejścia do narzędzia bibliotekarza są używane zamiast pliku biblioteki samego w sobie podczas produktów wyjściowych biblioteki zależności projektów są dołączane.  
  
- **Wersja**  
  
   Opcjonalnie **ciąg** parametru.  
  
   Umieszczenie numeru wersji w nagłówku pliku .exe lub .dll. Określ "`major[.minor]`". `major` i `minor` argumenty są liczbami dziesiętnymi z zakresu od 0 do 65 535.  
  
   Aby uzyskać więcej informacji, zobacz [/Version (informacje o wersji)](https://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

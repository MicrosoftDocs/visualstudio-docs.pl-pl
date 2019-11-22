---
title: Połącz zadanie | Microsoft Docs
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
ms.openlocfilehash: 181c32017a84328037ea46d49698821fa3cb41ea
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295883"
---
# <a name="link-task"></a>Połącz — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija narzędzia konsolidatora C++ wizualnego link. exe. Narzędzie konsolidatora łączy pliki i biblioteki obiektów Common Object Format (COFF), aby utworzyć plik wykonywalny (exe) lub bibliotekę dołączaną dynamicznie (DLL). Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **linku** . Większość parametrów zadań i kilku zestawów parametrów odpowiada opcji wiersza polecenia.  
  
- **AdditionalDependencies**  
  
   Opcjonalny parametr **String []** .  
  
   Określa listę plików wejściowych do dodania do polecenia.  
  
   Aby uzyskać więcej informacji, zobacz [łączenie plików wejściowych](https://msdn.microsoft.com/library/bb26fcc5-509a-4620-bc3e-b6c6e603a412).  
  
- **AdditionalLibraryDirectories**  
  
   Opcjonalny parametr **String []** .  
  
   Zastępuje ścieżkę biblioteki środowiska. Określ nazwę katalogu.  
  
   Aby uzyskać więcej informacji, zobacz [/LIBPATH (dodatkowa LIBPATH)](https://msdn.microsoft.com/library/7240af0b-9a3d-4d53-8169-2a92cd6958ba).  
  
- **AdditionalManifestDependencies**  
  
   Opcjonalny parametr **String []** .  
  
   Określa atrybuty, które zostaną umieszczone w sekcji `dependency` pliku manifestu.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTDEPENDENCY (Określ zależności manifestu)](https://msdn.microsoft.com/library/e4b68313-33a2-4c3e-908e-ac2b9f7d6a73). Zobacz również sekcję "pliki konfiguracji wydawcy" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.  
  
- **AdditionalOptions**  
  
   Opcjonalny parametr **ciągu** .  
  
   Lista opcji konsolidatora określona w wierszu polecenia. Na przykład **"** _/option1/option2 Option #_ ". Użyj tego parametru, aby określić Opcje konsolidatora, które nie są reprezentowane przez żaden inny parametr zadania **linku** .  
  
   Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](https://msdn.microsoft.com/library/c1d51b8a-bd23-416d-81e4-900e02b2c129).  
  
- **AddModuleNamesToAssembly**  
  
   Opcjonalny parametr **String []** .  
  
   Dodaje odwołanie do modułu do zestawu.  
  
   Aby uzyskać więcej informacji, zobacz [/ASSEMBLYMODULE (Dodaj moduł MSIL do zestawu)](https://msdn.microsoft.com/library/67357da8-e4b6-49fd-932c-329a5777f143).  
  
- **AllowIsolation**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, powoduje, że system operacyjny przeszukiwanie i ładowanie manifestu. Jeśli `false`, wskazuje, że biblioteki DLL są ładowane tak, jakby nie było manifestu.  
  
   Aby uzyskać więcej informacji, zobacz [/ALLOWISOLATION (odnośnik manifestu)](https://msdn.microsoft.com/library/6d41851e-b3c1-4bdf-beaa-031773089d6f).  
  
- **AssemblyDebug**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, emituje atrybut **DebuggableAttribute** wraz ze śledzeniem informacji debugowania i wyłącza optymalizacje JIT. Jeśli `false`, emituje atrybut **DebuggableAttribute** , ale wyłącza śledzenie informacji debugowania i włącza optymalizacje JIT.  
  
   Aby uzyskać więcej informacji, zobacz [/ASSEMBLYDEBUG (Add DebuggableAttribute)](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).  
  
- **AssemblyLinkResource**  
  
   Opcjonalny parametr **String []** .  
  
   Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Określ nazwę zasobu.  
  
   Aby uzyskać więcej informacji, zobacz [/ASSEMBLYLINKRESOURCE (link do zasobów .NET Framework)](https://msdn.microsoft.com/library/8b6ad184-1b33-47a4-8513-4803cf915b64).  
  
- **AttributeFileTracking**  
  
   Niejawny parametr **logiczny** .  
  
   Umożliwia dokładniejsze śledzenie plików, aby przechwycić zachowanie przyrostu łącza. Zawsze zwraca `true`.  
  
- **BaseAddress**  
  
   Opcjonalny parametr **ciągu** .  
  
   Ustawia adres podstawowy dla kompilowanego programu lub biblioteki DLL. Określ `{address[,size] | @filename,key}`.  
  
   Aby uzyskać więcej informacji, zobacz [/Base (adres podstawowy)](https://msdn.microsoft.com/library/00b9f6fe-0bd2-4772-a69c-7365eb199069).  
  
- **BuildingInIDE**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli wartość jest równa true, wskazuje, że MSBuild jest wywoływany z IDE. W przeciwnym razie wskazuje, że MSBuild jest wywoływany z wiersza polecenia.  
  
   Ten parametr nie ma równoważnej opcji konsolidatora.  
  
- **CLRImageType**  
  
   Opcjonalny parametr **ciągu** .  
  
   Ustawia typ obrazu środowiska uruchomieniowego języka wspólnego (CLR).  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **Domyślne** -  *\<brak >*  
  
  - **ForceIJWImage** -  **/CLRIMAGETYPE:IJW**  
  
  - **ForcePureILImage** -  **/CLRIMAGETYPE: czysty**  
  
  - **ForceSafeILImage** -  **/CLRIMAGETYPE:SAFE**  
  
    Aby uzyskać więcej informacji, zobacz [/CLRIMAGETYPE (Określ typ obrazu CLR)](https://msdn.microsoft.com/library/04c60ee6-9dd7-4391-bc03-6926ad0fa116).  
  
- **CLRSupportLastError**  
  
   Opcjonalny parametr **ciągu** .  
  
   Zachowuje kod ostatniego błędu funkcji wywoływanych za pomocą mechanizmu P/Invoke.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **Włączone** -  **/CLRSupportLastError**  
  
  - **Wyłączone** -  **/CLRSupportLastError: nie**  
  
  - **SystemDlls** -  **/CLRSupportLastError:SYSTEMDLL**  
  
    Aby uzyskać więcej informacji, zobacz [/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)](https://msdn.microsoft.com/library/b7057990-4154-4b1d-9fc9-6236f7be7575).  
  
- **CLRThreadAttribute**  
  
   Opcjonalny parametr **ciągu** .  
  
   Jawnie określa atrybut wątkowości dla punktu wejścia programu CLR.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **DefaultThreadingAttribute** -  **/CLRTHREADATTRIBUTE: brak**  
  
  - **MTAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: MTA**  
  
  - **STAThreadingAttribute** -  **/CLRTHREADATTRIBUTE: sta**  
  
    Aby uzyskać więcej informacji, zobacz [/CLRTHREADATTRIBUTE (ustaw atrybut wątku CLR)](https://msdn.microsoft.com/library/4907e9ef-5031-446c-aecf-0a0b32fae1e8).  
  
- **CLRUnmanagedCodeCheck**  
  
   Opcjonalny parametr **logiczny** .  
  
   Określa, czy konsolidator będzie stosował **SuppressUnmanagedCodeSecurityAttribute** do wygenerowanych przez konsolidatora wywołań P/Invoke z kodu zarządzanego do natywnych bibliotek DLL.  
  
   Aby uzyskać więcej informacji, zobacz [/CLRUNMANAGEDCODECHECK (Add SuppressUnmanagedCodeSecurityAttribute)](https://msdn.microsoft.com/library/73abc426-dab0-45e2-be85-0f9a14206cc2).  
  
- **CreateHotPatchableImage**  
  
   Opcjonalny parametr **ciągu** .  
  
   Przygotowuje obraz do stosowania poprawek na gorąco.  
  
   Określ jedną z następujących wartości, która odnosi się do opcji konsolidatora.  
  
  - **Enabled** -  **/FUNCTIONPADMIN**  
  
  - **X86Image** -  **/FUNCTIONPADMIN:5**  
  
  - **X64Image** -  **/FUNCTIONPADMIN:6**  
  
  - **ItaniumImage** -  **/functionpadmin: 16**  
  
    Aby uzyskać więcej informacji, zobacz [/functionpadmin (Create możliwy do poprawiania Image)](https://msdn.microsoft.com/library/25b02c13-1add-4fbd-add9-fcb30eb2cae7).  
  
- **DataExecutionPrevention**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, wskazuje, że plik wykonywalny został przetestowany pod kątem zgodności z funkcją zapobiegania wykonywaniu danych systemu Windows.  
  
   Aby uzyskać więcej informacji, zobacz [/NXCOMPAT (zgodny z zapobieganiem wykonywaniu danych)](https://msdn.microsoft.com/library/5858e7ff-24d3-4ac3-9046-af2c9e220d9b).  
  
- **DelayLoadDLLs**  
  
   Opcjonalny parametr **String []** .  
  
   Ten parametr powoduje *opóźnione ładowanie* bibliotek DLL. Określ nazwę pliku DLL, aby opóźnić ładowanie.  
  
   Aby uzyskać więcej informacji, zobacz [/DELAYLOAD (opóźnienie importowania ładowania)](https://msdn.microsoft.com/library/39ea0f1e-5c01-450f-9c75-2d9761ff9b28).  
  
- **DelaySign**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, częściowo podpisuje zestaw. Domyślnie wartość jest `false`.  
  
   Aby uzyskać więcej informacji, zobacz [/delaysign (częściowo podpisz zestaw)](https://msdn.microsoft.com/library/15244d30-3ecb-492f-a408-ffe81f38de20).  
  
- **Sterownik**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określ ten parametr, aby skompilować sterownik trybu jądra systemu Windows NT.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji konsolidatora.  
  
  - **NotSet** -  *\<none>*  
  
  - **Driver** -  **/Driver**  
  
  - **UpOnly** -  **/DRIVER:UPONLY**  
  
  - **WDM** -  **/DRIVER:WDM**  
  
    Aby uzyskać więcej informacji, zobacz [Sterownik systemu Windows NT — sterowniki trybu jądra](https://msdn.microsoft.com/library/aeee8e28-5d97-40f5-ba16-9f370fe8a1b8).  
  
- **EmbedManagedResourceFile**  
  
   Opcjonalny parametr **String []** .  
  
   Osadza plik zasobów w zestawie. Określ wymaganą nazwę pliku zasobu. Opcjonalnie można określić nazwę logiczną, która jest używana do ładowania zasobu, oraz opcję **prywatną** wskazującą w manifeście zestawu, że plik zasobów jest prywatny.  
  
   Aby uzyskać więcej informacji, zobacz [/ASSEMBLYRESOURCE (osadzanie zarządzanego zasobu)](https://msdn.microsoft.com/library/0ce6e1fb-921b-4b1b-a59c-d35388d789f2).  
  
- **EnableCOMDATFolding**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, włącza identyczne składanie COMDAT.  
  
   Aby uzyskać więcej informacji, zobacz `ICF[= iterations]` argument [/opt (optymalizacje)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **EnableUAC**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa, że informacje kontroli konta użytkownika (UAC) są osadzone w manifeście programu.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTUAC (osadzanie informacji UAC w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **EntryPointSymbol**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa funkcję punktu wejścia jako adres początkowy dla pliku. exe lub DLL. Określ nazwę funkcji jako wartość parametru.  
  
   Aby uzyskać więcej informacji, zobacz [/entry (symbol punktu wejścia)](https://msdn.microsoft.com/library/26c62ba2-4f52-4882-a7bd-7046a0abf445).  
  
- **FixedBaseAddress**  
  
   Opcjonalny parametr **logiczny** .  
  
   W przypadku `true`tworzy program lub plik DLL, który można załadować tylko przy użyciu preferowanego adresu podstawowego.  
  
   Aby uzyskać więcej informacji, zobacz [/FIXED (stały adres podstawowy)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).  
  
- **ForceFileOutput**  
  
   Opcjonalny parametr **ciągu** .  
  
   Nakazuje konsolidatorowi utworzenie prawidłowego pliku. exe lub DLL, nawet jeśli istnieje odwołanie do symbolu, ale nie zdefiniowane lub jest zdefiniowane wielokrotnie.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Włączono** -  **/Force**  
  
  - **MultiplyDefinedSymbolOnly** -  **/Force: wiele**  
  
  - **UndefinedSymbolOnly** -  **/Force: nierozwiązane**  
  
    Aby uzyskać więcej informacji, zobacz [/Force (Wymuś dane wyjściowe pliku)](https://msdn.microsoft.com/library/b1e9a218-a5eb-4e60-a4a4-65b4be15e5da).  
  
- **ForceSymbolReferences**  
  
   Opcjonalny parametr **String []** .  
  
   Ten parametr nakazuje konsolidatorowi dodanie określonego symbolu do tabeli symboli.  
  
   Aby uzyskać więcej informacji, zobacz [/include (Wymuszaj odwołania do symboli)](https://msdn.microsoft.com/library/4a039677-360a-480f-bd0b-448e239b449c).  
  
- **FunctionOrder**  
  
   Opcjonalny parametr **ciągu** .  
  
   Ten parametr optymalizuje program przez umieszczenie określonych spakowanych funkcji (COMDAT) w obrazie w ustalonej kolejności.  
  
   Aby uzyskać więcej informacji, zobacz [/Order (Put funkcje w kolejności)](https://msdn.microsoft.com/library/ecf5eb3e-e404-4e86-9a91-4e5ec157261a).  
  
- **GenerateDebugInformation**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program tworzy informacje debugowania dla pliku exe lub DLL.  
  
   Aby uzyskać więcej informacji, zobacz [/debug (generowanie informacji o debugowaniu)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).  
  
- **GenerateManifest**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program tworzy plik manifestu obok siebie.  
  
   Aby uzyskać więcej informacji, zobacz [/manifest (Create Side-by-Side manifest zestawu)](https://msdn.microsoft.com/library/98c52e1e-712c-4f49-b149-4d0a3501b600).  
  
- **GenerateMapFile**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program tworzy *plik mapy*. Rozszerzenie nazwy pliku mapy to. map.  
  
   Aby uzyskać więcej informacji, zobacz [/map (Generuj plik mapy)](https://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).  
  
- **HeapCommitSize**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa ilość pamięci fizycznej na stercie do przydzielenia w danym momencie.  
  
   Aby uzyskać więcej informacji, zobacz argument `commit` w [/Heap (Ustawianie rozmiaru sterty)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Zobacz również parametr **HeapReserveSize** .  
  
- **HeapReserveSize**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa całkowitą alokację sterty w pamięci wirtualnej.  
  
   Aby uzyskać więcej informacji, zobacz argument `reserve` w [/Heap (Ustawianie rozmiaru sterty)](https://msdn.microsoft.com/library/a3f71927-7f1d-492c-9fdb-dfccb1a043da). Zobacz również parametr **HeapCommitSize** w tej tabeli.  
  
- **IgnoreAllDefaultLibraries**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, nakazuje konsolidatorowi usunięcie co najmniej jednej biblioteki domyślnej z listy bibliotek, które przeszukuje, gdy rozwiązuje odwołania zewnętrzne.  
  
   Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **IgnoreEmbeddedIDL**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa, że żadne atrybuty IDL w kodzie źródłowym nie powinny być przetwarzane do pliku. idl.  
  
   Aby uzyskać więcej informacji, zobacz [/IGNOREIDL (nie Przetwarzaj atrybutów w MIDL)](https://msdn.microsoft.com/library/29514098-6a1c-4317-af2f-1dc268972780).  
  
- **IgnoreImportLibrary**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa, że biblioteka importowana, generowana przez tę konfigurację, nie powinna być importowana do projektów zależnych.  
  
   Ten parametr nie odpowiada opcji konsolidatora.  
  
- **IgnoreSpecificDefaultLibraries**  
  
   Opcjonalny parametr **String []** .  
  
   Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania. Oddziel wiele bibliotek przy użyciu średników.  
  
   Aby uzyskać więcej informacji, zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](https://msdn.microsoft.com/library/7270b673-6711-468e-97a7-c2925ac2be6e).  
  
- **ImageHasSafeExceptionHandlers**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, konsolidator tworzy obraz tylko wtedy, gdy może również generować tabelę obsługi wyjątków bezpiecznego obrazu.  
  
   Aby uzyskać więcej informacji, zobacz [/SAFESEH (obraz ma bezpieczne procedury obsługi wyjątków)](https://msdn.microsoft.com/library/7722ff99-b833-4c65-a855-aaca902ffcb7).  
  
- **ImportLibrary**  
  
   Nazwa biblioteki importu określona przez użytkownika, która zastępuje domyślną nazwę biblioteki.  
  
   Aby uzyskać więcej informacji, zobacz [/IMPLIB (Name import Library)](https://msdn.microsoft.com/library/fe8f71ab-7055-41b5-8ef8-2b97cfa4a432).  
  
- **KeyContainer**  
  
   Opcjonalny parametr **ciągu** .  
  
   Kontener, który zawiera klucz dla podpisanego zestawu.  
  
   Aby uzyskać więcej informacji, zobacz [/KEYCONTAINER (Określ kontener klucza do podpisania zestawu)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e). Zobacz również parametr **KeyFile** w tej tabeli.  
  
- **KeyFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa plik, który zawiera klucz dla podpisanego zestawu.  
  
   Aby uzyskać więcej informacji, zobacz [/keyfile (Określ klucz lub parę kluczy, aby podpisać zestaw)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06). Należy również zapoznać się z parametrem **kontenera** .  
  
- **LargeAddressAware**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, aplikacja może obsłużyć adresy większe niż 2 gigabajty.  
  
   Aby uzyskać więcej informacji, zobacz [/LARGEADDRESSAWARE (obsługa dużych adresów)](https://msdn.microsoft.com/library/a29756c8-e893-47a9-9750-1f0d25359385).  
  
- **LinkDLL**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program kompiluje bibliotekę DLL jako główny plik wyjściowy.  
  
   Aby uzyskać więcej informacji, zobacz [/dll (Kompilowanie biblioteki dll)](https://msdn.microsoft.com/library/c7685aec-31d0-490f-9503-fb5171a23609).  
  
- **LinkErrorReporting**  
  
   Opcjonalny parametr **ciągu** .  
  
   Umożliwia dostarczenie informacji o wewnętrznym błędzie kompilatora (lodem) bezpośrednio do firmy Microsoft.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NoErrorReport** -  **/errorReport: brak**  
  
  - **Monituj bezzwłocznie** -  **/errorReport: Prompt**  
  
  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**  
  
  - **SendErrorReport** -  **/errorReport: Send**  
  
    Aby uzyskać więcej informacji, zobacz [/errorreport (zgłaszaj wewnętrzne błędy konsolidatora)](https://msdn.microsoft.com/library/f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28).  
  
- **LinkIncremental**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, włącza łączenie przyrostowe.  
  
   Aby uzyskać więcej informacji, zobacz [/Incremental (łączenie przyrostowe)](https://msdn.microsoft.com/library/135656ff-94fa-4ad4-a613-22e1a2a5d16b).  
  
- **LinkLibraryDependencies**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa, że dane wyjściowe biblioteki z zależności projektu są automatycznie dołączane.  
  
   Ten parametr nie odpowiada opcji konsolidatora.  
  
- **LinkStatus**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa, że konsolidator ma wyświetlać wskaźnik postępu, który pokazuje, jaki procent łącza zostało zakończone.  
  
   Aby uzyskać więcej informacji, zobacz argument `STATUS` [/LTCG (generowanie kodu w czasie konsolidacji)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **LinkTimeCodeGeneration**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa opcje optymalizacji profilowanej.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **Domyślne** -  *\<brak >*  
  
  - **UseLinkTimeCodeGeneration** -  **/LTCG**  
  
  - **PGInstrument** -  **/LTCG:PGInstrument**  
  
  - **PGOptimization** -  **/LTCG: PGOptimize**  
  
  - **PGUpdate**  
  
     \- **/LTCG: PGUpdate**  
  
    Aby uzyskać więcej informacji, zobacz [/LTCG (generowanie kodu w czasie konsolidacji)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2).  
  
- **ManifestFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Zmienia domyślną nazwę pliku manifestu na określoną nazwę pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/MANIFESTFILE (Nazwij plik manifestu)](https://msdn.microsoft.com/library/befa5ab2-a9cf-4c9b-969a-e7b4a930f08d).  
  
- **MapExports**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, nakazuje konsolidatorowi uwzględnienie wyeksportowanych funkcji w pliku mapy.  
  
   Aby uzyskać więcej informacji, zobacz argument `EXPORTS` [/MapInfo (Dołącz informacje w mapfile)](https://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).  
  
- **MapFileName**  
  
   Opcjonalny parametr **ciągu** .  
  
   Zmienia domyślną nazwę pliku mapy na określoną nazwę pliku.  
  
- **MergedIDLBaseFileName**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę pliku i rozszerzenie nazwy pliku IDL.  
  
   Aby uzyskać więcej informacji, zobacz [/IDLOUT (Name MIDL Output Files)](https://msdn.microsoft.com/library/10d00a6a-85b4-4de1-8732-e422c6931509).  
  
- **MergeSections**  
  
   Opcjonalny parametr **ciągu** .  
  
   Łączy sekcje w obrazie. Określ `from-section=to-section`.  
  
   Aby uzyskać więcej informacji, zobacz [/merge (łączenie sekcji)](https://msdn.microsoft.com/library/10fb20c2-0b3f-4c8d-98a8-f69aedf03d52).  
  
- **MidlCommandFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określ nazwę pliku, który zawiera opcje wiersza polecenia MIDL.  
  
   Aby uzyskać więcej informacji, zobacz [/MIDL (Określ opcje wiersza polecenia MIDL)](https://msdn.microsoft.com/library/22dc259e-b34c-4ed3-a380-4beb734482c1).  
  
- **MinimumRequiredVersion**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa minimalną wymaganą wersję podsystemu. Argumenty są liczbami dziesiętnymi z zakresu od 0 do 65535.  
  
- **ModuleDefinitionFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę [pliku definicji modułu](https://msdn.microsoft.com/library/08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8).  
  
   Aby uzyskać więcej informacji, zobacz [/DEF (Określ plik definicji modułu)](https://msdn.microsoft.com/library/6497fa68-65f0-48ca-8f66-b87166fc631a).  
  
- **MSDOSStubFileName**  
  
   Opcjonalny parametr **ciągu** .  
  
   Dołącza określony program zastępczy systemu MS-DOS do programu systemu Win32.  
  
   Aby uzyskać więcej informacji, zobacz [/stub (nazwa pliku szczątkowego systemu MS-DOS)](https://msdn.microsoft.com/library/65221ffe-4f9a-4a14-ac69-3cfb79b40b5f).  
  
- **NoEntryPoint**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, określa plik DLL z tylko zasobami.  
  
   Aby uzyskać więcej informacji, zobacz [/NOENTRY (brak punktu wejścia)](https://msdn.microsoft.com/library/0214dd41-35ad-43ab-b892-e636e038621a).  
  
- **ObjectFiles**  
  
   Parametr niejawnego **ciągu []** .  
  
   Określa pliki obiektów, które są połączone.  
  
- **OptimizeReferences**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, eliminuje funkcje i/lub dane, które nigdy nie są przywoływane.  
  
   Aby uzyskać więcej informacji, zobacz argument `REF` w [/opt (optymalizacje)](https://msdn.microsoft.com/library/8f229863-5f53-48a8-9478-243a647093ac).  
  
- **OutputFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora.  
  
   Aby uzyskać więcej informacji, zobacz [/out (nazwa pliku wyjściowego)](https://msdn.microsoft.com/library/976210a4-e51f-4cfb-af5e-c16344455834).  
  
- **PerUserRedirection**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true` i rejestrowanie danych wyjściowych jest włączone, wymusza, aby zapisy rejestru **HKEY_CLASSES_ROOT** przekierowywać do **HKEY_CURRENT_USER**.  
  
- **PreprocessOutput**  
  
   Opcjonalny parametr `ITaskItem[]`.  
  
   Definiuje tablicę elementów wyjściowych preprocesora, które mogą być używane i emitowane przez zadania.  
  
- **PreventDllBinding**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, wskazuje, że program bind. exe nie powinien być powiązany z połączonym obrazem.  
  
   Aby uzyskać więcej informacji, zobacz [/ALLOWBIND (Zapobiegaj powiązaniu biblioteki dll)](https://msdn.microsoft.com/library/30e37e24-12e4-407e-988a-39d357403598).  
  
- **Profilu**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, tworzy plik wyjściowy, który może być używany z profilerem **narzędzi do oceny wydajności** .  
  
   Aby uzyskać więcej informacji, zobacz [/Profile (Profiler narzędzi do oceny wydajności)](https://msdn.microsoft.com/library/e676baa1-5063-47a3-a357-ba0d1f0d1699).  
  
- **ProfileGuidedDatabase**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę pliku. pgd, który będzie używany do przechowywania informacji o działającym programie  
  
   Aby uzyskać więcej informacji, zobacz [/PGD (Określ bazę danych dla optymalizacji](https://msdn.microsoft.com/library/9f312498-493b-461f-886f-92652257e443)profilowanej).  
  
- **ProgramDatabaseFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę bazy danych programu (PDB), którą tworzy konsolidator.  
  
   Aby uzyskać więcej informacji, zobacz [/PDB (Korzystanie z bazy danych programu)](https://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d).  
  
- **RandomizedBaseAddress**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program generuje obraz wykonywalny, który może być losowo zmieniany w czasie ładowania przy użyciu funkcji *losowego układu przestrzeni adresowej* (ASLR) systemu Windows.  
  
   Aby uzyskać więcej informacji, zobacz [/DYNAMICBASE (Użyj losowości układu przestrzeni adresowej)](https://msdn.microsoft.com/library/6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2).  
  
- **RegisterOutput**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, rejestruje podstawowe dane wyjściowe tej kompilacji.  
  
- **Wyrównanie sekcji**  
  
   Opcjonalny parametr **liczby całkowitej** .  
  
   Określa wyrównanie każdej sekcji w liniowej przestrzeni adresowej programu. Wartość parametru jest liczbą jednostek bajtów i jest potęgą liczby 2.  
  
   Aby uzyskać więcej informacji, zobacz [/align (wyrównanie sekcji)](https://msdn.microsoft.com/library/f2f8ac24-e90e-4bea-8205-f2960a3b1740).  
  
- **SetChecksum**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, ustawia sumę kontrolną w nagłówku pliku. exe.  
  
   Aby uzyskać więcej informacji, zobacz [/Release (Ustaw sumę kontrolną)](https://msdn.microsoft.com/library/93bcadf4-29ac-4824-914b-6997e3751d22).  
  
- **ShowProgress**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa szczegółowość raportów postępu dla operacji łączenia.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** -  *\<none>*  
  
  - **LinkVerbose** -  **/VERBOSE**  
  
  - **LinkVerboseLib** -  **/VERBOSE:Lib**  
  
  - **LinkVerboseICF** -  **/VERBOSE:ICF**  
  
  - **LinkVerboseREF** -  **/VERBOSE:REF**  
  
  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**  
  
  - **LinkVerboseCLR** -  **/VERBOSE:CLR**  
  
    Aby uzyskać więcej informacji, zobacz [/verbose (drukowanie komunikatów o postępie)](https://msdn.microsoft.com/library/9c347d98-4c37-4724-a39e-0983934693ab).  
  
- **Źródeł**  
  
   Wymagany `ITaskItem[]` parametr.  
  
   Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.  
  
- **SpecifySectionAttributes**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa atrybuty sekcji. Zastępuje to atrybuty, które zostały ustawione, gdy plik. obj sekcji został skompilowany.  
  
   Aby uzyskać więcej informacji, zobacz [/Section (Określ atrybuty sekcji)](https://msdn.microsoft.com/library/92b69d81-e421-462e-b46f-7d0dff9b9d16).  
  
- **StackCommitSize**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa ilość pamięci fizycznej w każdej alokacji po przydzieleniu dodatkowej pamięci.  
  
   Aby uzyskać więcej informacji, zobacz argument `commit` [/Stack (alokacje stosu)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StackReserveSize**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa całkowity rozmiar alokacji stosu w pamięci wirtualnej.  
  
   Aby uzyskać więcej informacji, zobacz argument `reserve` [/Stack (alokacje stosu)](https://msdn.microsoft.com/library/73283660-e4bd-47cc-b5ca-04c5d739034c).  
  
- **StripPrivateSymbols**  
  
   Opcjonalny parametr **ciągu** .  
  
   Tworzy drugi plik bazy danych programu (PDB), który pomija symbole, które nie mają być rozpowszechniane do klientów. Określ nazwę drugiego pliku PDB.  
  
   Aby uzyskać więcej informacji, zobacz [/PDBSTRIPPED (symbole prywatne)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).  
  
- **SubSystem**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa środowisko dla pliku wykonywalnego.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** -  *\<none>*  
  
  - **Konsola** -  **/SUBSYSTEM: Konsola**  
  
  - **Windows** -  **/SUBSYSTEM:WINDOWS**  
  
  - **Native** -  **/SUBSYSTEM:NATIVE**  
  
  - **Aplikacja EFI** -  **/SUBSYSTEM: EFI_APPLICATION**  
  
  - **Sterownik usługi rozruchu EFI** -  **/SUBSYSTEM: EFI_BOOT_SERVICE_DRIVER**  
  
  - **Interfejs EFI ROM** -  **/SUBSYSTEM: EFI_ROM**  
  
  - **EFI Runtime** -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**  
  
  - **WindowsCE** -  **/SUBSYSTEM:WINDOWSCE**  
  
  - **POSIX** -  **/SUBSYSTEM:POSIX**  
  
    Aby uzyskać więcej informacji, zobacz [/subsystem (Określanie podsystemu)](https://msdn.microsoft.com/library/d7b133cf-cf22-4da8-ab46-6552702c0b9b).  
  
- **SupportNobindOfDelayLoadedDLL**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, nakazuje konsolidatorowi nieuwzględnienie tabeli adresów importu (IAT) w końcowym obrazie.  
  
   Aby uzyskać więcej informacji, zobacz argument `NOBIND` [/Delay (ustawienia opóźnienia importowania ładowania)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SupportUnloadOfDelayLoadedDLL**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, nakazuje funkcji pomocnika ładowania opóźnień, aby obsługiwała jawne wyładowywanie biblioteki DLL.  
  
   Aby uzyskać więcej informacji, zobacz argument `UNLOAD` [/Delay (ustawienia opóźnienia importowania ładowania)](https://msdn.microsoft.com/library/9334b332-cc58-4dae-b10f-a4c75972d50c).  
  
- **SuppressStartupBanner**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.  
  
   Aby uzyskać więcej informacji, zobacz [/nologo (Pomijanie transparentu startowego) (Konsolidator)](https://msdn.microsoft.com/library/3b20dddd-eca6-4545-a331-9f70bf720197).  
  
- **SwapRunFromCD**  
  
   Opcjonalny parametr **logiczny** .  
  
   W przypadku `true`program instruuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
   Aby uzyskać więcej informacji, zobacz argument `CD` [/SWAPRUN (ładowanie danych wyjściowych konsolidatora do pliku wymiany)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Zobacz również parametr **SwapRunFromNET** .  
  
- **SwapRunFromNET**  
  
   Opcjonalny parametr **logiczny** .  
  
   W przypadku `true`program instruuje system operacyjny, aby najpierw skopiował dane wyjściowe konsolidatora do pliku wymiany, a następnie uruchomił obraz stamtąd.  
  
   Aby uzyskać więcej informacji, zobacz argument `NET` [/SWAPRUN (ładowanie danych wyjściowych konsolidatora do pliku wymiany)](https://msdn.microsoft.com/library/4a1e7f46-4399-4161-8dfc-d6a71beaf683). Zobacz również parametr **SwapRunFromCD** w tej tabeli.  
  
- **TargetMachine**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa platformę docelową dla programu lub biblioteki DLL.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **NotSet** -  *\<none>*  
  
  - **MachineARM** -  **/Machine: ARM**  
  
  - **MachineEBC** -  **/MACHINE:EBC**  
  
  - **MachineIA64** -  **/MACHINE:IA64**  
  
  - **MachineMIPS** -  **/MACHINE:MIPS**  
  
  - **MachineMIPS16** -  **/MACHINE:MIPS16**  
  
  - **MachineMIPSFPU** -  **/MACHINE:MIPSFPU**  
  
  - **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**  
  
  - **MachineSH4** -  **/MACHINE:SH4**  
  
  - **MachineTHUMB** -  **/Machine: kciuk**  
  
  - **MachineX64** -  **/MACHINE:X64**  
  
  - **MachineX86** -  **/MACHINE:X86**  
  
    Aby uzyskać więcej informacji, zobacz [/Machine (Określ platformę docelową)](https://msdn.microsoft.com/library/8d41bf4b-7e53-4ab9-9085-d852b08d31c2).  
  
- **TerminalServerAware**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, ustawia flagę w polu IMAGE_OPTIONAL_HEADER DllCharacteristics w opcjonalnym nagłówku obrazu programu. Po ustawieniu tej flagi serwer terminali nie wprowadza pewnych zmian do aplikacji.  
  
   Aby uzyskać więcej informacji, zobacz [/TSAWARE (Tworzenie aplikacji z obsługą serwera terminali)](https://msdn.microsoft.com/library/fe1c1846-de5b-4839-b562-93fbfe36cd29).  
  
- **Katalog trackerlogdirectory**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa katalog dziennika śledzenia.  
  
- **TreatLinkerWarningAsErrors**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator generuje ostrzeżenie.  
  
   Aby uzyskać więcej informacji, zobacz [/WX (Traktuj ostrzeżenia konsolidatora jako błędy)](https://msdn.microsoft.com/library/e4ba97c7-93f7-43ae-a4bb-d866790926c9).  
  
- **TurnOffAssemblyGeneration**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, program tworzy obraz dla bieżącego pliku wyjściowego bez zestawu .NET Framework.  
  
   Aby uzyskać więcej informacji, zobacz [/NOASSEMBLY (Create a module MSIL)](https://msdn.microsoft.com/library/3cea4e70-f451-4395-a626-1930b1b127fe).  
  
- **TypeLibraryFile**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa nazwę pliku i rozszerzenie nazwy pliku. tlb. Określ nazwę pliku lub ścieżkę i nazwę pliku.  
  
   Aby uzyskać więcej informacji, zobacz [/TLBOUT (Name. Plik TLB)](https://msdn.microsoft.com/library/0df6d078-2e48-46c9-a1a5-02674d85dce8).  
  
- **TypeLibraryResourceID**  
  
   Opcjonalny parametr **liczby całkowitej** .  
  
   Określa wartość określoną przez użytkownika dla biblioteki typów utworzonej przez konsolidator. Określ wartość od 1 do 65535.  
  
   Aby uzyskać więcej informacji, zobacz [/TLBID (Określ identyfikator zasobu dla biblioteki typów)](https://msdn.microsoft.com/library/434b28a2-4656-4d52-ac82-8b18bf486fb2).  
  
- **UACExecutionLevel**  
  
   Opcjonalny parametr **ciągu** .  
  
   Określa żądany poziom wykonywania aplikacji, gdy jest uruchamiany w ramach kontroli konta użytkownika.  
  
   Określ jedną z następujących wartości, z których każdy odpowiada opcji wiersza polecenia.  
  
  - **AsInvoker** - `level='asInvoker'`  
  
  - **HighestAvailable** - `level='highestAvailable'`  
  
  - **RequireAdministrator** - `level='requireAdministrator'`  
  
    Aby uzyskać więcej informacji, zobacz argument `level` [/MANIFESTUAC (osadza informacje funkcji kontroli konta użytkownika w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UACUIAccess**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, aplikacja pomija poziomy ochrony interfejsu użytkownika i dyski wejściowe w oknach wyższych uprawnień na pulpicie; w przeciwnym razie `false`.  
  
   Aby uzyskać więcej informacji, zobacz argument `uiAccess` [/MANIFESTUAC (osadza informacje funkcji kontroli konta użytkownika w manifeście)](https://msdn.microsoft.com/library/2d243c39-fa13-493c-b56f-d0d972a1603a).  
  
- **UseLibraryDependencyInputs**  
  
   Opcjonalny parametr **logiczny** .  
  
   Jeśli `true`, dane wejściowe narzędzia bibliotekarza są używane zamiast pliku biblioteki, gdy dane wyjściowe biblioteki są połączone w programie.  
  
- **Wersja**  
  
   Opcjonalny parametr **ciągu** .  
  
   Umieść numer wersji w nagłówku pliku. exe lub. dll. Określ wartość "`major[.minor]`". Argumenty `major` i `minor` są liczbami dziesiętnymi od 0 do 65535.  
  
   Aby uzyskać więcej informacji, zobacz [/Version (informacje o wersji)](https://msdn.microsoft.com/library/b86d0e86-dca6-4316-aee2-d863ccb9f223).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

---
title: Vbc — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3d829a439ec7fb61247e28146e80d4988f04623
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659699"
---
# <a name="vbc-task"></a>Vbc — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opakowuje vbc.exe, który tworzy pliki wykonywalne (.exe), bibliotek dołączanych dynamicznie (dll) lub modułów kodu (.netmodule). Aby uzyskać więcej informacji na temat vbc.exe, zobacz [kompilatora wiersza polecenia programu Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Vbc` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalnie `String[]` parametru.<br /><br /> Określa dodatkowe foldery, w którym do wyszukiwania określonego w atrybucie odwołania do zestawów.|  
|`AddModules`|Opcjonalnie `String[]` parametru.<br /><br /> Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu. Ten parametr odnosi się do [/addmodule](http://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) przełącznika kompilatora vbc.exe.|  
|`BaseAddress`|Opcjonalnie `String` parametru.<br /><br /> Określa adres podstawowy DLL. Ten parametr odnosi się do [/baseAddress](http://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) przełącznika kompilatora vbc.exe.|  
|`CodePage`|Opcjonalnie `Int32` parametru.<br /><br /> Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji. Ten parametr odnosi się do [/CODEPAGE](http://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) przełącznika kompilatora vbc.exe.|  
|`DebugType`|Opcjonalnie `String[]` parametru.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full`, który umożliwia dołączanie debugera do uruchomionego programu. Wartość `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchomiony w debugerze, ale tylko wtedy, gdy jest uruchomiony program jest dołączony do debugera jest wyświetlany kod języka asemblera. Aby uzyskać więcej informacji, zobacz [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Opcjonalnie `String[]` parametru.<br /><br /> Definiuje stałe warunkowe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określane za pomocą następującej składni:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Ten parametr odnosi się do [/ define](http://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) przełącznika kompilatora vbc.exe.|  
|`DelaySign`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadania, umieszcza klucz publiczny w zestawie. Jeśli `false`, zadanie jest w pełni podpisuje zestaw. Wartość domyślna to `false`. Ten parametr jest ignorowany, chyba że używana z `KeyFile` parametru lub `KeyContainer` parametru. Ten parametr odnosi się do [/DelaySign](http://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) przełącznika kompilatora vbc.exe.|  
|`DisabledWarnings`|Opcjonalnie `String` parametru.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić część numeryczna identyfikatora ostrzeżenia. Wielokrotne ostrzeżenia są oddzielone średnikami. Ten parametr odnosi się do [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) przełącznika kompilatora vbc.exe.|  
|`DocumentationFile`|Opcjonalnie `String` parametru.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybutu. Aby uzyskać więcej informacji, zobacz [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku .pdb. Aby uzyskać więcej informacji, zobacz [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Opcjonalnie `String` parametru.<br /><br /> Określa, jak zadanie powinno zgłosić wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` jest określona i wystąpi błąd wewnętrzny kompilatora, użytkownik jest monitowany przy użyciu opcji instytucji wysyłać dane o błędach do firmy Microsoft.<br /><br /> Jeśli `send` jest określona i wystąpi błąd wewnętrzny kompilatora, zadanie wysyła dane o błędach do firmy Microsoft.<br /><br /> Wartość domyślna to `none`, który zgłasza błędy w danych wyjściowych tylko tekst.<br /><br /> Ten parametr odnosi się do [/errorreport](http://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) przełącznika kompilatora vbc.exe.|  
|`FileAlignment`|Opcjonalnie `Int32` parametru.<br /><br /> Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odnosi się do [/filealign](http://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) przełącznika kompilatora vbc.exe.|  
|`GenerateDocumentation`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, generuje informacje o dokumentacji i umieszcza je w pliku XML o nazwie pliku wykonywalnego lub biblioteki, która tworzy zadanie. Aby uzyskać więcej informacji, zobacz [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Importuje przestrzenie nazw z kolekcji określonego elementu. Ten parametr odnosi się do [/importuje](http://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) przełącznika kompilatora vbc.exe.|  
|`KeyContainer`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Corresonds tego parametru, aby [/KeyContainer](http://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) przełącznika kompilatora vbc.exe.|  
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [/KeyFile](http://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|(Opcjonalne [String]<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> Określa wersję języka, "9" lub "10".|  
|`LinkResources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do zasobów .NET Framework w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym. Ten parametr odnosi się do [/linkresource](http://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) przełącznika kompilatora vbc.exe.|  
|`MainEntryPoint`|Opcjonalnie `String` parametru.<br /><br /> Określa klasę lub moduł, który zawiera `Sub Main` procedury. Corresonds tego parametru, aby [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) przełącznika kompilatora vbc.exe.|  
|`ModuleAssemblyName`|Opcjonalnie `String` parametru.<br /><br /> Określa zestaw, do którego należy ten moduł.|  
|`NoConfig`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, że kompilator nie powinien używać soubor vbc.rsp. Ten parametr odnosi się do [/noconfig](http://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) parametru kompilatora vbc.exe.|  
|`NoLogo`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparencie kompilatora. Ten parametr odnosi się do [/nologo](http://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) przełącznika kompilatora vbc.exe.|  
|`NoStandardLib`|Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że kompilator, aby nie odwoływać się do standardowych bibliotek. Ten parametr odnosi się do [/nostdlib](http://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) przełącznika kompilatora vbc.exe.|  
|`NoVBRuntimeReference`|Opcjonalnie `Boolean` parametru.<br /><br /> Wyłącznie do użytku wewnętrznego. W przypadku opcji true uniemożliwia automatyczne odwołanie do pliku Microsoft.VisualBasic.dll...|  
|`NoWarnings`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie wyłącza wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, umożliwia optymalizacje kompilatora. Ten parametr odnosi się do [/ optimize](http://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) przełącznika kompilatora vbc.exe.|  
|`OptionCompare`|Opcjonalnie `String` parametru.<br /><br /> Określa, jak są wykonywane porównywania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` Określa, że zadanie używa porównania ciągów binarnych. Wartość `text` Określa, że zadanie używa porównania ciągów tekstu. Wartość domyślna tego parametru to `binary`. Ten parametr odnosi się do [/optioncompare —](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) przełącznika kompilatora vbc.exe.|  
|`OptionExplicit`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, jawnej deklaracji zmiennych jest wymagana. Ten parametr odnosi się do [/optionexplicit —](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) przełącznika kompilatora vbc.exe.|  
|`OptionInfer`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, umożliwia wnioskowanie o typie zmiennych.|  
|`OptionStrict`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów. Ten parametr odnosi się do [/optionstrict —](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) przełącznika kompilatora vbc.exe.|  
|`OptionStrictType`|Opcjonalnie `String` parametru.<br /><br /> Określa, które semantykę typów ścisłych generować ostrzeżenie. Aktualnie obsługiwana jest tylko "niestandardowe". Ten parametr odnosi się do [/optionstrict —](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) przełącznika kompilatora vbc.exe.|  
|`OutputAssembly`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odnosi się do [/out](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) przełącznika kompilatora vbc.exe.|  
|`Platform`|Opcjonalnie `String` parametru.<br /><br /> Określa platformę procesora, który ma zostać użyty przez plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, `Itanium`, lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odnosi się do [/platform](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) przełącznika kompilatora vbc.exe.|  
|`References`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Ten parametr odnosi się do [/reference](http://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) przełącznika kompilatora vbc.exe.|  
|`RemoveIntegerChecks`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wyłącza sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ten parametr odnosi się do [/removeintchecks —](http://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) przełącznika kompilatora vbc.exe.|  
|`Resources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza zasób .NET Framework do pliku wyjściowego. Ten parametr odnosi się do [/Resource](http://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) przełącznika kompilatora vbc.exe.|  
|`ResponseFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia służące do tego zadania. Ten parametr odnosi się do [@ (Określ plik odpowiedzi)](http://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) — opcja kompilatora vbc.exe.|  
|`RootNamespace`|Opcjonalnie `String` parametru.<br /><br /> Określa przestrzeń nazw korzenia dla wszystkich deklaracji typów. Ten parametr odnosi się do [/rootnamespace —](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) przełącznika kompilatora vbc.exe.|  
|`SdkPath`|Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację mscorlib.dll i microsoft.visualbasic.dll. Ten parametr odnosi się do [/sdkpath —](http://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) przełącznika kompilatora vbc.exe.|  
|`Sources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa co najmniej jeden [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] plików źródłowych.|  
|`TargetCompactFramework`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, cele zadania [!INCLUDE[Compact](../includes/compact-md.md)]. Ta opcja odnosi się do [/netcf —](http://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) przełącznika kompilatora vbc.exe.|  
|`TargetType`|Opcjonalnie `String` parametru.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartości `library`, tworzy bibliotekę kodu `exe`, tworzy aplikacji konsoli, `module`, co powoduje utworzenie modułu, lub `winexe`, która tworzy Windows program. Wartość domyślna to `library`. Ten parametr odnosi się do [/target](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) przełącznika kompilatora vbc.exe.|  
|`Timeout`|Opcjonalnie `Int32` parametru.<br /><br /> Określa ilość czasu w milisekundach, po których zostanie zakończony wykonywalnego zadania podrzędnego. Wartość domyślna to `Int.MaxValue`, wskazujący, że nie okres limitu czasu.|  
|`ToolPath`|Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację, z którym zadanie załaduje podstawowego pliku wykonywalnego (vbc.exe). Jeśli nie określono tego parametru, zadanie używa ścieżki instalacji zestawu SDK odpowiadający wersję framework, na którym działa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`TreatWarningsAsErrors`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że zadanie używa obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępny. Używany wyłącznie przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Opcjonalnie `Boolean` parametru.<br /><br /> Kompilator dzienniki danych wyjściowych przy użyciu kodowania UTF-8. Ten parametr odnosi się do [/utf8output](http://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) przełącznika kompilatora vbc.exe.|  
|`Verbosity`|Opcjonalnie `String` parametru.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Poziom szczegółowości można `Quiet`, `Normal` (ustawienie domyślne) lub `Verbose`.|  
|`WarningsAsErrors`|Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń do traktowania jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](http://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` parametr ma wartość `true`.|  
|`Win32Icon`|Opcjonalnie `String` parametru.<br /><br /> Wstawia plik .ico w zestawie, który nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Ten parametr odnosi się do [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) przełącznika kompilatora vbc.exe.|  
|`Win32Resources`|Opcjonalnie `String` parametru.<br /><br /> Wstawia plik zasobów (.res) Win32 w pliku wyjściowym. Ten parametr odnosi się do [/win32resource —](http://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) przełącznika kompilatora vbc.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

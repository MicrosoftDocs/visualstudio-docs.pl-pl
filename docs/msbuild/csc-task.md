---
title: CSC — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a505194a71058d791b7d67d74cd203c43298d684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778417"
---
# <a name="csc-task"></a>Csc — Zadanie
Opakowuje *csc.exe*i tworzy pliki wykonywalne (*.exe* plików), bibliotek dołączanych dynamicznie (*.dll* plików), lub modułów kodu (*.netmodule* pliki). Aby uzyskać więcej informacji na temat *csc.exe*, zobacz [opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry `Csc` zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalnie `String[]` parametru.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-lib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Opcjonalnie `String` parametru.<br /><br /> Określa jeden lub wiele modułów jako część zestawu. Aby uzyskać więcej informacji, zobacz [- addmodule (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, kompiluje kod, który używa [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [-unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Opcjonalnie `String` parametru.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu. |
| `BaseAddress` | Opcjonalnie `String` parametru.<br /><br /> Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [- baseaddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy liczba całkowita arytmetyczny, który przepełnienie granic o typie danych powoduje wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [-zaznaczone (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Opcjonalnie `Int32` parametru.<br /><br /> Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [- codepage (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Opcjonalnie `String` parametru.<br /><br /> Określa typ debugowania. `DebugType` może być `full` lub `pdbonly`. Wartość domyślna to `full`, co pozwala debuger dołączony do uruchomionego programu. Określanie `pdbonly` umożliwia źródła debugowania kodu, gdy program jest uruchomiony w debugerze, ale są wyświetlane tylko asemblera, gdy uruchomiony program jest dołączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Opcjonalnie `String` parametru.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [— zdefiniuj (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że chcesz, aby podpisać zestaw całkowicie. Jeśli `false`, określa, że chcesz tylko umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr jest ignorowany, chyba że używany z `KeyFile` lub `KeyContainer` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [- delaysign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Opcjonalnie `Boolean` parametru.<br/><br/> Jeśli `true`, powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczne (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [- nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Opcjonalnie `String` parametru.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych (PDB) programu. Jeśli `false`, zadanie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Opcjonalnie `String` parametru.<br /><br /> Zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny C# do firmy Microsoft. Ten parametr może mieć wartość `prompt`, `send`, lub `none`. Jeśli parametr jest ustawiony na `prompt`, zostanie wyświetlony monit, gdy wystąpi błąd wewnętrzny kompilatora. Monit umożliwia elektronicznie Wyślij raport o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send`, raport o usterce są wysyłane automatycznie. Jeśli parametr jest ustawiony na `none`, tylko w tekst wyjściowy kompilatora zgłaszany jest błąd. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [- errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Opcjonalnie `Int32` parametru.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [- filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa bezwzględną ścieżkę do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [- fullpaths (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [- keycontainer (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [- keyfile (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa wersję języka. Aby uzyskać więcej informacji, zobacz [- langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zasobu w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym.<br /><br /> Pozycji przekazanych do tego parametru może zawierać wpisy opcjonalne metadane, o nazwie `LogicalName` i `Access`. `LogicalName` odnosi się do `identifier` parametru `/linkresource` przełączyć, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [- linkresource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [-main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę zestawu, który będzie należeć tego modułu. |
| `NoConfig` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, informuje kompilator, nie można skompilować przy użyciu *csc.rsp* pliku. Aby uzyskać więcej informacji, zobacz [- noconfig (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparencie kompilatora. Aby uzyskać więcej informacji, zobacz [- nologo (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uniemożliwia importowania *mscorlib.dll*, która określa całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub tworzyć własne systemową przestrzenią nazw i obiektów. Aby uzyskać więcej informacji, zobacz [- nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nie dołączaj domyślny manifest Win32. |
| `Optimize` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-Optymalizuj (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku wyjściowego zestawu odwołania. Aby uzyskać więcej informacji, zobacz [- opcji refout (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku informacji debugowania. Domyślna nazwa to nazwa pliku wyjściowego z *.pdb* rozszerzenia. |
| `Platform` | Opcjonalnie `String` parametru.<br /><br /> Określa platformę procesora, który ma zostać użyty przez plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [— odwołanie (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Można określić [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] odwołania aliasu w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku, dodając metadanych `Aliases` do oryginalnego elementu "Odwołanie". Na przykład można ustawić aliasu "LS1" w wierszu polecenia następujące Csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> należy użyć:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zasobów do pliku wyjściowego.<br /><br /> Pozycji przekazanych do tego parametru może zawierać wpisy opcjonalne metadane, o nazwie `LogicalName` i `Access`. `LogicalName` odnosi się do `identifier` parametru `/resource` przełączyć, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [-resource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Opcjonalnie `String` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia służące do tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików źródłowych. |
| `TargetType` | Opcjonalnie `String` parametru.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartości `library`, tworzy bibliotekę kodu `exe`, tworzy aplikacji konsoli, `module`, co powoduje utworzenie modułu, lub `winexe`, która tworzy Windows program. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [-target (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że zadanie używa obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępny. Używany wyłącznie przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Opcjonalnie `Boolean` parametru.<br /><br /> Kompilator dzienniki danych wyjściowych przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Opcjonalnie `Int32` parametru.<br /><br /> Określa poziom ostrzeżeń kompilatora do wyświetlenia. Aby uzyskać więcej informacji, zobacz [-warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń do traktowania jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru. |
| `WarningsNotAsErrors` | Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` parametr ma wartość `true`. |
| `Win32Icon` | Opcjonalnie `String` parametru.<br /><br /> Wstawia *.ico* pliku w zestawie, który nadaje plikowi wyjściowemu pożądany wygląd w **Eksploratora plików**. Aby uzyskać więcej informacji, zobacz [-win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Opcjonalnie `String` parametru.<br /><br /> Określa manifest Win32 do uwzględnienia. |
| `Win32Resource` | Opcjonalnie `String` parametru.<br /><br /> Wstawia zasób Win32 (*.res*) pliku w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-win32res (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy po elemencie <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
W poniższym przykładzie użyto `Csc` zadanie, aby skompilować plik wykonywalny przy użyciu plików źródłowych w `Compile` elementu kolekcji.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

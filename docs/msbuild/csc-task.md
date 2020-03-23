---
title: Zadanie csc | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c88e5aaef9262d320cdf61564078246dee46b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634269"
---
# <a name="csc-task"></a>Csc — Zadanie

Zawija *csc.exe*i tworzy pliki wykonywalne (pliki*exe),* biblioteki łączy dynamicznych (pliki*dll)* lub moduły kodu (*.netmodule* files). Aby uzyskać więcej informacji na temat *programu csc.exe*, zobacz [Opcje kompilatora języka C#.](/dotnet/csharp/language-reference/compiler-options/index)

## <a name="parameters"></a>Parametry

W poniższej tabeli `Csc` opisano parametry zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Parametr `String[]` opcjonalny.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-lib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Parametr `String` opcjonalny.<br /><br /> Określa jeden lub więcej modułów, które mają być częścią złożenia. Aby uzyskać więcej informacji, zobacz [-addmodule (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, kompiluje kod, który używa [niebezpiecznego](/dotnet/csharp/language-reference/keywords/unsafe) słowa kluczowego. Aby uzyskać więcej informacji, zobacz [-unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Parametr `String` opcjonalny.<br /><br /> Określa plik konfiguracji aplikacji zawierający ustawienia powiązania złożenia. |
| `BaseAddress` | Parametr `String` opcjonalny.<br /><br /> Określa preferowany adres podstawowy, pod którym ma być ładowana biblioteka DLL. Domyślny adres podstawowy biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego programu .NET Framework. Aby uzyskać więcej informacji, zobacz [-baseaddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy arytmetyka liczba całkowita, która przepełnia granice typu danych powoduje wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [-checked (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Parametr `Int32` opcjonalny.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [-codepage (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Parametr `String` opcjonalny.<br /><br /> Określa typ debugowania. `DebugType`może `full` być `pdbonly`lub . Wartość domyślna to `full`, która umożliwia dołączeniu debugera do uruchomionego programu. Określenie `pdbonly` umożliwia debugowanie kodu źródłowego po uruchomieniu programu w debugerze, ale wyświetla asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametr.<br /><br /> Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Parametr `String` opcjonalny.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [-define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa, że chcesz umieścić tylko klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz w pełni podpisany zestaw<br /><br /> Ten parametr nie ma wpływu, `KeyFile` chyba `KeyContainer` że jest używany z lub parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [-delaysign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Parametr `Boolean` opcjonalny.<br/><br/> Jeśli `true`, powoduje, że kompilator do wyjścia zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministic (C# Opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które mają być wyłączone. Aby uzyskać więcej informacji, zobacz [-nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Parametr `String` opcjonalny.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie generuje informacje debugowania i umieszcza je w pliku bazy danych programu (pdb). Jeśli `false`zadanie nie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Parametr `String` opcjonalny.<br /><br /> Zapewnia wygodny sposób zgłaszania błędu wewnętrznego języka C# do firmy Microsoft. Ten parametr może mieć `prompt` `send`wartość `none`, lub . Jeśli parametr jest `prompt`ustawiony na , zostanie wyświetlony monit o wystąpienie błędu kompilatora wewnętrznego. Monit umożliwia wysłanie raportu o błędzie drogą elektroniczną do firmy Microsoft. Jeśli parametr jest `send`ustawiony na , raport o błędzie jest wysyłany automatycznie. Jeśli parametr jest `none`ustawiony na , błąd jest zgłaszany tylko w danych wyjściowych tekstu kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [-errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Parametr `Int32` opcjonalny.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-fullpaths (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [-keycontainer (opcje kompilatora Języka C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę pliku zawierającą klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-keyfile (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Parametr `String` opcjonalny.<br /><br /> Określa wersję języka, którego chcesz użyć. Aby uzyskać więcej informacji, zobacz [-langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Tworzy łącze do zasobu programu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przekazywane do tego parametru mogą `LogicalName` mieć `Access`opcjonalne wpisy metadanych o nazwie i . `LogicalName`odpowiada parametrowi `identifier` przełącznika `/linkresource` i `Access` odpowiada parametrowi. `accessibility-modifier` Aby uzyskać więcej informacji, zobacz [-linkresource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [-main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę zestawu, do których ten moduł będzie częścią. |
| `NoConfig` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, informuje kompilator, aby nie kompilować z pliku *csc.rsp.* Aby uzyskać więcej informacji, zobacz [-noconfig (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji baner kompilatora. Aby uzyskać więcej informacji, zobacz [-nologo (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, zapobiega importowi *pliku mscorlib.dll*, który definiuje całą przestrzeń nazw systemu. Ten parametr służy do definiowania lub tworzenia własnych obszarów nazw systemu i obiektów. Aby uzyskać więcej informacji, zobacz [-nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, nie zawierają domyślnego manifestu Win32. |
| `Optimize` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, umożliwia optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę wyjściowego pliku zestawu odwołań. Aby uzyskać więcej informacji, zobacz [-refout (opcje kompilatora Języka C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę pliku informacji debugowania. Domyślną nazwą jest nazwa pliku wyjściowego z rozszerzeniem *pdb.* |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Określa platformę procesora, na który ma dotyczy plik wyjściowy. Ten parametr może mieć `x86` `x64`wartość `anycpu`, lub . Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Powoduje, że zadanie do importowania informacji o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [-reference (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Alias odwołania języka C# w pliku MSBuild można `Aliases` określić, dodając metadane do oryginalnego elementu "Odwołanie". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia Csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> można użyć:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Osadza zasób programu .NET Framework w pliku wyjściowym.<br /><br /> Elementy przekazywane do tego parametru mogą `LogicalName` mieć `Access`opcjonalne wpisy metadanych o nazwie i . `LogicalName`odpowiada parametrowi `identifier` przełącznika `/resource` i `Access` odpowiada parametrowi. `accessibility-modifier` Aby uzyskać więcej informacji, zobacz [-resource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Parametr `String` opcjonalny.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określanie pliku odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa jeden lub więcej plików źródłowych języka C#. |
| `TargetType` | Parametr `String` opcjonalny.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć `library`wartość , która `exe`tworzy bibliotekę kodu, `module`, która tworzy `winexe`aplikację konsoli, , która tworzy moduł, lub , który tworzy program Windows. Wartością domyślną jest `library`. Aby uzyskać więcej informacji, zobacz [-target (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Parametr `Boolean` opcjonalny.<br /><br /> Nakazuje zadanie używać obiektu kompilatora w trakcie, jeśli jest dostępny. Używane tylko przez program Visual Studio. |
| `Utf8Output` | Parametr `Boolean` opcjonalny.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Parametr `Int32` opcjonalny.<br /><br /> Określa poziom ostrzeżenia dla kompilatora do wyświetlenia. Aby uzyskać więcej informacji, zobacz [-warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które należy traktować jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatny `TreatWarningsAsErrors` tylko wtedy, gdy parametr jest ustawiony na `true`. |
| `Win32Icon` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik *.ico* do złożenia, co nadaje plikowi wyjściowemu pożądany wygląd w **Eksploratorze plików**. Aby uzyskać więcej informacji, zobacz [-win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Parametr `String` opcjonalny.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony. |
| `Win32Resource` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik zasobu Win32 (*.res*) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-win32res (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `Csc` użyto zadania do skompilowania `Compile` pliku wykonywalnego z plików źródłowych w kolekcji elementów.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

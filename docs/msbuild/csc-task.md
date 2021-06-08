---
title: Zadania Csc | Microsoft Docs
description: W tym artykule opisano zadanie MSBuild Csc, które opakowywuje kompilator języka C#, csc.exe i tworzy pliki .exe, .dll lub .netmodule.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10a63b114379f56ca5f253f853a1ff6bdd6c60dc
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588478"
---
# <a name="csc-task"></a>Csc — Zadanie

Opakuje *csc.exe* i tworzy pliki wykonywalne *(pliki.exe),* biblioteki linków dynamicznych *(pliki.dll)* lub moduły kodu *(pliki .netmodule).* Aby uzyskać więcej informacji na *csc.exe*, zobacz [Opcje kompilatora języka C#.](/dotnet/csharp/language-reference/compiler-options/index)

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Csc` zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Parametr `String[]` opcjonalny.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-lib (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option) |
| `AddModules` | Parametr `String` opcjonalny.<br /><br /> Określa co najmniej jeden moduł, który ma być częścią zestawu. Aby uzyskać więcej informacji, zobacz [-addmodule (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) |
| `AllowUnsafeBlocks` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , kompiluje kod, który używa [niebezpiecznego słowa kluczowego](/dotnet/csharp/language-reference/keywords/unsafe) . Aby uzyskać więcej informacji, zobacz [-unsafe (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option) |
| `ApplicationConfiguration` | Parametr `String` opcjonalny.<br /><br /> Określa plik konfiguracji aplikacji zawierający ustawienia powiązania zestawu. |
| `BaseAddress` | Parametr `String` opcjonalny.<br /><br /> Określa preferowany adres podstawowy, pod którym należy załadować bibliotekę DLL. Domyślny adres podstawowy biblioteki DLL jest ustawiany przez środowisko .NET Framework uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [-baseaddress (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option) |
| `CheckForOverflowUnderflow` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, czy arytmetyka całkowita, która przepełnia granice typu danych, powoduje wyjątek w czasie uruchamiania. Aby uzyskać więcej informacji, zobacz [-checked (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option) |
| `CodePage` | Parametr `Int32` opcjonalny.<br /><br /> Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [-codepage (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option) |
| `DebugType` | Parametr `String` opcjonalny.<br /><br /> Określa typ debugowania. `DebugType` Może to być `full` lub `pdbonly` . Wartość domyślna to `full` , co umożliwia dołączanie debugera do uruchomionego programu. Określanie włącza debugowanie kodu źródłowego, gdy program jest uruchomiony w debugerze, ale wyświetla asembler tylko wtedy, gdy uruchomiony program jest dołączony `pdbonly` do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametr .<br /><br /> Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) |
| `DefineConstants` | Parametr `String` opcjonalny.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [-define (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/define-compiler-option) |
| `DelaySign` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli , określa, że chcesz tylko `true` umieścić klucz publiczny w zestawie. Jeśli `false` , określa, że chcesz mieć w pełni podpisany zestaw<br /><br /> Ten parametr nie ma wpływu, chyba że jest używany z `KeyFile` albo lub `KeyContainer` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [-delaysign (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option) |
| `Deterministic` | Parametr `Boolean` opcjonalny.<br/><br/> Jeśli `true` , powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministic (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option) |
| `DisabledWarnings` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które mają być wyłączone. Aby uzyskać więcej informacji, zobacz [-nowarn (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option) |
| `DocumentationFile` | Parametr `String` opcjonalny.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-doc (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option) |
| `EmbedAllSources` | Parametr `Boolean` opcjonalny.<br /><br /> Osadź wszystkie pliki źródłowe w pliku PDB. Aby uzyskać więcej informacji, zobacz [-embed (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically) |
| `EmitDebugInformation` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , zadanie generuje informacje debugowania i umieszcza je w pliku bazy danych programu (.pdb). Jeśli `false` , zadanie nie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) |
| `ErrorReport` | Parametr `String` opcjonalny.<br /><br /> Zapewnia wygodny sposób raportowania błędu wewnętrznego języka C# do firmy Microsoft. Ten parametr może mieć wartość `prompt` , `send` lub `none` . Jeśli parametr jest ustawiony na wartość , po wystąpienia wewnętrznego błędu kompilatora zostanie `prompt` wyświetlony monit. Monit umożliwia wysłanie elektronicznego raportu o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send` wartość , raport o usterce jest wysyłany automatycznie. Jeśli parametr jest ustawiony na `none` , błąd jest zgłaszany tylko w tekstowych danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [-errorreport (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option) |
| `FileAlignment` | Parametr `Int32` opcjonalny.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-filealign (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option) |
| `GenerateFullPaths` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false` , określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-fullpaths (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option) |
| `KeyContainer` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [-keycontainer (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option) |
| `KeyFile` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-keyfile (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option) |
| `LangVersion` | Parametr `String` opcjonalny.<br /><br /> Określa wersję języka do użycia. Aby uzyskać więcej informacji, zobacz [-langversion (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) |
| `LinkResources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Tworzy link do zasobu .NET Framework w pliku wyjściowym; Plik zasobów nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przekazane do tego parametru mogą mieć opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access` . `LogicalName` odpowiada `identifier` parametrowi `/linkresource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi . Aby uzyskać więcej informacji, zobacz [-linkresource (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) |
| `MainEntryPoint` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [-main (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) |
| `ModuleAssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę zestawu, który będzie częścią tego modułu. |
| `NoConfig` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , informuje kompilator, aby nie kompilował za pomocą *pliku csc.rsp.* Aby uzyskać więcej informacji, zobacz [-noconfig (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option) |
| `NoLogo` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , pomija wyświetlanie informacji transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [-nologo (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option) |
| `NoStandardLib` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , uniemożliwia importowanie *mscorlib.dll*, który definiuje całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw i obiekty systemu. Aby uzyskać więcej informacji, zobacz [-nostdlib (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option) |
| `NoWin32Manifest` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , nie należy dołączać domyślnego manifestu Win32. |
| `Optimize` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , program włącza optymalizacje. Jeśli `false` , wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-optimize (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option) |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) |
| `OutputRefAssembly` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę wyjściowego pliku zestawu referencyjnego. Aby uzyskać więcej informacji, zobacz [-refout (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option) |
| `PdbFile` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę pliku informacji debugowania. Nazwa domyślna to nazwa pliku wyjściowego z *rozszerzeniem .pdb.* |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Określa platformę procesora, która ma być docelowa dla pliku wyjściowego. Ten parametr może mieć wartość `x86` , `x64` lub `anycpu` . Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platform (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option) |
| `References` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [-reference (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)<br /><br /> Alias odwołania w języku C# można określić w pliku MSBuild, dodając metadane do `Aliases` oryginalnego elementu "Odwołanie". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia Csc:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Należy użyć:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym.<br /><br /> Elementy przekazane do tego parametru mogą mieć opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access` . `LogicalName` odpowiada `identifier` parametrowi `/resource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi . Aby uzyskać więcej informacji, zobacz [-resource (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option) |
| `ResponseFiles` | Parametr `String` opcjonalny.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi).](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option) |
| `Sources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa co najmniej jeden plik źródłowy języka C#. |
| `TargetType` | Parametr `String` opcjonalny.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartość , co powoduje utworzenie biblioteki kodu , która tworzy aplikację konsolową , , która tworzy moduł lub `library` , który tworzy program systemu `exe` `module` `winexe` Windows. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [-target (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/target-compiler-option) |
| `TreatWarningsAsErrors` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true` , wszystkie ostrzeżenia są traktować jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option) |
| `UseHostCompilerIfAvailable` | Parametr `Boolean` opcjonalny.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używany tylko przez Visual Studio. |
| `Utf8Output` | Parametr `Boolean` opcjonalny.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option) |
| `WarningLevel` | Parametr `Int32` opcjonalny.<br /><br /> Określa poziom ostrzeżenia dla kompilatora do wyświetlenia. Aby uzyskać więcej informacji, zobacz [-warn (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) |
| `WarningsAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które mają być traktować jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr . |
| `WarningsNotAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)<br /><br /> Ten parametr jest przydatny tylko `TreatWarningsAsErrors` wtedy, gdy parametr jest ustawiony na `true` . |
| `Win32Icon` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik *ico* do zestawu, co zapewnia żądany wygląd pliku wyjściowego w **Eksplorator plików**. Aby uzyskać więcej informacji, zobacz [-win32icon (opcje kompilatora języka C#).](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) |
| `Win32Manifest` | Parametr `String` opcjonalny.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony. |
| `Win32Resource` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik zasobu Win32 *(res)* w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-win32res (opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option) |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `Csc` zadania do skompilowania pliku wykonywalnego z plików źródłowych w `Compile` kolekcji elementów.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

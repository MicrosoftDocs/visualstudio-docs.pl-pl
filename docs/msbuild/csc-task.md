---
title: CSC — zadanie | Microsoft Docs
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
ms.openlocfilehash: 6f77a2ab5bfa137ffbab13f92b15707f73c7869e
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167426"
---
# <a name="csc-task"></a>Csc — Zadanie

Zawija plik *CSC. exe*i tworzy pliki wykonywalne (*. exe* ), biblioteki dołączane dynamicznie (pliki *. dll* ) lub moduły kodu (pliki *. module* ). Aby uzyskać więcej informacji o pliku *CSC. exe*, zobacz [Opcje kompilatora języka C#](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Csc` zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalny `String[]` parametr.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-lib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Opcjonalny `String` parametr.<br /><br /> Określa co najmniej jeden moduł, który ma być częścią zestawu. Aby uzyskać więcej informacji, zobacz [-addmodule (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, kompiluje kod, który używa słowa kluczowego [UNSAFE](/dotnet/csharp/language-reference/keywords/unsafe) . Aby uzyskać więcej informacji, zobacz [-unsafe (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Opcjonalny `String` parametr.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu. |
| `BaseAddress` | Opcjonalny `String` parametr.<br /><br /> Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework. Aby uzyskać więcej informacji, zobacz [-BaseAddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy arytmetyczne liczby całkowite, które przepływają granice typu danych, powodują wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [— zaznaczone (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Opcjonalny `Int32` parametr.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [-CodePage (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Opcjonalny `String` parametr.<br /><br /> Określa typ debugowania. `DebugType`może być `full` lub `pdbonly`. Wartość domyślna to `full`, co umożliwia dołączenie debugera do działającego programu. Określanie `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla tylko asembler, gdy uruchomiony program jest podłączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametr.<br /><br /> Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Opcjonalny `String` parametr.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [-define (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz użyć w pełni podpisanego zestawu<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest `KeyFile` używany `KeyContainer` z parametrem or.<br /><br /> Aby uzyskać więcej informacji, zobacz [-delaysign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Opcjonalny `Boolean` parametr.<br/><br/> Jeśli `true`, powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczne (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [-nowarn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Opcjonalny `String` parametr.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-doc (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (. pdb). Jeśli `false`zadanie nie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Opcjonalny `String` parametr.<br /><br /> Zapewnia wygodny sposób zgłaszania wewnętrznego błędu języka C# do firmy Microsoft. Ten parametr może mieć wartość `prompt`, `send`, lub. `none` Jeśli parametr jest ustawiony na `prompt`, zostanie wyświetlony monit, gdy wystąpi wewnętrzny błąd kompilatora. Monit umożliwia elektroniczne wysyłanie raportu o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send`, raport o usterce jest wysyłany automatycznie. Jeśli parametr jest ustawiony na `none`, błąd jest raportowany tylko w danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [-errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Opcjonalny `Int32` parametr.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-fullpaths — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Aby uzyskać więcej informacji, zobacz [--containerer (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-keyfile (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Opcjonalny `String` parametr.<br /><br /> Określa wersję języka do użycia. Aby uzyskać więcej informacji, zobacz [-langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access`. `LogicalName`odpowiada `identifier` `/linkresource` parametrowi przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. Aby uzyskać więcej informacji, zobacz [-linkresource — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [— Main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę zestawu, którego częścią ma być ten moduł. |
| `NoConfig` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, instruuje kompilator, aby nie kompilować z plikiem *CSC. rsp* . Aby uzyskać więcej informacji, zobacz [-noconfig (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [-nologo (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, program zapobiega importowaniu *biblioteki mscorlib. dll*, która definiuje całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty. Aby uzyskać więcej informacji, zobacz [-nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`nie, nie dołączaj domyślnego manifestu Win32. |
| `Optimize` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-Optimize (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę wyjściowego pliku zestawu odwołania. Aby uzyskać więcej informacji, zobacz [-opcji refout (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku informacji o debugowaniu. Nazwa domyślna to nazwa pliku wyjściowego z rozszerzeniem *. pdb* . |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, lub. `anycpu` Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platform (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [-Reference (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Można określić alias odwołania C# w pliku MSBuild, dodając metadane `Aliases` do oryginalnego elementu "Reference". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia CSC:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Użyj:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access`. `LogicalName`odpowiada `identifier` `/resource` parametrowi przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. Aby uzyskać więcej informacji, zobacz [-Resource (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Opcjonalny `String` parametr.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa co najmniej jeden plik źródłowy języka C#. |
| `TargetType` | Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego. `library`Ten parametr może mieć wartość, która tworzy bibliotekę kodu, `exe`która tworzy aplikację `module`konsolową, która tworzy moduł lub `winexe`tworzy program systemu Windows. Wartością domyślną jest `library`. Aby uzyskać więcej informacji, zobacz [-Target (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Opcjonalny `Boolean` parametr.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używany tylko przez program Visual Studio. |
| `Utf8Output` | Opcjonalny `Boolean` parametr.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Opcjonalny `Int32` parametr.<br /><br /> Określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany. Aby uzyskać więcej informacji, zobacz [-warn (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatny tylko wtedy `TreatWarningsAsErrors` , gdy parametr jest `true`ustawiony na. |
| `Win32Icon` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik *ICO* w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w **Eksploratorze plików**. Aby uzyskać więcej informacji, zobacz [-win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Opcjonalny `String` parametr.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony. |
| `Win32Resource` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik zasobów Win32 (*. res*) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-win32res — (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Przykład

Poniższy przykład używa `Csc` zadania do kompilowania pliku wykonywalnego z plików źródłowych w kolekcji `Compile` elementów.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz także

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

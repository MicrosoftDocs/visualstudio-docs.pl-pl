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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9df54befff79b82703cb363fea92536285c68232
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888032"
---
# <a name="csc-task"></a>Csc — Zadanie
Zawija plik *CSC. exe*i tworzy pliki wykonywalne ( *. exe* ), biblioteki dołączane dynamicznie (pliki *. dll* ) lub moduły kodu (pliki *. module* ). Aby uzyskać więcej informacji na temat pliku *CSC. exe*, zobacz [ C# opcje kompilatora](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry `Csc` zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalny `String[]` parametr.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-libC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Opcjonalny `String` parametr.<br /><br /> Określa co najmniej jeden moduł, który ma być częścią zestawu. Aby uzyskać więcej informacji, zobacz [-addmoduleC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, kompiluje kod, który używa słowa kluczowego [UNSAFE](/dotnet/csharp/language-reference/keywords/unsafe) . Aby uzyskać więcej informacji, zobacz [-unsafe (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Opcjonalny `String` parametr.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu. |
| `BaseAddress` | Opcjonalny `String` parametr.<br /><br /> Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework. Aby uzyskać więcej informacji, zobacz [-BaseAddressC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy arytmetyczne liczby całkowite, które przepływają granice typu danych, powodują wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [-CheckedC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Opcjonalny `Int32` parametr.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [-CodePageC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Opcjonalny `String` parametr.<br /><br /> Określa typ debugowania. `DebugType`może być `full` lub `pdbonly`. Wartość domyślna to `full`, co umożliwia dołączenie debugera do działającego programu. Określanie `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla tylko asembler, gdy uruchomiony program jest podłączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametr.<br /><br /> Aby uzyskać więcej informacji, zobacz [-DebugC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Opcjonalny `String` parametr.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [-defineC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false`, określa, że chcesz użyć w pełni podpisanego zestawu<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest `KeyFile` używany `KeyContainer` z parametrem or.<br /><br /> Aby uzyskać więcej informacji, zobacz [-delaysignC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Opcjonalny `Boolean` parametr.<br/><br/> Jeśli `true`, powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczny (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [-nowarnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Opcjonalny `String` parametr.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-docC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (. pdb). Jeśli `false`zadanie nie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-DebugC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Opcjonalny `String` parametr.<br /><br /> Zapewnia wygodny sposób zgłaszania C# wewnętrznego błędu do firmy Microsoft. Ten parametr może mieć wartość `prompt`, `send`, lub `none`. Jeśli parametr jest ustawiony na `prompt`, zostanie wyświetlony monit, gdy wystąpi wewnętrzny błąd kompilatora. Monit umożliwia elektroniczne wysyłanie raportu o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send`, raport o usterce jest wysyłany automatycznie. Jeśli parametr jest ustawiony na `none`, błąd jest raportowany tylko w danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [-errorreportC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Opcjonalny `Int32` parametr.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-filealignC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-fullpaths —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Aby uzyskać więcej informacji, zobacz [--containererC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-KeyFileC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Opcjonalny `String` parametr.<br /><br /> Określa wersję języka do użycia. Aby uzyskać więcej informacji, zobacz [-langversionC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access`. `LogicalName`odpowiada parametrowi `/linkresource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. `identifier` Aby uzyskać więcej informacji, zobacz [-linkresource —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [— MainC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę zestawu, którego częścią ma być ten moduł. |
| `NoConfig` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, instruuje kompilator, aby nie kompilować z plikiem *CSC. rsp* . Aby uzyskać więcej informacji, zobacz [-noconfigC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [-nologoC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, program zapobiega importowaniu *biblioteki mscorlib. dll*, która definiuje całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty. Aby uzyskać więcej informacji, zobacz [-nostdlibC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`nie, nie dołączaj domyślnego manifestu Win32. |
| `Optimize` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-Optimize (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-outC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę wyjściowego pliku zestawu odwołania. Aby uzyskać więcej informacji, zobacz [-opcji refoutC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku informacji o debugowaniu. Nazwa domyślna to nazwa pliku wyjściowego z rozszerzeniem *. pdb* . |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platformC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [-ReferenceC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Możesz określić [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] alias odwołania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] w pliku, dodając metadane `Aliases` do oryginalnego elementu "odwołanie". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia CSC:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Użyj:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o `LogicalName` nazwach i `Access`. `LogicalName`odpowiada parametrowi `/resource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. `identifier` Aby uzyskać więcej informacji, zobacz [-ResourceC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Opcjonalny `String` parametr.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plik źródłowy. |
| `TargetType` | Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego. Ten `library`parametr może mieć wartość, która tworzy bibliotekę kodu, `exe`która `module`tworzy aplikację konsolową, która tworzy moduł lub `winexe`tworzy program systemu Windows. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [-TargetC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Opcjonalny `Boolean` parametr.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używane tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Opcjonalny `Boolean` parametr.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Opcjonalny `Int32` parametr.<br /><br /> Określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany. Aby uzyskać więcej informacji, zobacz [-warnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatny tylko wtedy `TreatWarningsAsErrors` , gdy parametr jest `true`ustawiony na. |
| `Win32Icon` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik *ICO* w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w **Eksploratorze plików**. Aby uzyskać więcej informacji, zobacz [-win32iconC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Opcjonalny `String` parametr.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony. |
| `Win32Resource` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik zasobów Win32 ( *. res*) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-win32res —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy <xref:Microsoft.Build.Tasks.ToolTaskExtension> z klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład używa `Csc` zadania do kompilowania pliku wykonywalnego z plików źródłowych `Compile` w kolekcji elementów.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

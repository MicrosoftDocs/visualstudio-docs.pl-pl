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
ms.openlocfilehash: 7443ba29a743f4936ae104d9d0bb556fae3c4e2d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595387"
---
# <a name="csc-task"></a>Csc — Zadanie
Zawija plik *CSC. exe*i tworzy pliki wykonywalne ( *. exe* ), biblioteki dołączane dynamicznie (pliki *. dll* ) lub moduły kodu (pliki *. module* ). Aby uzyskać więcej informacji na temat pliku *CSC. exe*, zobacz [ C# opcje kompilatora](/dotnet/csharp/language-reference/compiler-options/index).

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `Csc`.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalny parametr `String[]`.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [-libC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option). |
| `AddModules` | Opcjonalny parametr `String`.<br /><br /> Określa co najmniej jeden moduł, który ma być częścią zestawu. Aby uzyskać więcej informacji, zobacz [-addmoduleC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option). |
| `AllowUnsafeBlocks` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, kompiluje kod, który używa słowa kluczowego [UNSAFE](/dotnet/csharp/language-reference/keywords/unsafe) . Aby uzyskać więcej informacji, zobacz [-unsafe (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option). |
| `ApplicationConfiguration` | Opcjonalny parametr `String`.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu. |
| `BaseAddress` | Opcjonalny parametr `String`.<br /><br /> Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez środowisko uruchomieniowe języka wspólnego .NET Framework. Aby uzyskać więcej informacji, zobacz [-BaseAddressC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option). |
| `CheckForOverflowUnderflow` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, czy arytmetyczne liczby całkowite, które przepływają granice typu danych, powodują wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [-CheckedC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option). |
| `CodePage` | Opcjonalny parametr `Int32`.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [-CodePageC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option). |
| `DebugType` | Opcjonalny parametr `String`.<br /><br /> Określa typ debugowania. `DebugType` można `full` lub `pdbonly`. Wartość domyślna to `full`, co umożliwia dołączenie debugera do działającego programu. Określenie `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla tylko asembler, gdy uruchomiony program jest podłączony do debugera.<br /><br /> Ten parametr zastępuje parametr `EmitDebugInformation`.<br /><br /> Aby uzyskać więcej informacji, zobacz [-DebugC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `DefineConstants` | Opcjonalny parametr `String`.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [-defineC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option). |
| `DelaySign` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa, że chcesz umieścić klucz publiczny w zestawie. Jeśli `false`, określa, że ma być w pełni podpisany zestaw<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest używany z parametrem `KeyFile` lub `KeyContainer`.<br /><br /> Aby uzyskać więcej informacji, zobacz [-delaysignC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option). |
| `Deterministic` | Opcjonalny parametr `Boolean`.<br/><br/> Jeśli `true`, powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczny (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/deterministic-compiler-option). |
| `DisabledWarnings` | Opcjonalny parametr `String`.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [-nowarnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option). |
| `DocumentationFile` | Opcjonalny parametr `String`.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [-docC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option). |
| `EmitDebugInformation` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (. pdb). Jeśli `false`, zadanie emituje brak informacji o debugowaniu. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-DebugC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option). |
| `ErrorReport` | Opcjonalny parametr `String`.<br /><br /> Zapewnia wygodny sposób zgłaszania C# wewnętrznego błędu do firmy Microsoft. Ten parametr może mieć wartość `prompt`, `send`lub `none`. Jeśli parametr ma wartość `prompt`, zostanie wyświetlony monit, gdy wystąpi wewnętrzny błąd kompilatora. Monit umożliwia elektroniczne wysyłanie raportu o usterce do firmy Microsoft. Jeśli parametr ma wartość `send`, raport o usterce jest wysyłany automatycznie. Jeśli parametr ma wartość `none`, błąd jest raportowany tylko w danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [-errorreportC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option). |
| `FileAlignment` | Opcjonalny parametr `Int32`.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [-filealignC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option). |
| `GenerateFullPaths` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [-fullpaths —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option). |
| `KeyContainer` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Aby uzyskać więcej informacji, zobacz [--containererC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option). |
| `KeyFile` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-KeyFileC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option). |
| `LangVersion` | Opcjonalny parametr `String`.<br /><br /> Określa wersję języka do użycia. Aby uzyskać więcej informacji, zobacz [-langversionC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option). |
| `LinkResources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o nazwie `LogicalName` i `Access`. `LogicalName` odpowiada parametrowi `identifier` przełącznika `/linkresource`, a `Access` odpowiada parametrowi `accessibility-modifier`. Aby uzyskać więcej informacji, zobacz [-linkresource —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option). |
| `MainEntryPoint` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację metody `Main`. Aby uzyskać więcej informacji, zobacz [— MainC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option). |
| `ModuleAssemblyName` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę zestawu, którego częścią ma być ten moduł. |
| `NoConfig` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, instruuje kompilator, aby nie kompilować z plikiem *CSC. rsp* . Aby uzyskać więcej informacji, zobacz [-noconfigC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option). |
| `NoLogo` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [-nologoC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option). |
| `NoStandardLib` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program zapobiega importowaniu plików *mscorlib. dll*, które definiują całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty. Aby uzyskać więcej informacji, zobacz [-nostdlibC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option). |
| `NoWin32Manifest` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, nie dołączaj domyślnego manifestu Win32. |
| `Optimize` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, program wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [-Optimize (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option). |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-outC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option). |
| `OutputRefAssembly` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę wyjściowego pliku zestawu odwołania. Aby uzyskać więcej informacji, zobacz [-opcji refoutC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/refout-compiler-option). |
| `PdbFile` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę pliku informacji o debugowaniu. Nazwa domyślna to nazwa pliku wyjściowego z rozszerzeniem *. pdb* . |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`lub `anycpu`. Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [-platformC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option). |
| `References` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [-ReferenceC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> Można określić alias odwołania [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] w pliku [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] przez dodanie metadanych `Aliases` do oryginalnego elementu "odwołanie". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia CSC:<br /><br /> `CSC /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Użyj:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>` |
| `Resources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o nazwie `LogicalName` i `Access`. `LogicalName` odpowiada parametrowi `identifier` przełącznika `/resource`, a `Access` odpowiada parametrowi `accessibility-modifier`. Aby uzyskać więcej informacji, zobacz [-ResourceC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option). |
| `ResponseFiles` | Opcjonalny parametr `String`.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option). |
| `Sources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki źródłowe. |
| `TargetType` | Opcjonalny parametr `String`.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartość `library`, która tworzy bibliotekę kodu, `exe`, która tworzy aplikację konsolową, `module`, która tworzy moduł, lub `winexe`, który tworzy program systemu Windows. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [-TargetC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option). |
| `TreatWarningsAsErrors` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option). |
| `UseHostCompilerIfAvailable` | Opcjonalny parametr `Boolean`.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używane tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Opcjonalny parametr `Boolean`.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [-utf8output —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option). |
| `WarningLevel` | Opcjonalny parametr `Int32`.<br /><br /> Określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany. Aby uzyskać więcej informacji, zobacz [-warnC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option). |
| `WarningsAsErrors` | Opcjonalny parametr `String`.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr zastępuje parametr `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Opcjonalny parametr `String`.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Ten parametr jest przydatny tylko wtedy, gdy parametr `TreatWarningsAsErrors` jest ustawiony na `true`. |
| `Win32Icon` | Opcjonalny parametr `String`.<br /><br /> Wstawia plik *ICO* w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w **Eksploratorze plików**. Aby uzyskać więcej informacji, zobacz [-win32iconC# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option). |
| `Win32Manifest` | Opcjonalny parametr `String`.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony. |
| `Win32Resource` | Opcjonalny parametr `String`.<br /><br /> Wstawia plik zasobów Win32 ( *. res*) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [-win32res —C# (opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option). |

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy `Microsoft.Build.Tasks.ManagedCompiler`, która dziedziczy z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład używa zadania `Csc` do kompilowania pliku wykonywalnego z plików źródłowych w kolekcji `Compile` elementów.

```xml
<CSC
    Sources="@(Compile)"
    OutputAssembly="$(AppName).exe"
    EmitDebugInformation="true" />
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

---
title: Vbc — zadanie | Dokumentacja firmy Microsoft
ms.date: 04/12/2018
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 585a3d4940d11508dbe6d8874cb401cfe380a690
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623830"
---
# <a name="vbc-task"></a>Vbc — Zadanie
Opakowuje *vbc.exe*, który tworzy pliki wykonywalne (*.exe*), bibliotek dołączanych dynamicznie (*.dll*), lub modułów kodu (*.netmodule*). Aby uzyskać więcej informacji na temat *vbc.exe*, zobacz [wiersza polecenia kompilatora języka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `Vbc` zadania.


| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalnie `String[]` parametru.<br /><br /> Określa dodatkowe foldery, w którym do wyszukiwania określonego w atrybucie odwołania do zestawów. |
| `AddModules` | Opcjonalnie `String[]` parametru.<br /><br /> Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu. Ten parametr odnosi się do [- addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) przełączyć z *vbc.exe* kompilatora. |
| `BaseAddress` | Opcjonalnie `String` parametru.<br /><br /> Określa adres podstawowy DLL. Ten parametr odnosi się do [- baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) przełączyć z *vbc.exe* kompilatora. |
| `CodePage` | Opcjonalnie `Int32` parametru.<br /><br /> Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji. Ten parametr odnosi się do [- strona kodowa](/dotnet/visual-basic/reference/command-line-compiler/codepage) przełączyć z *vbc.exe* kompilatora. |
| `DebugType` | Opcjonalnie `String[]` parametru.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full`, który umożliwia dołączanie debugera do uruchomionego programu. Wartość `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchomiony w debugerze, ale tylko wtedy, gdy jest uruchomiony program jest dołączony do debugera jest wyświetlany kod języka asemblera. Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Opcjonalnie `String[]` parametru.<br /><br /> Definiuje stałe warunkowe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określane za pomocą następującej składni:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Ten parametr odnosi się do [— Zdefiniuj](/dotnet/visual-basic/reference/command-line-compiler/define) przełączyć z *vbc.exe* kompilatora. |
| `DelaySign` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadania, umieszcza klucz publiczny w zestawie. Jeśli `false`, zadanie jest w pełni podpisuje zestaw. Wartość domyślna to `false`. Ten parametr jest ignorowany, chyba że używana z `KeyFile` parametru lub `KeyContainer` parametru. Ten parametr odnosi się do [- delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) przełączyć z *vbc.exe* kompilatora. |
| `Deterministic` | Opcjonalnie `Boolean` parametru.<br/><br/> Jeśli `true`, powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministyczne](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Opcjonalnie `String` parametru.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić część numeryczna identyfikatora ostrzeżenia. Wielokrotne ostrzeżenia są oddzielone średnikami. Ten parametr odnosi się do [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) przełączyć z *vbc.exe* kompilatora. |
| `DocumentationFile` | Opcjonalnie `String` parametru.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybutu. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w *.pdb* pliku. Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Opcjonalnie `String` parametru.<br /><br /> Określa, jak zadanie powinno zgłosić wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` jest określona i wystąpi błąd wewnętrzny kompilatora, użytkownik jest monitowany z opcjonalnym, czy wysyłać dane o błędach do firmy Microsoft.<br /><br /> Jeśli `send` jest określona i wystąpi błąd wewnętrzny kompilatora, zadanie wysyła dane o błędach do firmy Microsoft.<br /><br /> Wartość domyślna to `none`, który zgłasza błędy w danych wyjściowych tylko tekst.<br /><br /> Ten parametr odnosi się do [- errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) przełączyć z *vbc.exe* kompilatora. |
| `FileAlignment` | Opcjonalnie `Int32` parametru.<br /><br /> Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odnosi się do [- filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) przełączyć z *vbc.exe* kompilatora. |
| `GenerateDocumentation` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, generuje informacje o dokumentacji i umieszcza je w pliku XML o nazwie pliku wykonywalnego lub biblioteki, która tworzy zadanie. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Importuje przestrzenie nazw z kolekcji określonego elementu. Ten parametr odnosi się do [— importuje](/dotnet/visual-basic/reference/command-line-compiler/imports) przełączyć z *vbc.exe* kompilatora. |
| `KeyContainer` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Ten parametr odnosi się do [- keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) przełączyć z *vbc.exe* kompilatora. |
| `KeyFile` | Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [- keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Opcjonalnie <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Określa [wersji językowej](/dotnet/visual-basic/language-reference/configure-language-version), takie jak "15.5". |
| `LinkResources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do zasobów .NET Framework w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym. Ten parametr odnosi się do [- linkresource —](/dotnet/visual-basic/reference/command-line-compiler/linkresource) przełączyć z *vbc.exe* kompilatora. |
| `MainEntryPoint` | Opcjonalnie `String` parametru.<br /><br /> Określa klasę lub moduł, który zawiera `Sub Main` procedury. Ten parametr odnosi się do [-głównego](/dotnet/visual-basic/reference/command-line-compiler/main) przełączyć z *vbc.exe* kompilatora. |
| `ModuleAssemblyName` | Opcjonalnie `String` parametru.<br /><br /> Określa zestaw, do którego należy ten moduł. |
| `NoConfig` | Opcjonalnie `Boolean` parametru.<br /><br /> Określa, że kompilator nie powinien używać *vbc.rsp* pliku. Ten parametr odnosi się do [- noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) parametru *vbc.exe* kompilatora. |
| `NoLogo` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparencie kompilatora. Ten parametr odnosi się do [- nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) przełączyć z *vbc.exe* kompilatora. |
| `NoStandardLib` | Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że kompilator, aby nie odwoływać się do standardowych bibliotek. Ten parametr odnosi się do [- nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) przełączyć z *vbc.exe* kompilatora. |
| `NoVBRuntimeReference` | Opcjonalnie `Boolean` parametru.<br /><br /> Wyłącznie do użytku wewnętrznego. W przypadku opcji true uniemożliwia automatyczne odwołanie do *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie wyłącza wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [- nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, umożliwia optymalizacje kompilatora. Ten parametr odnosi się do [— Optymalizacja](/dotnet/visual-basic/reference/command-line-compiler/optimize) przełączyć z *vbc.exe* kompilatora. |
| `OptionCompare` | Opcjonalnie `String` parametru.<br /><br /> Określa, jak są wykonywane porównywania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` Określa, że zadanie używa porównania ciągów binarnych. Wartość `text` Określa, że zadanie używa porównania ciągów tekstu. Wartość domyślna tego parametru to `binary`. Ten parametr odnosi się do [- optioncompare —](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) przełączyć z *vbc.exe* kompilatora. |
| `OptionExplicit` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, jawnej deklaracji zmiennych jest wymagana. Ten parametr odnosi się do [- optionexplicit —](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) przełączyć z *vbc.exe* kompilatora. |
| `OptionInfer` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, umożliwia wnioskowanie o typie zmiennych. |
| `OptionStrict` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów. Ten parametr odnosi się do [- optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) przełączyć z *vbc.exe* kompilatora. |
| `OptionStrictType` | Opcjonalnie `String` parametru.<br /><br /> Określa, które semantykę typów ścisłych generować ostrzeżenie. Aktualnie obsługiwana jest tylko "niestandardowe". Ten parametr odnosi się do [- optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) przełączyć z *vbc.exe* kompilatora. |
| `OutputAssembly` | Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odnosi się do [-out](/dotnet/visual-basic/reference/command-line-compiler/out) przełączyć z *vbc.exe* kompilatora. |
| `Platform` | Opcjonalnie `String` parametru.<br /><br /> Określa platformę procesora, który ma zostać użyty przez plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, `Itanium`, lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odnosi się do [— Platforma](/dotnet/visual-basic/reference/command-line-compiler/platform) przełączyć z *vbc.exe* kompilatora. |
| `References` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Ten parametr odnosi się do [— dokumentacja](/dotnet/visual-basic/reference/command-line-compiler/reference) przełączyć z *vbc.exe* kompilatora. |
| `RemoveIntegerChecks` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wyłącza sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ten parametr odnosi się do [- removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) przełączyć z *vbc.exe* kompilatora. |
| `Resources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza zasób .NET Framework do pliku wyjściowego. Ten parametr odnosi się do [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) przełączyć z *vbc.exe* kompilatora. |
| `ResponseFiles` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia służące do tego zadania. Ten parametr odnosi się do [@ (Określ plik odpowiedzi)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) opcji *vbc.exe* kompilatora. |
| `RootNamespace` | Opcjonalnie `String` parametru.<br /><br /> Określa przestrzeń nazw korzenia dla wszystkich deklaracji typów. Ten parametr odnosi się do [- rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) przełączyć z *vbc.exe* kompilatora. |
| `SdkPath` | Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację *mscorlib.dll* i *microsoft.visualbasic.dll*. Ten parametr odnosi się do [- sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) przełączyć z *vbc.exe* kompilatora. |
| `Sources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa jeden lub więcej plików źródłowych języka Visual Basic. |
| `TargetCompactFramework` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, cele zadania [!INCLUDE[Compact](../extensibility/includes/compact_md.md)]. Ta opcja odnosi się do [- netcf —](/dotnet/visual-basic/reference/command-line-compiler/netcf) przełączyć z *vbc.exe* kompilatora. |
| `TargetType` | Opcjonalnie `String` parametru.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartości `library`, tworzy bibliotekę kodu `exe`, tworzy aplikacji konsoli, `module`, co powoduje utworzenie modułu, lub `winexe`, która tworzy Windows program. Wartość domyślna to `library`. Ten parametr odnosi się do [-target](/dotnet/visual-basic/reference/command-line-compiler/target) przełączyć z *vbc.exe* kompilatora. |
| `Timeout` | Opcjonalnie `Int32` parametru.<br /><br /> Określa ilość czasu w milisekundach, po których zostanie zakończony wykonywalnego zadania podrzędnego. Wartość domyślna to `Int.MaxValue`, wskazujący, że nie okres limitu czasu. |
| `ToolPath` | Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację, z którym zadanie załaduje podstawowego pliku wykonywalnego (*vbc.exe*). Jeśli nie określono tego parametru, zadanie używa ścieżki instalacji zestawu SDK odpowiadający wersję framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `TreatWarningsAsErrors` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że zadanie używa obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępny. Używany wyłącznie przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| `Utf8Output` | Opcjonalnie `Boolean` parametru.<br /><br /> Kompilator dzienniki danych wyjściowych przy użyciu kodowania UTF-8. Ten parametr odnosi się do [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) przełączyć z *vbc.exe* kompilatora. |
| `Verbosity` | Opcjonalnie `String` parametru.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Poziom szczegółowości można `Quiet`, `Normal` (ustawienie domyślne) lub `Verbose`. |
| `WarningsAsErrors` | Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń do traktowania jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru. |
| `WarningsNotAsErrors` | Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [- warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` parametr ma wartość `true`. |
| `Win32Icon` | Opcjonalnie `String` parametru.<br /><br /> Wstawia *.ico* pliku w zestawie, który nadaje plikowi wyjściowemu pożądany wygląd w **Eksploratora plików**. Ten parametr odnosi się do [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) przełączyć z *vbc.exe* kompilatora. |
| `Win32Resources` | Opcjonalnie `String` parametru.<br /><br /> Wstawia zasób Win32 (*.res*) pliku w pliku wyjściowym. Ten parametr odnosi się do [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) przełączyć z *vbc.exe* kompilatora. |

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
 Poniższy przykład kompiluje projekt języka Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

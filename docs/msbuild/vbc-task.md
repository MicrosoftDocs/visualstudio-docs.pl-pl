---
title: VBC — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1710336ebc73be707e962733e37376b5689e10
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631240"
---
# <a name="vbc-task"></a>Vbc — Zadanie

Zawija *VBC. exe*, który tworzy pliki wykonywalne ( *. exe*), biblioteki dołączane dynamicznie (*dll*) lub moduły kodu ( *. module*). Aby uzyskać więcej informacji na temat *VBC. exe*, zobacz [Visual Basic kompilator wiersza polecenia](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `Vbc`.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalny parametr `String[]`.<br /><br /> Określa dodatkowe foldery, w których mają być wyszukiwane zestawy określone w atrybucie References. |
| `AddModules` | Opcjonalny parametr `String[]`.<br /><br /> Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu. Ten parametr odnosi się do przełącznika [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) kompilatora *VBC. exe* . |
| `BaseAddress` | Opcjonalny parametr `String`.<br /><br /> Określa adres podstawowy biblioteki DLL. Ten parametr odnosi się do przełącznika [-BaseAddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) kompilatora *VBC. exe* . |
| `CodePage` | Opcjonalny parametr `Int32`.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ten parametr odnosi się do przełącznika [-CodePage](/dotnet/visual-basic/reference/command-line-compiler/codepage) kompilatora *VBC. exe* . |
| `DebugType` | Opcjonalny parametr `String[]`.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full`, co umożliwia dołączanie debugera do działającego programu. Wartość `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera. Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Opcjonalny parametr `String[]`.<br /><br /> Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1* `=` *wartość1* `;` *symbol2* `=` *wartość2*<br /><br /> Ten parametr odpowiada przełącznikowi [-define](/dotnet/visual-basic/reference/command-line-compiler/define) kompilatora *VBC. exe* . |
| `DelaySign` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie umieszcza klucz publiczny w zestawie. Jeśli `false`, zadanie w pełni podpisuje zestaw. Wartość domyślna to `false`. Ten parametr nie ma żadnego efektu, chyba że jest używany z parametrem `KeyFile` ani parametrem `KeyContainer`. Ten parametr odnosi się do przełącznika [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) kompilatora *VBC. exe* . |
| `Deterministic` | Opcjonalny parametr `Boolean`.<br/><br/> Jeśli `true`, powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministycznie](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Opcjonalny parametr `String`.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do przełącznika [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilatora *VBC. exe* . |
| `DocumentationFile` | Opcjonalny parametr `String`.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje atrybut `GenerateDocumentation`. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku *. pdb* . Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Opcjonalny parametr `String`.<br /><br /> Określa, w jaki sposób zadanie ma raportować wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` jest określony i wystąpi wewnętrzny błąd kompilatora, użytkownik zostanie poproszony o podanie opcji, czy wysyłać dane błędów do firmy Microsoft.<br /><br /> Jeśli `send` jest określony i wystąpi wewnętrzny błąd kompilatora, zadanie wysyła dane błędu do firmy Microsoft.<br /><br /> Wartość domyślna to `none`, która raportuje błędy tylko w danych wyjściowych.<br /><br /> Ten parametr odnosi się do przełącznika [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) kompilatora *VBC. exe* . |
| `FileAlignment` | Opcjonalny parametr `Int32`.<br /><br /> Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odnosi się do przełącznika [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) kompilatora *VBC. exe* . |
| `GenerateDocumentation` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program generuje informacje o dokumentacji i umieszcza je w pliku XML z nazwą pliku wykonywalnego lub biblioteki tworzonego przez zadanie. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Importuje przestrzenie nazw z określonych kolekcji elementów. Ten parametr odnosi się do przełącznika [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) kompilatora *VBC. exe* . |
| `KeyContainer` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Ten parametr odnosi się do przełącznika [--](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) parameterer kompilatora *VBC. exe* . |
| `KeyFile` | Opcjonalny parametr `String`.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-KeyFile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Opcjonalny parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Określa [wersję językową](/dotnet/visual-basic/language-reference/configure-language-version), taką jak "15,5". |
| `LinkResources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Ten parametr odnosi się do przełącznika [-linkresource —](/dotnet/visual-basic/reference/command-line-compiler/linkresource) kompilatora *VBC. exe* . |
| `MainEntryPoint` | Opcjonalny parametr `String`.<br /><br /> Określa klasę lub moduł, który zawiera procedurę `Sub Main`. Ten parametr odnosi się do [-głównego](/dotnet/visual-basic/reference/command-line-compiler/main) przełącznika kompilatora *VBC. exe* . |
| `ModuleAssemblyName` | Opcjonalny parametr `String`.<br /><br /> Określa zestaw, który jest częścią tego modułu. |
| `NoConfig` | Opcjonalny parametr `Boolean`.<br /><br /> Określa, że kompilator nie powinien używać pliku *VBC. rsp* . Ten parametr odnosi się do parametru [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) kompilatora *VBC. exe* . |
| `NoLogo` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji transparentu kompilatora. Ten parametr odnosi się do przełącznika [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) kompilatora *VBC. exe* . |
| `NoStandardLib` | Opcjonalny parametr `Boolean`.<br /><br /> Powoduje, że kompilator nie odwołuje się do bibliotek standardowych. Ten parametr odnosi się do przełącznika [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) kompilatora *VBC. exe* . |
| `NoVBRuntimeReference` | Opcjonalny parametr `Boolean`.<br /><br /> Tylko do użytku wewnętrznego. W przypadku wartości true program uniemożliwia automatyczne odwołanie do *pliku Microsoft. VisualBasic. dll*. |
| `NoWarnings` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie pomija wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, włącza optymalizacje kompilatora. Ten parametr odpowiada przełącznikowi [-Optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) kompilatora *VBC. exe* . |
| `OptionCompare` | Opcjonalny parametr `String`.<br /><br /> Określa sposób, w jaki są wykonywane porównania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` określa, że zadanie używa porównywania ciągów binarnych. Wartość `text` określa, że zadanie używa porównania ciągów tekstowych. Wartość domyślna tego parametru to `binary`. Ten parametr odnosi się do przełącznika [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) kompilatora *VBC. exe* . |
| `OptionExplicit` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wymagana jest jawna deklaracja zmiennych. Ten parametr odnosi się do przełącznika [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) kompilatora *VBC. exe* . |
| `OptionInfer` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zezwala na wnioskowanie o typie zmiennych. |
| `OptionStrict` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie wymusza semantykę typu ścisłego w celu ograniczenia niejawnych konwersji typów. Ten parametr odnosi się do przełącznika [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *VBC. exe* . |
| `OptionStrictType` | Opcjonalny parametr `String`.<br /><br /> Określa, który semantyczny typ ma generować ostrzeżenie. Obecnie obsługiwana jest tylko wartość "Custom". Ten parametr odnosi się do przełącznika [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *VBC. exe* . |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odnosi [się do przełącznika kompilatora](/dotnet/visual-basic/reference/command-line-compiler/out) *VBC. exe* . |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, `Itanium`lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odpowiada przełącznikowi [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) kompilatora *VBC. exe* . |
| `References` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Ten parametr odpowiada przełącznikowi [-Reference](/dotnet/visual-basic/reference/command-line-compiler/reference) kompilatora *VBC. exe* . |
| `RemoveIntegerChecks` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wyłącza sprawdzanie błędów przepełnienia liczby całkowitej. Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) kompilatora *VBC. exe* . |
| `Resources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym. Ten parametr odnosi się do przełącznika [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) kompilatora *VBC. exe* . |
| `ResponseFiles` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Ten parametr odpowiada opcji [@ (Określ plik odpowiedzi)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) kompilatora *VBC. exe* . |
| `RootNamespace` | Opcjonalny parametr `String`.<br /><br /> Określa główną przestrzeń nazw dla wszystkich deklaracji typu. Ten parametr odnosi się do przełącznika [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) kompilatora *VBC. exe* . |
| `SdkPath` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację plików *mscorlib. dll* i *Microsoft. VisualBasic. dll*. Ten parametr odnosi się do przełącznika [-SdkPath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) kompilatora *VBC. exe* . |
| `Sources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa co najmniej jeden Visual Basic pliki źródłowe. |
| `TargetCompactFramework` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie odwołuje się do .NET Compact Framework. Ten przełącznik odpowiada przełącznikowi [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) kompilatora *VBC. exe* . |
| `TargetType` | Opcjonalny parametr `String`.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartość `library`, która tworzy bibliotekę kodu, `exe`, która tworzy aplikację konsolową, `module`, która tworzy moduł, lub `winexe`, który tworzy program systemu Windows. Wartość domyślna to `library`. Ten parametr odnosi się do przełącznika [-Target](/dotnet/visual-basic/reference/command-line-compiler/target) kompilatora *VBC. exe* . |
| `Timeout` | Opcjonalny parametr `Int32`.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `ToolPath` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (*VBC. exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, w której działa program MSBuild. |
| `TreatWarningsAsErrors` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Opcjonalny parametr `Boolean`.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używany tylko przez program Visual Studio. |
| `Utf8Output` | Opcjonalny parametr `Boolean`.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr odnosi się do przełącznika [-utf8output —](/dotnet/visual-basic/reference/command-line-compiler/utf8output) kompilatora *VBC. exe* . |
| `Verbosity` | Opcjonalny parametr `String`.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Poziom szczegółowości można `Quiet`, `Normal` (wartość domyślna) lub `Verbose`. |
| `WarningsAsErrors` | Opcjonalny parametr `String`.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr zastępuje parametr `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Opcjonalny parametr `String`.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr jest przydatny tylko wtedy, gdy parametr `TreatWarningsAsErrors` jest ustawiony na `true`. |
| `Win32Icon` | Opcjonalny parametr `String`.<br /><br /> Wstawia plik *ICO* w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w **Eksploratorze plików**. Ten parametr odnosi się do przełącznika [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) kompilatora *VBC. exe* . |
| `Win32Resources` | Opcjonalny parametr `String`.<br /><br /> Wstawia plik zasobów Win32 ( *. res*) do pliku wyjściowego. Ten parametr odnosi się do przełącznika [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) kompilatora *VBC. exe* . |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kompiluje projekt Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

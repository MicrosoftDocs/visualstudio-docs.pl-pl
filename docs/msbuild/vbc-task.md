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
ms.openlocfilehash: 30f1a45c384495ccd02c624ea42f91a4379226df
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167456"
---
# <a name="vbc-task"></a>Vbc — Zadanie

Zawija *VBC. exe*, który tworzy pliki wykonywalne (*. exe*), biblioteki dołączane dynamicznie (*dll*) lub moduły kodu (*. module*). Aby uzyskać więcej informacji na temat *VBC. exe*, zobacz [Visual Basic kompilator wiersza polecenia](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `Vbc` zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Opcjonalny `String[]` parametr.<br /><br /> Określa dodatkowe foldery, w których mają być wyszukiwane zestawy określone w atrybucie References. |
| `AddModules` | Opcjonalny `String[]` parametr.<br /><br /> Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu. Ten parametr odnosi się do przełącznika [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) kompilatora *VBC. exe* . |
| `BaseAddress` | Opcjonalny `String` parametr.<br /><br /> Określa adres podstawowy biblioteki DLL. Ten parametr odnosi się do przełącznika [-BaseAddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) kompilatora *VBC. exe* . |
| `CodePage` | Opcjonalny `Int32` parametr.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ten parametr odnosi się do przełącznika [-CodePage](/dotnet/visual-basic/reference/command-line-compiler/codepage) kompilatora *VBC. exe* . |
| `DebugType` | Opcjonalny `String[]` parametr.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full`, co umożliwia dołączenie debugera do działającego programu. Wartość `pdbonly` zezwala na Debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera. Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Opcjonalny `String[]` parametr.<br /><br /> Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1* `=` *value1* wartość1 `;` *symbol2* symbol2 `=` *wartość2*<br /><br /> Ten parametr odpowiada przełącznikowi [-define](/dotnet/visual-basic/reference/command-line-compiler/define) kompilatora *VBC. exe* . |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie umieszcza klucz publiczny w zestawie. Jeśli `false`, zadanie w pełni podpisuje zestaw. Wartość domyślna to `false`. Ten parametr nie ma żadnego efektu, `KeyFile` chyba że jest używany z `KeyContainer` parametrem lub parametrem. Ten parametr odnosi się do przełącznika [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) kompilatora *VBC. exe* . |
| `Deterministic` | Opcjonalny `Boolean` parametr.<br/><br/> Jeśli `true`, powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministycznie](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Opcjonalny `String` parametr.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do przełącznika [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilatora *VBC. exe* . |
| `DocumentationFile` | Opcjonalny `String` parametr.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybut. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`zadanie generuje informacje o debugowaniu i umieszcza je w pliku *. pdb* . Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Opcjonalny `String` parametr.<br /><br /> Określa, w jaki sposób zadanie ma raportować wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` jest określony i wystąpi wewnętrzny błąd kompilatora, użytkownik zostanie poproszony o podanie opcji, czy wysłać dane błędu do firmy Microsoft.<br /><br /> Jeśli `send` jest określona i wystąpi wewnętrzny błąd kompilatora, zadanie wysyła dane błędu do firmy Microsoft.<br /><br /> Wartość domyślna to `none`, która raportuje błędy tylko w danych wyjściowych.<br /><br /> Ten parametr odnosi się do przełącznika [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) kompilatora *VBC. exe* . |
| `FileAlignment` | Opcjonalny `Int32` parametr.<br /><br /> Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odnosi się do przełącznika [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) kompilatora *VBC. exe* . |
| `GenerateDocumentation` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, program generuje informacje dokumentacji i umieszcza je w pliku XML z nazwą pliku wykonywalnego lub biblioteki tworzonego przez zadanie. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Importuje przestrzenie nazw z określonych kolekcji elementów. Ten parametr odnosi się do przełącznika [-Imports](/dotnet/visual-basic/reference/command-line-compiler/imports) kompilatora *VBC. exe* . |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Ten parametr odnosi się do przełącznika [--](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) parameterer kompilatora *VBC. exe* . |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-KeyFile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Opcjonalny <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Określa [wersję językową](/dotnet/visual-basic/language-reference/configure-language-version), taką jak "15,5". |
| `LinkResources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Ten parametr odnosi się do przełącznika [-linkresource —](/dotnet/visual-basic/reference/command-line-compiler/linkresource) kompilatora *VBC. exe* . |
| `MainEntryPoint` | Opcjonalny `String` parametr.<br /><br /> Określa klasę lub moduł, który zawiera `Sub Main` procedurę. Ten parametr odnosi się do [-głównego](/dotnet/visual-basic/reference/command-line-compiler/main) przełącznika kompilatora *VBC. exe* . |
| `ModuleAssemblyName` | Opcjonalny `String` parametr.<br /><br /> Określa zestaw, który jest częścią tego modułu. |
| `NoConfig` | Opcjonalny `Boolean` parametr.<br /><br /> Określa, że kompilator nie powinien używać pliku *VBC. rsp* . Ten parametr odnosi się do parametru [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) kompilatora *VBC. exe* . |
| `NoLogo` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji transparentu kompilatora. Ten parametr odnosi się do przełącznika [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) kompilatora *VBC. exe* . |
| `NoStandardLib` | Opcjonalny `Boolean` parametr.<br /><br /> Powoduje, że kompilator nie odwołuje się do bibliotek standardowych. Ten parametr odnosi się do przełącznika [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) kompilatora *VBC. exe* . |
| `NoVBRuntimeReference` | Opcjonalny `Boolean` parametr.<br /><br /> Tylko do użytku wewnętrznego. W przypadku wartości true program uniemożliwia automatyczne odwołanie do *pliku Microsoft. VisualBasic. dll*. |
| `NoWarnings` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie pomija wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, włącza optymalizacje kompilatora. Ten parametr odpowiada przełącznikowi [-Optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) kompilatora *VBC. exe* . |
| `OptionCompare` | Opcjonalny `String` parametr.<br /><br /> Określa sposób, w jaki są wykonywane porównania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` określa, że zadanie używa porównywania ciągów binarnych. Wartość `text` określa, że zadanie używa porównania ciągów tekstowych. Wartość domyślna tego parametru to `binary`. Ten parametr odnosi się do przełącznika [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) kompilatora *VBC. exe* . |
| `OptionExplicit` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`wymagana jest jawna deklaracja zmiennych. Ten parametr odnosi się do przełącznika [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) kompilatora *VBC. exe* . |
| `OptionInfer` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zezwala na wnioskowanie o typie zmiennych. |
| `OptionStrict` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów. Ten parametr odnosi się do przełącznika [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *VBC. exe* . |
| `OptionStrictType` | Opcjonalny `String` parametr.<br /><br /> Określa, który semantyczny typ ma generować ostrzeżenie. Obecnie obsługiwana jest tylko wartość "Custom". Ten parametr odnosi się do przełącznika [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *VBC. exe* . |
| `OutputAssembly` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odnosi [się do przełącznika kompilatora](/dotnet/visual-basic/reference/command-line-compiler/out) *VBC. exe* . |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć `x86`wartość, `x64`, `Itanium`, lub. `anycpu` Wartość domyślna to `anycpu`. Ten parametr odpowiada przełącznikowi [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) kompilatora *VBC. exe* . |
| `References` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Ten parametr odpowiada przełącznikowi [-Reference](/dotnet/visual-basic/reference/command-line-compiler/reference) kompilatora *VBC. exe* . |
| `RemoveIntegerChecks` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, wyłącza sprawdzanie błędów przepełnienia liczby całkowitej. Wartością domyślną jest `false`. Ten parametr odnosi się do przełącznika [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) kompilatora *VBC. exe* . |
| `Resources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym. Ten parametr odnosi się do przełącznika [-Resource](/dotnet/visual-basic/reference/command-line-compiler/resource) kompilatora *VBC. exe* . |
| `ResponseFiles` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Ten parametr odpowiada opcji [@ (Określ plik odpowiedzi)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) kompilatora *VBC. exe* . |
| `RootNamespace` | Opcjonalny `String` parametr.<br /><br /> Określa główną przestrzeń nazw dla wszystkich deklaracji typu. Ten parametr odnosi się do przełącznika [-RootNamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) kompilatora *VBC. exe* . |
| `SdkPath` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację plików *mscorlib. dll* i *Microsoft. VisualBasic. dll*. Ten parametr odnosi się do przełącznika [-SdkPath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) kompilatora *VBC. exe* . |
| `Sources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa co najmniej jeden Visual Basic pliki źródłowe. |
| `TargetCompactFramework` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie jest przeznaczone dla .NET Compact Framework. Ten przełącznik odpowiada przełącznikowi [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) kompilatora *VBC. exe* . |
| `TargetType` | Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego. `library`Ten parametr może mieć wartość, która tworzy bibliotekę kodu, `exe`która tworzy aplikację `module`konsolową, która tworzy moduł lub `winexe`tworzy program systemu Windows. Wartość domyślna to `library`. Ten parametr odnosi się do przełącznika [-Target](/dotnet/visual-basic/reference/command-line-compiler/target) kompilatora *VBC. exe* . |
| `Timeout` | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `ToolPath` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (*VBC. exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, w której działa program MSBuild. |
| `TreatWarningsAsErrors` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Opcjonalny `Boolean` parametr.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używany tylko przez program Visual Studio. |
| `Utf8Output` | Opcjonalny `Boolean` parametr.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr odnosi się do przełącznika [-utf8output —](/dotnet/visual-basic/reference/command-line-compiler/utf8output) kompilatora *VBC. exe* . |
| `Verbosity` | Opcjonalny `String` parametr.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Poziom szczegółowości może być `Quiet` `Normal` (wartość domyślna), lub `Verbose`. |
| `WarningsAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror — (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr jest przydatny tylko wtedy `TreatWarningsAsErrors` , gdy parametr jest `true`ustawiony na. |
| `Win32Icon` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik *ICO* w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w **Eksploratorze plików**. Ten parametr odnosi się do przełącznika [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) kompilatora *VBC. exe* . |
| `Win32Resources` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik zasobów Win32 (*. res*) do pliku wyjściowego. Ten parametr odnosi się do przełącznika [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) kompilatora *VBC. exe* . |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Przykład

 Poniższy przykład kompiluje projekt Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

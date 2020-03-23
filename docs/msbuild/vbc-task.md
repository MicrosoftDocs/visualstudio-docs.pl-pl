---
title: Zadanie Vbc | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631240"
---
# <a name="vbc-task"></a>Vbc — Zadanie

Zawija *vbc.exe*, który produkuje pliki wykonywalne (*.exe*), biblioteki łączy dynamicznych (*.dll*) lub moduły kodu (*.netmodule*). Aby uzyskać więcej informacji na temat *programu vbc.exe*, zobacz [Visual Basic kompilator wiersza polecenia](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Parametry

 W poniższej tabeli `Vbc` opisano parametry zadania.

| Parametr | Opis |
|------------------------------| - |
| `AdditionalLibPaths` | Parametr `String[]` opcjonalny.<br /><br /> Określa dodatkowe foldery, w których mają być wyszukane zestawy określone w atrybucie Odwołania. |
| `AddModules` | Parametr `String[]` opcjonalny.<br /><br /> Powoduje, że kompilator udostępnia wszystkie informacje o typie z określonych plików do aktualnie kompilowany projekt. Ten parametr odpowiada przełącznikowi [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) kompilatora *vbc.exe.* |
| `BaseAddress` | Parametr `String` opcjonalny.<br /><br /> Określa adres podstawowy biblioteki DLL. Ten parametr odpowiada przełącznikowi [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) kompilatora *vbc.exe.* |
| `CodePage` | Parametr `Int32` opcjonalny.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ten parametr odpowiada przełącznikowi [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) kompilatora *vbc.exe.* |
| `DebugType` | Parametr `String[]` opcjonalny.<br /><br /> Powoduje, że kompilator do generowania informacji debugowania. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartością domyślną jest `full`, która umożliwia dołączanie debugera do uruchomionego programu. Wartość `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka zestawu tylko wtedy, gdy uruchomiony program jest dołączony do debugera. Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Parametr `String[]` opcjonalny.<br /><br /> Definiuje stałe kompilatora warunkowego. Pary symboli/wartości są oddzielone średnikami i są określone w następującej składni:<br /><br /> *symbol1* `=` *wartość1* `;` *symbol2* `=` *wartość2*<br /><br /> Ten parametr odpowiada przełącznikowi [-define](/dotnet/visual-basic/reference/command-line-compiler/define) kompilatora *vbc.exe.* |
| `DelaySign` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie umieszcza klucz publiczny w zestawie. Jeśli `false`zadanie w pełni podpisze zestaw. Wartością domyślną jest `false`. Ten parametr nie ma wpływu, chyba że jest używany z parametrem `KeyFile` lub parametrem. `KeyContainer` Ten parametr odpowiada przełącznikowi [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) kompilatora *vbc.exe.* |
| `Deterministic` | Parametr `Boolean` opcjonalny.<br/><br/> Jeśli `true`, powoduje, że kompilator do wyjścia zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.<br/><br/>Aby uzyskać więcej informacji, zobacz [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Parametr `String` opcjonalny.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić numeryczną część identyfikatora ostrzegawczego. Wiele ostrzeżeń są oddzielone średnikami. Ten parametr odpowiada przełącznikowi [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) kompilatora *vbc.exe.* |
| `DocumentationFile` | Parametr `String` opcjonalny.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybut. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie generuje informacje debugowania i umieszcza je w pliku *pdb.* Aby uzyskać więcej informacji, zobacz [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Parametr `String` opcjonalny.<br /><br /> Określa, jak zadanie powinno zgłaszać błędy kompilatora wewnętrznego. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` zostanie określony i wystąpi wewnętrzny błąd kompilatora, użytkownik jest monitowany z opcją, czy wysłać dane o błędzie do firmy Microsoft.<br /><br /> Jeśli `send` zostanie określony i wystąpi wewnętrzny błąd kompilatora, zadanie wysyła dane o błędzie do firmy Microsoft.<br /><br /> Wartością domyślną jest `none`, która zgłasza tylko błędy w danych wyjściowych tekstu.<br /><br /> Ten parametr odpowiada przełącznikowi [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) kompilatora *vbc.exe.* |
| `FileAlignment` | Parametr `Int32` opcjonalny.<br /><br /> Określa w bajtach, gdzie wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odpowiada przełącznikowi [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) kompilatora *vbc.exe.* |
| `GenerateDocumentation` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program ,generuje informacje o dokumentacji i umieszcza go w pliku XML o nazwie pliku wykonywalnego lub biblioteki, którą tworzy zadanie. Aby uzyskać więcej informacji, zobacz [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Importuje obszary nazw z określonych kolekcji elementów. Ten parametr odpowiada przełącznikowi [-imports](/dotnet/visual-basic/reference/command-line-compiler/imports) kompilatora *vbc.exe.* |
| `KeyContainer` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Ten parametr odpowiada przełącznikowi [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) kompilatora *vbc.exe.* |
| `KeyFile` | Parametr `String` opcjonalny.<br /><br /> Określa nazwę pliku zawierającą klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Parametr <xref:System.String?displayProperty=fullName> opcjonalny.<br /><br /> Określa [wersję językową](/dotnet/visual-basic/language-reference/configure-language-version), taką jak "15.5". |
| `LinkResources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Tworzy łącze do zasobu programu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Ten parametr odpowiada przełącznikowi [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) kompilatora *vbc.exe.* |
| `MainEntryPoint` | Parametr `String` opcjonalny.<br /><br /> Określa klasę lub moduł zawierający `Sub Main` procedurę. Ten parametr odpowiada przełącznikowi [-main](/dotnet/visual-basic/reference/command-line-compiler/main) kompilatora *vbc.exe.* |
| `ModuleAssemblyName` | Parametr `String` opcjonalny.<br /><br /> Określa zestaw, do których ten moduł jest częścią. |
| `NoConfig` | Parametr `Boolean` opcjonalny.<br /><br /> Określa, że kompilator nie powinien używać pliku *vbc.rsp.* Ten parametr odpowiada parametrowi [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) kompilatora *vbc.exe.* |
| `NoLogo` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, pomija wyświetlanie informacji baner kompilatora. Ten parametr odpowiada przełącznikowi [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) kompilatora *vbc.exe.* |
| `NoStandardLib` | Parametr `Boolean` opcjonalny.<br /><br /> Powoduje, że kompilator nie odwołuje się do bibliotek standardowych. Ten parametr odpowiada przełącznikowi [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) kompilatora *vbc.exe.* |
| `NoVBRuntimeReference` | Parametr `Boolean` opcjonalny.<br /><br /> Tylko do użytku wewnętrznego. Jeśli true, zapobiega automatyczne odwoływanie się do *microsoft.VisualBasic.dll*. |
| `NoWarnings` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie pomija wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, umożliwia optymalizacje kompilatora. Ten parametr odpowiada przełącznikowi [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) kompilatora *vbc.exe.* |
| `OptionCompare` | Parametr `String` opcjonalny.<br /><br /> Określa sposób porównywania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` określa, że zadanie używa binarnych porównań ciągów. Wartość `text` określa, że zadanie używa porównań ciągów tekstowych. Domyślną wartością tego `binary`parametru jest . Ten parametr odpowiada przełącznikowi [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) kompilatora *vbc.exe.* |
| `OptionExplicit` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`wymagana jest wyraźna deklaracja zmiennych. Ten parametr odpowiada przełącznikowi [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) kompilatora *vbc.exe.* |
| `OptionInfer` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, umożliwia wnioskowanie o typie zmiennych. |
| `OptionStrict` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie wymusza semantykę typu ścisłego, aby ograniczyć konwersje typu niejawnego. Ten parametr odpowiada przełącznikowi [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *vbc.exe.* |
| `OptionStrictType` | Parametr `String` opcjonalny.<br /><br /> Określa, które semantyka typu ścisłego generuje ostrzeżenie. Obecnie obsługiwane jest tylko "niestandardowe". Ten parametr odpowiada przełącznikowi [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) kompilatora *vbc.exe.* |
| `OutputAssembly` | Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odpowiada przełącznikowi [-out](/dotnet/visual-basic/reference/command-line-compiler/out) kompilatora *vbc.exe.* |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Określa platformę procesora, na który ma dotyczy plik wyjściowy. Ten parametr może mieć `x86` `x64`wartość `Itanium`, `anycpu`, , lub . Wartość domyślna to `anycpu`. Ten parametr odpowiada przełącznikowi [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) kompilatora *vbc.exe.* |
| `References` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Powoduje, że zadanie do importowania informacji o typie publicznym z określonych elementów do bieżącego projektu. Ten parametr odpowiada przełącznikowi [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference) kompilatora *vbc.exe.* |
| `RemoveIntegerChecks` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`funkcja całkowita wyłączy sprawdzanie błędów przepełnienia. Wartością domyślną jest `false`. Ten parametr odpowiada przełącznikowi [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) kompilatora *vbc.exe.* |
| `Resources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Osadza zasób programu .NET Framework w pliku wyjściowym. Ten parametr odpowiada przełącznikowi [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) kompilatora *vbc.exe.* |
| `ResponseFiles` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Ten parametr odpowiada opcji [@ (Określ plik odpowiedzi)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) kompilatora *vbc.exe.* |
| `RootNamespace` | Parametr `String` opcjonalny.<br /><br /> Określa główny obszar nazw dla wszystkich deklaracji typów. Ten parametr odpowiada przełącznikowi [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) kompilatora *vbc.exe.* |
| `SdkPath` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację *pliku mscorlib.dll* i *pliku microsoft.visualbasic.dll*. Ten parametr odpowiada przełącznikowi [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) kompilatora *vbc.exe.* |
| `Sources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa jeden lub więcej plików źródłowych języka Visual Basic. |
| `TargetCompactFramework` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie jest przeznaczone dla platformy .NET Compact Framework. Ten przełącznik odpowiada przełącznikowi [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) kompilatora *vbc.exe.* |
| `TargetType` | Parametr `String` opcjonalny.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć `library`wartość , która `exe`tworzy bibliotekę kodu, `module`, która tworzy `winexe`aplikację konsoli, , która tworzy moduł, lub , który tworzy program Windows. Wartość domyślna to `library`. Ten parametr odpowiada przełącznikowi [-target](/dotnet/visual-basic/reference/command-line-compiler/target) kompilatora *vbc.exe.* |
| `Timeout` | Parametr `Int32` opcjonalny.<br /><br /> Określa czas w milisekundach, po upływie którego plik wykonywalny zadania zostanie zakończony. Wartością domyślną jest `Int.MaxValue`, wskazując, że nie ma okresu przeoczynia. |
| `ToolPath` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowane bazowy plik wykonywalny (*vbc.exe*). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji SDK odpowiadającej wersji struktury z uruchomionym msbuild. |
| `TreatWarningsAsErrors` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Parametr `Boolean` opcjonalny.<br /><br /> Nakazuje zadanie używać obiektu kompilatora w trakcie, jeśli jest dostępny. Używane tylko przez program Visual Studio. |
| `Utf8Output` | Parametr `Boolean` opcjonalny.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr odpowiada przełącznikowi [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) kompilatora *vbc.exe.* |
| `Verbosity` | Parametr `String` opcjonalny.<br /><br /> Określa szczegółowość danych wyjściowych kompilatora. Szczegółowość może być `Quiet` `Normal` , (domyślna) lub `Verbose`. |
| `WarningsAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które należy traktować jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr. |
| `WarningsNotAsErrors` | Parametr `String` opcjonalny.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Ten parametr jest przydatny `TreatWarningsAsErrors` tylko wtedy, gdy parametr jest ustawiony na `true`. |
| `Win32Icon` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik *.ico* do złożenia, co nadaje plikowi wyjściowemu pożądany wygląd w **Eksploratorze plików**. Ten parametr odpowiada przełącznikowi [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) kompilatora *vbc.exe.* |
| `Win32Resources` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik zasobu Win32 (*.res*) do pliku wyjściowego. Ten parametr odpowiada przełącznikowi [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) kompilatora *vbc.exe.* |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kompiluje projekt języka Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia języka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

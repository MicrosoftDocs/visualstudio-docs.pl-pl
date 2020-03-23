---
title: AL (Łącznik zespołu) Zadanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6861fee8691c32415111347ab673f9e48bfb9e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634594"
---
# <a name="al-assembly-linker-task"></a>AL (Łącznik zespołu) zadanie

Zadanie AL zawija *program AL.exe*, narzędzie dystrybuowane za pomocą zestawu Windows Software Development Kit (SDK). To narzędzie do konsolidatora zestawu służy do tworzenia zestawu z manifestem z jednego lub więcej plików, które są modułami lub plikami zasobów. Kompilatory i środowiska programistyczne może już zapewnić te możliwości, więc często nie jest konieczne, aby użyć tego zadania bezpośrednio. Zestaw Konsolidator jest najbardziej przydatne dla deweloperów, którzy potrzebują utworzyć pojedynczy zestaw z wielu plików składników, takich jak te, które mogą być produkowane z rozwoju języka mieszanego. To zadanie nie łączy modułów w jeden plik zestawu; poszczególne moduły muszą być nadal rozmieszczone i dostępne, aby wynikowy zespół został prawidłowo załadowany. Aby uzyskać więcej informacji na temat *AL.exe*, zobacz [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry

 W poniższej tabeli `AL` opisano parametry zadania.

| Parametr | Opis |
|---------------------| - |
| `AlgorithmID` | Parametr `String` opcjonalny.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, `/algid` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Parametr `String` opcjonalny.<br /><br /> Określa adres, pod którym zostanie załadowana biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje ładują się szybciej, jeśli określisz adres podstawowy bibliotek DLL, zamiast zezwalać systemowi operacyjnemu na przenoszenie bibliotek DLL w obszarze procesu. Ten parametr odpowiada[adresowi](/dotnet/framework/tools/al-exe-assembly-linker)/base . |
| `CompanyName` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Company` pola w złożeniu. Aby uzyskać więcej informacji, `/comp[any]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Configuration` pola w złożeniu. Aby uzyskać więcej informacji, `/config[uration]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Copyright` pola w złożeniu. Aby uzyskać więcej informacji, `/copy[right]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, `/c[ulture]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Parametr `Boolean` opcjonalny.<br /><br /> `true`umieścić tylko klucz publiczny w zgromadzeniu; `false` , aby w pełni podpisać zespół. Aby uzyskać więcej informacji, `/delay[sign]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Description` pola w złożeniu. Aby uzyskać więcej informacji, `/descr[iption]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Osadza określone zasoby w obrazie, który zawiera manifest zestawu. To zadanie kopiuje zawartość pliku zasobu do obrazu. Elementy przekazywane do tego parametru mogą mieć dołączone `LogicalName` opcjonalne metadane i `Access`. Metadane `LogicalName` są używane do określania wewnętrznego identyfikatora zasobu.  Metadane `Access` można ustawić, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, `/embed[resource]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Parametr `String` opcjonalny.<br /><br /> Osadza określony plik w zestawie o nazwie `Security.Evidence`zasobu .<br /><br /> Nie można `Security.Evidence` używać dla zwykłych zasobów. Ten parametr odpowiada `/e[vidence]` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Opcjonalny `Int32` parametr tylko do odczytu.<br /><br /> Określa kod zakończenia dostarczony przez wykonane polecenie. |
| `FileVersion` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `File Version` pola w złożeniu. Aby uzyskać więcej informacji, `/fileversion` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Parametr `String` opcjonalny.<br /><br /> Określa wartość `Flags` pola w złożeniu. Aby uzyskać więcej informacji, `/flags` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Parametr `Boolean` opcjonalny.<br /><br /> Powoduje, że zadanie używać ścieżki bezwzględnej dla wszystkich plików, które są zgłaszane w komunikacie o błędzie. Ten parametr odpowiada `/fullpaths` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Parametr `String` opcjonalny.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Zadanie podpisze zestaw końcowy za pomocą klucza prywatnego. Aby uzyskać więcej informacji, `/keyn[ame]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Parametr `String` opcjonalny.<br /><br /> Określa plik zawierający parę kluczy lub tylko klucz publiczny do podpisania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, `/keyf[ile]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Łączy określone pliki zasobów z zestawem. Zasób staje się częścią zestawu, ale plik nie jest kopiowany. Elementy przekazane do tego parametru mogą mieć dołączone `LogicalName`opcjonalne metadane o nazwie , `Target`i `Access`. Metadane `LogicalName` są używane do określania wewnętrznego identyfikatora zasobu. Metadane `Target` można określić ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po czym kompiluje ten nowy plik do zestawu. Metadane `Access` można ustawić, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, `/link[resource]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Parametr `String` opcjonalny.<br /><br /> Określa w pełni kwalifikowaną nazwę (*class.method*) metody, która ma być używana jako punkt wejścia podczas konwertowania modułu na plik wykonywalny. Ten parametr odpowiada `/main` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku wygenerowanego przez to zadanie. Ten parametr odpowiada `/out` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Parametr `String` opcjonalny.<br /><br /> Ogranicza, na której platformie można uruchomić ten kod; musi być `x86`jednym `Itanium` `x64`z `anycpu`, , lub . Wartość domyślna to `anycpu`. Ten parametr odpowiada `/platform` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Product` pola w złożeniu. Aby uzyskać więcej informacji, `/prod[uct]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `ProductVersion` pola w złożeniu. Aby uzyskać więcej informacji, `/productv[ersion]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Parametr `String[]` opcjonalny.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje przekazywania do konsolidatora zestawu. |
| `SdkToolsPath` | Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe. |
| `SourceModules` | Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Jeden lub więcej modułów, które mają być skompilowane w zestawie. Moduły zostaną wymienione w manifeście wynikowego zestawu i nadal będą musiały być dystrybuowane i dostępne w celu załadowania zestawu. Elementy przekazywane do tego parametru mogą `Target`mieć dodatkowe metadane o nazwie , który określa ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po czym kompiluje ten nowy plik do zestawu. Aby uzyskać więcej informacji, zobacz dokumentację [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Ten parametr odpowiada liście modułów przekazanych do *Al.exe* bez określonego przełącznika. |
| `TargetType` | Parametr `String` opcjonalny.<br /><br /> Określa format pliku wyjściowego: `library` (biblioteka `exe` kodu), (aplikacja `win` konsoli) lub (aplikacja oparta na systemie Windows). Wartość domyślna to `library`. Ten parametr odpowiada `/t[arget]` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Parametr `String` opcjonalny.<br /><br /> Określa zestaw, z którego mają dziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultury. Określony zestaw musi mieć silną nazwę.<br /><br /> Zestaw utworzony za pomocą `TemplateFile` parametru będzie złożeniem satelicie. Ten parametr odpowiada `/template` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Parametr `Int32` opcjonalny.<br /><br /> Określa czas w milisekundach, po upływie którego plik wykonywalny zadania zostanie zakończony. Wartością domyślną jest `Int.MaxValue`, wskazując, że nie ma okresu przeoczynia. |
| `Title` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Title` pola w złożeniu. Aby uzyskać więcej informacji, `/title` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Parametr `String` opcjonalny.<br /><br /> Określa lokalizację, z której zadanie zostanie załadowane bazowy plik wykonywalny (Al.exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji SDK odpowiadającej wersji struktury z uruchomionym msbuild. |
| `Trademark` | Parametr `String` opcjonalny.<br /><br /> Określa ciąg dla `Trademark` pola w złożeniu. Aby uzyskać więcej informacji, `/trade[mark]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Parametr `String` opcjonalny.<br /><br /> Określa informacje o wersji dla tego zestawu. Format ciągu to *major.minor.build.revision*. Wartość domyślna to 0. Aby uzyskać więcej informacji, `/v[ersion]` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Parametr `String` opcjonalny.<br /><br /> Wstawia plik *.ico* do złożenia. Plik *.ico* nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Ten parametr odpowiada `/win32icon` opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Parametr `String` opcjonalny.<br /><br /> Wstawia zasób Win32 (plik *.res)* do pliku wyjściowego. Aby uzyskać więcej informacji, `/win32res` zobacz dokumentację opcji w [al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, <xref:Microsoft.Build.Utilities.ToolTask> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład tworzy zestaw z określonymi opcjami.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>Zobacz też

* [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
* [Zadania](../msbuild/msbuild-tasks.md)

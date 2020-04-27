---
title: AL (Konsolidator zestawu) — zadanie | Microsoft Docs
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
ms.openlocfilehash: 5c7964c6654d1f6996d1acc44542e3a7bf093a52
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167465"
---
# <a name="al-assembly-linker-task"></a>AL (Konsolidator zestawu) — zadanie

Zadanie AL zapakuje *Al. exe*, narzędzie, które jest dystrybuowane z zestawem Windows Software Development Kit (SDK). To narzędzie konsolidatora zestawu służy do tworzenia zestawu z manifestem z co najmniej jednego pliku, który jest modułem lub plikami zasobów. Kompilatory i środowiska programistyczne mogą już zapewnić te możliwości, więc często nie jest konieczne bezpośrednie używanie tego zadania. Konsolidator zestawu jest najbardziej przydatny dla deweloperów, którzy chcą utworzyć pojedynczy zestaw z wielu plików składników, takich jak te, które mogą być tworzone na podstawie programowania w języku mieszanym. To zadanie nie łączy modułów w pojedynczy plik zestawu; poszczególne moduły muszą być nadal dystrybuowane i dostępne w celu poprawnego załadowania zestawu. Aby uzyskać więcej informacji na temat *Al. exe*, zobacz [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `AL` zadania.

| Parametr | Opis |
|---------------------| - |
| `AlgorithmID` | Opcjonalny `String` parametr.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, zobacz dokumentację `/algid` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Opcjonalny `String` parametr.<br /><br /> Określa adres, pod którym zostanie załadowana biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje ładują się szybciej, jeśli określisz adres podstawowy bibliotek DLL, zamiast zezwalać systemowi operacyjnemu na przeniesienie bibliotek DLL w przestrzeni procesu. Ten parametr odpowiada[adresowi](/dotnet/framework/tools/al-exe-assembly-linker)/Base. |
| `CompanyName` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Company` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/comp[any]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Configuration` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/config[uration]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Copyright` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/copy[right]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, zobacz dokumentację `/c[ulture]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Opcjonalny `Boolean` parametr.<br /><br /> `true`Aby umieścić tylko klucz publiczny w zestawie; `false` aby w pełni podpisać zestaw. Aby uzyskać więcej informacji, zobacz dokumentację `/delay[sign]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Description` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/descr[iption]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza określone zasoby w obrazie zawierającym manifest zestawu. To zadanie kopiuje zawartość pliku zasobów do obrazu. Elementy przesłane do tego parametru mogą zawierać opcjonalne metadane dołączone do nich `LogicalName` i. `Access` `LogicalName` Metadane są używane do określania wewnętrznego identyfikatora dla zasobu.  `Access` Metadane można ustawić tak, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/embed[resource]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Opcjonalny `String` parametr.<br /><br /> Osadza określony plik w zestawie z nazwą zasobu `Security.Evidence`.<br /><br /> Nie można używać `Security.Evidence` do zwykłych zasobów. Ten parametr odpowiada `/e[vidence]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia dostarczony przez wykonane polecenie. |
| `FileVersion` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `File Version` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/fileversion` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Opcjonalny `String` parametr.<br /><br /> Określa wartość dla `Flags` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/flags` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Opcjonalny `Boolean` parametr.<br /><br /> Powoduje, że zadanie używa ścieżki bezwzględnej dla wszystkich plików, które są raportowane w komunikacie o błędzie. Ten parametr odpowiada `/fullpaths` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Opcjonalny `String` parametr.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację `/keyn[ame]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Opcjonalny `String` parametr.<br /><br /> Określa plik, który zawiera parę kluczy lub tylko klucz publiczny do podpisywania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację `/keyf[ile]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Łączy określone pliki zasobów z zestawem. Zasób stał się częścią zestawu, ale plik nie jest kopiowany. Elementy przesłane do tego parametru mogą zawierać opcjonalne metadane o nazwie `LogicalName`, `Target`i. `Access` `LogicalName` Metadane są używane do określania wewnętrznego identyfikatora dla zasobu. `Target` Metadane mogą określać ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po którym kompiluje ten nowy plik do zestawu. `Access` Metadane można ustawić tak, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/link[resource]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Opcjonalny `String` parametr.<br /><br /> Określa w pełni kwalifikowaną nazwę (*Class. Method*) metody, która ma być używana jako punkt wejścia podczas konwertowania modułu do pliku wykonywalnego. Ten parametr odpowiada `/main` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku wygenerowanego przez to zadanie. Ten parametr odpowiada `/out` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Opcjonalny `String` parametr.<br /><br /> Ogranicza platformę, na której można uruchomić ten kod; musi mieć jedną z `x86`wartości `Itanium`, `x64`,, `anycpu`lub. Wartość domyślna to `anycpu`. Ten parametr odpowiada `/platform` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Product` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/prod[uct]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `ProductVersion` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/productv[ersion]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Opcjonalny `String[]` parametr.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje do przekazania do konsolidatora zestawu. |
| `SdkToolsPath` | Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak Resgen. exe. |
| `SourceModules` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Jeden lub więcej modułów do skompilowania w zestawie. Moduły zostaną wyświetlone w manifeście zestawu, który będzie nadal musiał być dystrybuowany i dostępny w celu załadowania zestawu. Elementy przesłane do tego parametru mogą mieć dodatkowe metadane o nazwie `Target`, który określa ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po czym kompiluje ten nowy plik do zestawu. Aby uzyskać więcej informacji, zobacz dokumentację programu [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). Ten parametr odnosi się do listy modułów przesyłanych do *Al. exe* bez określonego przełącznika. |
| `TargetType` | Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego: `library` (Biblioteka kodu), `exe` (Aplikacja konsolowa) lub `win` (aplikacja oparta na systemie Windows). Wartość domyślna to `library`. Ten parametr odpowiada `/t[arget]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Opcjonalny `String` parametr.<br /><br /> Określa zestaw, z którego mają dziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultura. Określony zestaw musi mieć silną nazwę.<br /><br /> Zestaw utworzony przy użyciu `TemplateFile` parametru będzie zestawem satelickim. Ten parametr odpowiada `/template` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `Title` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Title` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/title` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (Al. exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, w której działa program MSBuild. |
| `Trademark` | Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Trademark` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/trade[mark]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Opcjonalny `String` parametr.<br /><br /> Określa informacje o wersji tego zestawu. Format ciągu to *główna. pomocnicza. kompilacja. poprawka*. Wartość domyślna to 0. Aby uzyskać więcej informacji, zobacz dokumentację `/v[ersion]` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Opcjonalny `String` parametr.<br /><br /> Wstawia plik *. ico* w zestawie. Plik *. ico* zapewnia plikowi wyjściowemu odpowiedni wygląd w Eksploratorze plików. Ten parametr odpowiada `/win32icon` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Opcjonalny `String` parametr.<br /><br /> Wstawia zasób Win32 (plik *. res* ) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz dokumentację `/win32res` opcji w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

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

## <a name="see-also"></a>Zobacz także

* [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
* [Zadania](../msbuild/msbuild-tasks.md)

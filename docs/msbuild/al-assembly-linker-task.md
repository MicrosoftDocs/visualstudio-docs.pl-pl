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
ms.openlocfilehash: d90e6c94d07b73e79d793982944bca395a562df2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593476"
---
# <a name="al-assembly-linker-task"></a>AL (Konsolidator zestawu) — zadanie
Zadanie AL zapakuje *Al. exe*, narzędzie, które jest dystrybuowane z [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. To narzędzie konsolidatora zestawu służy do tworzenia zestawu z manifestem z co najmniej jednego pliku, który jest modułem lub plikami zasobów. Kompilatory i środowiska programistyczne mogą już zapewnić te możliwości, więc często nie jest konieczne bezpośrednie używanie tego zadania. Konsolidator zestawu jest najbardziej przydatny dla deweloperów, którzy chcą utworzyć pojedynczy zestaw z wielu plików składników, takich jak te, które mogą być tworzone na podstawie programowania w języku mieszanym. To zadanie nie łączy modułów w pojedynczy plik zestawu; poszczególne moduły muszą być nadal dystrybuowane i dostępne w celu poprawnego załadowania zestawu. Aby uzyskać więcej informacji na temat *Al. exe*, zobacz [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `AL`.

| Parametr | Opis |
|---------------------| - |
| `AlgorithmID` | Opcjonalny parametr `String`.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/algid` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Opcjonalny parametr `String`.<br /><br /> Określa adres, pod którym zostanie załadowana biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje ładują się szybciej, jeśli określisz adres podstawowy bibliotek DLL, zamiast zezwalać systemowi operacyjnemu na przeniesienie bibliotek DLL w przestrzeni procesu. Ten parametr odpowiada[adresowi](/dotnet/framework/tools/al-exe-assembly-linker)/Base. |
| `CompanyName` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Company` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/comp[any]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Configuration` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/config[uration]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Copyright` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/copy[right]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/c[ulture]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Opcjonalny parametr `Boolean`.<br /><br /> `true` umieścić tylko klucz publiczny w zestawie; `false` w celu pełnego podpisania zestawu. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/delay[sign]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Description` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/descr[iption]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Osadza określone zasoby w obrazie zawierającym manifest zestawu. To zadanie kopiuje zawartość pliku zasobów do obrazu. Elementy przesłane do tego parametru mogą mieć opcjonalne metadane dołączone do nich o nazwie `LogicalName` i `Access`. Metadane `LogicalName` są używane do określania wewnętrznego identyfikatora dla zasobu.  Metadane `Access` można ustawić na `private`, aby zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/embed[resource]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Opcjonalny parametr `String`.<br /><br /> Osadza określony plik w zestawie przy użyciu nazwy zasobu `Security.Evidence`.<br /><br /> Nie można używać `Security.Evidence` do zwykłych zasobów. Ten parametr odpowiada opcji `/e[vidence]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia dostarczony przez wykonane polecenie. |
| `FileVersion` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `File Version` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/fileversion` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Opcjonalny parametr `String`.<br /><br /> Określa wartość dla pola `Flags` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/flags` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Opcjonalny parametr `Boolean`.<br /><br /> Powoduje, że zadanie używa ścieżki bezwzględnej dla wszystkich plików, które są raportowane w komunikacie o błędzie. Ten parametr odpowiada opcji `/fullpaths` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Opcjonalny parametr `String`.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/keyn[ame]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Opcjonalny parametr `String`.<br /><br /> Określa plik, który zawiera parę kluczy lub tylko klucz publiczny do podpisywania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/keyf[ile]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Łączy określone pliki zasobów z zestawem. Zasób stał się częścią zestawu, ale plik nie jest kopiowany. Elementy przesłane do tego parametru mogą mieć opcjonalne metadane dołączone do nich o nazwie `LogicalName`, `Target`i `Access`. Metadane `LogicalName` są używane do określania wewnętrznego identyfikatora dla zasobu. Metadane `Target` mogą określać ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po którym kompiluje ten nowy plik do zestawu. Metadane `Access` można ustawić na `private`, aby zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/link[resource]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Opcjonalny parametr `String`.<br /><br /> Określa w pełni kwalifikowaną nazwę (*Class. Method*) metody, która ma być używana jako punkt wejścia podczas konwertowania modułu do pliku wykonywalnego. Ten parametr odpowiada opcji `/main` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku wygenerowanego przez to zadanie. Ten parametr odpowiada opcji `/out` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Opcjonalny parametr `String`.<br /><br /> Ogranicza platformę, na której można uruchomić ten kod; musi mieć jedną z `x86`, `Itanium`, `x64`lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odpowiada opcji `/platform` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Product` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/prod[uct]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `ProductVersion` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/productv[ersion]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Opcjonalny parametr `String[]`.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje do przekazania do konsolidatora zestawu. |
| `SdkToolsPath` | Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak Resgen. exe. |
| `SourceModules` | Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Jeden lub więcej modułów do skompilowania w zestawie. Moduły zostaną wyświetlone w manifeście zestawu, który będzie nadal musiał być dystrybuowany i dostępny w celu załadowania zestawu. Elementy przenoszone do tego parametru mogą zawierać dodatkowe metadane o nazwie `Target`, która określa ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po czym kompiluje ten nowy plik do zestawu. Aby uzyskać więcej informacji, zobacz dokumentację programu [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). Ten parametr odnosi się do listy modułów przesyłanych do *Al. exe* bez określonego przełącznika. |
| `TargetType` | Opcjonalny parametr `String`.<br /><br /> Określa format pliku wyjściowego: `library` (Biblioteka kodu), `exe` (Aplikacja konsolowa) lub `win` (aplikacja oparta na systemie Windows). Wartość domyślna to `library`. Ten parametr odpowiada opcji `/t[arget]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Opcjonalny parametr `String`.<br /><br /> Określa zestaw, z którego mają dziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultura. Określony zestaw musi mieć silną nazwę.<br /><br /> Zestaw utworzony przy użyciu `TemplateFile` parametr będzie zestawem satelickim. Ten parametr odpowiada opcji `/template` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Opcjonalny parametr `Int32`.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, co oznacza, że nie ma limitu czasu. |
| `Title` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Title` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/title` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Opcjonalny parametr `String`.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (Al. exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | Opcjonalny parametr `String`.<br /><br /> Określa ciąg dla pola `Trademark` w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/trade[mark]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Opcjonalny parametr `String`.<br /><br /> Określa informacje o wersji tego zestawu. Format ciągu to *główna. pomocnicza. kompilacja. poprawka*. Wartość domyślna to 0. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/v[ersion]` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Opcjonalny parametr `String`.<br /><br /> Wstawia plik *. ico* w zestawie. Plik *. ico* zapewnia plikowi wyjściowemu odpowiedni wygląd w Eksploratorze plików. Ten parametr odpowiada opcji `/win32icon` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Opcjonalny parametr `String`.<br /><br /> Wstawia zasób Win32 (plik *. res* ) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz dokumentację opcji `/win32res` w [Al. exe (Konsolidator zestawu)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

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

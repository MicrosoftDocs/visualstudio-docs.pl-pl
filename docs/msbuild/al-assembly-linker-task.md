---
title: AL (Assembly Linker) zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39340e268d41207e9b054866ecebe613f7836347
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951282"
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker) zadanie
Al — zadanie jest zawijany *AL.exe*, to narzędzie, które jest rozpowszechniana z [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. To narzędzie Assembly Linker służy do tworzenia zestawu z manifestem z co najmniej jeden plik, który jest modułem lub plikiem zasobów. Kompilatory języków i środowisk programistycznych może już zapewniają te funkcje, często nie jest niezbędne do korzystania z tego zadania bezpośrednio. Assembly Linker jest najbardziej użyteczna dla deweloperów, konieczności tworzenia w jednym zestawie z wielu plików składników, takich jak oferowanych od etapu programowania w językach mieszanych. To zadanie nie łączyć modułów w pliku jednym zestawie; indywidualne moduły muszą być rozproszone i dostępne, aby Wynikowy zestaw można prawidłowo załadować. Aby uzyskać więcej informacji na temat *AL.exe*, zobacz [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `AL` zadania.

| Parametr | Opis |
|---------------------| - |
| `AlgorithmID` | Opcjonalnie `String` parametru.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, zobacz dokumentację dla `/algid` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `BaseAddress` | Opcjonalnie `String` parametru.<br /><br /> Określa adres, pod którym zostanie załadowana biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje ładują się szybciej, jeśli określony adres podstawowy bibliotek DLL, a nie pozwalając systemowi operacyjnemu na przeniesienie biblioteki dll w przestrzeni procesu. Ten parametr odnosi się do uwzględniają[adres](/dotnet/framework/tools/al-exe-assembly-linker). |
| `CompanyName` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Company` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/comp[any]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Configuration` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Configuration` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/config[uration]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Copyright` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Copyright` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/copy[right]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Culture` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, zobacz dokumentację dla `/c[ulture]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `DelaySign` | Opcjonalnie `Boolean` parametru.<br /><br /> `true` Aby umieścić klucz publiczny w zestawie; `false` można całkowicie podpisać zestaw. Aby uzyskać więcej informacji, zobacz dokumentację dla `/delay[sign]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Description` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Description` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/descr[iption]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EmbedResources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określone zasoby są osadzane w obrazie, który zawiera manifest zestawu. To zadanie kopiuje zawartość pliku zasobu do obrazu. Elementy przekazanych do tego parametru może być opcjonalne metadane dołączonych do nich o nazwie `LogicalName` i `Access`. `LogicalName` Metadanych jest używany do określenia wewnętrznym identyfikatorem zasobu.  `Access` Można ustawić metadanych `private` przed zasobu nie są widoczne dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację dla `/embed[resource]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `EvidenceFile` | Opcjonalnie `String` parametru.<br /><br /> Osadza określony plik w zestawie z nazwą zasobu `Security.Evidence`.<br /><br /> Nie można użyć `Security.Evidence` dla zwykłych zasobów. Ten parametr odnosi się do `/e[vidence]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ExitCode` | Opcjonalnie `Int32` parametr tylko do odczytu danych wyjściowych.<br /><br /> Określa kod zakończenia, dostarczone przez wykonanego polecenia. |
| `FileVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `File Version` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/fileversion` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Flags` | Opcjonalnie `String` parametru.<br /><br /> Określa wartość dla `Flags` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/flags` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `GenerateFullPaths` | Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że zadanie używa ścieżki bezwzględnej dla wszelkich plików zgłoszonych w komunikacie o błędzie. Ten parametr odnosi się do `/fullpaths` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyContainer` | Opcjonalnie `String` parametru.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Zadanie następnie podpisze ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację dla `/keyn[ame]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `KeyFile` | Opcjonalnie `String` parametru.<br /><br /> Określa plik, który zawiera parę kluczy lub klucz publiczny, aby podpisać zestaw. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację dla `/keyf[ile]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `LinkResources` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Łączy określone pliki zasobów do zestawu. Zasób staje się częścią zestawu, ale plik nie jest kopiowany. Elementy przekazanych do tego parametru może być opcjonalne metadane dołączonych do nich o nazwie `LogicalName`, `Target`, i `Access`. `LogicalName` Metadanych jest używany do określenia wewnętrznym identyfikatorem zasobu. `Target` Metadanych można określić ścieżkę i nazwę pliku, do którego zadanie skopiuje plik, po upływie którego kompiluje tego nowego pliku w zestawie. `Access` Można ustawić metadanych `private` przed zasobu nie są widoczne dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację dla `/link[resource]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `MainEntryPoint` | Opcjonalnie `String` parametru.<br /><br /> Określa w pełni kwalifikowaną nazwę (*class.method*) metody do użycia jako punkt wejścia podczas konwertowania modułu do pliku wykonywalnego. Ten parametr odnosi się do `/main` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `OutputAssembly` | Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku, generowane przez to zadanie. Ten parametr odnosi się do `/out` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Platform` | Opcjonalnie `String` parametru.<br /><br /> Ogranicza platformy, które ten kod może działać na; musi być jednym z `x86`, `Itanium`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Ten parametr odnosi się do `/platform` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductName` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Product` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/prod[uct]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ProductVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `ProductVersion` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/productv[ersion]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ResponseFiles` | Opcjonalnie `String[]` parametru.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje do przejścia do Assembly Linker. |
| `SdkToolsPath` | Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe. |
| `SourceModules` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Przynajmniej jeden moduł skompilowany w zestawie. Moduły zostaną wyświetlone w manifeście zestawu wynikowego i nadal obowiązują rozproszone i dostępne w kolejności dla zestawu do załadowania. Elementy przekazany do tego parametru może mieć dodatkowe metadane o nazwie `Target`, która określa ścieżkę i nazwę pliku, do którego zadanie skopiuje plik, po upływie którego kompiluje tego nowego pliku w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). Ten parametr odnosi się do listy modułów przekazany do *Al.exe* bez określonego przełącznika. |
| `TargetType` | Opcjonalnie `String` parametru.<br /><br /> Określa format pliku wyjściowego: `library` (biblioteka kodu) `exe` (Aplikacja konsoli) lub `win` (aplikacji systemu Windows). Wartość domyślna to `library`. Ten parametr odnosi się do `/t[arget]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `TemplateFile` | Opcjonalnie `String` parametru.<br /><br /> Określa zestaw, z którego można odziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultury. Określony zestaw musi mieć silną nazwę.<br /><br /> Zestaw utworzony przy użyciu `TemplateFile` parametr będzie zestawem satelickim. Ten parametr odnosi się do `/template` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Timeout` | Opcjonalnie `Int32` parametru.<br /><br /> Określa ilość czasu w milisekundach, po których zostanie zakończony wykonywalnego zadania podrzędnego. Wartość domyślna to `Int.MaxValue`, wskazujący, że nie okres limitu czasu. |
| `Title` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Title` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/title` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `ToolPath` | Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację, z którym zadanie załaduje podstawowego pliku wykonywalnego (Al.exe). Jeśli nie określono tego parametru, zadanie używa ścieżki instalacji zestawu SDK odpowiadający wersję framework, na którym działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| `Trademark` | Opcjonalnie `String` parametru.<br /><br /> Określa ciąg dla `Trademark` pole w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację dla `/trade[mark]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Version` | Opcjonalnie `String` parametru.<br /><br /> Określa informacje o wersji dla tego zestawu. Format ciągu jest *główna.pomocnicza.kompilacja.poprawka*. Wartość domyślna to 0. Aby uzyskać więcej informacji, zobacz dokumentację dla `/v[ersion]` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Icon` | Opcjonalnie `String` parametru.<br /><br /> Wstawia *.ico* pliku w zestawie. *.Ico* pliku nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Ten parametr odnosi się do `/win32icon` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |
| `Win32Resource` | Opcjonalnie `String` parametru.<br /><br /> Wstawia zasób Win32 (*.res* pliku) w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz dokumentację dla `/win32res` opcji [Al.exe (Assembly Linker)](/dotnet/framework/tools/al-exe-assembly-linker). |

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).

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

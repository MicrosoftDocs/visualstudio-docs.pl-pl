---
title: Zadanie generateresource | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd5946612889e98b3b90f2ee3cb8665c43827a5e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634061"
---
# <a name="generateresource-task"></a>GenerateResource — zadanie

Konwertuje między plikami *.txt* i *.resx* (format zasobów opartym na XML) i plikami binarnymi *.resources* w języku common language, które mogą być osadzone w pliku wykonywalnym binarnym środowiska uruchomieniowego lub kompilowane w zestawy satelickie. To zadanie jest zwykle używane do konwertowania plików *.txt* lub *.resx* na pliki *.resources.* Zadanie `GenerateResource` jest funkcjonalnie podobne do [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry

W poniższej tabeli `GenerateResource` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalInputs`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Zawiera dodatkowe dane wejściowe do sprawdzania zależności wykonywane przez to zadanie. Na przykład pliki projektu i obiektów docelowych zazwyczaj powinny być dane wejściowe, tak aby jeśli są one aktualizowane, wszystkie zasoby są generowane ponownie.|
|`EnvironmentVariables`|Parametr `String[]` opcjonalny.<br /><br /> Określa tablicę par nazw i wartości zmiennych środowiskowych, które powinny być przekazywane do zduplikowanego *pliku resgen.exe,* oprócz (lub selektywnie zastępowania) zwykłego bloku środowiska.|
|`ExcludedInputPaths`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa tablicę elementów określających ścieżki, z których śledzone dane wejściowe będą ignorowane podczas sprawdzania stanu aktualności.|
|`ExecuteAsTool`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program , uruchamia *plik tlbimp.exe* i *aximp.exe* z odpowiedniej struktury docelowej poza proc, aby wygenerować niezbędne zestawy otoki. Ten parametr umożliwia wielokrotne `ResolveComReferences`kierowanie .|
|`FilesWritten`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera nazwy wszystkich plików zapisanych na dysku. Obejmuje to plik pamięci podręcznej, jeśli istnieje. Ten parametr jest przydatny w implementacjach Clean.|
|`MinimalRebuildFromTracking`|Parametr `Boolean` opcjonalny.<br /><br /> Pobiera lub ustawia przełącznik, który określa, czy śledzone przyrostowej kompilacji będą używane. Jeśli `true`włączona jest kompilacja przyrostowa; w przeciwnym razie przebudowa zostanie wymuszona.|
|`NeverLockTypeAssemblies`|Parametr `Boolean` opcjonalny.<br /><br /> Pobiera lub ustawia wartość logiczną, która określa, czy utworzyć nową [Domenę Aplikacji](/dotnet/api/system.appdomain) do oceny zasobów (*.resx*) plików (true) lub utworzyć nową [AppDomain](/dotnet/api/system.appdomain) tylko wtedy, gdy pliki zasobów odwołać się do zestawu użytkownika (false).|
|`OutputResources`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa nazwę wygenerowanych plików, takich jak pliki *.resources.* Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pasującego pliku wejściowego, a utworzony plik *.resources* zostanie umieszczony w katalogu zawierającym plik wejściowy.|
|`PublicClass`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, tworzy silnie typizowane klasy zasobów jako klasy publicznej.|
|`References`|Parametr `String[]` opcjonalny.<br /><br /> Odwołania do ładowania typów w *plikach .resx* z. Elementy danych pliku *resx* mogą mieć typ .NET. Po odczytaniu pliku *.resx* należy to rozwiązać. Zazwyczaj jest rozpoznawany pomyślnie przy użyciu standardowych reguł ładowania typu. Jeśli podasz zestawy `References`w , mają pierwszeństwo.<br /><br /> Ten parametr nie jest wymagany dla silnie wpisanych zasobów.|
|`SdkToolsPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do konwersji. Elementy przekazywane do tego parametru muszą mieć jedno z następujących rozszerzeń plików:<br /><br /> -   *.txt*: Określa rozszerzenie pliku tekstowego do konwersji. Pliki tekstowe mogą zawierać tylko zasoby ciągów.<br />-   *.resx*: Określa rozszerzenie pliku zasobów opartego na języku XML do konwersji.<br />-   *.restext*: Określa ten sam format co *.txt*. To inne rozszerzenie jest przydatne, jeśli chcesz wyraźnie odróżnić pliki źródłowe, które zawierają zasoby z innych plików źródłowych w procesie kompilacji.<br />-   *.resources*: Określa rozszerzenie pliku zasobów do konwersji.|
|`StateFile`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa ścieżkę do opcjonalnego pliku pamięci podręcznej, który jest używany do przyspieszenia sprawdzania zależności łączy w plikach wejściowych *.resx.*|
|`StronglyTypedClassName`|Parametr `String` opcjonalny.<br /><br /> Określa nazwę klasy dla klasy zasobów silnie typizowane. Jeśli ten parametr nie jest określony, używana jest nazwa podstawowa pliku zasobów.|
|`StronglyTypedFilename`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa nazwę pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy jest używana jako podstawowa nazwa pliku, z rozszerzeniem zależnym od języka. Na przykład: *MyClass.cs*.|
|`StronglyTypedLanguage`|Parametr `String` opcjonalny.<br /><br /> Określa język używany podczas generowania źródła klasy dla silnie typizowanego zasobu. Ten parametr musi być zgodny dokładnie jeden z języków używanych przez CodeDomProvider. Na `VB` przykład: `C#`lub .<br /><br /> Przekazując wartość do tego parametru, należy poinstruować zadanie do generowania silnie typizowanych zasobów.|
|`StronglyTypedManifestPrefix`|Parametr `String` opcjonalny.<br /><br /> Określa obszar nazw zasobu lub prefiks manifestu do użycia w wygenerowanym źródle klasy dla silnie typizowanego zasobu.|
|`StronglyTypedNamespace`|Parametr `String` opcjonalny.<br /><br /> Określa obszar nazw, który ma być używany dla wygenerowanego źródła klasy dla silnie typizowanego zasobu. Jeśli ten parametr nie jest określony, wszystkie silnie wpisane zasoby znajdują się w globalnej przestrzeni nazw.|
|`TLogReadFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują dzienniki śledzenia odczytu.|
|`TLogWriteFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują dzienniki śledzenia zapisu.|
|`ToolArchitecture`|Parametr <xref:System.String?displayProperty=fullName> opcjonalny.<br /><br /> Służy do określenia, czy *tracker.exe* musi być używany do odradzania *ResGen.exe*.<br /><br /> Powinny być przyswojenia dla <xref:Microsoft.Build.Utilities.ExecutableType> członka wyliczenia. Jeśli `String.Empty`program , używa heurystyki do określenia architektury domyślnej. Powinny być analizowalne dla członka microsoft.build.Utilities.ExecutableType wyliczenia.|
|`TrackerFrameworkPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji programu .NET Framework zawierającej *plik FileTracker.dll*.<br /><br /> Jeśli jest ustawiona, użytkownik bierze odpowiedzialność za upewnienie się, że bity *filetracker.dll,* które przechodzą odpowiada bitness *ResGen.exe,* które zamierzają użyć. Jeśli nie jest ustawiona, zadanie decyduje o odpowiedniej lokalizacji na podstawie bieżącej wersji programu .NET Framework.|
|`TrackerLogDirectory`|Parametr `String` opcjonalny.<br /><br /> Określa katalog pośredni, w którym zostaną umieszczone dzienniki śledzenia z uruchamiania tego zadania.|
|`TrackerSdkPath`|Parametr `String` opcjonalny.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji SDK systemu Windows zawierającej *program Tracker.exe*.<br /><br /> Jeśli jest ustawiona, użytkownik bierze odpowiedzialność za upewnienie się, że bitness *programu Tracker.exe,* który przechodzą, odpowiada bitowości *programu ResGen.exe,* którego zamierza użyć. Jeśli nie jest ustawiona, zadanie decyduje o odpowiedniej lokalizacji na podstawie bieżącego zestawu Windows SDK.|
|`TrackFileAccess`|Parametr <xref:System.Boolean> opcjonalny.<br /><br /> Jeśli true, katalog pliku wejściowego jest używany do rozpoznawania względnych ścieżek plików.|
|`UseSourcePath`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, określa, że katalog pliku wejściowego ma być używany do rozpoznawania względnych ścieżek plików.|

## <a name="remarks"></a>Uwagi

Ponieważ pliki *resx* mogą zawierać łącza do innych plików zasobów, nie wystarczy po prostu porównać znaczniki czasu plików *.resx* i *.resources,* aby sprawdzić, czy dane wyjściowe są aktualne. Zamiast tego `GenerateResource` zadanie podąża za łączami w *plikach .resx* i sprawdza również sygnatury czasowe połączonych plików. Oznacza to, że zazwyczaj `Inputs` nie `Outputs` należy używać i `GenerateResource` atrybuty na miejsce docelowe zawierające zadanie, ponieważ może to spowodować, że zostanie pominięty, gdy faktycznie należy uruchomić.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

Podczas korzystania z MSBuild 4.0 do kierowania .NET 3.5 projektów kompilacji może zakończyć się niepowodzeniem na x86 zasobów. Aby obejść ten problem, można utworzyć obiekt docelowy jako zestaw AnyCPU.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto zadania do generowania `GenerateResource` plików *.resources* z plików określonych przez kolekcję `Resx` elementów.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Zadanie `GenerateResource` używa metadanych \<> \<LogicalName elementu EmbeddedResource>, aby nazwać zasób osadzony w zestawie.

Zakładając, że zestaw nosi nazwę myAssembly, następujący kod generuje osadzony zasób o nazwie *someQualifier.someResource.resources:*

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<metadanych> LogicalName zasób będzie miał nazwę *myAssembly.myResource.resources*.  W tym przykładzie dotyczy tylko visual basic i visual C# proces kompilacji.

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

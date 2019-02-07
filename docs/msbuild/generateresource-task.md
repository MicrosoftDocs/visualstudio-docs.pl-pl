---
title: Generateresource — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c63e9293cffca2c1b071dcd537c0f49f8faa438
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853982"
---
# <a name="generateresource-task"></a>GenerateResource — zadanie
Wykonuje konwersję między *.txt* i *resx* plików (w formacie zasobów opartych na języku XML) i środowisko uruchomieniowe języka wspólnego binarne *Resources* pliki, które można osadzić w binarnym środowiska uruchomieniowego pliku wykonywalnego lub skompilowane do zestawów satelickich. To zadanie jest zazwyczaj używana do konwersji *.txt* lub *resx* plików *Resources* plików. `GenerateResource` Zadanie jest podobne do [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry `GenerateResource` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalInputs`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Zawiera dodatkowe dane wejściowe, aby sprawdzanie zależności wykonywane przez to zadanie. Na przykład pliki projektu i obiektów docelowych zwykle należy danych wejściowych, więc, że jeśli są one aktualizowane wszystkie zasoby są generowane.|
|`EnvironmentVariables`|Opcjonalnie `String[]` parametru.<br /><br /> Określa tablicę par nazw wartości zmiennych środowiskowych, które powinny być przekazywane do zduplikowanych *resgen.exe*, oprócz (lub selektywnie zastępowanie) blok regularnych środowiska.|
|`ExcludedInputPaths`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa tablicę elementów, które określają ścieżek, z których śledzone dane wejściowe zostaną zignorowane podczas sprawdzania na bieżąco.|
|`ExecuteAsTool`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uruchamia *tlbimp.exe* i *aximp.exe* z odpowiedniego obiektu docelowego framework-procesem do generowania zestawów niezbędne otoki. Ten parametr umożliwia wielowersyjności kodu programu `ResolveComReferences`.|
|`FilesWritten`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera nazwy wszystkie pliki zapisane na dysku. Obejmuje to plik pamięci podręcznej, jeśli istnieje. Ten parametr jest przydatne w przypadku implementacji czysty.|
|`MinimalRebuildFromTracking`|Opcjonalnie `Boolean` parametru.<br /><br /> Pobiera lub ustawia przełącznik, który określa, czy będzie używana śledzonych kompilacji przyrostowej. Jeśli `true`, kompilacja przyrostowa jest włączone; w przeciwnym razie zostanie wymuszone ponownej kompilacji.|
|`NeverLockTypeAssemblies`|Opcjonalnie `Boolean` parametru.<br /><br /> Pobiera lub ustawia wartość logiczna określająca, czy do tworzenia nowego [AppDomain](/dotnet/api/system.appdomain) do oceny zasobów (*resx*) plików (PRAWDA) lub utworzyć nową [AppDomain](/dotnet/api/system.appdomain) tylko wtedy, gdy pliki zasobów odwoływać się do zestawów użytkownika (false).|
|`OutputResources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa nazwę wygenerowanego plików, takich jak *Resources* plików. Jeśli nie określisz nazwy, nazwa odpowiedniego pliku wejściowego jest używana i *Resources* utworzony plik zostanie umieszczony w katalogu, który zawiera plik wejściowy.|
|`PublicClass`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy silnie typizowanej klasy zasobów jako klasę publiczną.|
|`References`|Opcjonalnie `String[]` parametru.<br /><br /> Odwołania można załadować typów w *resx* plików z. *resx* elementy danych pliku może mieć typ architektury .NET. Gdy *resx* plik jest do odczytu, musi to być rozwiązane. Zwykle rozwiązania problemu pomyślnie za pomocą standardowej, trwa ładowanie reguł. Jeśli podasz zestawów w `References`, ich wyższy priorytet.<br /><br /> Ten parametr nie jest wymagane dla silnie typizowanych zasobów.|
|`SdkToolsPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do przekonwertowania. Pozycji przekazanych do tego parametru musi mieć jedną z następujących rozszerzeń pliku:<br /><br /> -   *.txt*: Określa rozszerzenie pliku tekstowego do przekonwertowania. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów.<br />-   *resx*: Określa rozszerzenie pliku zasobów w formacie XML do konwersji.<br />-   *.restext*: Określa tego samego formatu co *.txt*. To rozszerzenie innej jest przydatne, jeśli chcesz wyraźnie odróżnić pliki źródłowe, zawierające zasoby z innych plikach źródłowych w procesie kompilacji.<br />-   *.resources*: Określa rozszerzenie pliku zasobu do konwersji.|
|`StateFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa ścieżkę do pliku opcjonalne pamięci podręcznej, który jest używany w celu przyspieszenia sprawdzania łączy w zależności *resx* plików wejściowych.|
|`StronglyTypedClassName`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę klasy dla silnie typizowanej klasy zasobów. Jeśli ten parametr nie jest określony, używany jest podstawowej nazwy pliku zasobów.|
|`StronglyTypedFilename`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku dla pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy jest używany jako podstawowej nazwy pliku z rozszerzeniem zależne od języka. Na przykład: *MyClass.cs*.|
|`StronglyTypedLanguage`|Opcjonalnie `String` parametru.<br /><br /> Określa język do użycia podczas generowania klasy źródło silnie typizowanych zasobów. Ten parametr musi być zgodna dokładnie jeden z języków używany przez element CodeDomProvider. Na przykład: `VB` lub `C#`.<br /><br /> Przez przekazanie wartości do tego parametru, możesz poinstruować zadania, aby wygenerować silnie typizowanych zasobów.|
|`StronglyTypedManifestPrefix`|Opcjonalnie `String` parametru.<br /><br /> Określa prefiks przestrzeni nazw lub manifest zasobu, do użytku w źródle wygenerowanej klasy silnie typizowanych zasobów.|
|`StronglyTypedNamespace`|Opcjonalnie `String` parametru.<br /><br /> Określa przestrzeń nazw dla generowanej klasy źródło silnie typizowanych zasobów. Jeśli ten parametr nie jest określony, wszystkie zasoby silnie typizowane znajdują się w globalnej przestrzeni nazw.|
|`TLogReadFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują odczytu dzienniki śledzenia.|
|`TLogWriteFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują zapisu dzienniki śledzenia.|
|`ToolArchitecture`|Opcjonalnie <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Używany do określenia czy *Tracker.exe* musi zostać użyte zduplikować *ResGen.exe*.<br /><br /> Powinien być przeanalizowania do elementu członkowskiego <xref:Microsoft.Build.Utilities.ExecutableType> wyliczenia. Jeśli `String.Empty`, używa heurystyki do określenia architektura domyślne. Powinien być przeanalizowania do elementu członkowskiego wyliczenia Microsoft.Build.Utilities.ExecutableType.|
|`TrackerFrameworkPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji środowiska .NET Framework, który zawiera *FileTracker.dll*.<br /><br /> Jeśli ustawiony, użytkownik przyjmuje odpowiedzialność za zapewnienie, że wartości bitowości *FileTracker.dll* zostaną pomyślnie odpowiada wartości bitowości *ResGen.exe* , będą one używane. W przeciwnym razie zestawu, zadanie decyduje, odpowiednią lokalizację, w oparciu o bieżącą wersję systemu .NET Framework.|
|`TrackerLogDirectory`|Opcjonalnie `String` parametru.<br /><br /> Określa katalog pośredni, w którym zostaną umieszczone dzienniki śledzenia uruchamianie tego zadania.|
|`TrackerSdkPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji zestawu Windows SDK, który zawiera *Tracker.exe*.<br /><br /> Jeśli ustawiony, użytkownik przyjmuje odpowiedzialność za zapewnienie, że wartości bitowości *Tracker.exe* zostaną pomyślnie odpowiada wartości bitowości *ResGen.exe* , będą one używane. W przeciwnym razie zestawu, zadanie decyduje, odpowiednią lokalizację, w oparciu o bieżący zestaw Windows SDK.|
|`TrackFileAccess`|Opcjonalnie <xref:System.Boolean> parametru.<br /><br /> W przypadku opcji true rozpoznawania względnych ścieżek plików jest używany katalog pliku wejściowego.|
|`UseSourcePath`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że katalog pliku wejściowego ma być używany do rozpoznawania względnych ścieżek plików.|

## <a name="remarks"></a>Uwagi
Ponieważ *resx* plików mogą zawierać łącza do innych plików zasobów nie jest wystarczające, aby porównać po prostu *resx* i *Resources* plików sygnatur czasowych, aby zobaczyć, czy dane wyjściowe aktualne. Zamiast tego `GenerateResource` zadania jest zgodna z łączy w *resx* pliki i sprawdza, czy znacznikami czasu plików połączonych. Oznacza to, że nie należy generalnie używać `Inputs` i `Outputs` atrybutów na docelowym zawierający `GenerateResource` zadania, ponieważ może to doprowadzić do pominięcia podczas faktycznie należy uruchomić.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

Przy użyciu programu MSBuild 4.0 projektów docelowych .NET 3.5, kompilacja może zakończyć się niepowodzeniem na x86 zasobów. Aby obejść ten problem, możesz utworzyć element docelowy jako zestawu AnyCPU.

## <a name="example"></a>Przykład
W poniższym przykładzie użyto `GenerateResource` zadania do wygenerowania *Resources* plików z plików określone przez `Resx` elementu kolekcji.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

`GenerateResource` Zadanie używa \<LogicalName > Metadane \<EmbeddedResource > element, aby nazwa zasobu, który jest osadzony w zestawie.

Przy założeniu, że zestaw jest o nazwie myAssembly, poniższy kod generuje osadzony zasób o nazwie *someQualifier.someResource.resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<LogicalName > metadane, będą miały postać zasobu *myAssembly.myResource.resources*.  Ten przykład dotyczy tylko dla procesu kompilacji w Visual Basic i Visual C#.

## <a name="see-also"></a>Zobacz także
[Zadania](../msbuild/msbuild-tasks.md)  
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

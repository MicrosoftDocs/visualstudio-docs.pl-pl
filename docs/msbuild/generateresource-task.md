---
title: GenerateResource — zadanie | Microsoft Docs
description: Użyj zadania MSBuild GenerateResource, aby przekonwertować pliki. txt lub. resx oraz pliki binarne plików binarnych środowiska uruchomieniowego języka wspólnego.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 124e5dcc3666698dd71927e15c3686038233c317
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436880"
---
# <a name="generateresource-task"></a>GenerateResource — zadanie

Konwertuje pliki *. txt* i *. resx* (format zasobów opartych na języku XML) i *pliki binarne środowiska* uruchomieniowego języka wspólnego, które mogą być osadzone w binarnym pliku wykonywalnym środowiska uruchomieniowego lub skompilowane w zestawach satelickich. To zadanie jest zwykle używane do konwertowania plików *txt* lub *resx* na pliki *resources* . `GenerateResource`Zadanie jest podobne do [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `GenerateResource` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalInputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Zawiera dodatkowe dane wejściowe do sprawdzania zależności wykonane przez to zadanie. Na przykład pliki projektu i elementów docelowych zazwyczaj powinny być danymi wejściowymi, aby w przypadku ich aktualizacji wszystkie zasoby zostały ponownie wygenerowane.|
|`EnvironmentVariables`|Opcjonalny `String[]` parametr.<br /><br /> Określa tablicę par nazwa-wartość zmiennych środowiskowych, które powinny być przesyłane do zduplikowanego *resgen.exe*, oprócz (lub selektywnego przesłaniania) zwykłego bloku środowiska.|
|`ExcludedInputPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa tablicę elementów, które określają ścieżki, z których śledzone dane wejściowe zostaną zignorowane podczas sprawdzania.|
|`ExecuteAsTool`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` program uruchamia *tlbimp.exe* i *aximp.exe* z odpowiedniego platformy docelowej, aby wygenerować niezbędne zestawy otoki. Ten parametr umożliwia wiele elementów docelowych `ResolveComReferences` .|
|`FilesWritten`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera nazwy wszystkich plików, które są zapisywane na dysku. Obejmuje to plik pamięci podręcznej, jeśli istnieje. Ten parametr jest przydatny w przypadku implementacji czystego.|
|`MinimalRebuildFromTracking`|Opcjonalny `Boolean` parametr.<br /><br /> Pobiera lub ustawia przełącznik określający, czy zostanie użyta śledzona kompilacja przyrostowa. Jeśli `true` kompilacja przyrostowa jest włączona; w przeciwnym razie zostanie wymuszone ponowne kompilowanie.|
|`NeverLockTypeAssemblies`|Opcjonalny `Boolean` parametr.<br /><br /> Pobiera lub ustawia wartość logiczną określającą, czy należy utworzyć nową [domenę aplikacji](/dotnet/api/system.appdomain) , aby oszacować pliki zasobów (*. resx*) (true) lub utworzyć nową [domenę aplikacji](/dotnet/api/system.appdomain) tylko wtedy, gdy pliki zasobów odwołują się do zestawu użytkownika (false).|
|`OutputResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa nazwę wygenerowanych plików, takich jak pliki *resources* . Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pasującego pliku wejściowego, a utworzony plik *resources* zostanie umieszczony w katalogu zawierającym plik wejściowy.|
|`PublicClass`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , tworzy klasę zasobów o jednoznacznie określonym typie jako Klasa publiczna.|
|`References`|Opcjonalny `String[]` parametr.<br /><br /> Odwołania do typów ładowania w plikach *resx* z. elementy danych pliku *resx* mogą mieć typ .NET. Po odczytaniu pliku *resx* należy rozwiązać ten problem. Zwykle jest ona rozwiązywana pomyślnie przy użyciu standardowych reguł ładowania typów. Jeśli postanowisz zestawy w `References` , mają one pierwszeństwo.<br /><br /> Ten parametr nie jest wymagany w przypadku zasobów o jednoznacznie określonym typie.|
|`SdkToolsPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *resgen.exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do przekonwertowania. Elementy przesłane do tego parametru muszą mieć jedno z następujących rozszerzeń:<br /><br /> -   *. txt*: Określa rozszerzenie pliku tekstowego do przekonwertowania. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów.<br />-   *. resx*: Określa rozszerzenie pliku zasobów opartego na języku XML do przekonwertowania.<br />-   *. restext*: określa ten sam format jako *txt*. To inne rozszerzenie jest przydatne, jeśli chcesz wyraźnie odróżnić pliki źródłowe zawierające zasoby z innych plików źródłowych w procesie kompilacji.<br />-   *. resources*: Określa rozszerzenie pliku zasobu do przekonwertowania.|
|`StateFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa ścieżkę do opcjonalnego pliku pamięci podręcznej, który jest używany do przyspieszenia sprawdzania zależności linków w plikach wejściowych *. resx* .|
|`StronglyTypedClassName`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę klasy dla klasy zasobów o jednoznacznie określonym typie. Jeśli ten parametr nie jest określony, zostanie użyta nazwa podstawowa pliku zasobu.|
|`StronglyTypedFilename`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa nazwę pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy zostanie użyta jako podstawowa nazwa pliku z rozszerzeniem zależnym od języka. Na przykład: *MyClass.cs*.|
|`StronglyTypedLanguage`|Opcjonalny `String` parametr.<br /><br /> Określa język, który ma być używany podczas generowania źródła klasy dla zasobu silnie określonego typu. Ten parametr musi być zgodny z dokładnie jednym z języków używanych przez CodeDomProvider. Na przykład: `VB` lub `C#` .<br /><br /> Przekazując wartość do tego parametru, nakazujesz zadanie generowania zasobów o jednoznacznie określonym typie.|
|`StronglyTypedManifestPrefix`|Opcjonalny `String` parametr.<br /><br /> Określa przestrzeń nazw zasobów lub prefiks manifestu do użycia w wygenerowanym źródle klasy dla zasobu silnie określonego typu.|
|`StronglyTypedNamespace`|Opcjonalny `String` parametr.<br /><br /> Określa przestrzeń nazw, która ma być używana dla wygenerowanego źródła klasy dla zasobu silnie określonego typu. Jeśli ten parametr nie jest określony, wszystkie zasoby o jednoznacznie określonym typie znajdują się w globalnej przestrzeni nazw.|
|`TLogReadFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów reprezentujących dzienniki śledzenia odczytu.|
|`TLogWriteFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów reprezentujących dzienniki śledzenia zapisu.|
|`ToolArchitecture`|Opcjonalny <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Służy do określenia, czy *Tracker.exe* należy użyć do duplikowania *ResGen.exe*.<br /><br /> Powinien być możliwy do przeanalizowania dla elementu członkowskiego <xref:Microsoft.Build.Utilities.ExecutableType> wyliczenia. Jeśli `String.Empty` , używa algorytmu heurystycznego do określenia architektury domyślnej. Powinien być możliwy do przeanalizowania w składowej Microsoft.Build.Utilities.Exewyliczenia cutableType.|
|`TrackerFrameworkPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji .NET Framework zawierającej *FileTracker.dll*.<br /><br /> W przypadku ustawienia użytkownik jest odpowiedzialny za upewnienie się, że liczba bitów *FileTracker.dll* przekazana jest zgodna z bitową *ResGen.exe* , która ma być używana. Jeśli nie zostanie ustawiona, zadanie decyduje o odpowiedniej lokalizacji w oparciu o bieżącą wersję .NET Framework.|
|`TrackerLogDirectory`|Opcjonalny `String` parametr.<br /><br /> Określa katalog pośredni, w którym będą umieszczane dzienniki śledzenia z uruchamiania tego zadania.|
|`TrackerSdkPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji Windows SDK zawierającej *Tracker.exe*.<br /><br /> W przypadku ustawienia użytkownik jest odpowiedzialny za upewnienie się, że liczba bitów *Tracker.exe* przekazana jest zgodna z bitową *ResGen.exe* , która ma być używana. Jeśli nie zostanie ustawiona, zadanie decyduje o odpowiedniej lokalizacji na podstawie bieżącego Windows SDK.|
|`TrackFileAccess`|Opcjonalny <xref:System.Boolean> parametr.<br /><br /> W przypadku wartości true katalog pliku wejściowego jest używany do rozpoznawania względnych ścieżek plików.|
|`UseSourcePath`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , określa, że katalog pliku wejściowego ma być używany do rozpoznawania względnych ścieżek plików.|

## <a name="remarks"></a>Uwagi

Ponieważ pliki *resx* mogą zawierać linki do innych plików zasobów, nie wystarczy po prostu porównać sygnatury czasowe plików *resx* i *resources* , aby sprawdzić, czy dane wyjściowe są aktualne. Zamiast tego `GenerateResource` zadanie następuje po linków w plikach *resx* i sprawdza również sygnatury czasowe połączonych plików. Oznacza to, że nie należy generalnie używać `Inputs` i `Outputs` atrybutów w miejscu docelowym zawierającym `GenerateResource` zadanie, ponieważ może to spowodować, że zostanie pominięte, gdy powinien zostać rzeczywiście uruchomiony.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

W przypadku używania programu MSBuild 4,0 do celów projektów programu .NET 3,5 kompilacja może zakończyć się niepowodzeniem w zasobach x86. Aby obejść ten problem, można utworzyć obiekt docelowy jako zestaw AnyCPU.

## <a name="example"></a>Przykład

Poniższy przykład używa `GenerateResource` zadania do generowania plików *resources* z plików określonych przez `Resx` kolekcję elementów.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

`GenerateResource`Zadanie używa \<LogicalName> metadanych \<EmbeddedResource> elementu, aby nazwać zasób osadzony w zestawie.

Przy założeniu, że zestaw nosi nazwę, poniższy kod generuje osadzony zasób o nazwie *someQualifier. someResource. resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez \<LogicalName> metadanych zasób zostałby nazwany *. WebResource. resources*.  Ten przykład dotyczy tylko procesu kompilacji Visual Basic i Visual C#.

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

---
title: GenerateResource — zadanie | Microsoft Docs
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
ms.openlocfilehash: c0e83cc04b309a940f5aa4c5a36099f10afddcc3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594803"
---
# <a name="generateresource-task"></a>GenerateResource — zadanie
Konwertuje pliki *. txt* i *. resx* (format zasobów opartych na języku XML) i *pliki binarne środowiska* uruchomieniowego języka wspólnego, które mogą być osadzone w binarnym pliku wykonywalnym środowiska uruchomieniowego lub skompilowane w zestawach satelickich. To zadanie jest zwykle używane do konwertowania plików *txt* lub *resx* na pliki *resources* . Zadanie `GenerateResource` działa podobnie jak [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator).

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `GenerateResource`.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalInputs`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Zawiera dodatkowe dane wejściowe do sprawdzania zależności wykonane przez to zadanie. Na przykład pliki projektu i elementów docelowych zazwyczaj powinny być danymi wejściowymi, aby w przypadku ich aktualizacji wszystkie zasoby zostały ponownie wygenerowane.|
|`EnvironmentVariables`|Opcjonalny parametr `String[]`.<br /><br /> Określa tablicę par nazwa-wartość zmiennych środowiskowych, które powinny być przesyłane do *Resgen. exe*, oprócz (lub selektywnego przesłaniania) zwykłego bloku środowiska.|
|`ExcludedInputPaths`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa tablicę elementów, które określają ścieżki, z których śledzone dane wejściowe zostaną zignorowane podczas sprawdzania.|
|`ExecuteAsTool`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program uruchamia *Tlbimp. exe* i *Aximp. exe* z odpowiednich platform docelowych w celu wygenerowania niezbędnych zestawów otoki. Ten parametr umożliwia wiele elementów docelowych `ResolveComReferences`.|
|`FilesWritten`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera nazwy wszystkich plików, które są zapisywane na dysku. Obejmuje to plik pamięci podręcznej, jeśli istnieje. Ten parametr jest przydatny w przypadku implementacji czystego.|
|`MinimalRebuildFromTracking`|Opcjonalny parametr `Boolean`.<br /><br /> Pobiera lub ustawia przełącznik określający, czy zostanie użyta śledzona kompilacja przyrostowa. Jeśli `true`, kompilacja przyrostowa jest włączona; w przeciwnym razie zostanie wymuszone ponowne kompilowanie.|
|`NeverLockTypeAssemblies`|Opcjonalny parametr `Boolean`.<br /><br /> Pobiera lub ustawia wartość logiczną określającą, czy należy utworzyć nową [domenę aplikacji](/dotnet/api/system.appdomain) , aby oszacować pliki zasobów ( *. resx*) (true) lub utworzyć nową [domenę aplikacji](/dotnet/api/system.appdomain) tylko wtedy, gdy pliki zasobów odwołują się do zestawu użytkownika (false).|
|`OutputResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa nazwę wygenerowanych plików, takich jak pliki *resources* . Jeśli nazwa nie zostanie określona, zostanie użyta nazwa pasującego pliku wejściowego, a utworzony plik *resources* zostanie umieszczony w katalogu zawierającym plik wejściowy.|
|`PublicClass`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program tworzy klasę zasobów o jednoznacznie określonym typie jako klasę publiczną.|
|`References`|Opcjonalny parametr `String[]`.<br /><br /> Odwołania do typów ładowania w plikach *resx* z. elementy danych pliku *resx* mogą mieć typ .NET. Po odczytaniu pliku *resx* należy rozwiązać ten problem. Zwykle jest ona rozwiązywana pomyślnie przy użyciu standardowych reguł ładowania typów. Jeśli postanowisz zestawy w `References`, mają pierwszeństwo.<br /><br /> Ten parametr nie jest wymagany w przypadku zasobów o jednoznacznie określonym typie.|
|`SdkToolsPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak *Resgen. exe*.|
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do przekonwertowania. Elementy przesłane do tego parametru muszą mieć jedno z następujących rozszerzeń:<br /><br /> -    *. txt*: Określa rozszerzenie pliku tekstowego do przekonwertowania. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów.<br />-    *. resx*: Określa rozszerzenie pliku zasobów opartego na języku XML do przekonwertowania.<br />-    *. restext*: określa ten sam format jako *txt*. To inne rozszerzenie jest przydatne, jeśli chcesz wyraźnie odróżnić pliki źródłowe zawierające zasoby z innych plików źródłowych w procesie kompilacji.<br />-    *. resources*: Określa rozszerzenie pliku zasobu do przekonwertowania.|
|`StateFile`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa ścieżkę do opcjonalnego pliku pamięci podręcznej, który jest używany do przyspieszenia sprawdzania zależności linków w plikach wejściowych *. resx* .|
|`StronglyTypedClassName`|Opcjonalny parametr `String`.<br /><br /> Określa nazwę klasy dla klasy zasobów o jednoznacznie określonym typie. Jeśli ten parametr nie jest określony, zostanie użyta nazwa podstawowa pliku zasobu.|
|`StronglyTypedFilename`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa nazwę pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy zostanie użyta jako podstawowa nazwa pliku z rozszerzeniem zależnym od języka. Na przykład: *MyClass.cs*.|
|`StronglyTypedLanguage`|Opcjonalny parametr `String`.<br /><br /> Określa język, który ma być używany podczas generowania źródła klasy dla zasobu silnie określonego typu. Ten parametr musi być zgodny z dokładnie jednym z języków używanych przez CodeDomProvider. Na przykład: `VB` lub `C#`.<br /><br /> Przekazując wartość do tego parametru, nakazujesz zadanie generowania zasobów o jednoznacznie określonym typie.|
|`StronglyTypedManifestPrefix`|Opcjonalny parametr `String`.<br /><br /> Określa przestrzeń nazw zasobów lub prefiks manifestu do użycia w wygenerowanym źródle klasy dla zasobu silnie określonego typu.|
|`StronglyTypedNamespace`|Opcjonalny parametr `String`.<br /><br /> Określa przestrzeń nazw, która ma być używana dla wygenerowanego źródła klasy dla zasobu silnie określonego typu. Jeśli ten parametr nie jest określony, wszystkie zasoby o jednoznacznie określonym typie znajdują się w globalnej przestrzeni nazw.|
|`TLogReadFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów reprezentujących dzienniki śledzenia odczytu.|
|`TLogWriteFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr tylko do odczytu.<br /><br /> Pobiera tablicę elementów reprezentujących dzienniki śledzenia zapisu.|
|`ToolArchitecture`|Opcjonalny parametr <xref:System.String?displayProperty=fullName>.<br /><br /> Służy do określenia, czy *plik śledzący. exe* ma być używany do duplikowania *Resgen. exe*.<br /><br /> Powinien być możliwy do przeanalizowania dla elementu członkowskiego wyliczenia <xref:Microsoft.Build.Utilities.ExecutableType>. Jeśli `String.Empty`, używa algorytmu heurystycznego do określenia architektury domyślnej. Powinien być możliwy do przeanalizowania dla elementu członkowskiego wyliczenia Microsoft. Build. Utilities. ExecutableType.|
|`TrackerFrameworkPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji .NET Framework, która zawiera *FileTracker. dll*.<br /><br /> Jeśli ta wartość jest ustawiona, użytkownik jest odpowiedzialny za upewnienie się, że liczba bitów *FileTracker. dll* , które są przekazywane, jest zgodna z bitową *Resgen. exe* , której zamierza użyć. Jeśli nie zostanie ustawiona, zadanie decyduje o odpowiedniej lokalizacji w oparciu o bieżącą wersję .NET Framework.|
|`TrackerLogDirectory`|Opcjonalny parametr `String`.<br /><br /> Określa katalog pośredni, w którym będą umieszczane dzienniki śledzenia z uruchamiania tego zadania.|
|`TrackerSdkPath`|Opcjonalny parametr `String`.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji Windows SDK, która zawiera *plik śledzący. exe*.<br /><br /> Jeśli ta wartość jest ustawiona, użytkownik jest odpowiedzialny za upewnienie się, że liczba bitów w pliku *śledzenia. exe* jest zgodna z bitową *Resgen. exe* , której zamierza użyć. Jeśli nie zostanie ustawiona, zadanie decyduje o odpowiedniej lokalizacji na podstawie bieżącego Windows SDK.|
|`TrackFileAccess`|Opcjonalny parametr <xref:System.Boolean>.<br /><br /> W przypadku wartości true katalog pliku wejściowego jest używany do rozpoznawania względnych ścieżek plików.|
|`UseSourcePath`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określa, że katalog pliku wejściowego ma być używany do rozpoznawania względnych ścieżek plików.|

## <a name="remarks"></a>Uwagi
Ponieważ pliki *resx* mogą zawierać linki do innych plików zasobów, nie wystarczy po prostu porównać sygnatury czasowe plików *resx* i *resources* , aby sprawdzić, czy dane wyjściowe są aktualne. Zamiast tego zadanie `GenerateResource` wykonuje poniższe linki w plikach *resx* i sprawdza również sygnatury czasowe połączonych plików. Oznacza to, że nie należy zasadniczo używać atrybutów `Inputs` i `Outputs` w elemencie docelowym zawierającym zadanie `GenerateResource`, ponieważ może to spowodować, że zostanie pominięte, gdy powinien zostać rzeczywiście uruchomiony.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

W przypadku używania programu MSBuild 4,0 do celów projektów programu .NET 3,5 kompilacja może zakończyć się niepowodzeniem w zasobach x86. Aby obejść ten problem, można utworzyć obiekt docelowy jako zestaw AnyCPU.

## <a name="example"></a>Przykład
Poniższy przykład używa zadania `GenerateResource` do generowania plików *resources* z plików określonych przez kolekcję `Resx` Item.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Zadanie `GenerateResource` używa \<logicznej > metadanych elementu \<EmbeddedResource >, aby nazwać zasób osadzony w zestawie.

Przy założeniu, że zestaw nosi nazwę, poniższy kod generuje osadzony zasób o nazwie *someQualifier. someResource. resources*:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Bez metadanych \<LogicalName >, zasób zostałby nazwany *. WebResource. resources*.  Ten przykład ma zastosowanie tylko do Visual Basic i procesu C# kompilacji wizualnej.

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

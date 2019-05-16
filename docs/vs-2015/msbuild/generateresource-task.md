---
title: Generateresource — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 712d0de957ff7f780567c927fb1b18b100f8f6ca
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703519"
---
# <a name="generateresource-task"></a>GenerateResource — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wykonuje konwersję między txt i pliki resx (w formacie zasobów opartych na języku XML) i common language runtime binarnych plików Resources, które mogą być osadzone w wykonywalnym pliku danych binarnych środowiska uruchomieniowego lub skompilowane do zestawów satelickich. To zadanie jest zazwyczaj używany w konwersji plików txt lub resx na pliki .resource. `GenerateResource` Zadanie jest podobne do [resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateResource` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalInputs`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Zawiera dodatkowe dane wejściowe, aby sprawdzanie zależności wykonywane przez to zadanie. Na przykład pliki projektu i obiektów docelowych zwykle należy danych wejściowych, więc, że jeśli są one aktualizowane wszystkie zasoby są generowane.|  
|`EnvironmentVariables`|Opcjonalnie `String[]` parametru.<br /><br /> Określa tablicę par nazwa wartość w środowisku zmiennych, które powinny być przekazywane do zduplikowanych resgen.exe, oprócz (lub selektywnie zastępowanie) blok regularnych środowiska.|  
|`ExcludedInputPaths`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa tablicę elementów, które określają ścieżek, z których śledzone dane wejściowe zostaną zignorowane podczas sprawdzania na bieżąco.|  
|`ExecuteAsTool`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uruchamia tlbimp.exe i aximp.exe z odpowiedniego obiektu docelowego framework-procesem do generowania zestawów niezbędne otoki. Ten parametr umożliwia wielowersyjności kodu programu `ResolveComReferences`.|  
|`FilesWritten`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera nazwy wszystkie pliki zapisane na dysku. Obejmuje to plik pamięci podręcznej, jeśli istnieje. Ten parametr jest przydatne w przypadku implementacji czysty.|  
|`MinimalRebuildFromTracking`|Opcjonalnie `Boolean` parametru.<br /><br /> Pobiera lub ustawia przełącznik, który określa, czy będzie używana śledzonych kompilacji przyrostowej. Jeśli `true`, kompilacja przyrostowa jest włączone; w przeciwnym razie zostanie wymuszone ponownej kompilacji.|  
|`NeverLockTypeAssemblies`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa nazwę wygenerowanego plików, na przykład plików Resources. Jeśli nie określisz nazwy, używana jest nazwa odpowiedniego pliku wejściowego i plik Resources, który jest tworzony jest umieszczany w katalogu, który zawiera plik wejściowy.|  
|`OutputResources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa nazwę wygenerowanego plików, na przykład plików Resources. Jeśli nie określisz nazwy, używana jest nazwa odpowiedniego pliku wejściowego i plik Resources, który jest tworzony jest umieszczany w katalogu, który zawiera plik wejściowy.|  
|`PublicClass`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy silnie typizowanej klasy zasobów jako klasę publiczną.|  
|`References`|Opcjonalnie `String[]` parametru.<br /><br /> Odwołania można załadować typów w plikach resx z. Elementy danych pliku ResX może mieć typ architektury .NET. Podczas odczytywania pliku ResX to muszą zostać rozwiązane. Zwykle rozwiązania problemu pomyślnie za pomocą standardowej, trwa ładowanie reguł. Jeśli podasz zestawów w `References`, ich wyższy priorytet.<br /><br /> Ten parametr nie jest wymagane dla silnie typizowanych zasobów.|  
|`SdkToolsPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy do przekonwertowania. Pozycji przekazanych do tego parametru musi mieć jedną z następujących rozszerzeń pliku:<br /><br /> -   `.txt`: Określa rozszerzenie pliku tekstowego do przekonwertowania. Pliki tekstowe mogą zawierać tylko zasoby w postaci ciągów.<br />-   `.resx`: Określa rozszerzenie pliku zasobów w formacie XML do konwersji.<br />-   `.restext`: Określa ten sam format jak txt. To rozszerzenie innej jest przydatne, jeśli chcesz wyraźnie odróżnić pliki źródłowe, zawierające zasoby z innych plikach źródłowych w procesie kompilacji.<br />-   `.resources`: Określa rozszerzenie pliku zasobu do konwersji.|  
|`StateFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa ścieżkę do pliku opcjonalne pamięci podręcznej, który jest używany w celu przyspieszenia sprawdzania łączy w danych wejściowych plików resx zależności.|  
|`StronglyTypedClassName`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę klasy dla silnie typizowanej klasy zasobów. Jeśli ten parametr nie jest określony, używany jest podstawowej nazwy pliku zasobów.|  
|`StronglyTypedFilename`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku dla pliku źródłowego. Jeśli ten parametr nie jest określony, nazwa klasy jest używany jako podstawowej nazwy pliku z rozszerzeniem zależne od języka. Na przykład: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Opcjonalnie `String` parametru.<br /><br /> Określa język do użycia podczas generowania klasy źródło silnie typizowanych zasobów. Ten parametr musi być zgodna dokładnie jeden z języków używany przez element CodeDomProvider. Na przykład: `VB` lub `C#`.<br /><br /> Przez przekazanie wartości do tego parametru, możesz poinstruować zadania, aby wygenerować silnie typizowanych zasobów.|  
|`StronglyTypedManifestPrefix`|Opcjonalnie `String` parametru.<br /><br /> Określa prefiks przestrzeni nazw lub manifest zasobu, do użytku w źródle wygenerowanej klasy silnie typizowanych zasobów.|  
|`StronglyTypedNamespace`|Opcjonalnie `String` parametru.<br /><br /> Określa przestrzeń nazw dla generowanej klasy źródło silnie typizowanych zasobów. Jeśli ten parametr nie jest określony, wszystkie zasoby silnie typizowane znajdują się w globalnej przestrzeni nazw.|  
|`TLogReadFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują odczytu dzienniki śledzenia.|  
|`TLogWriteFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru tylko do odczytu.<br /><br /> Pobiera tablicę elementów, które reprezentują zapisu dzienniki śledzenia.|  
|`ToolArchitecture`|(Opcjonalne [String]<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> Używany do określenia, czy Tracker.exe musi zostać użyte zduplikować ResGen.exe.<br /><br /> Powinien być przeanalizowania do elementu członkowskiego <xref:Microsoft.Build.Utilities.ExecutableType> wyliczenia. Jeśli `String.Empty`, używa heurystyki do określenia architektura domyślne. Powinien być przeanalizowania do elementu członkowskiego wyliczenia Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametr.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji środowiska .NET Framework, który zawiera FileTracker.dll.<br /><br /> Jeśli zestaw, użytkownik przyjmuje odpowiedzialność za zapewnienie, że wartości bitowości FileTracker.dll, który przekazują dopasowuje wartości bitowości programu ResGen.exe, które będą one używane. W przeciwnym razie zestawu, zadanie decyduje, odpowiednią lokalizację, w oparciu o bieżącą wersję systemu .NET Framework.|  
|`TrackerLogDirectory`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametr.<br /><br /> Określa katalog pośredni, w którym zostaną umieszczone dzienniki śledzenia uruchamianie tego zadania.|  
|`TrackerSdkPath`|Optional <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametr.<br /><br /> Określa ścieżkę do odpowiedniej lokalizacji zestawu Windows SDK, który zawiera Tracker.exe.<br /><br /> Jeśli zestaw, użytkownik przyjmuje odpowiedzialność za zapewnienie, że wartości bitowości Tracker.exe który przekazują dopasowuje wartości bitowości programu ResGen.exe, które będą one używane. W przeciwnym razie zestawu, zadanie decyduje, odpowiednią lokalizację, w oparciu o bieżący zestaw Windows SDK.|  
|`TrackFileAccess`|(Opcjonalnie) [logiczną]<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> W przypadku opcji true rozpoznawania względnych ścieżek plików jest używany katalog pliku wejściowego.|  
|`UseSourcePath`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że katalog pliku wejściowego ma być używany do rozpoznawania względnych ścieżek plików.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ pliki resx może zawierać łącza do innych plików zasobów, nie jest wystarczające, aby po prostu porównania .resx oraz .resource sygnatury czasowe pliku, aby sprawdzić, czy dane wyjściowe są aktualne. Zamiast tego `GenerateResource` zadanie śledzi linki w plikach resx i sprawdza, czy znacznikami czasu plików połączonych. Oznacza to, że nie należy generalnie używać `Inputs` i `Outputs` atrybutów na docelowym zawierający `GenerateResource` zadania, ponieważ może to doprowadzić do pominięcia podczas faktycznie należy uruchomić.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
 Przy użyciu programu MSBuild 4.0 projektów docelowych .NET 3.5, kompilacja może zakończyć się niepowodzeniem na x86 zasobów. Aby obejść ten problem, możesz utworzyć element docelowy jako zestawu AnyCPU.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GenerateResource` zadania, aby wygenerować plików Resources z plików określone przez `Resx` elementu kolekcji.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` Zadanie używa \<LogicalName > Metadane \<EmbeddedResource > element, aby nazwa zasobu, który jest osadzony w zestawie.  
  
 Przy założeniu, że zestaw jest o nazwie myAssembly, poniższy kod generuje osadzony zasób o nazwie someQualifier.someResource.resources:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Bez \<LogicalName > metadane, zasobu będą miały postać myAssembly.myResource.resources.  Ten przykład dotyczy tylko dla procesu kompilacji w Visual Basic i Visual C#.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

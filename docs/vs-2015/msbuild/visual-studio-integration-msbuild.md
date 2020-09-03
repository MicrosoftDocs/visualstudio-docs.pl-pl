---
title: Integracja z programem Visual Studio (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c90019aa24047524005ba70aa4f1aec75f89c71d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825422"
---
# <a name="visual-studio-integration-msbuild"></a>Integracja z programem Visual Studio (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hosty programu Visual Studio [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do ładowania i kompilowania projektów zarządzanych. Ponieważ [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] jest odpowiedzialny za projekt, prawie każdy projekt w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formacie może być pomyślnie używany w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , nawet jeśli projekt został utworzony przez inne narzędzie i ma dostosowany proces kompilacji.  
  
 W tym temacie opisano konkretne aspekty [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] hostingu, które należy wziąć pod uwagę podczas dostosowywania projektów i plików docelowych, które chcesz załadować i skompilować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Dzięki temu można upewnić się, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funkcje, takie jak IntelliSense i debugowanie, są wykonywane w projekcie niestandardowym.  
  
 Aby uzyskać informacje na temat projektów C++, zobacz [pliki projektu](/cpp/build/reference/project-files).  
  
## <a name="project-file-name-extensions"></a>Rozszerzenia nazwy pliku projektu  
 MSBuild.exe rozpoznaje wszystkie rozszerzenia nazw plików projektu pasujące do wzorca. * proj. Jednak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoznaje tylko podzestaw tych rozszerzeń nazw plików projektu, które określają system projektu specyficzny dla języka, który załaduje projekt. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie ma [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] systemu projektu opartego na języku neutralnym.  
  
 Na przykład [!INCLUDE[csprcs](../includes/csprcs-md.md)] system projektu ładuje pliki csproj, ale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie może załadować pliku. xxproj. Plik projektu dla plików źródłowych w dowolnym języku musi używać tego samego rozszerzenia co [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../includes/csprcs-md.md)] plików projektu do załadowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="well-known-target-names"></a>Dobrze znane nazwy elementów docelowych  
 Kliknięcie polecenia **Build** w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spowoduje wykonanie domyślnego obiektu docelowego w projekcie. Często ta lokalizacja docelowa jest również nazywana `Build` . Wybranie polecenia **Kompiluj ponownie** lub **Wyczyść** spowoduje podjęcie próby wykonania obiektu docelowego o tej samej nazwie w projekcie. Kliknięcie przycisku **Publikuj** spowoduje wykonanie elementu docelowego o nazwie `PublishOnly` w projekcie.  
  
## <a name="configurations-and-platforms"></a>Konfiguracje i platformy  
 Konfiguracje są reprezentowane w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektach według właściwości pogrupowanych w `PropertyGroup` elemencie, który zawiera `Condition` atrybut. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sprawdzają te warunki, aby utworzyć listę konfiguracji projektu i platform do wyświetlenia. Aby pomyślnie wyodrębnić tę listę, warunki muszą mieć format podobny do następującego:  
  
```  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w tym celu przeszukiwane są warunki `PropertyGroup` , `ItemGroup` , `Import` , właściwości i elementy.  
  
## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pozwala zmienić nazwę typu elementu w projekcie za pomocą właściwości **Akcja kompilacji** okna [właściwości pliku](https://msdn.microsoft.com/013c4aed-08d6-4dce-a124-ca807ca08959) . `Compile``EmbeddedResource` `Content` nazwy typu elementu,,, i `None` są zawsze wyświetlane w tym menu, wraz z innymi nazwami typów elementów, które znajdują się już w projekcie. Aby zapewnić, że wszystkie nazwy typów elementów niestandardowych są zawsze dostępne w tym menu, można dodać nazwy do typu elementu o nazwie `AvailableItemName` . Na przykład dodanie następującego elementu do pliku projektu spowoduje dodanie do tego menu niestandardowego typu `JScript` dla wszystkich projektów, które go zaimportują:  
  
```  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
> Niektóre nazwy typów elementów są specyficzne dla, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ale nie są wymienione na liście rozwijanej.  
  
## <a name="in-process-compilers"></a>Kompilatory wewnątrz–procesowe  
 Gdy jest to możliwe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program podejmie próbę użycia w procesie wersji [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilatora w celu zwiększenia wydajności. (Nie dotyczy [!INCLUDE[csprcs](../includes/csprcs-md.md)] ) Aby to działanie działało prawidłowo, muszą zostać spełnione następujące warunki:  
  
- W obiekcie docelowym projektu musi istnieć zadanie o nazwie `Vbc` dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektów.  
  
- `UseHostCompilerIfAvailable`Parametr zadania musi być ustawiony na wartość true.  
  
## <a name="design-time-intellisense"></a>Technologia IntelliSense — czas projektowania  
 Aby uzyskać pomoc techniczną IntelliSense w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , zanim kompilacja wygenerowała zestaw danych wyjściowych, muszą zostać spełnione następujące warunki:  
  
- Musi istnieć obiekt docelowy o nazwie `Compile` .  
  
- `Compile`Element docelowy lub jedna z jego zależności musi wywoływać zadanie kompilatora dla projektu, takie jak `Csc` lub `Vbc` .  
  
- `Compile`Element docelowy lub jedna z jego zależności musi spowodować, że kompilator otrzyma wszystkie niezbędne parametry dla IntelliSense, szczególnie wszystkie odwołania.  
  
- Warunki wymienione w sekcji "kompilatory w procesie" muszą być spełnione.  
  
## <a name="building-solutions"></a>Tworzenie rozwiązań  
 W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , plik rozwiązania i kolejność kompilacji projektu są kontrolowane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] siebie. Podczas kompilowania rozwiązania z msbuild.exe w wierszu polecenia [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] analizuje plik rozwiązania i porządkuje kompilacje projektu. W obu przypadkach projekty są kompilowane indywidualnie w kolejności zależności, a odwołania projektu do projektu nie są przenoszone. Natomiast w przypadku kompilowania poszczególnych projektów przy użyciu msbuild.exe są przenoszone odwołania projektu do projektu.  
  
 Podczas kompilowania wewnątrz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Właściwość `$(BuildingInsideVisualStudio)` jest ustawiana na `true` . Ta wartość może być używana w projekcie lub plików targets, aby spowodować, że kompilacja zadziała inaczej.  
  
## <a name="displaying-properties-and-items"></a>Wyświetlanie właściwości i elementów  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoznaje pewne nazwy i wartości właściwości. Na przykład następująca właściwość w projekcie spowoduje, że **aplikacja systemu Windows** będzie wyświetlana w polu **Typ aplikacji** w **projektancie projektu**.  
  
```  
<OutputType>WinExe</OutputType>  
```  
  
 Wartość właściwości można edytować w **projektancie projektu** i zapisać w pliku projektu. Jeśli taka właściwość ma nieprawidłową wartość przez ręczną edycję, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program wyświetli ostrzeżenie podczas ładowania projektu i zastąpi nieprawidłową wartość wartością domyślną.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozumie wartości domyślne dla niektórych właściwości. Te właściwości nie zostaną utrwalone w pliku projektu, chyba że mają wartości inne niż domyślne.  
  
 Właściwości z dowolnymi nazwami nie są wyświetlane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby zmodyfikować dowolne właściwości w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , należy otworzyć plik projektu w edytorze XML i ręcznie go edytować. Aby uzyskać więcej informacji, zobacz sekcję [Edytowanie plików projektu w programie Visual Studio](#BKMK_EditingProjects) w dalszej części tego tematu.  
  
 Elementy zdefiniowane w projekcie z dowolnymi nazwami typów elementów są domyślnie wyświetlane w Eksplorator rozwiązań w węźle projektu. Aby ukryć element z ekranu, ustaw `Visible` metadane na `false` . Na przykład następujący element będzie uczestniczyć w procesie kompilacji, ale nie będzie wyświetlany w Eksplorator rozwiązań.  
  
```  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Elementy zadeklarowane w plikach zaimportowanych do projektu nie są wyświetlane domyślnie. Elementy utworzone w procesie kompilacji nigdy nie są wyświetlane w Eksplorator rozwiązań.  
  
## <a name="conditions-on-items-and-properties"></a>Postanowienia dot. elementów i właściwości  
 W trakcie kompilacji wszystkie warunki są w pełni przestrzegane.  
  
 Podczas określania wartości właściwości do wyświetlenia, właściwości, które [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uważają, że zależy od konfiguracji, są oceniane inaczej niż właściwości, które traktują niezależną konfigurację. Dla właściwości, które uzna za zależne od konfiguracji, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ustawia `Configuration` `Platform` odpowiednio właściwości i i instruuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] o ponownej ocenie projektu. Dla właściwości, które uzna za niezależne od konfiguracji, nie określono, jak zostaną ocenione warunki.  
  
 Wyrażenia warunkowe dla elementów są zawsze ignorowane na potrzeby decydowania, czy element powinien być wyświetlany w Eksplorator rozwiązań.  
  
## <a name="debugging"></a>Debugowanie  
 W celu znalezienia i uruchomienia zestawu wyjściowego i dołączenia debugera [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wymagane są właściwości `OutputPath` , `AssemblyName` i `OutputType` prawidłowo zdefiniowane. Debuger nie zostanie dołączony, jeśli proces kompilacji nie spowodował, że kompilator wygenerował plik. pdb.  
  
## <a name="design-time-target-execution"></a>Wykonanie docelowego czasu projektowania  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] próbuje wykonać obiekty docelowe o określonych nazwach podczas ładowania projektu. Te elementy docelowe obejmują,,, `Compile` `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` i `CopyRunEnvironmentFiles` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamia te elementy docelowe, aby można było zainicjować kompilator w celu udostępnienia funkcji IntelliSense, debuger może być zainicjowany i można rozpoznać odwołania wyświetlane w Eksplorator rozwiązań. Jeśli te elementy docelowe nie są obecne, projekt zostanie załadowany i skompilowany prawidłowo, ale środowisko czasu projektowania w programie nie będzie w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pełni funkcjonalne.  
  
## <a name="editing-project-files-in-visual-studio"></a><a name="BKMK_EditingProjects"></a> Edytowanie plików projektu w programie Visual Studio  
 Aby edytować [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekt bezpośrednio, można otworzyć plik projektu w edytorze XML programu Visual Studio.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Zwolnij projekt**.  
  
     Projekt jest oznaczony **(niedostępny)**.  
  
2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz polecenie **Edytuj \<Project File> **.  
  
     Plik projektu zostanie otwarty w edytorze XML programu Visual Studio.  
  
3. Edytuj, Zapisz, a następnie zamknij plik projektu.  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz polecenie **Załaduj ponownie projekt**.  
  
## <a name="intellisense-and-validation"></a>Technologia IntelliSense i walidacja  
 W przypadku edytowania plików projektu przy użyciu edytora XML technologia IntelliSense i walidacja są sterowane przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliki schematów. Są one instalowane w pamięci podręcznej schematów, które można znaleźć w *\<Visual Studio installation directory>* \Xml\Schemas\1033\MSBuild.  
  
 Typy podstawowe [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] są zdefiniowane w Microsoft. Build. Core. xsd i wspólnych typach używanych przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są zdefiniowane w Microsoft. Build. CommonTypes. xsd. Aby dostosować schematy w taki sposób, aby była dostępna funkcja IntelliSense i sprawdzanie poprawności dla niestandardowych typów elementów, właściwości i zadań, można edytować Microsoft. Build. xsd lub utworzyć własny schemat zawierający schematy CommonTypes lub Core. Jeśli utworzysz własny schemat, musisz skierować Edytor XML, aby znaleźć go przy użyciu okna **Właściwości** .  
  
## <a name="editing-loaded-project-files"></a>Edytowanie wczytanych plików projektu  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] buforuje zawartość plików projektu i plików zaimportowanych przez pliki projektu. Jeśli edytujesz załadowany plik projektu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program automatycznie wyświetli monit o ponowne załadowanie projektu, aby zmiany zaczęły obowiązywać. Jednak Jeśli edytujesz plik zaimportowany przez załadowany projekt, nie zostanie wyświetlony monit o ponowne załadowanie i musisz ręcznie zwolnić i załadować projekt, aby zmiany zaczęły obowiązywać.  
  
## <a name="output-groups"></a>Grupy danych wyjściowych  
 Kilka elementów docelowych zdefiniowanych w Microsoft. Common. targets ma nazwy kończące się na `OutputGroups` lub `OutputGroupDependencies` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wywołuje te elementy docelowe w celu pobrania określonych list danych wyjściowych projektu. Na przykład `SatelliteDllsProjectOutputGroup` obiekt docelowy tworzy listę wszystkich zestawów satelickich, które utworzy kompilacja. Te grupy wyjściowe są używane przez funkcje, takie jak publikowanie, wdrażanie i projekt do odwołań projektu. Projekty, które nie definiują ich, będą ładowane i kompilowane w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale niektóre funkcje mogą nie funkcjonować prawidłowo.  
  
## <a name="reference-resolution"></a>Rozpoznawanie odwołania  
 Rozpoznawanie odwołań to proces używania elementów odwołania przechowywanych w pliku projektu do lokalizowania rzeczywistych zestawów. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aby można było wyświetlić szczegółowe właściwości każdego odwołania w oknie **Właściwości** , należy wyzwolić rozwiązanie referencyjne. Na poniższej liście opisano trzy typy odwołań oraz sposób ich rozwiązywania.  
  
- Odwołania do zestawu:  
  
  System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveAssemblyReferences` . Ten element docelowy powinien generować elementy o nazwie typu elementu `ReferencePath` . Każdy z tych elementów powinien mieć specyfikację elementu (wartość `Include` atrybutu elementu) zawierającą pełną ścieżkę do odwołania. Elementy powinny mieć wszystkie metadane z elementów wejściowych przenoszone wraz z następującymi nowymi metadanymi:  

  - `CopyLocal`, wskazując, czy zestaw powinien być skopiowany do folderu wyjściowego, ustaw na wartość true lub false.  

  - `OriginalItemSpec`, zawierający specyfikację oryginalnego elementu odwołania.  

  - `ResolvedFrom`Ustaw na wartość "{TargetFrameworkDirectory}", jeśli został on rozwiązany z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] katalogu.  
  
- Odwołania COM:  
  
     System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveCOMReferences` . Ten element docelowy powinien generować elementy o nazwie typu elementu `ComReferenceWrappers` . Każdy z tych elementów powinien mieć specyfikację elementu zawierającą pełną ścieżkę do zestawu międzyoperacyjnego dla odwołania COM. Elementy powinny mieć wszystkie metadane z elementów wejściowych przeprowadzonych przez program, oprócz nowych metadanych o nazwie `CopyLocal` , wskazujących, czy zestaw powinien być skopiowany do folderu wyjściowego, ustawić na wartość true lub false.  
  
- Odwołania natywne  
  
     System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveNativeReferences` . Ten element docelowy powinien generować elementy o nazwie typu elementu `NativeReferenceFile` . Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazaną przez program, a także do nowego fragmentu metadanych o nazwie `OriginalItemSpec` , zawierających pierwotną specyfikację elementu odwołania.  
  
## <a name="performance-shortcuts"></a>Skróty wydajności  
 Jeśli zaczniesz debugowanie w interfejsie użytkownika programu Visual Studio (wybierając klawisz F5 lub wybierając **Debuguj**, **Rozpocznij debugowanie** na pasku menu), proces kompilacji używa szybkiej kontroli aktualizacji w celu zwiększenia wydajności. W niektórych przypadkach, gdy niestandardowe kompilacje tworzą pliki, które są zbudowane z kolei, sprawdzanie szybkiej aktualizacji nie identyfikuje poprawnie zmienionych plików. Projekty wymagające dokładniejszych testów aktualizacji mogą wyłączyć szybkie sprawdzanie przez ustawienie zmiennej środowiskowej `DISABLEFASTUPTODATECHECK=1` . Alternatywnie projekty można ustawić jako właściwość programu MSBuild w projekcie lub w pliku importowanym przez projekt.  
  
 W przypadku regularnych kompilacji w programie Visual Studio sprawdzanie szybkiej aktualizacji nie ma zastosowania, a projekt zostanie skompilowany jako jeśli wywołano kompilację w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: zwiększanie procesu kompilacji programu Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Uruchamianie kompilacji z poziomu środowiska IDE](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Rejestrowanie rozszerzeń .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Item — element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property — element (MSBuild)](../msbuild/property-element-msbuild.md)   
 [Target — element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [VBC, zadanie](../msbuild/vbc-task.md)

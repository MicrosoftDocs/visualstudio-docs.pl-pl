---
title: Zadanie MSBuild | Dokumenty firmy Microsoft
ms.date: 07/30/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a312bfe8c88b0ac523666779970cc28e3a7c798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633177"
---
# <a name="msbuild-task"></a>zadanie MSBuild

Tworzy projekty MSBuild z innego projektu MSBuild.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `MSBuild` opisano parametry zadania.

| Parametr | Opis |
|-----------------------------------| - |
| `BuildInParallel` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`projekty określone w `Projects` parametrze są budowane równolegle, jeśli jest to możliwe. Wartość domyślna to `false`. |
| `Projects` | Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki projektu do utworzenia. |
| `Properties` | Parametr `String` opcjonalny.<br /><br /> Lista rozdzielanych średnikami par nazw/wartości właściwości do zastosowania jako właściwości globalnych do projektu podrzędnego. Po określeniu tego parametru jest funkcjonalnie równoważne ustawienie właściwości, które mają przełącznik **-property** podczas tworzenia z [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Przykład:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Po przełączeniu właściwości do projektu `Properties` za pośrednictwem parametru, MSBuild może utworzyć nowe wystąpienie projektu, nawet jeśli plik projektu został już załadowany. MSBuild tworzy pojedyncze wystąpienie projektu dla danej ścieżki projektu i unikatowy zestaw właściwości globalnych. Na przykład to zachowanie umożliwia tworzenie wielu zadań MSBuild, które wywołują *myproject.proj,* z Configuration=Release i otrzymujesz pojedyncze wystąpienie *myproject.proj* (jeśli w zadaniu nie określono żadnych unikatowych właściwości). Jeśli określisz właściwość, która nie została jeszcze widoczna przez MSBuild, MSBuild tworzy nowe wystąpienie projektu, które można sbudować równolegle do innych wystąpień projektu. Na przykład release konfiguracji można tworzyć w tym samym czasie co konfiguracji debugowania.|
| `RebaseOutputs` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`ścieżki względne docelowych elementów wyjściowych z projektów zbudowanych mają ich ścieżki dostosowane do względem projektu wywołującego. Wartość domyślna to `false`. |
| `RemoveProperties` | Parametr `String` opcjonalny.<br /><br /> Określa zestaw właściwości globalnych do usunięcia. |
| `RunEachTargetSeparately` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie MSBuild wywołuje każdy obiekt docelowy na liście przekazany do MSBuild po jednym na raz, a nie w tym samym czasie. Ustawienie tego `true` parametru na gwarancje, że kolejne obiekty docelowe są wywoływane, nawet jeśli wcześniej wywoływane obiekty docelowe nie powiodły się. W przeciwnym razie błąd kompilacji zatrzyma wywołanie wszystkich kolejnych obiektów docelowych. Wartość domyślna to `false`. |
| `SkipNonexistentProjects` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`pliki projektu, które nie istnieją na dysku, zostaną pominięte. W przeciwnym razie takie projekty spowoduje błąd. |
| `StopOnFirstFailure` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, gdy jeden z projektów nie uda się zbudować, nie więcej projektów zostanie zbudowany. Obecnie nie jest to obsługiwane podczas tworzenia równolegle (z wieloma procesorami). |
| `TargetAndPropertyListSeparators` | Parametr `String[]` opcjonalny.<br /><br /> Określa listę obiektów docelowych i `Project` właściwości jako metadane elementu). Separatory zostaną un-escaped przed przetworzeniem. na przykład %3B (wysunięty znak ";") będzie traktowany tak, jakby był nieułomowanym ';'. |
| `TargetOutputs` | Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca dane wyjściowe zbudowany obiektów docelowych ze wszystkich plików projektu. Zwracane są tylko dane wyjściowe z określonych obiektów docelowych, a nie wszystkie produkty, które mogą istnieć w przypadku obiektów docelowych, od których zależą te obiekty docelowe.<br /><br /> Parametr `TargetOutputs` zawiera również następujące metadane:<br /><br /> -   `MSBuildSourceProjectFile`: Plik projektu MSBuild, który zawiera obiekt docelowy, który ustawia dane wyjściowe.<br />-   `MSBuildSourceTargetName`: Cel, który ustawia dane wyjściowe. **Uwaga:**  Jeśli chcesz zidentyfikować dane wyjściowe z każdego pliku projektu `MSBuild` lub obiektu docelowego oddzielnie, uruchom zadanie oddzielnie dla każdego pliku projektu lub obiektu docelowego. Jeśli zadanie `MSBuild` zostanie uruchomione tylko raz, aby utworzyć wszystkie pliki projektu, dane wyjściowe wszystkich obiektów docelowych są zbierane w jedną tablicę. |
| `Targets` | Parametr `String` opcjonalny.<br /><br /> Określa obiekt docelowy lub obiekty docelowe do utworzenia w plikach projektu. Użyj średnika, aby oddzielić listę nazw docelowych. Jeśli w `MSBuild` zadaniu nie określono żadnych obiektów docelowych, zostaną utworzone domyślne obiekty docelowe określone w plikach projektu. **Uwaga:**  Obiekty docelowe muszą występować we wszystkich plikach projektu. Jeśli tak nie jest, wystąpi błąd kompilacji. |
| `ToolsVersion` | Parametr `String` opcjonalny.<br /><br /> Określa, `ToolsVersion` aby używać podczas tworzenia projektów przekazanych do tego zadania.<br /><br /> Umożliwia zadanie MSBuild do tworzenia projektu, który jest przeznaczony dla innej wersji programu .NET Framework niż określona w projekcie. Prawidłowe `2.0`wartości `3.0` `3.5`to i . Wartością `3.5`domyślną jest . |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

 W przeciwieństwie do korzystania z [zadania Exec](../msbuild/exec-task.md) do *uruchamiania programu MSBuild.exe,* to zadanie używa tego samego procesu MSBuild do tworzenia projektów podrzędnych. Lista już utworzonych obiektów docelowych, które można pominąć, jest współużytkowana przez kompilacje nadrzędne i podrzędne. To zadanie jest również szybsze, ponieważ nie jest tworzony żaden nowy proces MSBuild.

 To zadanie może przetwarzać nie tylko pliki projektu, ale także pliki rozwiązań.

 Każda konfiguracja, która jest wymagana przez MSBuild, aby umożliwić tworzenie projektów w tym samym czasie, nawet jeśli konfiguracja obejmuje infrastrukturę zdalną (na przykład porty, protokoły, limity czasu, ponownych prób i tak dalej), musi być konfigurowalna przy użyciu pliku konfiguracyjnego. Jeśli to możliwe, elementy konfiguracji powinny być określone `MSBuild` jako parametry zadania w zadaniu.

 Począwszy od MSBuild 3.5, projekty rozwiązania teraz powierzchni TargetOutputs ze wszystkich projektów podrzędnych, które tworzy.

## <a name="pass-properties-to-projects"></a>Przekazywanie właściwości do projektów

 W wersjach MSBuild przed MSBuild 3.5 przekazywanie różnych zestawów właściwości do różnych projektów wymienionych w elemencie MSBuild było wyzwaniem. Jeśli użyto atrybutu Właściwości [zadania MSBuild,](../msbuild/msbuild-task.md)jego ustawienie zostało zastosowane do wszystkich projektów, które są tworzone, chyba że [wsadowa zadanie MSBuild](../msbuild/msbuild-task.md) i warunkowo pod warunkiem, różne właściwości dla każdego projektu na liście towarów.

 MSBuild 3.5 udostępnia jednak dwa nowe zastrzeżone elementy metadanych, Właściwości i Właściwości Dodatkowe, które zapewniają elastyczny sposób przekazywania różnych właściwości dla różnych projektów budowanych przy użyciu [zadania MSBuild.](../msbuild/msbuild-task.md)

> [!NOTE]
> Te nowe elementy metadanych mają zastosowanie tylko do elementów przekazanych w atrybucie Projekty [zadania MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Zalety budowania wielu procesorów

 Jedną z głównych zalet korzystania z tych nowych metadanych występuje podczas tworzenia projektów równolegle w systemie wieloprocesorowym. Metadane umożliwia konsolidację wszystkich projektów w jednym wywołaniu [zadania MSBuild](../msbuild/msbuild-task.md) bez konieczności wykonywania żadnych zadań wsadowych lub warunkowych MSBuild. A po wywołaniu tylko jednego [zadania MSBuild,](../msbuild/msbuild-task.md)wszystkie projekty wymienione w Projects atrybut zostanie zbudowany równolegle. (Tylko jednak, jeśli `BuildInParallel=true` atrybut jest obecny w [zadaniu MSBuild](../msbuild/msbuild-task.md).) Aby uzyskać więcej informacji, zobacz [Tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadane właściwości

 Po określeniu, właściwości metadane zastępuje parametr Właściwości zadania, podczas gdy [additionalproperties](#additionalproperties-metadata) metadane pobiera dołączane do definicji parametru.

 Typowym scenariuszem jest podczas tworzenia wielu plików rozwiązania przy użyciu [zadania MSBuild](../msbuild/msbuild-task.md), tylko przy użyciu różnych konfiguracji kompilacji. Można utworzyć rozwiązanie a1 przy użyciu konfiguracji debugowania i rozwiązania a2 przy użyciu konfiguracji wydania. W programie MSBuild 2.0 ten plik projektu będzie wyglądał następująco:

> [!NOTE]
> W poniższym przykładzie "..." reprezentuje dodatkowe pliki rozwiązania.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Za pomocą właściwości metadanych, jednak można uprościć to, aby użyć jednego [zadania MSBuild](../msbuild/msbuild-task.md), jak pokazano poniżej:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <Properties>Configuration=Debug</Properties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"/>
    </Target>
</Project>
```

 \-lub -

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
        <ProjectToBuild Include="a2.sln">
            <Properties>Configuration=Release</Properties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Debug"/>
    </Target>
</Project>
```

## <a name="additionalproperties-metadata"></a>Metadane additionalproperties

 Należy wziąć pod uwagę następujący scenariusz, w którym są two pliki rozwiązania przy użyciu [zadania MSBuild](../msbuild/msbuild-task.md), zarówno przy użyciu konfiguracji wydania, ale jeden przy użyciu architektury x86, a drugi przy użyciu architektury ia64. W msbuild 2.0, należy utworzyć wiele wystąpień [zadania MSBuild:](../msbuild/msbuild-task.md)jeden do tworzenia projektu przy użyciu konfiguracji wydania z architekturą x86, drugi przy użyciu konfiguracji wydania z architekturą ia64. Plik projektu będzie wyglądał następująco:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 Za pomocą additionalproperties metadanych, można uprościć to, aby użyć jednego [zadania MSBuild](../msbuild/msbuild-task.md) przy użyciu następujących czynności:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
            <AdditionalProperties>Architecture=x86
              </AdditionalProperties>
        </ProjectToBuild>
        <ProjectToBuild Include="a2.sln">
            <AdditionalProperties>Architecture=ia64
              </AdditionalProperties>
        </ProjectToBuild>
    </ItemGroup>
    <Target Name="Build">
        <MSBuild Projects="@(ProjectToBuild)"
          Properties="Configuration=Release"/>
    </Target>
</Project>
```

## <a name="example"></a>Przykład

 Poniższy przykład używa `MSBuild` zadania do tworzenia projektów `ProjectReferences` określonych przez kolekcję towarów. Wynikowe dane wyjściowe docelowe `AssembliesBuiltByChildProjects` są przechowywane w kolekcji towarów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ProjectReferences Include="*.*proj" />
    </ItemGroup>

    <Target Name="BuildOtherProjects">
        <MSBuild
            Projects="@(ProjectReferences)"
            Targets="Build">
            <Output
                TaskParameter="TargetOutputs"
                ItemName="AssembliesBuiltByChildProjects" />
        </MSBuild>
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

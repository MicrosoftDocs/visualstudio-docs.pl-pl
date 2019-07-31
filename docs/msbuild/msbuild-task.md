---
title: Zadanie MSBuild | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2689113da88246470032ed658b2472c3845adcd
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681369"
---
# <a name="msbuild-task"></a>zadanie MSBuild

Kompiluje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] innego projektu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `MSBuild` zadania.

| Parametr | Opis |
|-----------------------------------| - |
| `BuildInParallel` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`projekty określone `Projects` w parametrze są wbudowane równolegle, jeśli jest to możliwe. Wartość domyślna to `false`. |
| `Projects` | Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki projektu do skompilowania. |
| `Properties` | Opcjonalny `String` parametr.<br /><br /> Rozdzielana średnikami lista par nazwa-wartość właściwości, które mają być stosowane jako właściwości globalne do projektu podrzędnego. Po określeniu tego parametru jest on funkcjonalnie równoważny z ustawieniem właściwości, które mają przełącznik **-Właściwość** podczas kompilowania przy użyciu programu [*MSBuild. exe*](../msbuild/msbuild-command-line-reference.md). Na przykład:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> W przypadku przekazania właściwości do projektu za pomocą `Properties` parametru, program może utworzyć nowe wystąpienie projektu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nawet jeśli plik projektu został już załadowany. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]tworzy pojedyncze wystąpienie projektu dla danej ścieżki projektu i unikatowy zestaw właściwości globalnych. Na przykład takie zachowanie umożliwia utworzenie wielu zadań programu MSBuild wywołujących obiekt *WebProject. proj*z opcją Configuration = Release i uzyskanie jednego wystąpienia elementu WebProject *. proj* (Jeśli w zadaniu nie określono żadnych unikatowych właściwości). Jeśli określisz właściwość, która nie była jeszcze widoczna [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]w programie, program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tworzy nowe wystąpienie projektu, które może być wbudowane równolegle z innymi wystąpieniami projektu. Na przykład konfiguracja wersji może być kompilowana w tym samym czasie co Konfiguracja debugowania.|
| `RebaseOutputs` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`ścieżki względne docelowych elementów wyjściowych z skompilowanych projektów są dostosowane do projektu wywołującego. Wartość domyślna to `false`. |
| `RemoveProperties` | Opcjonalny `String` parametr.<br /><br /> Określa zestaw właściwości globalnych do usunięcia. |
| `RunEachTargetSeparately` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , zadanie wywołuje każdy obiekt docelowy na liście przekazaną do jednej naraz, a nie w tym samym czasie. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Ustawienie tego parametru `true` gwarantuje, że kolejne elementy docelowe są wywoływane nawet wtedy, gdy wcześniej wywołane obiekty docelowe nie powiodły się. W przeciwnym razie błąd kompilacji spowoduje zatrzymanie wywołania wszystkich kolejnych elementów docelowych. Wartość domyślna to `false`. |
| `SkipNonexistentProjects` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`pliki projektu, które nie istnieją na dysku, zostaną pominięte. W przeciwnym razie takie projekty spowodują wystąpienie błędu. |
| `StopOnFirstFailure` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`nie uda się skompilować jednego z projektów, nie zostaną skompilowane żadne dalsze projekty. Obecnie nie jest to obsługiwane w przypadku kompilowania równoległego (z wieloma procesorami). |
| `TargetAndPropertyListSeparators` | Opcjonalny `String[]` parametr.<br /><br /> Określa listę elementów docelowych i właściwości jako `Project` metadanych elementu. Separatory zostaną cofnięte przed przetworzeniem. np.% 3B (znak ucieczki ";") będzie traktowany jako ";", tak jakby był ";". |
| `TargetOutputs` | <xref:Microsoft.Build.Framework.ITaskItem> Opcjonalny`[]` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca dane wyjściowe z skompilowanych obiektów docelowych ze wszystkich plików projektu. Zwracane są tylko dane wyjściowe z określonych obiektów docelowych, nie wszystkie wyjścia, które mogą istnieć w przypadku elementów docelowych, od których zależą te elementy docelowe.<br /><br /> `TargetOutputs` Parametr zawiera również następujące metadane:<br /><br /> -   `MSBuildSourceProjectFile`: Plik [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu, który zawiera obiekt docelowy, który ustawia dane wyjściowe.<br />-   `MSBuildSourceTargetName`: Obiekt docelowy, który ustawia dane wyjściowe. **Uwaga:**  Jeśli chcesz oddzielnie identyfikować dane wyjściowe z każdego pliku projektu lub celu, uruchom `MSBuild` zadanie osobno dla każdego pliku lub celu projektu. Jeśli uruchomisz `MSBuild` zadanie tylko raz, aby skompilować wszystkie pliki projektu, dane wyjściowe wszystkich obiektów docelowych zostaną zebrane w jednej tablicy. |
| `Targets` | Opcjonalny `String` parametr.<br /><br /> Określa element docelowy lub cel do skompilowania w plikach projektu. Użyj średnika, aby oddzielić listę nazw docelowych. Jeśli w `MSBuild` zadaniu nie określono żadnych elementów docelowych, domyślne elementy docelowe określone w plikach projektu są kompilowane. **Uwaga:**  Elementy docelowe muszą wystąpić we wszystkich plikach projektu. Jeśli tak nie jest, wystąpi błąd kompilacji. |
| `ToolsVersion` | Opcjonalny `String` parametr.<br /><br /> Określa, `ToolsVersion` który ma być używany podczas kompilowania projektów do tego zadania.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Umożliwia zadanie skompilowania projektu, który jest przeznaczony dla innej wersji .NET Framework niż określona w projekcie. Prawidłowe wartości to `2.0`, `3.0` i `3.5`. Wartość domyślna to `3.5`. |
| `UnloadProjectsOnCompletion` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`projekt zostanie zwolniony po zakończeniu operacji. |
| `UseResultsCache` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`zostanie zwrócony, buforowany wynik będzie zwracany, jeśli jest obecny.<br /><br />  Jeśli zadanie MSBuild zostanie uruchomione, jego wynik zostanie zbuforowany w zakresie <br /><br /> (ProjectFileName, GlobalProperties) [TargetNames]<br /><br /> jako lista elementów kompilacji |

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> z klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

 W przeciwieństwie do uruchamiania programu *MSBuild. exe*przy użyciu [zadania exec](../msbuild/exec-task.md) , to zadanie używa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tego samego procesu do kompilowania projektów podrzędnych. Lista już skompilowanych obiektów docelowych, które mogą być pominięte, jest udostępniana między kompilacjami nadrzędnymi i podrzędnymi. To zadanie jest również szybsze, ponieważ nie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest tworzony żaden nowy proces.

 To zadanie może przetwarzać nie tylko pliki projektu, ale również pliki rozwiązań.

 Każda konfiguracja wymagana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] program w celu umożliwienia kompilowania projektów w tym samym czasie, nawet jeśli konfiguracja obejmuje infrastrukturę zdalną (na przykład porty, protokoły, limity czasu, ponowne próby itd.), należy skonfigurować za pomocą plik konfiguracji. Jeśli to możliwe, elementy konfiguracji powinny być określone jako parametry zadania w `MSBuild` zadaniu.

 Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5, projekty rozwiązań TargetOutputs teraz wszystkie projekty podrzędne, które tworzy.

## <a name="pass-properties-to-projects"></a>Przekazywanie właściwości do projektów

 W wersjach [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wcześniejszych niż 3,5 przekazanie różnych zestawów właściwości do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] różnych projektów wymienionych w elemencie było trudne. Jeśli użyto atrybutu właściwości [zadania programu MSBuild](../msbuild/msbuild-task.md), jego ustawienie zostało zastosowane do wszystkich projektów, chyba że zostanie wykonane [zadanie](../msbuild/msbuild-task.md) wsadowe i warunkowo podano różne właściwości dla każdego projektu na liście elementów.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]3,5, jednak udostępnia dwa nowe zastrzeżone elementy metadanych, właściwości i AdditionalProperties, które zapewniają elastyczny sposób przekazywania różnych właściwości dla różnych projektów tworzonych przy użyciu [zadania programu MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Te nowe elementy metadanych mają zastosowanie tylko do elementów przekazaną w atrybucie projects [zadania MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Zalety kompilacji na wiele procesorów

 Jedną z głównych korzyści wynikających z używania tych nowych metadanych jest występuje w przypadku równoległego kompilowania projektów w systemie wielu procesorów. Metadane umożliwiają konsolidowanie wszystkich projektów do pojedynczego wywołania [zadania programu MSBuild](../msbuild/msbuild-task.md) bez konieczności wykonywania żadnych zadań wsadowych lub operacji warunkowych [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . Po wywołaniu tylko jednego [zadania programu MSBuild](../msbuild/msbuild-task.md)wszystkie projekty wymienione w atrybucie projects zostaną skompilowane równolegle. (Jeśli `BuildInParallel=true` jednak atrybut jest obecny w zadaniu [MSBuild](../msbuild/msbuild-task.md)). Aby uzyskać więcej informacji, zobacz [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadane właściwości

 Gdy ta wartość jest określona, metadane właściwości przesłaniają parametr właściwości zadania, podczas gdy metadane [AdditionalProperties](#additionalproperties-metadata) są dołączane do definicji parametru.

 Typowy scenariusz polega na tworzeniu wielu plików rozwiązania przy użyciu [zadania programu MSBuild](../msbuild/msbuild-task.md)przy użyciu różnych konfiguracji kompilacji. Możesz chcieć skompilować rozwiązanie a1 przy użyciu konfiguracji debugowania i rozwiązania a2 przy użyciu konfiguracji wydania. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 plik projektu będzie wyglądać następująco:

> [!NOTE]
> W poniższym przykładzie: "..." reprezentuje dodatkowe pliki rozwiązania.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Korzystając z metadanych właściwości, można jednak uprościć to użycie jednego [zadania MSBuild](../msbuild/msbuild-task.md), jak pokazano poniżej:

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

 \- lub —

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

## <a name="additionalproperties-metadata"></a>Metadane AdditionalProperties

 Rozważmy Poniższy scenariusz, w którym tworzysz dwa pliki rozwiązania przy użyciu [zadania programu MSBuild](../msbuild/msbuild-task.md), zarówno przy użyciu konfiguracji wydania, ale przy użyciu architektury x86, jak i innych przy użyciu architektury ia64. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 należy utworzyć wiele wystąpień [zadania MSBuild](../msbuild/msbuild-task.md): jeden do kompilowania projektu przy użyciu konfiguracji wydania z architekturą x86, drugą przy użyciu konfiguracji wydania z architekturą ia64. Plik projektu będzie wyglądać następująco:

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

 Za pomocą metadanych AdditionalProperties można uprościć to użycie pojedynczego [zadania programu MSBuild](../msbuild/msbuild-task.md) przy użyciu następujących funkcji:

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

 Poniższy przykład używa `MSBuild` zadania do kompilowania projektów określonych `ProjectReferences` przez kolekcję elementów. Wynikowe wyjściowe elementy docelowe są przechowywane w `AssembliesBuiltByChildProjects` kolekcji elementów.

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

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

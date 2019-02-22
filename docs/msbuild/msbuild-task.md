---
title: Zadanie MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 2b3a8b210c91019b2b7285288c7826f4983dfed6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627327"
---
# <a name="msbuild-task"></a>zadanie MSBuild
Kompilacje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów z innego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `MSBuild` zadania.


| Parametr | Opis |
|-----------------------------------| - |
| `BuildInParallel` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, projekty, określone w `Projects` parametru są kompilowane w sposób równoległy, jeśli jest to możliwe. Wartość domyślna to `false`. |
| `Projects` | Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki projektu do kompilacji. |
| `Properties` | Opcjonalnie `String` parametru.<br /><br /> Rozdzielana średnikami lista par nazwa/wartość właściwości do zastosowania jako globalne właściwości do projektu podrzędnego. W przypadku określenia tego parametru jest funkcjonalnie równoważny z ustawieniem dla właściwości, które mają **— właściwość** przełącznika, gdy kompilujesz za pomocą [ *MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Na przykład:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Podczas przekazywania właściwości do projektu przy użyciu `Properties` parametru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tworzy nowe wystąpienie projektu, nawet wtedy, gdy plik projektu został już załadowany. Podczas tworzenia nowego wystąpienia projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] traktuje je jako inny projekt, który ma inne właściwości globalnych i która może być kompilowana równolegle z innymi wystąpieniami projektu. Na przykład konfiguracja wydania można utworzyć w tym samym czasie co Konfiguracja debugowania. |
| `RebaseOutputs` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, ścieżki względne obiektu docelowego, dane wyjściowe elementy z skompilowanych projektach mają ich ścieżek dostosowane względem projektu wywołującego. Wartość domyślna to `false`. |
| `RemoveProperties` | Opcjonalnie `String` parametru.<br /><br /> Określa zestaw właściwości globalne do usunięcia. |
| `RunEachTargetSeparately` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadanie wywołuje każdego obiektu docelowego, na liście, który został przekazany do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pojedynczo, a nie w tym samym czasie. Ustawienie tego parametru na `true` gwarantuje, że kolejne elementy docelowe są wywoływane, nawet wtedy, gdy wcześniej wywoływana elementy docelowe nie powiodło się. W przeciwnym razie błąd kompilacji przestaną wywołania wszystkie kolejne elementy docelowe. Wartość domyślna to `false`. |
| `SkipNonexistentProjects` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, pliki projektu, które nie istnieją na dysku zostanie pominięte. W przeciwnym razie takich projektów spowoduje błąd. |
| `StopOnFirstFailure` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, gdy jeden z projektów nie powiedzie się skompilować, zostaną skompilowane żadne projekty więcej. Obecnie nie jest to obsługiwane podczas kompilowania równolegle (z wielu procesorów). |
| `TargetAndPropertyListSeparators` | Opcjonalnie `String[]` parametru.<br /><br /> Określa listę obiektów docelowych i właściwości jako `Project` metadanych elementu). Separatory będzie niezmieniony przed rozpoczęciem przetwarzania. np. % 3B (o zmienionym znaczeniu ";") będzie traktowane tak, jakby był to niezmieniony ";". |
| `TargetOutputs` | Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego tylko do odczytu.<br /><br /> Zwraca wszystkie pliki projektu wyjścia skompilowanych elementów docelowych. Tylko dane wyjściowe z elementów docelowych, które zostały określone są zwracane, nie jakiekolwiek dane wyjściowe, które mogą występować na obiekty docelowe, które zależą od tych celów.<br /><br /> `TargetOutputs` Parametr zawiera również następujące metadane:<br /><br /> -   `MSBuildSourceProjectFile`: [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Pliku projektu, który zawiera element docelowy ustawić dane wyjściowe.<br />-   `MSBuildSourceTargetName`: Obiekt docelowy ustawić dane wyjściowe. **Uwaga:**  Jeśli chcesz zidentyfikować dane wyjściowe z każdego pliku projektu lub docelowe oddzielnie, uruchom `MSBuild` zadań osobno dla każdego pliku projektu lub docelowego. Jeśli uruchamiasz `MSBuild` zadanie tylko raz, aby utworzyć wszystkie pliki projektu, dane wyjściowe wszystkie elementy docelowe są zbierane w tablicy. |
| `Targets` | Opcjonalnie `String` parametru.<br /><br /> Określa cel lub cele do kompilacji w plikach projektu. Oddziel listę nazw docelowych za pomocą średnika. Jeśli nie określono żadnych elementów docelowych w `MSBuild` zadań, są tworzone w domyślnych elementów docelowych określone w plikach projektu. **Uwaga:**  Cele musi przypadać w plikach projektu. Jeśli tak się nie stanie, występuje błąd kompilacji. |
| `ToolsVersion` | Opcjonalnie `String` parametru.<br /><br /> Określa `ToolsVersion` do użycia podczas tworzenia projektów przekazany do tego zadania.<br /><br /> Włącza [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania, aby skompilować projekt, który jest przeznaczony dla innej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] niż określona w projekcie. Prawidłowe wartości to `2.0`, `3.0` i `3.5`. Wartość domyślna to `3.5`. |
| `UnloadProjectsOnCompletion` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, projekt zostanie zwolniona po zakończeniu operacji. |
| `UseResultsCache` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, buforowane wynik zostanie zwrócony, jeśli jest obecny.<br /><br />  Jeśli zostanie uruchomione zadanie MSBuild, wynik będzie zapisywane w zakresie <br /><br /> (ProjectFileName GlobalProperties) [TargetNames]<br /><br /> jako listę elementów kompilacji |

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

 W przeciwieństwie do [Exec — zadanie](../msbuild/exec-task.md) można uruchomić *MSBuild.exe*, to zadanie używa tych samych [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proces kompilacji projektów podrzędnych. Wykaz już utworzone obiekty docelowe, których można było pominąć jest współużytkowana przez nadrzędne i podrzędne kompilacji. To zadanie jest również szybciej ponieważ żadnego nowego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] utworzeniu procesu.

 To zadanie może przetworzyć, nie tylko pliki projektu, ale także pliki rozwiązania.

 Żadnej konfiguracji, która jest wymagana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] umożliwiające projektów do kompilacji w tym samym czasie, nawet wtedy, gdy konfiguracja obejmuje zdalnego infrastruktury (na przykład portów, protokołów, limity czasu, ponownych prób i tak dalej), musi nastąpić można skonfigurować za pomocą plik konfiguracji. Jeśli to możliwe, elementy konfiguracji powinien móc można określić jako parametry zadania na `MSBuild` zadania.

 Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, rozwiązania projekty teraz powierzchni TargetOutputs ze wszystkich projektów podrzędnych, kompiluje je.

## <a name="pass-properties-to-projects"></a>Przekazania właściwości do projektów
 W wersjach [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] przed [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, przekazując różne zestawy właściwości do różnych projektów na liście [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementu była utrudniona. Jeśli używasz właściwości atrybutu [zadanie MSBuild](../msbuild/msbuild-task.md), a następnie jego ustawienia została zastosowana do wszystkich projektów kompilowana, chyba że użytkownik partii [zadanie MSBuild](../msbuild/msbuild-task.md) i warunkowo różnych właściwości dla każdego projektu w listy elementów.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, jednak zapewnia dwie nowe zarezerwowane elementów metadanych, właściwości i dodatkowe właściwości, które zapewniają elastyczny sposób w celu uwzględnienia różnych właściwości dla różnych projektów jest skompilowany przy użyciu [zadanie MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
>  Te nowe elementy metadanych są stosowane tylko do pozycji przekazanych w atrybucie projektów [zadanie MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Korzyści kompilacji wieloprocesorowej
 Występuje jeden z głównych korzyści z używania tych nowych metadanych podczas kompilowania projektów równolegle na systemem wieloprocesorowym. Metadane umożliwia konsolidowanie wszystkie projekty w jednym [zadanie MSBuild](../msbuild/msbuild-task.md) wywołania bez konieczności wykonywania żadnych adapterów przetwarzania wsadowego i warunkowego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. Kiedy można wywołać tylko jeden [zadanie MSBuild](../msbuild/msbuild-task.md), wszystkie projekty wymienionych w atrybucie projektów zostanie skompilowany w sposób równoległy. (Tylko w przypadku jednak, jeśli `BuildInParallel=true` atrybut znajduje się w [zadanie MSBuild](../msbuild/msbuild-task.md).) Aby uzyskać więcej informacji, zobacz [kompilacji wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Właściwości metadanych
 Typowy scenariusz polega na w przypadku tworzenia wielu plików rozwiązania przy użyciu [zadanie MSBuild](../msbuild/msbuild-task.md), tylko przy użyciu innych konfiguracji kompilacji. Chcesz tworzyć a1 rozwiązania przy użyciu a2 konfiguracji i rozwiązanie debugowania przy użyciu konfiguracji wydania. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, ten plik projektu będzie wyglądać podobnie do poniższego:

> [!NOTE]
>  W poniższym przykładzie "..." reprezentuje pliki dodatkowe rozwiązania.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Za pomocą właściwości metadanych, jednak można uprościć na używanie pojedynczej [zadanie MSBuild](../msbuild/msbuild-task.md), jak pokazano w poniższych:

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

## <a name="additionalproperties-metadata"></a>Dodatkowe właściwości metadanych
 Rozważmy następujący scenariusz, w którym tworzysz dwa pliki rozwiązania za pomocą [zadanie MSBuild](../msbuild/msbuild-task.md), zarówno za pomocą konfiguracji wydania, ale ją przy użyciu x86 architektury, a druga za pomocą architektury ia64. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, należy utworzyć wiele wystąpień [zadanie MSBuild](../msbuild/msbuild-task.md): jeden do skompilowania projektu przy użyciu konfiguracji wydania przy użyciu x86 architektury, druga Konfiguracja wydania przy użyciu ia64 Architektura. Plik projektu będzie wyglądać następująco:

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

 Za pomocą dodatkowe właściwości metadanych, można uprościć na używanie pojedynczej [zadanie MSBuild](../msbuild/msbuild-task.md) przy użyciu następujących:

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
 W poniższym przykładzie użyto `MSBuild` zadań do tworzenia projektów, określony przez `ProjectReferences` elementu kolekcji. Wynikowy element docelowy, dane wyjściowe są przechowywane w `AssembliesBuiltByChildProjects` elementu kolekcji.

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
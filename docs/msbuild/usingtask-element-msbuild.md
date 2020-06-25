---
title: UsingTask — element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14556467e0907818333695b3388b2d11f3467ed7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289160"
---
# <a name="usingtask-element-msbuild"></a>UsingTask, element (MSBuild)

Mapuje zadanie, do którego odwołuje się element [zadania](../msbuild/task-element-msbuild.md) , do zestawu, który zawiera implementację zadania.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Składnia

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> W przeciwieństwie do właściwości i elementów *first* , `UsingTask` zostanie użyty pierwszy element, który ma zastosowanie do elementu `TaskName` ; Aby przesłonić zadania, należy zdefiniować nowe `UsingTask` *przed* istniejącym.

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Architecture`|Atrybut opcjonalny.<br /><br /> Określa, że zadanie musi zostać uruchomione w procesie określonej liczby bitów. Jeśli bieżący proces nie spełnia wymagań, zadanie zostanie uruchomione w procesie hosta zadania, który wykonuje.<br /><br /> Obsługiwane wartości to `x86` (32-bitowe), `x64` (64-bitowe), `CurrentArchitecture` i `*` (dowolna architektura).|  
|`AssemblyName`|`AssemblyName`Atrybut lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Nazwa zestawu do załadowania. `AssemblyName`Atrybut akceptuje zestawy o silnych nazwach, chociaż silne nazewnictwo nie jest wymagane. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu przy użyciu <xref:System.Reflection.Assembly.Load%2A> metody z platformy .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli `AssemblyFile` atrybut jest używany.|
|`AssemblyFile`|Albo `AssemblyName` `AssemblyFile` atrybut jest wymagany.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełne ścieżki lub ścieżki względne. Ścieżki względne są względne dla katalogu pliku projektu lub pliku docelowego, gdzie `UsingTask` jest zadeklarowany element. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A> metody z platformy .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli `AssemblyName` atrybut jest używany.|
|`Runtime`|Atrybut opcjonalny.<br /><br /> Określa, że zadanie musi zostać uruchomione w środowisku uruchomieniowym .NET Framework określonej wersji. Jeśli bieżący proces nie spełnia wymagań, zadanie zostanie uruchomione w procesie hosta zadania, który wykonuje. Nieobsługiwane w programie .NET Core MSBuild.<br /><br /> Obsługiwane wartości to `CLR2` (.NET Framework 3,5), `CLR4` (.NET Framework 4.7.2 lub nowsze), `CurrentRuntime` i `*` (dowolne środowisko uruchomieniowe).|  
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, która jest odpowiedzialna za generowanie wystąpień określonej `Task` nazwy.  Użytkownik może także określić `Task` jako element podrzędny, który fabryka zadań odbiera i używa do generowania zadania. Zawartość programu `Task` jest specyficzna dla fabryki zadań.|
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania do odwołania z zestawu. Jeśli niejasności są możliwe, ten atrybut powinien zawsze określać pełne przestrzenie nazw. Jeśli jest niejasności, MSBuild wybiera dowolne dopasowanie, co może spowodować nieoczekiwane wyniki.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ParameterGroup —](../msbuild/parametergroup-element.md)|Zestaw parametrów, które są wyświetlane w zadaniu wygenerowanym przez określony `TaskFactory` .|
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są przesyłane do programu `TaskFactory` w celu wygenerowania wystąpienia zadania.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 Zmienne środowiskowe, właściwości wiersza polecenia, właściwości na poziomie projektu i elementy na poziomie projektu mogą być przywoływane w `UsingTask` elementach zawartych w pliku projektu bezpośrednio lub za pomocą zaimportowanego pliku projektu. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Właściwości na poziomie projektu i elementy nie mają znaczenia, jeśli `UsingTask` element pochodzi z jednego z plików *. Tasks* , które są globalnie zarejestrowane w aparacie MSBuild. Wartości na poziomie projektu nie są globalne dla programu MSBuild.

 W programie MSBuild 4,0 przy użyciu zadań można ładować z plików *. overridetask* .

Zestaw zawierający zadanie niestandardowe jest ładowany podczas `Task` pierwszego użycia.

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać `UsingTask` elementu z `AssemblyName` atrybutem.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak używać `UsingTask` elementu z `AssemblyFile` atrybutem.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Instrukcje: Konfigurowanie obiektów docelowych i zadań](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

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
ms.openlocfilehash: 7bd62738a89b38adb6cd01d6a33d661e95144d34
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565269"
---
# <a name="usingtask-element-msbuild"></a>UsingTask, element (MSBuild)
Mapuje zadanie, do którego odwołuje się element [zadania](../msbuild/task-element-msbuild.md) , do zestawu, który zawiera implementację zadania.

 \<Project > \<UsingTask >

## <a name="syntax"></a>Składnia

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> W przeciwieństwie do właściwości i elementów, zostanie użyty *pierwszy* `UsingTask` element, który ma zastosowanie do `TaskName`; Aby zastąpić zadania, należy zdefiniować nowe `UsingTask` *przed* istniejącym.

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`AssemblyName`|Wymagany jest atrybut `AssemblyName` lub atrybut `AssemblyFile`.<br /><br /> Nazwa zestawu do załadowania. Atrybut `AssemblyName` akceptuje zestawy o silnych nazwach, chociaż silne nazewnictwo nie jest wymagane. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu za pomocą metody <xref:System.Reflection.Assembly.Load%2A> w programie .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli jest używany atrybut `AssemblyFile`.|
|`AssemblyFile`|Wymagany jest `AssemblyName` lub `AssemblyFile` atrybut.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełne ścieżki lub ścieżki względne. Ścieżki względne są względne dla katalogu pliku projektu lub pliku docelowego, w którym zadeklarowany jest element `UsingTask`. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A> w programie .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli jest używany atrybut `AssemblyName`.|
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, która jest odpowiedzialna za generowanie wystąpień określonej nazwy `Task`.  Użytkownik może także określić `TaskBody` jako element podrzędny, który fabryka zadań odbiera i używa do wygenerowania zadania. Zawartość `TaskBody` jest specyficzna dla fabryki zadań.|
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania do odwołania z zestawu. Jeśli niejasności są możliwe, ten atrybut powinien zawsze określać pełne przestrzenie nazw. Jeśli jest niejasności, MSBuild wybiera dowolne dopasowanie, co może spowodować nieoczekiwane wyniki.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Zestaw parametrów, które są wyświetlane w zadaniu wygenerowanym przez określony `TaskFactory`.|
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są przesyłane do `TaskFactory` w celu wygenerowania wystąpienia zadania.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Uwagi
 Zmienne środowiskowe, właściwości wiersza polecenia, właściwości na poziomie projektu i elementy na poziomie projektu mogą być przywoływane w `UsingTask` elementów zawartych w pliku projektu bezpośrednio lub za pomocą zaimportowanego pliku projektu. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Właściwości na poziomie projektu i elementy nie mają znaczenia, jeśli element `UsingTask` jest pochodzący z jednego z plików *. Tasks* , które są globalnie zarejestrowane w aparacie MSBuild. Wartości na poziomie projektu nie są globalne dla programu MSBuild.

 W programie MSBuild 4,0 przy użyciu zadań można ładować z plików *. overridetask* .

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać elementu `UsingTask` z atrybutem `AssemblyName`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody>
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać elementu `UsingTask` z atrybutem `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

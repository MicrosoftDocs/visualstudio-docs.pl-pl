---
title: UsingTask Element (MSBuild) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 22d61fe30e9eb68697f073ca0bcfbcc515e513dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431452"
---
# <a name="usingtask-element-msbuild"></a>UsingTask element (MSBuild)

Mapuje zadanie, do którego odwołuje się w [Task](../msbuild/task-element-msbuild.md) element do zestawu, który zawiera implementację zadania.

 \<> projektu \<usingTask>

## <a name="syntax"></a>Składnia

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> W przeciwieństwie do właściwości *first* `UsingTask` i elementów, `TaskName` pierwszy element, który ma zastosowanie do a będą używane; aby zastąpić zadania, należy zdefiniować nowy `UsingTask` *przed* istniejącym.

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`AssemblyName`|Wymagany jest `AssemblyName` atrybut lub `AssemblyFile` atrybut.<br /><br /> Nazwa zestawu do załadowania. Atrybut `AssemblyName` akceptuje zestawy o silnej nazwie, chociaż silne nazewnictwo nie jest wymagane. Za pomocą tego atrybutu jest odpowiednikiem <xref:System.Reflection.Assembly.Load%2A> ładowania zestawu przy użyciu metody w .NET.<br /><br /> Nie można użyć tego `AssemblyFile` atrybutu, jeśli używany jest atrybut.|
|`AssemblyFile`|Wymagany jest `AssemblyName` `AssemblyFile` atrybut lub atrybut.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełne ścieżki lub ścieżki względne. Ścieżki względne są względem katalogu pliku projektu lub pliku `UsingTask` docelowego, w którym element jest zadeklarowany. Za pomocą tego atrybutu jest odpowiednikiem <xref:System.Reflection.Assembly.LoadFrom%2A> ładowania zestawu przy użyciu metody w .NET.<br /><br /> Nie można użyć tego `AssemblyName` atrybutu, jeśli używany jest atrybut.|
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, która jest odpowiedzialna za generowanie wystąpień o określonej `Task` nazwie.  Użytkownik może również `Task` określić jako element podrzędny, który fabryka zadań odbiera i używa do generowania zadania. Zawartość `Task` są specyficzne dla fabryki zadań.|
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania do odwołania z zestawu. Jeśli niejednoznaczności są możliwe, ten atrybut należy zawsze określić pełne przestrzenie nazw. Jeśli istnieją niejasności, MSBuild wybiera dowolne dopasowanie, które może spowodować nieoczekiwane wyniki.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Grupa parametrów](../msbuild/parametergroup-element.md)|Zestaw parametrów wyświetlanych w zadaniu generowanym `TaskFactory`przez określony program .|
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są `TaskFactory` przekazywane do generowania wystąpienia zadania.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 Zmienne środowiskowe, właściwości wiersza polecenia, właściwości na poziomie projektu i elementy `UsingTask` na poziomie projektu mogą odwoływać się do elementów zawartych w pliku projektu bezpośrednio lub za pośrednictwem importowanego pliku projektu. Aby uzyskać więcej informacji, zobacz [Zadania](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Właściwości i elementy na poziomie projektu `UsingTask` nie mają znaczenia, jeśli element pochodzi z jednego z plików *zadań.tasks,* które są globalnie zarejestrowane w silniku MSBuild. Wartości na poziomie projektu nie są globalne do MSBuild.

 W msbuild 4.0, za pomocą zadań można ładować z plików *.overridetask.*

Zestaw zawierający zadanie niestandardowe jest `Task` ładowany, gdy jest używany po raz pierwszy.

## <a name="example"></a>Przykład

 W poniższym przykładzie `UsingTask` pokazano, `AssemblyName` jak używać elementu z atrybutem.

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

 W poniższym przykładzie `UsingTask` pokazano, `AssemblyFile` jak używać elementu z atrybutem.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

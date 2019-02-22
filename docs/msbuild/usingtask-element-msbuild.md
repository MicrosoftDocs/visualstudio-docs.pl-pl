---
title: Usingtask — Element (MSBuild) | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b97999b7a6aa56dc9be17d853c306c71a5ff290
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645748"
---
# <a name="usingtask-element-msbuild"></a>Usingtask — element (MSBuild)
Mapuje zadanie, które odwołują się [zadań](../msbuild/task-element-msbuild.md) element do zestawu zawierającego implementację zadania.

 \<Projekt > \<UsingTask >

## <a name="syntax"></a>Składnia

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`AssemblyName`|Albo `AssemblyName` atrybutu lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Nazwa zestawu do załadowania. `AssemblyName` Atrybut akceptuje zestawy o silnych nazwach, silne nazwy nie jest wymagany. Przy użyciu tego atrybutu jest równoważne z ładowaniem zestawu, za pomocą <xref:System.Reflection.Assembly.Load%2A> metody na platformie .NET.<br /><br /> Nie można używać tego atrybutu, jeśli `AssemblyFile` atrybut jest używany.|
|`AssemblyFile`|Albo `AssemblyName` lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełne ścieżki lub ścieżek względnych. Względne ścieżki są względne wobec katalogu pliku projektu lub pliku obiektów docelowych gdzie `UsingTask` elementu jest zadeklarowany. Przy użyciu tego atrybutu jest równoważne z ładowaniem zestawu, za pomocą <xref:System.Reflection.Assembly.LoadFrom%2A> metody na platformie .NET.<br /><br /> Nie można używać tego atrybutu, jeśli `AssemblyName` atrybut jest używany.|
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, który jest odpowiedzialny za Generowanie wystąpień z określonym `Task` nazwy.  Użytkownik może również określić `TaskBody` jako element podrzędny, która fabryka zadań odbiera używana do generowania zadania. Zawartość `TaskBody` są specyficzne dla fabryki zadań.|
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania, odwołanie z zestawu. Możliwe są niejasności, ten atrybut należy zawsze określić pełną przestrzeni nazw. Jeśli występują niejasności, program MSBuild wybiera dopasowanie dowolnego spowodować uzyskanie nieoczekiwanych wyników.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Zestaw parametrów, które pojawiają się na zadanie, który jest generowany przez określony `TaskFactory`.|
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są przekazywane do `TaskFactory` do generowania wystąpienia zadania.|

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Element główny wymagany [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. |

## <a name="remarks"></a>Uwagi
 Zmienne środowiskowe, właściwości wiersza polecenia, właściwości na poziomie projektu i elementy na poziomie projektu może być przywoływany w `UsingTask` elementy zawarte w pliku projektu, albo plik bezpośrednio lub za pośrednictwem importowanym projekcie. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

> [!NOTE]
>  Właściwości na poziomie projektu i elementy nie mają znaczenia jeśli `UsingTask` element pochodzi z jednego z *.tasks* pliki, które są globalnie zarejestrowane w usłudze aparatu MSBuild. Wartości na poziomie projektu nie są globalne do programu MSBuild.

 W wersji 4.0 programu MSBuild, przy użyciu zadań mogą być ładowane z *.overridetask* plików.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać `UsingTask` element z `AssemblyName` atrybutu.

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
 Poniższy przykład pokazuje, jak używać `UsingTask` element z `AssemblyFile` atrybutu.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

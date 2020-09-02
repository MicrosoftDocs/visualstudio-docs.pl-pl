---
title: UsingTask — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf2882120f2e4c27e33b105585ba56261122055d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815402"
---
# <a name="usingtask-element-msbuild"></a>UsingTask — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mapuje zadanie, do którego odwołuje się element [zadania](../msbuild/task-element-msbuild.md) , do zestawu, który zawiera implementację zadania.  
  
 \<Project>  
 \<UsingTask>  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`AssemblyName`|`AssemblyName`Atrybut lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Nazwa zestawu do załadowania. `AssemblyName`Atrybut akceptuje zestawy o silnych nazwach, chociaż silne nazewnictwo nie jest wymagane. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu przy użyciu <xref:System.Reflection.Assembly.Load%2A> metody z platformy .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli `AssemblyFile` atrybut jest używany.|  
|`AssemblyFile`|Albo `AssemblyName` `AssemblyFile` atrybut jest wymagany.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełne ścieżki lub ścieżki względne. Ścieżki względne są względne dla katalogu pliku projektu lub pliku docelowego, gdzie `UsingTask` jest zadeklarowany element. Użycie tego atrybutu jest równoznaczne z załadowaniem zestawu przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A> metody z platformy .NET.<br /><br /> Tego atrybutu nie można użyć, jeśli `AssemblyName` atrybut jest używany.|  
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, która jest odpowiedzialna za generowanie wystąpień określonej `Task` nazwy.  Użytkownik może także określić `TaskBody` jako element podrzędny, który fabryka zadań odbiera i używa do generowania zadania. Zawartość programu `TaskBody` jest specyficzna dla fabryki zadań.|  
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania do odwołania z zestawu. Jeśli niejasności są możliwe, ten atrybut powinien zawsze określać pełne przestrzenie nazw. Jeśli jest niejasności, MSBuild wybiera dowolne dopasowanie, co może spowodować nieoczekiwane wyniki.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[ParameterGroup —](../msbuild/parametergroup-element.md)|Zestaw parametrów, które są wyświetlane w zadaniu wygenerowanym przez określony `TaskFactory` .|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są przesyłane do programu `TaskFactory` w celu wygenerowania wystąpienia zadania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymagany element główny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Zmienne środowiskowe, właściwości wiersza polecenia i właściwości na poziomie projektu mogą być przywoływane w dowolnym miejscu `UsingTask` elementu, jeśli pojawia się w pliku projektu jawnie lub za pomocą zaimportowanego pliku projektu. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
> Właściwości na poziomie projektu nie mają znaczenia, jeśli `UsingTask` element pochodzi z jednego z plików. Tasks, które są globalnie zarejestrowane w aparacie MSBuild. Właściwości na poziomie projektu nie są globalne dla programu MSBuild.  
  
 W programie MSBuild 4,0 przy użyciu zadań można ładować z plików. overridetask.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `UsingTask` elementu z `AssemblyName` atrybutem.  
  
```  
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
 Poniższy przykład pokazuje, jak używać `UsingTask` elementu z `AssemblyFile` atrybutem.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

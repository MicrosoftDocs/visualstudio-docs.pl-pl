---
title: Element parametru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a815d2ef623a35030469fa631cae65653c2fe2d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185225"
---
# <a name="parameter-element"></a>Parameter — Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera informacje dotyczące określonego parametru zadania, które jest generowane przez `UsingTask``TaskFactory` .  Nazwa elementu jest nazwą parametru.  Aby uzyskać więcej informacji, zobacz [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`ParameterType`|Atrybut opcjonalny.<br /><br /> Typ .NET parametru, na przykład "System. String".|  
|`Output`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli `true` , ten parametr jest parametrem wyjściowym zadania. Domyślna wartość to `false`.|  
|`Required`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli `true` , ten parametr jest wymaganym parametrem zadania. Domyślna wartość to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[ParameterGroup —](../msbuild/parametergroup-element.md)|Zawiera opcjonalną listę parametrów, które będą obecne w zadaniu wygenerowanym przez `UsingTask``TaskFactory` .|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `Parameter` elementu.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

---
title: Output — element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 52b8ef11e295d60e71a59820a48bca5e477c639d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163600"
---
# <a name="output-element-msbuild"></a>Output — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przechowuje wartości wyjściowe zadania w elementach i we właściwościach.  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`TaskParameter`|Atrybut wymagany.<br /><br /> Nazwa parametru wyjściowego zadania.|  
|`PropertyName`|`PropertyName` `ItemName` Wymagany jest atrybut or.<br /><br /> Właściwość, która otrzymuje wartość parametru wyjściowego zadania. Projekt może następnie odwołać się do właściwości przy użyciu `$(` *PropertyName* `)` składni PropertyName. Ta nazwa właściwości może być nową nazwą właściwości lub nazwą, która jest już zdefiniowana w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `ItemName` jest również używany.|  
|`ItemName`|`PropertyName` `ItemName` Wymagany jest atrybut or.<br /><br /> Element, który otrzymuje wartość parametru wyjściowego zadania. Projekt może odwoływać się do elementu z `@(` składnią *itemName* `)` . Nazwa elementu może być nazwą nowego elementu lub nazwą, która jest już zdefiniowana w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `PropertyName` jest również używany.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Tworzy i wykonuje wystąpienie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadania.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `Csc` zadanie wykonywane wewnątrz `Target` elementu. Elementy i właściwości przesłane do parametrów zadania są zadeklarowane poza zakresem tego przykładu. Wartość z parametru Output `OutputAssembly` jest przechowywana w `FinalAssemblyName` elemencie, a wartość z parametru Output `BuildSucceeded` jest przechowywana we `BuildWorked` właściwości. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)

---
title: Zadanie właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea16950e47760e89204503413fd98811e781d059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184058"
---
# <a name="createproperty-task"></a>CreateProperty — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wypełnia właściwości wartościami z przekazaną. Pozwala to na kopiowanie wartości z jednej właściwości lub ciągu do innej.  
  
## <a name="attributes"></a>Atrybuty  
 W poniższej tabeli opisano parametry `CreateProperty` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Value`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa wartość, która ma zostać skopiowana do nowej właściwości.|  
|`ValueSetByTask`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera tę samą wartość, co `Value` parametr. Tego parametru należy użyć tylko wtedy, gdy nie ma właściwości Output ustawionej przez, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] gdy pomija otaczający element docelowy, ponieważ dane wyjściowe są aktualne.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CreateProperty` zadania do utworzenia `NewFile` właściwości przy użyciu kombinacji wartości `SourceFilename` `SourceFileExtension` właściwości i.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Po uruchomieniu projektu wartość `NewFile` właściwości jest `Module1.vb` .  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)

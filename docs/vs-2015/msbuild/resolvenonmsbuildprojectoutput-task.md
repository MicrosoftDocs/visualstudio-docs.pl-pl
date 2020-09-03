---
title: ResolveNonMSBuildProjectOutput — — Zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aaf99affe9c29762aa8b47ea76419da429089b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156158"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa pliki wyjściowe dla odwołań projektu innych niż MSBuild.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveNonMSBuildProjectOutput` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg XML, który zawiera rozpoznane dane wyjściowe projektu.|  
|`ProjectReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa odwołania do projektu.|  
|`ResolvedOutputPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę rozwiązanych ścieżek odwołań (i zachowuje pierwotne atrybuty odwołania projektu).|  
|`UnresolvedProjectReferences`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odwołań projektu, których nie można rozpoznać przy użyciu prewiązanej listy danych wyjściowych.<br /><br /> Ponieważ program Visual Studio rozpoznaje tylko wstępnie projekty programów innych niż MSBuild, oznacza to, że odwołania do projektu na tej liście są w formacie MSBuild.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

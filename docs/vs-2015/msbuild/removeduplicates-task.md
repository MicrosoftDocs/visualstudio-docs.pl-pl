---
title: RemoveDuplicates — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73ad829c86305ff4d9a54025467e262d56e24dbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159243"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usuwa zduplikowane elementy z określonej kolekcji elementów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RemoveDuplicates` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Filtered`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera kolekcję elementów z usuniętymi wszystkimi zduplikowanymi elementami.|  
|`Inputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Kolekcja elementów, z której mają zostać usunięte zduplikowane elementy.|  
  
## <a name="remarks"></a>Uwagi  
 To zadanie uwzględnia wielkość liter i nie porównuje metadanych elementów podczas określania duplikatów.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `RemoveDuplicates` zadania, aby usunąć zduplikowane elementy z `MyItems` kolekcji elementów. Po zakończeniu zadania `FilteredItems` Kolekcja elementów zawiera jeden element.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Zadania](../msbuild/msbuild-tasks.md)

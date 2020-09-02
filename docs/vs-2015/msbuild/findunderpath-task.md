---
title: FindUnderPath — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c679352fb8db81379ab93e800efa9f631773c36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149741"
---
# <a name="findunderpath-task"></a>FindUnderPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, które elementy w określonej kolekcji elementów mają ścieżki, które znajdują się w lub poniżej określonego folderu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FindUnderPath` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa pliki, których ścieżki należy porównać ze ścieżką określoną przez `Path` parametr.|  
|`InPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały znalezione pod określoną ścieżką.|  
|`OutOfPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które nie zostały odnalezione w określonej ścieżce.|  
|`Path`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa ścieżkę folderu, która ma być używana jako odwołanie.|  
|`UpdateToAbsolutePaths`|Opcjonalny `Boolean` parametr.<br /><br /> W przypadku wartości true ścieżki elementów wyjściowych są aktualizowane jako ścieżki bezwzględne.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zadania, `FindUnderPath` Aby określić, czy pliki zawarte w `MyFiles` elemencie mają ścieżki istniejące w ścieżce określonej przez `SearchPath` Właściwość. Po zakończeniu zadania `FilesNotFoundInPath` element zawiera `File1.txt` plik, a `FilesFoundInPath` element zawiera `File2.txt` plik.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)

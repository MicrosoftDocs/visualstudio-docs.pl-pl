---
title: GetFrameworkSdkPath — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d527b00e8cbfe6a6f4ad5d112a23e46d4edb8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149570"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pobiera ścieżkę do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GetFrameworkSdkPath` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 2,0, jeśli istnieje. W przeciwnym razie zwraca `String.Empty` .|  
|`FrameworkSdkVersion35Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 3,5, jeśli istnieje. W przeciwnym razie zwraca `String.Empty` .|  
|`FrameworkSdkVersion40Path`|Opcjonalny `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 4,0, jeśli istnieje. W przeciwnym razie zwraca `String.Empty` .|  
|`Path`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszego zestawu SDK platformy .NET, jeśli obecna jest jakakolwiek wersja. W przeciwnym razie zwraca `String.Empty` .|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `GetFrameworkSdkPath` zadania do przechowywania ścieżki do [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] `SdkPath` właściwości.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

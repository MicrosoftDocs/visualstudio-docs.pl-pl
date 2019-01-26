---
title: Getframeworksdkpath — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1ca2a4c77471f4b6767269e511d690c6c094a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947273"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — zadanie
Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GetFrameworkSdkPath` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Opcjonalnie `String` parametru wyjściowego tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 2.0, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Opcjonalnie `String` parametru wyjściowego tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 3.5, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Opcjonalnie `String` parametru wyjściowego tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu SDK platformy .NET w wersji 4.0, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`Path`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera ścieżkę do najnowszy zestaw SDK platformy .NET, jeśli dowolna wersja jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GetFrameworkSdkPath` zadania do ścieżki do przechowywania [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] w `SdkPath` właściwości.  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
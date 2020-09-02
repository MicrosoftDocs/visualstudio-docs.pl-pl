---
title: UnregisterAssembly — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193236"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wyrejestrowuje określone zestawy na potrzeby współdziałania z modelem COM. Wykonuje odwrotność [zadania RegisterAssembly —](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `UnregisterAssembly` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa zestawy do wyrejestrowania.|  
|`AssemblyListFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Zawiera informacje o stanie między `RegisterAssembly` zadaniem a `UnregisterAssembly` zadaniem. Zapobiega to próbie wyrejestrowania zestawu, którego nie udało się zarejestrować w `RegisterAssembly` zadaniu.<br /><br /> Jeśli ten parametr jest określony, `Assemblies` Parametry i `TypeLibFiles` są ignorowane.|  
|`TypeLibFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Wyrejestrowuje określoną bibliotekę typów z określonego zestawu. **Uwaga:**  Ten parametr jest wymagany tylko wtedy, gdy nazwa pliku biblioteki typów jest inna niż nazwa zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Nie jest wymagane, aby zestaw istniał dla tego zadania. Jeśli spróbujesz wyrejestrować zestaw, który nie istnieje, zadanie zakończy się powodzeniem z ostrzeżeniem. Dzieje się tak, ponieważ jest to zadanie, aby usunąć rejestrację zestawu z rejestru. Jeśli zestaw nie istnieje, nie znajduje się w rejestrze, a tym samym zadanie zakończyło się pomyślnie.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> klasy, która sama dziedziczy z <xref:System.MarshalByRefObject> klasy. `MarshalByRefObject`Klasa zapewnia taką samą funkcjonalność jak <xref:Microsoft.Build.Utilities.Task> Klasa, ale można ją utworzyć w swojej własnej domenie aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `UnregisterAssembly` zadania, aby wyrejestrować zestaw w ścieżce określonej przez `OutputPath` `FileName` właściwości i, jeśli istnieje.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [RegisterAssembly —, zadanie](../msbuild/registerassembly-task.md)   
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

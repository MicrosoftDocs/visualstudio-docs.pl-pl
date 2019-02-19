---
title: Unregisterassembly — zadanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 497a767a1cd67c08e82a743d0665a152c5dd7062
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54833722"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Wyrejestrowuje określonych zestawów do celów międzyoperacyjności COM. Wykonuje odwrotnej [registerassembly — zadanie](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `UnregisterAssembly` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, które mają zostać wyrejestrowana.|  
|`AssemblyListFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Zawiera informacje na temat stanu między `RegisterAssembly` zadań i `UnregisterAssembly` zadań. Zapobiega to zadanie próby wyrejestrowanie zestawie, do którego nie można zarejestrować w `RegisterAssembly` zadania.<br /><br /> Jeśli ten parametr jest określony, `Assemblies` i `TypeLibFiles` parametry są ignorowane.|  
|`TypeLibFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Wyrejestrowuje określonej biblioteki typu z określonego zestawu. **Uwaga:**  Ten parametr jest tylko wymagane, jeśli nazwa pliku biblioteki typów jest inna niż nazwa zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Nie jest wymagane, że ten zestaw istnieje dla tego zadania odnieść sukces. Jeśli użytkownik podejmie próbę wyrejestrowanie zestawie, który nie istnieje, zadanie zakończy się pomyślnie z ostrzeżeniem. Dzieje się tak, ponieważ jest on zadania to zadanie do usunięcia rejestracji zestawów z rejestru. Jeśli zestaw nie istnieje, nie znajduje się w rejestrze i w związku z tym, zadanie zakończyło się pomyślnie.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> klasa, która sama dziedziczy <xref:System.MarshalByRefObject> klasy. `MarshalByRefObject` Klasa udostępnia taką samą funkcjonalność jak <xref:Microsoft.Build.Utilities.Task> klasy, ale może być utworzone w domenie aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `UnregisterAssembly` zadanie, aby wyrejestrować zestawów w ścieżce określonej przez `OutputPath` i `FileName` właściwości, jeśli taki istnieje.  
  
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
 [Registerassembly — zadanie](../msbuild/registerassembly-task.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

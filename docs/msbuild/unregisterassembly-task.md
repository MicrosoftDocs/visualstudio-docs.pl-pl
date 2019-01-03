---
title: Unregisterassembly — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d07e9bec84e735082ce1392eaf8db33c3c617c06
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917335"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — zadanie
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
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Registerassembly — zadanie](../msbuild/registerassembly-task.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
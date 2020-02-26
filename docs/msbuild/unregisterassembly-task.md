---
title: UnregisterAssembly — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22be291184ebf02ae0455f5b4656b1dec976dc89
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578288"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — zadanie
Wyrejestrowuje określone zestawy na potrzeby współdziałania z modelem COM. Wykonuje odwrotność [zadania RegisterAssembly —](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `UnregisterAssembly`.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa zestawy do wyrejestrowania.|
|`AssemblyListFile`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Zawiera informacje o stanie między zadaniem `RegisterAssembly` i `UnregisterAssembly` zadaniem. Zapobiega to próbie wyrejestrowania zestawu, którego nie można zarejestrować w zadaniu `RegisterAssembly`.<br /><br /> Jeśli ten parametr jest określony, `Assemblies` i `TypeLibFiles` parametry zostaną zignorowane.|
|`TypeLibFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Wyrejestrowuje określoną bibliotekę typów z określonego zestawu. **Uwaga:**  Ten parametr jest wymagany tylko wtedy, gdy nazwa pliku biblioteki typów jest inna niż nazwa zestawu.|

## <a name="remarks"></a>Uwagi
 Nie jest wymagane, aby zestaw istniał dla tego zadania. Jeśli spróbujesz wyrejestrować zestaw, który nie istnieje, zadanie zakończy się powodzeniem z ostrzeżeniem. Dzieje się tak, ponieważ jest to zadanie, aby usunąć rejestrację zestawu z rejestru. Jeśli zestaw nie istnieje, nie znajduje się w rejestrze, a tym samym zadanie zakończyło się pomyślnie.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, która sama dziedziczy z klasy <xref:System.MarshalByRefObject>. Klasa `MarshalByRefObject` zapewnia te same funkcje co Klasa <xref:Microsoft.Build.Utilities.Task>, ale można ją utworzyć w swojej domenie aplikacji.

## <a name="example"></a>Przykład
 Poniższy przykład używa zadania `UnregisterAssembly`, aby wyrejestrować zestaw w ścieżce określonej przez właściwości `OutputPath` i `FileName`, jeśli istnieje.

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

## <a name="see-also"></a>Zobacz też
- [RegisterAssembly —, zadanie](../msbuild/registerassembly-task.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
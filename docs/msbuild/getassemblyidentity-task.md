---
title: GetAssemblyIdentity — — zadanie | Microsoft Docs
description: Użyj zadania MSBuild GetAssemblyIdentity — do pobrania tożsamości zestawu z określonych plików i wyprowadzania informacji o tożsamości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8e242864ca68e0d84ace5f8ebeefd02881a394f
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436858"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity — zadanie

Pobiera tożsamości zestawu z określonych plików i wyświetla informacje o tożsamości.

## <a name="task-parameters"></a>Parametry zadania

W poniższej tabeli opisano parametry `GetAssemblyIdentity` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera pobraną tożsamość zestawu.|
|`AssemblyFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki, z których mają zostać pobrane tożsamości.|

## <a name="remarks"></a>Uwagi

Elementy wyjściowe przez `Assemblies` parametr zawierają wpisy metadanych elementu o nazwach `Version` , `PublicKeyToken` i `Culture` .

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pobiera tożsamość plików określonych w `MyAssemblies` elemencie i wyprowadza je do `MyAssemblyIdentities` elementu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

---
title: Zadanie wyrejestrowania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2f8cddcf9bf0632914d1a6de1cc904dbf0f173e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631500"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — zadanie

Wyrejestrowanie określonych zestawów do celów współdziałanych COM. Wykonuje odwrotną stronę [zadania RegisterAssembly](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parametry

 W poniższej tabeli `UnregisterAssembly` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy, które mają być wyrejestrowane.|
|`AssemblyListFile`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Zawiera informacje o stanie `RegisterAssembly` między `UnregisterAssembly` zadaniem a zadaniem. Zapobiega to próbie wyrejestrowania zestawu, którego rejestracja `RegisterAssembly` w zadaniu nie powiodła się.<br /><br /> Jeśli ten parametr jest `Assemblies` `TypeLibFiles` określony, parametry i są ignorowane.|
|`TypeLibFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Wyrejestrowaje określoną bibliotekę typów z określonego zestawu. **Uwaga:**  Ten parametr jest niezbędny tylko wtedy, gdy nazwa pliku biblioteki typów jest inna niż nazwa zestawu.|

## <a name="remarks"></a>Uwagi

 Nie jest wymagane, że zestaw istnieje dla tego zadania, aby zakończyć się pomyślnie. Jeśli spróbujesz wyrejestrować zestaw, który nie istnieje, zadanie zakończy się pomyślnie z ostrzeżeniem. Dzieje się tak, ponieważ jest zadaniem tego zadania, aby usunąć rejestrację zestawu z rejestru. Jeśli zestaw nie istnieje, nie jest w rejestrze, a zatem zadanie powiodło się.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> klasy, <xref:System.MarshalByRefObject> która sama dziedziczy z klasy. Klasa `MarshalByRefObject` zapewnia taką samą <xref:Microsoft.Build.Utilities.Task> funkcjonalność jak klasa, ale można utworzyć wystąpienia w własnej domenie aplikacji.

## <a name="example"></a>Przykład

 W poniższym przykładzie `UnregisterAssembly` użyto zadania do wyrejestrowania zestawu na ścieżce określonej przez `OutputPath` i `FileName` właściwości, jeśli istnieje.

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

- [Zarejestruj zadanie rejestrujasnajednak](../msbuild/registerassembly-task.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
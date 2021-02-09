---
title: Dotknięcie zadania | Microsoft Docs
description: Poznaj parametry i użycie zadania Touch programu MSBuild, które ustawia czasy dostępu i modyfikacji plików.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b31beb15ddfd1078d72c247535e2bc835b8c31e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902645"
---
# <a name="touch-task"></a>Touch — Zadanie

Ustawia czasy dostępu i modyfikacji plików.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `Touch` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AlwaysCreate`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` program utworzy wszystkie pliki, które jeszcze nie istnieją.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa kolekcję plików do dotknięcia.|
|`ForceTouch`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , wymusza działanie pliku, nawet jeśli pliki są tylko do odczytu.|
|`Time`|Opcjonalny `String` parametr.<br /><br /> Określa godzinę inną niż bieżąca godzina. Format musi być formatem, który jest akceptowalny dla <xref:System.DateTime.Parse%2A> metody.|
|`TouchedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera kolekcję elementów, które zostały pomyślnie naruszone.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania, `Touch` Aby zmienić czasy dostępu i modyfikacji plików określonych w `Files` kolekcji elementów i umieszcza listę pomyślnie naruszonych plików w `FilesTouched` kolekcji elementów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

<ItemGroup>
    <Files Include="File1.cs;File2.cs;File3.cs" />
</ItemGroup>

    <Target Name="TouchFiles">
        <Touch
            Files="@(Files)">
            <Output
                TaskParameter="TouchedFiles"
                ItemName="FilesTouched"/>
    </Touch>
</Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

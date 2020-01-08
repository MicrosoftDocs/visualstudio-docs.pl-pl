---
title: Dotknięcie zadania | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d34d8edca64987f9b6c4648bef1f239aca4d5ba
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594945"
---
# <a name="touch-task"></a>Touch — Zadanie
Ustawia czasy dostępu i modyfikacji plików.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `Touch`.

|Parametr|Opis|
|---------------|-----------------|
|`AlwaysCreate`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, program tworzy wszystkie pliki, które jeszcze nie istnieją.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa kolekcję plików do dotknięcia.|
|`ForceTouch`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, wymusza nadanie pliku, nawet jeśli pliki są tylko do odczytu.|
|`Time`|Opcjonalny parametr `String`.<br /><br /> Określa godzinę inną niż bieżąca godzina. Format musi być formatem, który jest akceptowalny dla metody <xref:System.DateTime.Parse%2A>.|
|`TouchedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera kolekcję elementów, które zostały pomyślnie naruszone.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 Poniższy przykład używa zadania `Touch`, aby zmienić czasy dostępu i modyfikacji plików określonych w kolekcji `Files` elementów i umieszcza listę pomyślnie naruszonych plików w kolekcji `FilesTouched` elementów.

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

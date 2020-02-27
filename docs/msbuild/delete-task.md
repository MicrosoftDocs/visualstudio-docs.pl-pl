---
title: Usuń zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634282"
---
# <a name="delete-task"></a>Delete — Zadanie

Usuwa określone pliki.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania `Delete`.

|Parametr|Opis|
|---------------|-----------------|
|`DeletedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa pliki, które zostały pomyślnie usunięte.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do usunięcia.|
|`TreatErrorsAsWarnings`|Opcjonalny parametr `Boolean`<br /><br /> Jeśli `true`, błędy są rejestrowane jako ostrzeżenia. Wartością domyślną jest `false`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Należy zachować ostrożność w przypadku używania symboli wieloznacznych z zadaniem `Delete`. Można łatwo usunąć niewłaściwe pliki z wyrażeniami, takimi jak `$(SomeProperty)\**\*.*` lub `$(SomeProperty)/**/*.*`, zwłaszcza jeśli właściwość zwraca pusty ciąg, w którym to przypadku parametr `Files` może zostać oceniony jako katalog główny dysku i usunąć wiele więcej niż chcesz usunąć.

## <a name="example"></a>Przykład

Poniższy przykład usuwa plik *MojaApl. pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

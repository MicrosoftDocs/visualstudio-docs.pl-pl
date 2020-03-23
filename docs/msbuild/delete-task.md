---
title: Usuń zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634282"
---
# <a name="delete-task"></a>Delete — Zadanie

Usuwa określone pliki.

## <a name="parameters"></a>Parametry

W poniższej tabeli `Delete` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DeletedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa pliki, które zostały pomyślnie usunięte.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do usunięcia.|
|`TreatErrorsAsWarnings`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli `true`błędy są rejestrowane jako ostrzeżenia. Wartością domyślną jest `false`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Należy zachować ostrożność podczas korzystania `Delete` z symboli wieloznacznych z zadaniem. Można łatwo usunąć niewłaściwe pliki z `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*`wyrażeniami, takimi jak lub , zwłaszcza jeśli `Files` właściwość ma wartość pustego ciągu, w którym to przypadku parametr może ocenić do katalogu głównego dysku i usunąć znacznie więcej niż chcesz usunąć.

## <a name="example"></a>Przykład

Poniższy przykład usuwa plik *MyApp.pdb*.

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

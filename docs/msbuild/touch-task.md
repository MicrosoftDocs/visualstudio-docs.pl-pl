---
title: Touch — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96bf92f6e0649a2d1eedda63d6159c3de95ae6bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938859"
---
# <a name="touch-task"></a>Touch — Zadanie
Ustawia czas dostępu i modyfikacji plików.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `Touch` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AlwaysCreate`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy pliki, które jeszcze nie istnieje.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa kolekcję plików touch.|
|`ForceTouch`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, wymusza touch plików, nawet jeśli pliki są tylko do odczytu.|
|`Time`|Opcjonalnie `String` parametru.<br /><br /> Określa czas niż bieżący czas. Format musi być w formacie, który jest dopuszczalne <xref:System.DateTime.Parse%2A> metody.|
|`TouchedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera kolekcję elementów, które zostały pomyślnie korzystał z usług.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto `Touch` zadanie, aby zmienić czas dostępu i modyfikacji plików określonych w `Files` elementu kolekcji i umieszcza na liście pomyślnie modyfikacji plików w `FilesTouched` elementu kolekcji.

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
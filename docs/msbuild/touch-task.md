---
title: Zadanie dotykowe | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 873783196a3eebdaca9cc4278b091e084c1488b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631656"
---
# <a name="touch-task"></a>Touch — Zadanie

Ustawia czasy dostępu i modyfikacji plików.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `Touch` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AlwaysCreate`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, tworzy wszystkie pliki, które jeszcze nie istnieją.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa kolekcję plików do dotknięcia.|
|`ForceTouch`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program wymusza dotknięcie pliku, nawet jeśli pliki są tylko do odczytu.|
|`Time`|Parametr `String` opcjonalny.<br /><br /> Określa czas inny niż bieżący czas. Format musi być formatem, który <xref:System.DateTime.Parse%2A> jest dopuszczalny dla metody.|
|`TouchedFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera kolekcję elementów, które zostały pomyślnie dotknął.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 W poniższym `Touch` przykładzie użyto zadania, aby zmienić czasy dostępu i modyfikacji plików określonych w kolekcji `Files` elementów i umieszcza listę pomyślnie dotknął plików w kolekcji `FilesTouched` elementów.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

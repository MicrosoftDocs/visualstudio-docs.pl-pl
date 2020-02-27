---
title: Element zadania elementu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4364e6c3f637fdf2c3e02a52d3163e5cdd8a5861
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634334"
---
# <a name="createitem-task"></a>CreateItem — zadanie

Wypełnia kolekcje elementów elementami wejściowymi. Umożliwia to skopiowanie elementów z jednej listy do innej.

> [!NOTE]
> To zadanie jest przestarzałe. Począwszy od .NET Framework 3,5, grupy elementów mogą być umieszczane w elementach [docelowych](../msbuild/target-element-msbuild.md) . Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

## <a name="attributes"></a>Atrybuty

 W poniższej tabeli opisano parametry zadania `CreateItem`.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalMetadata`|Opcjonalny `String` parametr tablicy.<br /><br /> Określa dodatkowe metadane do dołączenia do elementów danych wyjściowych.  Określ nazwę i wartość metadanych dla elementu przy użyciu następującej składni:<br /><br /> *MetadataValue* `=`<br /><br /> Wiele par nazwa/wartość metadanych powinna być oddzielona średnikami. Jeśli nazwa lub wartość zawiera średnik lub dowolne inne znaki specjalne, muszą one być zmienione. Aby uzyskać więcej informacji, zobacz [jak: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Określa elementy, które mają zostać wykluczone z kolekcji elementów wyjściowych. Ten parametr może zawierać specyfikacje symboli wieloznacznych. Aby uzyskać więcej informacji, zobacz [elementy](../msbuild/msbuild-items.md) i [instrukcje: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).|
|`Include`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem>parametr `[]`.<br /><br /> Określa elementy do uwzględnienia w kolekcji elementów wyjściowych. Ten parametr może zawierać specyfikacje symboli wieloznacznych.|
|`PreserveExistingMetadata`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `True`, należy zastosować dodatkowe metadane, jeśli jeszcze nie istnieją.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu tworzy nową kolekcję elementów o nazwie `MySourceItemsWithMetadata` z kolekcji Item `MySourceItems`. Zadanie `CreateItem` wypełnia kolekcję nowych elementów elementami w `MySourceItems` elemencie. Następnie dodaje dodatkowy wpis metadanych o nazwie `MyMetadata` z wartością `Hello` do każdego elementu w nowej kolekcji.

 Po wykonaniu zadania kolekcja `MySourceItemsWithMetadata` elementów zawiera elementy *plik1. resx* i *plik2. resx*z wpisami metadanych dla `MyMetadata`. Kolekcja elementów `MySourceItems` nie została zmieniona.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceItems Include="file1.resx;file2.resx" />
    </ItemGroup>

    <Target Name="NewItems">
        <CreateItem
            Include="@(MySourceItems)"
            AdditionalMetadata="MyMetadata=Hello">
           <Output
               TaskParameter="Include"
               ItemName="MySourceItemsWithMetadata"/>
        </CreateItem>

    </Target>

</Project>
```

 W poniższej tabeli opisano wartość elementu wyjściowego po wykonaniu zadania. Metadane elementu są wyświetlane w nawiasach po elemencie.

|Kolekcja elementów|Spis treści|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*plik1. resx* (`MyMetadata="Hello"`)<br /><br /> *plik2. resx* (`MyMetadata="Hello"`)|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

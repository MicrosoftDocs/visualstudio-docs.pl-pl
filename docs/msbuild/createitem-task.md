---
title: Tworzenie zadania elementu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634334"
---
# <a name="createitem-task"></a>CreateItem — zadanie

Wypełnia kolekcje towarów za pomocą elementów wejściowych. Dzięki temu elementy mogą być kopiowane z jednej listy do drugiej.

> [!NOTE]
> To zadanie jest przestarzałe. Począwszy od programu .NET Framework 3.5, grupy elementów mogą być umieszczane w elementach [docelowych.](../msbuild/target-element-msbuild.md) Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md).

## <a name="attributes"></a>Atrybuty

 W poniższej tabeli `CreateItem` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalMetadata`|Opcjonalny `String` parametr tablicy.<br /><br /> Określa dodatkowe metadane do dołączenia do elementów wyjściowych.  Określ nazwę i wartość metadanych elementu z następującą składnią:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Wiele par nazw metadanych/wartości należy rozdzielić średnikiem. Jeśli nazwa lub wartość zawiera średnik lub inne znaki specjalne, muszą one zostać zmienione. Aby uzyskać więcej informacji, zobacz [Jak: Ucieczka znaków specjalnych w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa elementy, które mają być wykluczone z kolekcji elementów wyjściowych. Ten parametr może zawierać dane techniczne symboli wieloznacznych. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md) i [Jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).|
|`Include`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametr.<br /><br /> Określa elementy, które mają być uwzględnione w kolekcji elementów wyjściowych. Ten parametr może zawierać dane techniczne symboli wieloznacznych.|
|`PreserveExistingMetadata`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `True`, zastosuj dodatkowe metadane tylko wtedy, gdy jeszcze nie istnieją.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu tworzy nową `MySourceItemsWithMetadata` kolekcję `MySourceItems`towarów o nazwie z kolekcji towarów . Zadanie `CreateItem` wypełnia kolekcję nowego elementu elementami `MySourceItems` w elemencie. Następnie dodaje dodatkowy wpis metadanych o nazwie `MyMetadata` z wartością `Hello` do każdego elementu w nowej kolekcji.

 Po wykonaniu zadania kolekcja `MySourceItemsWithMetadata` elementów zawiera elementy *file1.resx* i *file2.resx,* oba `MyMetadata`z wpisami metadanych dla . Kolekcja `MySourceItems` towarów pozostaje niezmieniona.

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

 W poniższej tabeli opisano wartość elementu wyjściowego po wykonaniu zadania. Metadane elementu są wyświetlane w nawiasie po elemencie.

|Kolekcja przedmiotów|Spis treści|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*plik1.resx* `MyMetadata="Hello"`( )<br /><br /> *plik2.resx* `MyMetadata="Hello"`( )|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

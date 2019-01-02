---
title: Createitem — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50b1f56be7b32bd21b9b5785caac003b7ee86d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860887"
---
# <a name="createitem-task"></a>CreateItem — zadanie
Wypełnia kolekcji elementów z elementów wejściowych. Dzięki temu elementy, które mają być kopiowane z jednej listy do innej.  
  
> [!NOTE]
>  To zadanie jest przestarzały. Począwszy od programu .NET Framework 3.5, element grupy mogą być wprowadzane w ramach [docelowej](../msbuild/target-element-msbuild.md) elementów. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Atrybuty  
 W poniższej tabeli opisano parametry `CreateItem` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalMetadata`|Opcjonalnie `String` tablicy parametrów.<br /><br /> Określa dodatkowe metadane, aby dołączyć do elementów wyjściowych.  Określ nazwę metadanych i wartość dla elementu przy użyciu następującej składni:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Wiele pary nazwa/wartość metadanych powinny być oddzielone średnikami. Jeśli nazwa lub wartość zawiera średnikami lub innych znaków specjalnych, muszą być wyjściowym. Aby uzyskać więcej informacji, zobacz [jak: Znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa elementy, które mają zostać wykluczone z kolekcji element danych wyjściowych. Ten parametr może zawierać specyfikacji symbolu wieloznacznego. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md) i [jak: Wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.<br /><br /> Określa elementy do uwzględnienia w kolekcji elementów danych wyjściowych. Ten parametr może zawierać specyfikacji symbolu wieloznacznego.|  
|`PreserveExistingMetadata`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `True`, dodatkowe metadane stosowane tylko wtedy, jeśli jeszcze nie istnieje.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy nową kolekcję elementów o nazwie `MySourceItemsWithMetadata` z kolekcji element `MySourceItems`. `CreateItem` Zadań wypełnia nową kolekcję elementów z elementami w `MySourceItems` elementu. Następnie dodaje wpis dodatkowe metadane o nazwie `MyMetadata` o wartości `Hello` do każdego elementu, do nowej kolekcji.  
  
 Po wykonaniu zadania `MySourceItemsWithMetadata` kolekcji elementów zawiera elementy *file1.resx* i *file2.resx*, oba metadata wpisy dla `MyMetadata`. `MySourceItems` Kolekcji elementów pozostaje niezmieniony.  
  
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
  
 W poniższej tabeli opisano wartość elementu danych wyjściowych po wykonaniu zadania. Metadane elementu jest wyświetlany w nawiasie po elemencie.  
  
|Kolekcja elementów|Spis treści|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|*File1.resx* (`MyMetadata="Hello"`)<br /><br /> *file2.resx* (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
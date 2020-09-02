---
title: WriteLinesToFile — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f530648c7dd772fb60148f4d755d4a4ffb420cbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419962"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje ścieżki określonych elementów do określonego pliku tekstowego.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `WriteLinestoFile` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`File`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik, do którego mają zostać zapisane elementy.|  
|`Lines`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa elementy do zapisu w pliku.|  
|`Overwrite`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` zadanie zastąpi istniejącą zawartość pliku.|  
|`Encoding`|Opcjonalny `String` parametr.<br /><br /> Wybiera kodowanie znaków, na przykład "Unicode".  Zobacz też <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `Overwrite` jest `true` , tworzy nowy plik, zapisuje zawartość w pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie nadpisany. Jeśli `Overwrite` jest `false` , dołącza zawartość do pliku, tworząc plik docelowy, jeśli jeszcze nie istnieje.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zadania, `WriteLinesToFile` Aby zapisać ścieżki elementów w `MyItems` kolekcji elementów do pliku określonego przez `MyTextFile` kolekcję elementów.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

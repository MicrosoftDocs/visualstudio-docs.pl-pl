---
title: Dotknięcie zadania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144259"
---
# <a name="touch-task"></a>Touch — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
```  
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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

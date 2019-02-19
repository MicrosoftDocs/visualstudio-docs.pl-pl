---
title: Touch — zadanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: eb0ab3daf6d23d9a70a9889479bdf6a19ddec041
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54762560"
---
# <a name="touch-task"></a>Touch — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

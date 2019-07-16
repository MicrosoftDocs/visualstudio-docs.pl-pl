---
title: 'Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93451d6d49082621df48c734de951e6a4bc7e281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156622"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Instrukcje: Wyświetlanie listy elementów rozdzielanych przecinkami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas pracy z elementu listy w [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]), czasami jest to przydatne do wyświetlania zawartości listy tych elementów w sposób, który jest łatwy do odczytania. Lub możesz mieć do zadań, która przyjmuje listę elementów oddzielonych specjalne separatora. W obu przypadkach można określić ciąg separatora listy elementów.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Oddziel przecinkami elementów na liście  
 Domyślnie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa średników do oddzielania elementów listy. Na przykład, rozważmy `Message` element z następujących wartości:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Gdy `@(TXTFile)` listy elementów zawiera elementy App1.txt, App2.txt i App3.txt, komunikat:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Jeśli chcesz zmienić domyślne zachowanie, możesz określić własne separatora. Składnia określająca element separatora listy jest następująca:  
  
 `@(ItemListName, '<separator>')`  
  
 Separator może być pojedynczy znak lub ciąg, a musi być ujęta w apostrofy.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Aby wstawić przecinek i spację między elementami  
  
- Notacja elementu podobny do następującego:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [Exec](../msbuild/exec-task.md) zadanie jest uruchamiane narzędzie findstr, aby znaleźć ciągów tekstowych określonej w pliku Phrases.txt. W poleceniu findstr literałów ciągów znaków są wskazywane przez **/c:** przełączyć, więc separator elementów `/c:` jest wstawiany między elementami w `@(Phrase)` listy elementów.  
  
 W tym przykładzie jest równoważne wiersza polecenia:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)

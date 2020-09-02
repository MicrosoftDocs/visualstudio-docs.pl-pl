---
title: 'Instrukcje: znaki specjalne ucieczki w MSBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178348"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Porady: znaki specjalne ucieczki w MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre znaki mają specjalne znaczenie w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plikach projektu. Przykłady znaków obejmują średnika (;) i gwiazdki (*). Aby uzyskać pełną listę tych znaków specjalnych, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Aby można było używać tych znaków specjalnych jako literałów w pliku projektu, muszą one być określone przy użyciu składni%*XX*, gdzie *XX* reprezentuje wartość szesnastkową ASCII znaku.  
  
## <a name="msbuild-special-characters"></a>Znaki specjalne w programie MSBuild  
 Przykładem miejsca, w którym są używane znaki specjalne, znajduje się w `Include` atrybucie list elementów. Na przykład następująca lista elementów deklaruje dwa elementy: `MyFile.cs` i `MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Jeśli chcesz zadeklarować element, który zawiera średnik w nazwie, należy użyć składni%*XX* , aby wyjść z średnika i zapobiec [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] deklarowaniu dwóch oddzielnych elementów. Na przykład poniższy element wyprowadza średnik i deklaruje jeden element o nazwie `MyFile.cs;MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Aby użyć znaku specjalnego MSBuild jako znaku literału  
  
- Użyj notacji%*XX* zamiast znaku specjalnego, gdzie *XX* reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znaku literału, użyj wartości `%2A` .  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md) [Elementy](../msbuild/msbuild-items.md) programu MSBuild

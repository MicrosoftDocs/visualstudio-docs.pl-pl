---
title: Tworzenie wsadowe MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799393"
---
# <a name="msbuild-batching"></a>Przetwarzanie wsadowe w programie MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Program ma możliwość dzielenia list elementów na różne kategorie lub partie, na podstawie metadanych elementów i uruchamiania obiektu docelowego lub zadania jednokrotnie przy każdej partii.  
  
## <a name="task-batching"></a>Tworzenie partii zadań  
 Tworzenie wsadowe zadań pozwala uprościć pliki projektu, zapewniając sposób dzielenia list elementów na różne partie i przekazywanie poszczególnych partii do zadania oddzielnie. Oznacza to, że plik projektu musi mieć tylko jedno zadanie i jego atrybuty, nawet jeśli można wykonać kilka razy.  
  
 Należy określić, że chcesz [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wykonać operację wsadową z zadaniem przy użyciu notacji%(*ItemMetaDataName*) w jednym z atrybutów zadania. Poniższy przykład dzieli `Example` listę elementów na partie na podstawie `Color` wartości metadanych elementu i przekazuje poszczególne partie do `MyTask` zadania oddzielnie.  
  
> [!NOTE]
> Jeśli nie odwołuje się do listy elementów w innym miejscu atrybutów zadania lub nazwa metadanych może być niejednoznaczna, można użyć notacji%(*obiekt ItemCollection. ItemMetaDataName*), aby w pełni kwalifikować wartość metadanych elementu do użycia podczas tworzenia partii.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Aby zapoznać się z bardziej szczegółowymi przykładami wsadowymi, zobacz [metadane elementu w partii zadań](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Przetwarzanie wsadowe docelowe  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sprawdza, czy dane wejściowe i wyjściowe elementu docelowego są aktualne przed uruchomieniem obiektu docelowego. Jeśli dane wejściowe i wyjściowe są aktualne, element docelowy jest pomijany. Jeśli zadanie wewnątrz obiektu docelowego używa tworzenia pakietów wsadowych, należy [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] określić, czy dane wejściowe i wyjściowe dla każdej partii elementów są aktualne. W przeciwnym razie obiekt docelowy jest wykonywany za każdym razem, gdy zostanie osiągnięty.  
  
 Poniższy przykład pokazuje `Target` element, który zawiera `Outputs` atrybut z notacją%(*ItemMetaDataName*). [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podzieli `Example` listę elementów na partie na podstawie `Color` metadanych elementu i analizuje sygnatury czasowe plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z partii nie są aktualne, obiekt docelowy jest uruchamiany. W przeciwnym razie element docelowy zostanie pominięty.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Aby uzyskać inny przykład tworzenia wsadowych obiektów docelowych, zobacz [metadane elementu w przetwarzaniu wsadowym](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funkcje właściwości korzystające z metadanych  
 Przetwarzanie wsadowe może być kontrolowane przez funkcje właściwości, które obejmują metadane. Przykład:  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 używa <xref:System.IO.Path.Combine%2A> do łączenia ścieżki folderu głównego z ścieżką elementu kompilacji.  
  
 Funkcje właściwości mogą nie występować w obrębie wartości metadanych.  Przykład:  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 nie jest dozwolone.  
  
 Aby uzyskać więcej informacji na temat funkcji właściwości, zobacz [funkcje właściwości](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)

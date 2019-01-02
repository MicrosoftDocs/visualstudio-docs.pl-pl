---
title: Przetwarzanie wsadowe MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b5f5f2a4d45500e9d96926d856f4895a1a144dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888013"
---
# <a name="msbuild-batching"></a>Przetwarzanie wsadowe programu MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ma możliwość podzielić listy elementów na różnych kategorii lub serii, na podstawie metadanych elementu i uruchom docelowego lub zadanie jeden raz z każdej partii.  
  
## <a name="task-batching"></a>Przetwarzanie wsadowe zadań  
 Przetwarzanie wsadowe zadań umożliwia uproszczenie plików projektu, umożliwiając podzielić listy elementów na różnych partii i przekazanie każdego wskaźnika tych partii w zadanie oddzielnie. Oznacza to, że plik projektu tylko trzeba zadania i jego atrybutów zadeklarowany raz, nawet kilka razy może zostać uruchomione.  
  
 Określ, czy program [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania przetwarzania wsadowego za pomocą zadania przy użyciu %(\<ItemMetaDataName >) Notacja w jeden z atrybutów zadania. Poniższy przykład dzieli `Example` na podstawie listy elementów w partie `Color` wartość metadanych elementu i przekazuje partii do `MyTask` zadań oddzielnie.  
  
> [!NOTE]
>  Jeśli użytkownik nie odwołują się do listy elementów w innym miejscu w atrybutach zadania lub nazwa metadanych może być niejednoznaczna, możesz użyć %(\<ItemCollection.ItemMetaDataName >) Notacja do pełnej kwalifikacji wartość elementu metadanych na potrzeby przetwarzania wsadowego.  
  
```xml  
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
  
 Aby uzyskać bardziej szczegółowe przykłady przetwarzania wsadowego, zobacz [metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Przetwarzaniu wsadowym obiektów docelowych  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sprawdza, jeśli dane wejściowe i wyjściowe, obiektu docelowego są aktualne przed uruchomieniem element docelowy. Jeśli zarówno dane wejściowe i wyjściowe są aktualne, element docelowy jest pomijany. Jeśli zadanie w celu korzysta z dzielenia na partie, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] potrzebuje do ustalenia, czy dane wejściowe i wyjściowe dla każdego zestawu elementów jest aktualny. W przeciwnym razie element docelowy jest wykonywane za każdym razem, gdy jego osiągnięciu.  
  
 W poniższym przykładzie przedstawiono `Target` element, który zawiera `Outputs` atrybutem %(\<ItemMetaDataName >) notacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Dzieli `Example` na podstawie listy elementów w partie `Color` elementu metadanych i analizowanie znacznikami czasu plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z usługi batch nie są aktualne, element docelowy zostanie uruchomiony. W przeciwnym razie element docelowy jest pomijany.  
  
```xml  
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
  
 Aby uzyskać inny przykład przetwarzaniu wsadowym obiektów docelowych, zobacz [metadane elementu w przetwarzaniu wsadowym obiektów docelowych](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funkcje właściwości przy użyciu metadanych  
 Przetwarzanie wsadowe mogą być kontrolowane przez funkcje właściwości, które zawierają metadane. Na przykład  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 używa <xref:System.IO.Path.Combine%2A> połączyć ścieżka do folderu głównego, przy użyciu ścieżki elementu kompilacji.  
  
 Funkcje właściwości nie może występować w wartości metadanych.  Na przykład  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 nie jest dozwolone.  
  
 Aby uzyskać więcej informacji na temat funkcji właściwości, zobacz [funkcji właściwości](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Itemmetadata — element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
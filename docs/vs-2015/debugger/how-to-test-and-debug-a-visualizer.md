---
title: 'Instrukcje: testowanie i debugowanie wizualizatora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18261d9e8c6c7d3f65dea7c72439b29f4e2e0df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176504"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Porady: testowanie i debugowanie wizualizera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po napisaniu wizualizatora należy go debugować i testować.  
  
 Jednym ze sposobów przetestowania wizualizatora jest zainstalowanie go w programie Visual Studio i wywołanie go z okna debugera. (Zobacz [How to: Install the wizualizatorer](../debugger/how-to-install-a-visualizer.md)). Jeśli to zrobisz, musisz użyć drugiego wystąpienia programu Visual Studio do dołączenia i debugowania wizualizatora, który jest uruchomiony w pierwszym wystąpieniu debugera.  
  
 Łatwiejszym sposobem debugowania wizualizatora jest uruchomienie wizualizatora z sterownika testowego. Interfejsy API wizualizatora ułatwiają tworzenie takiego sterownika, który jest nazywany *hostem deweloperskim wizualizatora*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Aby utworzyć wizualizację hosta do programowania  
  
1. W klasie po stronie debugera Dołącz metodę statyczną, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiekt i wywołuje jego metodę show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Parametry używane do konstruowania hosta są obiektem danych, który będzie wyświetlany w wizualizatorze ( `objectToVisualize` ) i typie klasy po stronie debugera.  
  
2. Dodaj następującą instrukcję, aby wywołać metodę `TestShowVisualizer` . Jeśli utworzono wizualizator w bibliotece klas, musisz utworzyć plik wykonywalny, aby wywołać bibliotekę klas i umieścić tę instrukcję w pliku wykonywalnym:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Aby zapoznać się z bardziej kompletnym przykładem, zobacz [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: pisanie wizualizatora w języku C #](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

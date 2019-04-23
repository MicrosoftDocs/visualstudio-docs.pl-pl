---
title: 'Instrukcje: Testowanie i debugowanie Wizualizera | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044099"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Instrukcje: Testowanie i debugowanie Wizualizera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po napisaniu wizualizatora, należy do debugowania i testowania.  
  
 Jednym ze sposobów, aby przetestować Wizualizator jest zamontowany w programie Visual Studio i wywoływania go z okna debugera. (Zobacz [jak: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md).) Jeśli to zrobisz, musisz użyć drugiego wystąpienia programu Visual Studio do dołączenia i debugowanie wizualizatora, w którym jest uruchomiony w pierwszej kolejności debugera.  
  
 Łatwiejsze debugowanie wizualizera jest przeprowadzić wizualizatora sterowniku testu. Wizualizator interfejsów API ułatwiają tworzenie takich sterownika, który jest nazywany *hosta rozwoju Wizualizator*.  
  
### <a name="to-create-a-visualizer-development-host"></a>W celu utworzenia hosta rozwoju wizualizatora  
  
1. W klasie po stronie debugera zawierają statycznej metody, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiektów i wywołuje swoją metodę show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Parametry używane do konstruowania hosta jest obiekt danych, który ma być wyświetlany w wizualizatorze (`objectToVisualize`) i typ klasy po stronie debugera.  
  
2. Dodaj następującą instrukcję, aby wywołać `TestShowVisualizer`. Jeśli Twoje visualizer został utworzony w bibliotece klas, musisz utworzyć plik wykonywalny do wywołania biblioteki klas i umieszczania tej instrukcji w plik wykonywalny:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Aby uzyskać pełniejszy przykład, zobacz [instruktażu: Pisanie wizualizatora w C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Instrukcje: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

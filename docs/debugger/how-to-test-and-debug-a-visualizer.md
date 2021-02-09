---
title: Testowanie i debugowanie wizualizatora | Microsoft Docs
description: Przetestuj i Debuguj wizualizator, uruchamiając go ze sterownika testowego (hosta programowania wizualizatora) lub instalując program w programie Visual Studio i wywołując go z okna debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b01c97c0ee72a3d29052d98d8a37cdc746c26d27
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923280"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Porady: testowanie i debugowanie wizualizera
Po napisaniu wizualizatora należy go debugować i testować.

Jednym ze sposobów przetestowania wizualizatora jest zainstalowanie go w programie Visual Studio i wywołanie go z okna debugera. (Zobacz [How to: Install the wizualizatorer](../debugger/how-to-install-a-visualizer.md)). Jeśli to zrobisz, musisz użyć drugiego wystąpienia programu Visual Studio do dołączenia i debugowania wizualizatora, który jest uruchomiony w pierwszym wystąpieniu debugera.

Łatwiejszym sposobem debugowania wizualizatora jest uruchomienie wizualizatora z sterownika testowego. Interfejsy API wizualizatora ułatwiają tworzenie takiego sterownika, który jest nazywany *hostem deweloperskim wizualizatora*.

### <a name="to-create-a-visualizer-development-host"></a>Aby utworzyć wizualizację hosta do programowania

1. W klasie po stronie debugera Dołącz metodę statyczną, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiekt i wywołuje jego metodę show:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Parametry używane do konstruowania hosta są obiektem danych, który będzie wyświetlany w wizualizatorze ( `objectToVisualize` ) i typie klasy po stronie debugera.

2. Dodaj następującą instrukcję, aby wywołać metodę `TestShowVisualizer` . Jeśli utworzono wizualizator w bibliotece klas, musisz utworzyć plik wykonywalny, aby wywołać bibliotekę klas i umieścić tę instrukcję w pliku wykonywalnym:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Aby zapoznać się z bardziej kompletnym przykładem, zobacz [Przewodnik: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

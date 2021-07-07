---
title: Testowanie i debugowanie narzędzia Visualizer | Microsoft Docs
description: Przetestuj i debuguj wizualizator, uruchamiając go ze sterownika testowego (hosta dewelopera wizualizatora) lub instalując w programie Visual Studio i wywołując go z okna debugera.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
ms.openlocfilehash: fa97453d08650b78a02eda873a01afe9e376caec
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298247"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Porady: testowanie i debugowanie wizualizera
Po napisie wizualizatora musisz go debugować i przetestować.

Jednym ze sposobów testowania wizualizatora jest zainstalowanie go w Visual Studio wywołaniu go z okna debugera. (Zobacz [Instalowania wizualizatora).](../debugger/how-to-install-a-visualizer.md) Jeśli to zrobisz, konieczne będzie użycie drugiego wystąpienia klasy Visual Studio w celu dołączenia i debugowania wizualizatora, który jest uruchomiony w pierwszym wystąpieniu debugera.

Łatwiejszym sposobem debugowania wizualizatora jest uruchomienie wizualizatora z sterownika testowego. Interfejsy API wizualizatora ułatwiają tworzenie takiego sterownika, który jest nazywany hostem *dewelopera wizualizatora*.

>[!NOTE]
> Obecnie sterownik testowy jest obsługiwany tylko podczas wywoływania wizualizatora z .NET Framework aplikacji.

### <a name="to-create-a-visualizer-development-host"></a>Aby utworzyć hosta dewelopera wizualizatora

1. W klasie po stronie debugera uwzględnij metodę statyczną, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiekt i wywołuje jego metodę show:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Parametry używane do konstruowania hosta to obiekt danych, który będzie wyświetlany w wizualizatorze ( ) i typ `objectToVisualize` klasy po stronie debugera.

2. Dodaj następującą instrukcje w celu `TestShowVisualizer` wywołania . Jeśli wizualizator został utworzony w bibliotece klas, musisz utworzyć plik wykonywalny, aby wywołać bibliotekę klas i umieścić tę instrukcje w pliku wykonywalnym:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Aby uzyskać bardziej szczegółowy przykład, zobacz [Przewodnik: pisanie wizualizatora w języku C#.](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)

## <a name="see-also"></a>Zobacz też
- [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

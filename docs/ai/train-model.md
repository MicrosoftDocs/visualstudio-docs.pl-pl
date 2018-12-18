---
title: Prześlij zadanie uczenia modelu w usłudze Azure Batch AI
description: uczenie modelu chmury
keywords: sztuczna inteligencja, program visual studio, train model chmury
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: 6fd6f8befce66a117f5f2dcb598a7359ba9c15c0
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307648"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trenowanie modeli sztucznej Inteligencji w usłudze Azure Batch AI

Usługa Batch AI to zarządzana usługa, która umożliwia analitykom danych i badaczom SI trenowanie SI i innych modeli uczenia maszynowego w klastrach maszyn wirtualnych platformy Azure, łącznie z maszynami wirtualnymi z obsługą procesorów GPU. Opisuje wymagania dotyczące zadania, aby znaleźć dane wejściowe i przechowywania danych wyjściowych, a usługa Batch AI obsługuje pozostałe. [Dowiedz się więcej na temat usługi Azure Batch AI](https://docs.microsoft.com/azure/batch-ai/overview)

Jest zintegrowany z Visual Studio Tools dla sztucznej Inteligencji, dzięki czemu można dynamicznie skalować w poziomie szkolenie modeli na platformie Azure.  Po [zainstalowany program Visual Studio Tools for AI](installation.md), ułatwia utworzenie nowego projektu języka Python za pomocą wstępnie przygotowanych przepisy w galerii przykładów usługi Azure Machine Learning.

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwera** , otwierając **narzędzia si** menu i wybierając pozycję **wybierz klastra**

    ![Selektor klastra](media/train-model/select-cluster.png)

2. Rozwiń **narzędzia si**. Wszystkie zasoby usługi Batch AI, w których masz będzie można automatycznie wykryte i są wyświetlane w Eksploratorze serwera.

    ![Galeria przykładów](media/train-model/batchai.png)

3. Wybierz **Widok > Team Explorer...**  otworzyć **Team Explorer** okna, w którym można połączyć się z usługi GitHub lub DevOps platformy Azure lub klonowanie repozytorium.

    ![Okno Eksploratora zespołu DevOps platformy Azure, usługi GitHub, wyświetlanie i klonowanie repozytorium](media/train-model/team-explorer.png)

4. W polu adres URL w taki sposób, w obszarze **lokalne repozytoria Git**, wprowadź `https://github.com/Microsoft/samples-for-ai`, wprowadź folderu na sklonowane pliki i wybierz **klonowania**.

    > [!Tip]
    > Folder, który określisz w programie Team Explorer jest dany folder do odbierania sklonowane pliki. W odróżnieniu od `git clone` polecenia Tworzenie własnego klonu w programie Team Explorer nie tworzy automatycznie podfolder o nazwie repozytorium.

5. Po ukończeniu klonowania kliknij **Plik > Otwórz rozwiązanie > Projekt / rozwiązanie**

    ![Galeria przykładów](media/train-model/open-solution.png)

6. Otwórz **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w katalogu sklonowane repozytorium

    ![Galeria przykładów](media/train-model/tensorflowexamples.png)

7. Zestaw mnist ręcznie ZAPISANYCH projektu jako **projekt startowy**

    ![Galeria przykładów](media/train-model/mnist-startup.png)

8. <strong>Kliknij prawym przyciskiem myszy **projektu mnist ręcznie ZAPISANYCH** **Prześlij zadanie**</strong>

    ![Galeria przykładów](media/train-model/submit-job.png)
9. Wybierz swoje **usługi Azure Batch AI** klastra, a następnie kliknij przycisk **importu**. Wybierz `AzureBatchAI_TF_MNIST.json` plik, aby szybko wypełnić niektóre wartości domyślnych, takich jak obraz platformy Docker do użycia. Następnie kliknij przycisk **przesyłania**

    ![Galeria przykładów](media/train-model/submit-batch.png)

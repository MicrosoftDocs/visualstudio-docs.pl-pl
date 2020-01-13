---
title: Prześlij zadanie do uczenia modelu w Azure Batch AI
description: uczenie modelu w chmurze
keywords: AI, Visual Studio, model uczenia, Chmura
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: dec70c9e9aeb9c916b511241a74b550354aff175
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915773"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Uczenie modeli AI w Azure Batch AI

Batch AI to zarządzana usługa umożliwiająca analitykom danych i badaczom SI trenowanie SI i innych modeli uczenia maszynowego w klastrach maszyn wirtualnych platformy Azure łącznie z maszynami wirtualnymi i wsparciem procesora GPU. Użytkownik opisuje wymagania dotyczące zadania, miejsce wyszukiwania danych wejściowych oraz miejsce przechowywania danych wyjściowych, a usługa Batch AI zajmuje się resztą. [Dowiedz się więcej o Azure Batch AI](/azure/batch-ai/overview)

Jest ona zintegrowana z Visual Studio Tools for AI, dzięki czemu można dynamicznie skalować modele szkoleniowe na platformie Azure.  Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt w języku Python przy użyciu wstępnych przepisów w galerii przykładów Azure Machine Learning.

1. Uruchom program Visual Studio. Otwórz **Eksplorator serwera** , otwierając menu **narzędzia AI** i wybierając **pozycję Wybierz klaster** .

    ![Wybór klastra](media/train-model/select-cluster.png)

2. Rozwiń węzeł **narzędzia AI**. Wszystkie Batch AI zasoby będą wykrywane i wyświetlane w Eksplorator serwera.

    ![Galeria przykładów](media/train-model/batchai.png)

3. Wybierz pozycję **wyświetl > Team Explorer...** , aby otworzyć okno **Team Explorer** , w którym można nawiązać połączenie z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno programu Team Explorer pokazujące platformę Azure DevOps, GitHub i klonowanie repozytorium](media/train-model/team-explorer-devops.png)

4. W polu adres URL w obszarze **lokalne repozytoria Git**wprowadź `https://github.com/Microsoft/samples-for-ai`, wprowadź folder dla sklonowanych plików, a następnie wybierz pozycję **Klonuj**.

    > [!Tip]
    > Folder określony w Team Explorer jest folderem, w którym mają zostać odebrane sklonowane pliki. W przeciwieństwie do polecenia `git clone`, utworzenie klonu w Team Explorer nie powoduje automatycznego utworzenia podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij pozycję **plik > Otwórz rozwiązanie > projektu/rozwiązania**

    ![Galeria przykładów](media/train-model/open-solution.png)

6. Otwórz **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w katalogu sklonowanym repozytorium

    ![Galeria przykładów](media/train-model/tensorflowexamples.png)

7. Ustaw projekt MNIST ręcznie jako **projekt startowy**

    ![Galeria przykładów](media/train-model/mnist-startup.png)

8. <strong>Kliknij prawym przyciskiem myszy **projekt mnist ręcznie,** **Prześlij zadanie**</strong>

    ![Galeria przykładów](media/train-model/submit-job.png)
9. Wybierz klaster **Azure Batch AI** , a następnie kliknij przycisk **Importuj**. Wybierz plik `AzureBatchAI_TF_MNIST.json`, aby szybko wypełnić niektóre wartości domyślne, takie jak obraz platformy Docker, który ma być używany. Następnie kliknij przycisk **Prześlij**

    ![Galeria przykładów](media/train-model/submit-batch.png)

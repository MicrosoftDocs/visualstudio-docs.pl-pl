---
title: Prześlij zadanie, aby nauczyć model
description: Prześlij zadanie, aby nauczyć model przy użyciu Azure Batch AI
ms.custom: SEO-VS-2020
keywords: AI, Visual Studio, model uczenia, Chmura
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: 110468de264370b22d64dae40cf55e9766804c31
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036616"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Uczenie modeli AI w Azure Batch AI

Batch AI to zarządzana usługa, która umożliwia naukowcom zajmującym się danymi oraz badaczom sztucznej inteligencji szkolenie modeli sztucznej inteligencji i innych modeli uczenia maszynowego w klastrach z maszynami wirtualnymi platformy Azure, w tym maszynami wirtualnymi z obsługą procesorów GPU. Użytkownik opisuje wymagania dotyczące zadania, miejsce wyszukiwania danych wejściowych oraz miejsce przechowywania danych wyjściowych, a usługa Batch AI zajmuje się resztą. [Dowiedz się więcej o Azure Batch AI](/azure/batch-ai/overview)

Jest ona zintegrowana z Visual Studio Tools for AI, dzięki czemu można dynamicznie skalować modele szkoleniowe na platformie Azure.  Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt w języku Python przy użyciu wstępnych przepisów w galerii przykładów Azure Machine Learning.

1. Uruchom program Visual Studio. Otwórz **Eksplorator serwera** , otwierając menu **narzędzia AI** i wybierając **pozycję Wybierz klaster** .

    ![Wybór klastra](media/train-model/select-cluster.png)

2. Rozwiń węzeł **narzędzia AI**. Wszystkie Batch AI zasoby będą wykrywane i wyświetlane w Eksplorator serwera.

    ![Galeria przykładów](media/train-model/batchai.png)

3. Wybierz pozycję **wyświetl > Team Explorer...** , aby otworzyć okno **Team Explorer** , w którym można nawiązać połączenie z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno programu Team Explorer pokazujące platformę Azure DevOps, GitHub i klonowanie repozytorium](media/train-model/team-explorer-devops.png)

4. W polu adres URL w obszarze **lokalne repozytoria Git**wprowadź `https://github.com/Microsoft/samples-for-ai` , wprowadź folder dla sklonowanych plików, a następnie wybierz pozycję **Klonuj**.

    > [!Tip]
    > Folder określony w Team Explorer jest folderem, w którym mają zostać odebrane sklonowane pliki. W przeciwieństwie do `git clone` polecenia, utworzenie klonu w Team Explorer nie tworzy automatycznie podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij pozycję **plik > Otwórz rozwiązanie > projektu/rozwiązania**

    ![Galeria przykładów](media/train-model/open-solution.png)

6. Otwórz **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w katalogu sklonowanym repozytorium

    ![Galeria przykładów](media/train-model/tensorflowexamples.png)

7. Ustaw projekt MNIST ręcznie jako **projekt startowy**

    ![Galeria przykładów](media/train-model/mnist-startup.png)

8. <strong>Kliknij prawym przyciskiem myszy **projekt mnist ręcznie,** **Prześlij zadanie**</strong>

    ![Galeria przykładów](media/train-model/submit-job.png)
9. Wybierz klaster **Azure Batch AI** , a następnie kliknij przycisk **Importuj**. Wybierz `AzureBatchAI_TF_MNIST.json` plik, aby szybko wypełnić niektóre wartości domyślne, takie jak obraz platformy Docker, który ma być używany. Następnie kliknij przycisk **Prześlij**

    ![Galeria przykładów](media/train-model/submit-batch.png)

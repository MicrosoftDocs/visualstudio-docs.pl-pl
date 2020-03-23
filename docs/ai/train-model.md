---
title: Prześlij zadanie do szkolenia modelu w usłudze Azure Batch AI
description: pociąg modelu chmury
keywords: ai, studio wizualne, model pociągu, chmura
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: dec70c9e9aeb9c916b511241a74b550354aff175
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75915773"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Trenuj modele sztucznej inteligencji w usłudze Azure Batch AI

Batch AI to zarządzana usługa, która umożliwia naukowcom zajmującym się danymi oraz badaczom sztucznej inteligencji szkolenie modeli sztucznej inteligencji i innych modeli uczenia maszynowego w klastrach z maszynami wirtualnymi platformy Azure, w tym maszynami wirtualnymi z obsługą procesorów GPU. Użytkownik opisuje wymagania dotyczące zadania, miejsce wyszukiwania danych wejściowych oraz miejsce przechowywania danych wyjściowych, a usługa Batch AI zajmuje się resztą. [Dowiedz się więcej o sztucznej inteligencji wsadowej platformy Azure](/azure/batch-ai/overview)

Jest zintegrowany z programem Visual Studio Tools for AI, dzięki czemu można dynamicznie skalować modele szkoleniowe w poziomie na platformie Azure.  Po [zainstalowaniu programu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt języka Python przy użyciu wstępnie utworzonych receptur w galerii przykładów usługi Azure Machine Learning.

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwerów,** otwierając menu **Narzędzia AI** i wybierając **pozycję Wybierz klaster**

    ![Wybór klastra](media/train-model/select-cluster.png)

2. Rozwiń **narzędzia AI**. Wszystkie posiadane zasoby ai partii zostaną automatycznie wykryte i pojawią się w Eksploratorze serwerów.

    ![Przykładowa galeria](media/train-model/batchai.png)

3. Wybierz **opcję Wyświetl > Eksploratorze zespołu...,** aby otworzyć okno **Eksploratora zespołu,** w którym można połączyć się z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno Eksploratora zespołu przedstawiające usługi Azure DevOps, GitHub i klonowanie repozytorium](media/train-model/team-explorer-devops.png)

4. W polu URL w **obszarze Lokalne repozytoria Git**wprowadź , `https://github.com/Microsoft/samples-for-ai`wprowadź folder sklonowanych plików i wybierz opcję **Klonuj**.

    > [!Tip]
    > Folder określony w Eksploratorze zespołu jest specyficznym folderem do odbierania sklonowanych plików. W `git clone` przeciwieństwie do polecenia, utworzenie klona w Eksploratorze zespołu nie powoduje automatycznego utworzenia podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij **przycisk Plik > Otwarte rozwiązanie > projekt / rozwiązanie**

    ![Przykładowa galeria](media/train-model/open-solution.png)

6. Otwórz **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w sklonowanym repozytorium

    ![Przykładowa galeria](media/train-model/tensorflowexamples.png)

7. Ustawianie projektu MNIST jako **projektu startowego**

    ![Przykładowa galeria](media/train-model/mnist-startup.png)

8. <strong>Kliknij prawym przyciskiem myszy **projekt MNIST,** **Prześlij zadanie**</strong>

    ![Przykładowa galeria](media/train-model/submit-job.png)
9. Wybierz klaster **AI usługi Azure Batch,** a następnie kliknij przycisk **Importuj**. Wybierz `AzureBatchAI_TF_MNIST.json` plik, aby szybko wypełnić niektóre wartości domyślne, takie jak obraz platformy Docker do użycia. Następnie kliknij przycisk **Prześlij**

    ![Przykładowa galeria](media/train-model/submit-batch.png)

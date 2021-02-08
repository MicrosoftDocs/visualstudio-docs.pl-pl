---
title: Prześlij zadanie, aby nauczyć model
description: Prześlij zadanie, aby nauczyć model przy użyciu Azure Batch AI
ms.custom: SEO-VS-2020
keywords: AI, Visual Studio, model uczenia, Chmura
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: e1bb1d0bde1b564fe9a35f3527c7b3803c7e9d78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841305"
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Uczenie modeli AI w Azure Batch AI

Batch AI to zarządzana usługa, która umożliwia naukowcom zajmującym się danymi oraz badaczom sztucznej inteligencji szkolenie modeli sztucznej inteligencji i innych modeli uczenia maszynowego w klastrach z maszynami wirtualnymi platformy Azure, w tym maszynami wirtualnymi z obsługą procesorów GPU. Użytkownik opisuje wymagania dotyczące zadania, miejsce wyszukiwania danych wejściowych oraz miejsce przechowywania danych wyjściowych, a usługa Batch AI zajmuje się resztą. [Dowiedz się więcej o Azure Batch AI](/azure/batch-ai/overview)

Jest ona zintegrowana z Visual Studio Tools for AI, dzięki czemu można dynamicznie skalować modele szkoleniowe na platformie Azure.  Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt w języku Python przy użyciu wstępnych przepisów w galerii przykładów Azure Machine Learning.

1. Uruchom program Visual Studio. Otwórz **Eksplorator serwera** , otwierając menu **narzędzia AI** i wybierając **pozycję Wybierz klaster** .

    ![Wybór klastra](media/train-model/select-cluster.png)

2. Rozwiń węzeł **narzędzia AI**. Wszystkie Batch AI zasoby będą wykrywane i wyświetlane w Eksplorator serwera.

    ![Zrzut ekranu przedstawiający rozwinięte drzewo folderów dla narzędzi AI w Eksplorator serwera, w którym wyświetlane są rozbudowane podfoldery Azure Batch AI i Azure Machine Learning.](media/train-model/batchai.png)

3. Wybierz pozycję **wyświetl > Team Explorer...** , aby otworzyć okno **Team Explorer** , w którym można nawiązać połączenie z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno programu Team Explorer pokazujące platformę Azure DevOps, GitHub i klonowanie repozytorium](media/train-model/team-explorer-devops.png)

4. W polu adres URL w obszarze **lokalne repozytoria Git** wprowadź `https://github.com/Microsoft/samples-for-ai` , wprowadź folder dla sklonowanych plików, a następnie wybierz pozycję **Klonuj**.

    > [!Tip]
    > Folder określony w Team Explorer jest folderem, w którym mają zostać odebrane sklonowane pliki. W przeciwieństwie do `git clone` polecenia, utworzenie klonu w Team Explorer nie tworzy automatycznie podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij pozycję **plik > Otwórz rozwiązanie > projektu/rozwiązania**

    ![Zrzut ekranu przedstawiający część menu plik Eksplorator serwera z wybranym poleceniem Otwórz i projekt/rozwiązanie wybrane w menu kontekstowym.](media/train-model/open-solution.png)

6. Otwórz **Samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w katalogu sklonowanym repozytorium

    ![Zrzut ekranu przedstawiający plik rozwiązania TensorflowExamples. sln wymieniony w treści folderu TensorflowExamples w repozytorium Samples-for-AI.](media/train-model/tensorflowexamples.png)

7. Ustaw projekt MNIST ręcznie jako **projekt startowy**

    ![Zrzut ekranu przedstawiający opcję Ustaw jako projekt startowy wybrany w menu kontekstowym dla projektu MNIST ręcznie w Eksplorator rozwiązań.](media/train-model/mnist-startup.png)

8. <strong>Kliknij prawym przyciskiem myszy **projekt mnist ręcznie,** **Prześlij zadanie**</strong>

    ![Zrzut ekranu przedstawiający zadanie przesyłania wybrane w menu kontekstowym dla projektu MNIST ręcznie w Eksplorator rozwiązań.](media/train-model/submit-job.png)
9. Wybierz klaster **Azure Batch AI** , a następnie kliknij przycisk **Importuj**. Wybierz `AzureBatchAI_TF_MNIST.json` plik, aby szybko wypełnić niektóre wartości domyślne, takie jak obraz platformy Docker, który ma być używany. Następnie kliknij przycisk **Prześlij**

    ![Zrzut ekranu okna dialogowego przesyłanie zadania z wartościami wypełninymi dla klastra, skryptu uruchamiania, nazwy zadania, nazwy obrazu, prefiksu ścieżki StdOutErr i parametrów interfejsu wiersza polecenia.](media/train-model/submit-batch.png)

---
title: Tworzenie projektu
description: Tworzenie projektu przy użyciu przykładu z galerii usługi Azure Machine Learning
keywords: AI, Visual Studio, Azure Machine Learning
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: e6c5b8201b39f82e4c4645196ca543e2567b6e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841552"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Tworzenie projektu AI z Galerii Azure Machine Learning w programie Visual Studio

Azure Machine Learning jest zintegrowana z Visual Studio Tools for AI. Można jej użyć do przesyłania zadań uczenia maszynowego do zdalnych celów obliczeniowych, takich jak maszyny wirtualne platformy Azure, klastry Spark i inne. 

Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt w języku Python przy użyciu wstępnych przepisów w galerii przykładów Azure Machine Learning.

> [!NOTE]
> Należy zainstalować Azure Machine Learning Workbench. 

1. Uruchom program Visual Studio. Otwórz **Eksplorator serwera** , otwierając menu **narzędzia AI** i wybierając **pozycję Wybierz klaster** .

    ![Wybór klastra](media/create-project-gallery/select-cluster.png)

2. Zaloguj się do swojej subskrypcji Azure Machine Learning, klikając prawym przyciskiem myszy węzeł **Azure Machine Learning** w Eksplorator serwera następnie wybierz pozycję **Zaloguj** i postępuj zgodnie z instrukcjami.

    ![logowanie](media/create-project-gallery/azureml-login.png)

3. Wybierz pozycję **narzędzia AI > Azure Machine Learning galerii przykładów**.

    ![Galeria przykładów](media/create-project-gallery/gallery.png)

4. Na potrzeby tego przewodnika Szybki Start wybierz przykład "**mnist ręcznie using TensorFlow**", a następnie kliknij przycisk **Instaluj**. Podaj następujące elementy:

   - **Grupa zasobów**: Grupa zasobów platformy Azure, w której będą przechowywane Twoje metadane
   - **Konto**: Azure Machine Learning konto eksperymentowania
   - **Obszar roboczy**: Azure Machine Learning obszar roboczy
   - **Typ projektu**: platforma uczenia maszynowego. W tym przypadku wybierz **TensorFlow**
   - **Dodaj do rozwiązania**: określa, czy dodać do bieżącego rozwiązania programu Visual Studio, czy też utworzyć i otworzyć nowe rozwiązanie
   - **Ścieżka projektu**: lokalizacja, w której ma zostać zapisany kod
   - **Nazwa projektu**: wpisz **TensorFlowMNIST**

   ![Projekt wynikający z użycia szablonu aplikacji języka Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Program Visual Studio tworzy plik projektu ( `.pyproj` plik na dysku) wraz z innymi plikami zdefiniowanymi w przykładzie. W przypadku szablonu "MNIST ręcznie" projekt zawiera kilka plików.

    ![Zrzut ekranu przedstawiający program Visual Studio Eksplorator rozwiązań pokazujący pliki projektu TensorFlowMNIST. Kod dla tf_mnist. PR jest wyświetlany w oknie głównym.](media/create-project-gallery/azml-mnist.png)

6. Prześlij zadanie do Azure Machine Learning.

    ![Zrzut ekranu przedstawiający Eksplorator rozwiązań programu Visual Studio z menu kontekstowego dla projektu TensorFlowMNIST z "Prześlij zadanie..." niezaznaczone.](media/create-project-gallery/submit-azml.png)

7. Uruchom w kontenerze platformy Docker lub na komputerze lokalnym

    ![Zrzut ekranu przedstawiający okno dialogowe przesyłania zadania z opcją Użyj klastra o wartości "Azure:/local" i skrypcie uruchamiania ustawionym na "tf_mnist. pr".](media/create-project-gallery/azml-local.png)

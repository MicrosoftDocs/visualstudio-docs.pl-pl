---
title: Tworzenie projektu
description: Tworzenie projektu przy użyciu przykładu z galerii usługi Azure Machine Learning
keywords: AI, Visual Studio, Azure Machine Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: d5e73757e10eec5e7e8c290772822f49129fd1e5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915900"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Tworzenie projektu AI z Galerii Azure Machine Learning w programie Visual Studio

Azure Machine Learning jest zintegrowana z Visual Studio Tools for AI. Można jej użyć do przesyłania zadań uczenia maszynowego do zdalnych celów obliczeniowych, takich jak maszyny wirtualne platformy Azure, klastry Spark i inne. 

Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt w języku Python przy użyciu wstępnych przepisów w galerii przykładów Azure Machine Learning.

> [!NOTE]
> Należy zainstalować Azure Machine Learning Workbench. Aby go zainstalować, zobacz [instalacja Azure Machine Learning — szybki start](/azure/machine-learning/preview/quickstart-installation)

1. Uruchom program Visual Studio. Otwórz **Eksplorator serwera** , otwierając menu **narzędzia AI** i wybierając **pozycję Wybierz klaster** .

    ![Wybór klastra](media/create-project-gallery/select-cluster.png)

2. Zaloguj się do swojej subskrypcji Azure Machine Learning, klikając prawym przyciskiem myszy węzeł **Azure Machine Learning** w Eksplorator serwera następnie wybierz pozycję **Zaloguj** i postępuj zgodnie z instrukcjami.

    ![Nazwa logowania](media/create-project-gallery/azureml-login.png)

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

5. Program Visual Studio tworzy plik projektu (plik `.pyproj` na dysku) wraz z innymi plikami zdefiniowanymi w przykładzie. W przypadku szablonu "MNIST ręcznie" projekt zawiera kilka plików.

    ![mnist ręcznie](media/create-project-gallery/azml-mnist.png)

6. Prześlij zadanie do Azure Machine Learning.

    ![mnist ręcznie](media/create-project-gallery/submit-azml.png)

7. Uruchom w kontenerze platformy Docker lub na komputerze lokalnym

    ![mnist ręcznie](media/create-project-gallery/azml-local.png)

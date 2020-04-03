---
title: Tworzenie projektu
description: tworzenie projektu przy użyciu przykładu z galerii uczenia maszynowego platformy Azure
keywords: ai, visual studio, azure machine learning
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: fb1158015f1a7065514511b8d62810c937382b7f
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638686"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Tworzenie projektu sztucznej inteligencji z galerii usługi Azure Machine Learning Gallery w programie Visual Studio

Usługa Azure Machine Learning jest zintegrowana z programem Visual Studio Tools for AI. Służy do przesyłania zadań uczenia maszynowego do zdalnych celów obliczeniowych, takich jak maszyny wirtualne platformy Azure, klastry Platformy Spark i inne. 

Po [zainstalowaniu programu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt języka Python przy użyciu wstępnie utworzonych receptur w galerii przykładów usługi Azure Machine Learning.

> [!NOTE]
> Musi być zainstalowany system Azure Machine Learning Workbench. Aby go zainstalować, zapoznaj się z [przewodnikiem szybki start instalacji usługi Azure Machine Learning](/azure/machine-learning/preview/quickstart-installation)

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwerów,** otwierając menu **Narzędzia AI** i wybierając **pozycję Wybierz klaster**

    ![Wybór klastra](media/create-project-gallery/select-cluster.png)

2. Zaloguj się do subskrypcji usługi Azure Machine Learning, klikając prawym przyciskiem myszy węzeł **usługi Azure Machine Learning** w Eksploratorze serwera, a następnie wybierz pozycję Zaloguj **się** i postępuj zgodnie ze wskazówkami.

    ![logowanie](media/create-project-gallery/azureml-login.png)

3. Wybierz pozycję **Narzędzia sztucznej inteligencji > przykładowej galerii usługi Azure Machine Learning**.

    ![Przykładowa galeria](media/create-project-gallery/gallery.png)

4. W tym przewodniku Szybki start wybierz przykład "**MNIST using TensorFlow**" i kliknij przycisk **Zainstaluj**. Podaj następujące informacje:

   - **Grupa zasobów:** grupa zasobów platformy Azure, w której będą przechowywane metadane
   - **Konto**: Konto eksperymentów usługi Azure Machine Learning
   - **Obszar roboczy:** obszar roboczy usługi Azure Machine Learning
   - **Typ projektu:** struktura uczenia maszynowego. W takim przypadku wybierz **TensorFlow**
   - **Dodaj do rozwiązania:** określa, czy dodać do bieżącego rozwiązania programu Visual Studio, czy utworzyć i otworzyć nowe rozwiązanie
   - **Ścieżka projektu:** Lokalizacja, aby zapisać kod
   - **Nazwa projektu**: Typ **TensorFlowMNIST**

   ![Wynikowy projekt podczas korzystania z szablonu aplikacji języka Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Program Visual Studio tworzy `.pyproj` plik projektu (plik na dysku) wraz z innymi plikami zdefiniowanymi w przykładzie. Z szablonem "MNIST" projekt zawiera kilka plików.

    ![mnist](media/create-project-gallery/azml-mnist.png)

6. Prześlij zadanie do usługi Azure Machine Learning.

    ![mnist](media/create-project-gallery/submit-azml.png)

7. Uruchamianie w kontenerze platformy Docker lub na komputerze lokalnym

    ![mnist](media/create-project-gallery/azml-local.png)

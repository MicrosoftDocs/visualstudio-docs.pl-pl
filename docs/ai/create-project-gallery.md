---
title: Tworzenie projektu
description: Tworzenie projektu przy użyciu przykładu z usługi azure machine learning galerii
keywords: sztuczna inteligencja, programu visual studio, usługi azure machine learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 5694bfe49e88d0ea5911e72abba842e98f54e373
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538073"
---
# <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Utwórz projekt sztucznej Inteligencji z galerii usługi Azure Machine Learning w programie Visual Studio

Usługa Azure Machine Learning jest zintegrowane z Visual Studio Tools dla sztucznej Inteligencji. Służy do przesyłania zadań uczenia maszyny do zdalnego obliczeniowych elementów docelowych, takich jak usługa Azure virtual machines, klastry Spark i nie tylko. Dowiedz się więcej o [eksperymentowanie w usłudze Machine Learning platformy Azure](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration)

Po [zainstalowany program Visual Studio Tools for AI](installation.md), ułatwia utworzenie nowego projektu języka Python za pomocą wstępnie przygotowanych przepisy w galerii przykładów usługi Azure Machine Learning.

> [!NOTE]
> Musi być zainstalowana aplikacja Azure Machine Learning Workbench. Aby go zainstalować, zobacz [szybkiego startu instalacji usługi Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation)

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwera** , otwierając **narzędzia si** menu i wybierając pozycję **wybierz klastra**

    ![Selektor klastra](media/create-project-gallery/select-cluster.png)

2. Zaloguj się do subskrypcji usługi Azure Machine Learning, klikając prawym przyciskiem myszy **usługi Azure Machine Learning** węzła w Eksploratorze serwera wybierz **logowania** i postępuj zgodnie z instrukcjami.

    ![Zaloguj się](media/create-project-gallery/azureml-login.png)

3. Wybierz **narzędzia SI > Galeria usługi Azure Machine Learning przykładowe**.

    ![Galeria przykładów](media/create-project-gallery/gallery.png)

4. W tym przewodniku Szybki Start wybierz pozycję "**mnist ręcznie ZAPISANYCH przy użyciu TensorFlow**" przykładowy, a następnie kliknij przycisk **zainstalować**. Należy dostarczyć następujące elementy:

   - **Grupa zasobów**: Grupa zasobów platformy Azure, w którym będą przechowywane metadane
   - **Konto**: Usługa Azure Machine Learning eksperymentowania konta
   - **Obszar roboczy**: Obszar roboczy usługi Azure Machine Learning
   - **Typ projektu**: Struktura learning maszyny. W takim przypadku wybierz **TensorFlow**
   - **Dodaj do rozwiązania**: Określa, czy należy dodać do bieżącego rozwiązania programu Visual Studio lub Utwórz i Otwórz nowe rozwiązanie
   - **Ścieżka projektu**: Lokalizacja, aby zapisać kod
   - **Nazwa projektu**: Type **TensorFlowMNIST**

   ![Projekt wynikowy, korzystając z szablonu aplikacji w języku Python](media/create-project-gallery/new-AzureSampleProject.png)

5. Program Visual Studio tworzy pliku projektu ( `.pyproj` pliku na dysku) wraz z innymi plikami zdefiniowane w próbce. Z szablonem "Mnist ręcznie ZAPISANYCH" Projekt zawiera kilka plików.

    ![mnist ręcznie zapisanych](media/create-project-gallery/azml-mnist.png)

6. Prześlij zadanie usługi Azure Machine Learning.

    ![mnist ręcznie zapisanych](media/create-project-gallery/submit-azml.png)

7. Uruchom w kontenerze platformy Docker lub na komputerze lokalnym

    ![mnist ręcznie zapisanych](media/create-project-gallery/azml-local.png)
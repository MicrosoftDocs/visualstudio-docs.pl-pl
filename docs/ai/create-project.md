---
title: Tworzenie projektu AI na podstawie szablonu
description: Dowiedz się, jak za pomocą Visual Studio Tools for AI utworzyć projekt AI z różnych szablonów.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 28eccd9c564b7d368e823288311a823fdff86fb3
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726401"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Tworzenie projektu AI na podstawie szablonu w programie Visual Studio

Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt AI przy użyciu różnych szablonów.

1. Uruchom program Visual Studio.

2. Wybierz pozycję **plik > nowy > projekt** (Ctrl + Shift + N). W oknie dialogowym **Nowy projekt** Wyszukaj ciąg "**narzędzia AI**" i wybierz odpowiedni szablon. Należy zauważyć, że wybranie szablonu powoduje wyświetlenie krótkiego opisu tego, co zawiera szablon.

    ![Okno dialogowe nowego projektu program VS2017 z szablonem języka Python](media/create-project/new-ai-project.png)

3. W tym przewodniku Szybki Start wybierz szablon "**aplikacja TensorFlow**", Nadaj projektowi nazwę (np. "mnist ręcznie") i lokalizację, a następnie wybierz **przycisk OK**.

4. Program Visual Studio tworzy plik projektu ( `.pyproj` plik na dysku) wraz z innymi plikami, zgodnie z opisem w szablonie. W przypadku szablonu "aplikacja TensorFlow" projekt zawiera jeden plik o nazwie identycznej z projektem. Plik jest domyślnie otwarty w edytorze programu Visual Studio.

    ![Projekt wynikający z użycia szablonu aplikacji języka Python](media/create-project/new-tensorflowapp.png)

5. Zwróć uwagę, że w kodzie już zaimportowano kilka bibliotek, w tym TensorFlow, numpy, sys i OS. Dodatkowo uruchamia swoją aplikację z pewnymi argumentami wejściowymi, aby łatwo włączyć przełączenie lokalizacji danych szkolenia wejściowego, modeli wyjściowych i plików dziennika. Te parametry są przydatne w przypadku przesyłania zadań do wielu kontekstów obliczeniowych (program IE w innym katalogu w lokalnym polu deweloperskim niż w udziale plików platformy Azure).

6. Projekt ma także pewne właściwości, które zostały utworzone, aby ułatwić debugowanie aplikacji przez automatyczne przekazywanie argumentów wiersza polecenia do tych parametrów wejściowych. **Kliknij prawym przyciskiem myszy** projekt, a następnie wybierz polecenie **Właściwości**

    ![Zrzut ekranu przedstawiający Eksplorator rozwiązań programu Visual Studio z menu kontekstowego dla TensorFlowApplication1 z wybranymi właściwościami.](media/create-project/project-properties.png)

7. Kliknij kartę **debugowanie** , aby zobaczyć automatycznie dodane argumenty skryptu. można je zmienić w razie potrzeby w miejscu, w którym znajdują się dane wejściowe, oraz miejsce przechowywania danych wyjściowych.

    ![Zrzut ekranu karty debugowanie w ustawieniach właściwości dla TensorFlowApplication1, pokazujący argumenty skryptu dla projektu.](media/create-project//project-properties_1.png)

8. Uruchom program, naciskając klawisze CTRL + F5 lub wybierając pozycję **debuguj > Rozpocznij bez debugowania** w menu. Wyniki są wyświetlane w oknie konsoli.

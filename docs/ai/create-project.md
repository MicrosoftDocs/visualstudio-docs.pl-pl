---
title: Tworzenie projektu SI na podstawie szablonu
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 759ee562e5d3648cf831c6a1247bc660596336a1
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638590"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Tworzenie projektu AI na podstawie szablonu w programie Visual Studio

Po [zainstalowaniu programu Visual Studio Tools for AI](installation.md)można łatwo utworzyć nowy projekt AI przy użyciu różnych szablonów.

1. Uruchom program Visual Studio.

2. Wybierz **opcję Plik > Nowy projekt >** (Ctrl+Shift+N). W oknie dialogowym **Nowy projekt** wyszukaj hasło "**Narzędzia AI**" i wybierz odpowiedni szablon. Należy zauważyć, że wybranie szablonu powoduje wyświetlenie krótkiego opisu tego, co zapewnia szablon.

    ![Okno dialogowe Nowy projekt vs2017 z szablonem języka Python](media/create-project/new-ai-project.png)

3. Dla tego przewodnika Szybki start wybierz szablon "**TensorFlow Application**", nadaj projektowi nazwę (na przykład "MNIST") i lokalizację, a następnie wybierz **przycisk OK**.

4. Program Visual Studio tworzy `.pyproj` plik projektu (plik na dysku) wraz z innymi plikami, zgodnie z opisem przez szablon. Za pomocą szablonu "TensorFlow Application" projekt zawiera jeden plik o takiej samej nazwie jak projekt. Plik jest domyślnie otwarty w edytorze programu Visual Studio.

    ![Wynikowy projekt podczas korzystania z szablonu aplikacji języka Python](media/create-project/new-tensorflowapp.png)

5. Zwróć uwagę, że kod importuje już kilka bibliotek, w tym TensorFlow, numpy, sys i os. Ponadto uruchamia aplikację gotowy z niektórych argumentów wejściowych, aby łatwo włączyć przełączanie lokalizacji danych szkoleniowych wejściowych, modeli wyjściowych i plików dziennika. Te params są przydatne podczas przesyłania zadań do wielu kontekstów obliczeniowych (tj. inny katalog w lokalnym polu dev niż w udziale plików platformy Azure).

6. Projekt ma również pewne właściwości utworzone w celu ułatwienia debugowania aplikacji przez automatyczne przekazywanie argumentów wiersza polecenia do tych parametrów wejściowych. **Kliknij prawym przyciskiem myszy** projekt, a następnie wybierz polecenie **Właściwości**

    ![Właściwości](media/create-project/project-properties.png)

7. Kliknij kartę **Debugowanie,** aby wyświetlić automatycznie dodane argumenty skryptu. można je zmienić w razie potrzeby, gdzie znajdują się dane wejściowe i gdzie chcesz dane wyjściowe przechowywane.

    ![Właściwości](media/create-project//project-properties_1.png)

8. Uruchom program, naciskając klawisze Ctrl+F5 lub wybierając **debugowanie > rozpocznij bez debugowania** w menu. Wyniki są wyświetlane w oknie konsoli.

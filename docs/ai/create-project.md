---
title: Tworzenie projektu sztucznej Inteligencji na podstawie szablonu
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: e8b3f7a12b13c931513962a10d1eb5fcd4344174
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786112"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Tworzenie projektu sztucznej Inteligencji z szablonu w programie Visual Studio

Po [zainstalowany program Visual Studio Tools for AI](installation.md), ułatwia utworzenie nowego projektu sztucznej Inteligencji przy użyciu różnych szablonów.

1. Uruchom program Visual Studio.

2. Wybierz **Plik > Nowy > Projekt** (Ctrl + Shift + N). W **nowy projekt** okno dialogowe, wyszukaj "**narzędzia si**", a następnie wybierz szablon ma. Należy pamiętać, że wybranie szablonu wyświetla krótki opis, w jaki szablon zawiera.

    ![Program VS2017 okna dialogowego Nowy projekt z szablonu języka Python](media/create-project/new-ai-project.png)

3. W tym przewodniku Szybki Start wybierz pozycję "**aplikacji TensorFlow**" szablonu, należy nadać projektowi nazwę (na przykład "mnist ręcznie ZAPISANYCH") i lokalizację, a następnie wybierz pozycję **OK**.

4. Program Visual Studio tworzy pliku projektu ( `.pyproj` pliku na dysku) wraz z innymi plikami zgodnie z opisem w szablonie. Z szablonem "TensorFlow aplikacja" projektu zawiera jeden plik o nazwie taka sama jak projekt. Plik jest otwarty w edytorze programu Visual Studio domyślnie.

    ![Projekt wynikowy, korzystając z szablonu aplikacji w języku Python](media/create-project/new-tensorflowapp.png)

5. Zwróć uwagę, że kod importuje już kilka bibliotek, takich jak TensorFlow, numpy, sys i systemu operacyjnego. Ponadto możesz już aplikacji rozpoczynają się one od niektórych argumentów wejściowych umożliwiające łatwe przełączanie lokalizacji danych wejściowych szkoleniowych, modele danych wyjściowych i pliki dziennika. Te parametry są przydatne podczas przesyłania zadań do wielu konteksty obliczeniowe (ie inny katalog w swojej lokalnej okna niż w udziale plików platformy Azure).

6. Projekt zawiera również właściwościami, który został utworzony, aby ułatwić debugowanie aplikacji automatycznie przekazując argumenty wiersza polecenia do tych parametrów wejściowych. **Kliknij prawym przyciskiem myszy** projekt następnie wybierz pozycję **właściwości**

    ![Właściwości](media/create-project/project-properties.png)

7. Kliknij przycisk **debugowania** dodano kartę, aby zobaczyć argumenty skryptu automatycznie. można je zmienić zgodnie z potrzebami, na którym znajduje się dane wejściowe i gdzie ma się dane wyjściowe przechowywane.

    ![Właściwości](media/create-project//project-properties_1.png)

8. Uruchom program, naciskając klawisze Ctrl + F5 lub wybierając **Debuguj > Uruchom bez debugowania** w menu. Wyniki są wyświetlane w oknie konsoli.

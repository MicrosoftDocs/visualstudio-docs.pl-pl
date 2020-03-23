---
title: Szybki start — tworzenie projektu języka Python przy użyciu funkcji Cookiecutter
description: W tym przewodniku Szybki start utworzysz projekt programu Visual Studio dla języka Python przy użyciu szablonu Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f3e7f56f4a36a7958cba9bd7092f38d735123d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62954512"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Szybki start: tworzenie projektu na podstawie szablonu cookiecutter

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)można łatwo utworzyć nowy projekt za pomocą szablonu cookiecutter, w tym wiele, które są publikowane w usłudze GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) udostępnia graficzny interfejs użytkownika do odnajdowania szablonów, opcji szablonów wejściowych oraz tworzenia projektów i plików. Jest dołączony do programu Visual Studio 2017 i nowszych i może być zainstalowany oddzielnie we wcześniejszych wersjach programu Visual Studio.

1. W przypadku tego przewodnika Szybki start najpierw zainstaluj dystrybucję Języka Python Anaconda3, która zawiera niezbędne pakiety Pythona dla szablonu Cookiecutter pokazanego tutaj. Uruchom instalator programu Visual Studio, wybierz pozycję **Modyfikuj,** rozwiń opcje **tworzenia języka Python** po prawej stronie i wybierz pozycję **Anaconda3** (32-bitowe lub 64-bitowe). Należy pamiętać, że instalacja może zająć trochę czasu w zależności od szybkości Internetu, ale jest to najprostszy sposób instalowania potrzebnych pakietów.

1. Uruchom program Visual Studio.

1. Wybierz **plik** > **nowy** > **z cookiecutter**. To polecenie otwiera okno w programie Visual Studio, w którym można przeglądać szablony.

    ![Nowy szablon projektu z cookiecutter](media/projects-from-cookiecutter1.png)

1. Wybrano szablon **Microsoft/python-sklearn-classifier-cookiecutter,** a następnie wybierz przycisk **Dalej**. (Proces może potrwać kilka minut przy pierwszym użyciu określonego szablonu, ponieważ program Visual Studio instaluje wymagane pakiety Języka Python).

1. W następnym kroku ustaw lokalizację nowego projektu w polu **Utwórz do,** a następnie wybierz pozycję **Utwórz i otwórz projekt**.

    ![Drugi krok za pomocą Cookiecutter, ustawianie właściwości projektu](media/projects-from-cookiecutter2.png)

1. Po zakończeniu procesu zostanie wyświetlony komunikat **Pomyślnie utworzone pliki przy użyciu szablonu...**. Projekt jest otwierany w Eksploratorze rozwiązań automatycznie.

1. Naciśnij **klawisz Ctrl**+**F5** lub wybierz **opcję Debugowanie** > **start bez debugowania,** aby uruchomić program.

    ![Dane wyjściowe projektu szablonu python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z Pythonem w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Użyj rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md)
- [Ręczne identyfikowanie istniejącego interpretera języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i wcześniejszych](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

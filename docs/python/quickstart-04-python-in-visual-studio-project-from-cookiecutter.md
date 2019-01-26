---
title: Przewodnik Szybki Start — Tworzenie projektu języka Python za pomocą Cookiecutter
description: W tym przewodniku Szybki Start utworzysz projekt programu Visual Studio dla języka Python za pomocą szablonów Cookiecutter.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9dd949f921c3d504823e9204e0974617c8a2b3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953188"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Szybki start: Tworzenie projektu z szablonu Cookiecutter

Po [zainstalowane obsługi języka Python w programie Visual Studio 2017](installing-python-support-in-visual-studio.md), można łatwo utworzyć nowy projekt z szablonu Cookiecutter, w tym wiele, które są publikowane w witrynie GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) zapewnia graficzny interfejs użytkownika do odnalezienia szablonów, wprowadź opcje szablonu oraz tworzenie projektów i plików. On wchodzi w skład programu Visual Studio 2017 i mogą być zainstalowane oddzielnie we wcześniejszych wersjach programu Visual Studio.

1. W tym przewodniku Szybki Start należy najpierw zainstalować dystrybucji anaconda3, wersja języka Python, która obejmuje niezbędne pakiety języka Python dla szablonu Cookiecutter, pokazano poniżej. Uruchom Instalatora programu Visual Studio, wybierz **Modyfikuj**, rozwiń opcje **programowania w języku Python** po prawej stronie i wybierz pozycję **Anaconda3** (32-bitowy lub 64-bitowych). Należy pamiętać, że instalacja może zająć trochę czasu w zależności od szybkości Internetu, ale jest to najprostszy sposób, aby zainstalować wymagane pakiety.

1. Uruchom program Visual Studio.

1. Wybierz **pliku** > **nowe** > **z Cookiecutter**. To polecenie powoduje otwarcie okna w programie Visual Studio, w którym można przeglądać szablony.

    ![Nowy projekt z szablonów Cookiecutter](media/projects-from-cookiecutter1.png)

1. Wybrane **Microsoft/python-skryptu sklearn klasyfikatora cookiecutter** szablonu, następnie wybierz pozycję **dalej**. (Ten proces może potrwać kilka minut po raz pierwszy używasz Cookiecutter).

1. W następnym kroku, należy ustawić lokalizację dla nowego projektu w **utworzyć do** pole, a następnie wybierz opcję **Utwórz**.

    ![Drugi etap przy użyciu Cookiecutter, ustawianie właściwości projektu](media/projects-from-cookiecutter2.png)

1. Po zakończeniu procesu zostanie wyświetlony komunikat **plików utworzony pomyślnie.** Wybierz polecenie **Otwórz w Eksploratorze rozwiązań** otworzyć projektu.

1. Naciśnij klawisz **Ctrl**+**F5** lub wybierz **debugowania** > **Uruchom bez debugowania** do uruchomienia programu.

    ![Dane wyjściowe projektu szablonu języka python — skryptu sklearn klasyfikatora cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Używanie rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md)
- [Ręcznie Zidentyfikuj istniejące interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

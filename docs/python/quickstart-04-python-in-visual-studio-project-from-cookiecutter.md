---
title: Szybki Start — tworzenie projektów języka Python za pomocą Cookiecutter
description: W tym przewodniku szybki start utworzysz projekt programu Visual Studio dla języka Python przy użyciu szablonu Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902438"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Szybki Start: Tworzenie projektu na podstawie szablonu Cookiecutter

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md), można łatwo utworzyć nowy projekt na podstawie szablonu Cookiecutter, w tym wielu opublikowanych w serwisie GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) udostępnia graficzny interfejs użytkownika umożliwiający odnajdywanie szablonów, opcji szablonów wejściowych i tworzenie projektów i plików. Jest on dołączony do programu Visual Studio 2017 lub nowszego i można go zainstalować oddzielnie we wcześniejszych wersjach programu Visual Studio.

1. W tym przewodniku Szybki Start należy najpierw zainstalować dystrybucję Anaconda3 w języku Python, która obejmuje niezbędne pakiety języka Python dla szablonu Cookiecutter w tym miejscu. Uruchom Instalatora programu Visual Studio, wybierz pozycję **Modyfikuj**, rozwiń opcje programowania w języku **Python** po prawej stronie, a następnie wybierz pozycję **Anaconda3** (32-bitowy lub 64-bitowy). Należy pamiętać, że instalacja może zająć trochę czasu w zależności od szybkości Internetu, ale jest to najprostszy sposób instalacji wymaganych pakietów.

1. Uruchom program Visual Studio.

1. Wybierz pozycję **plik**  >  **Nowy**  >  **z Cookiecutter**. To polecenie otwiera okno w programie Visual Studio, w którym można przeglądać szablony.

    ![Nowy projekt z szablonu Cookiecutter](media/projects-from-cookiecutter1.png)

1. Zaznaczono szablon **Microsoft/Python-skryptu sklearn-klasyfikator-cookiecutter** , a następnie wybierz przycisk **dalej**. (Proces może potrwać kilka minut przy pierwszym użyciu określonego szablonu, ponieważ program Visual Studio instaluje wymagane pakiety języka Python).

1. W następnym kroku Ustaw lokalizację nowego projektu w polu **Utwórz do** , a następnie wybierz pozycję **Utwórz i Otwórz projekt**.

    ![Drugi krok przy użyciu Cookiecutter, Ustawianie właściwości projektu](media/projects-from-cookiecutter2.png)

1. Po zakończeniu procesu zobaczysz komunikat **pomyślnie utworzono pliki przy użyciu szablonu...**. Projekt zostanie otwarty w Eksplorator rozwiązań automatycznie.

1. Naciśnij klawisz **Ctrl** + **F5** lub wybierz pozycję **Debuguj**  >  **Uruchom bez debugowania** , aby uruchomić program.

    ![Dane wyjściowe języka Python-skryptu sklearn-klasyfikatora — cookiecutter szablonu](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: współpraca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Użyj rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md)
- [Ręcznie Zidentyfikuj istniejący interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i starszych wersjach](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

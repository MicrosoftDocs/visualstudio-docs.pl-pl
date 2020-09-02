---
title: Szybki Start — Tworzenie projektu w języku Python przy użyciu szablonu
description: W tym przewodniku szybki start utworzysz projekt programu Visual Studio dla języka Python przy użyciu wbudowanego szablonu dla aplikacji z podstawową kolbą.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 089be3e6f28a939979f6bd97097ea7558824b493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429765"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Szybki Start: Tworzenie projektu w języku Python na podstawie szablonu w programie Visual Studio

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md), można łatwo utworzyć nowy projekt w języku Python przy użyciu różnych szablonów. W tym przewodniku szybki start utworzysz prostą aplikację do kolby przy użyciu szablonu. Projekt wynikający z tego projektu jest podobny do projektu tworzonego ręcznie za pomocą [przewodnika Szybki Start — Tworzenie aplikacji sieci Web z kolbą](../ide/quickstart-python.md).

1. Uruchom program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**, a następnie w oknie dialogowym **Nowy projekt** Wyszukaj ciąg "pusta Kolba", wybierz szablon **projektu sieci Web o pustej kolbie** na liście środkowej, Nadaj projektowi nazwę i wybierz polecenie **OK**:

    ![Tworzenie nowego projektu z szablonem projektu sieci Web pustej kolby](media/quickstart-python-06-blank-flask-template.png)

1. Program Visual Studio wyświetli prośbę o okno dialogowe z informacją, że **ten projekt wymaga pakietów zewnętrznych.** To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *requirements.txt* określający zależność od kolby. Program Visual Studio może automatycznie zainstalować pakiety i zapewnia możliwość instalacji ich w *środowisku wirtualnym*. W środowisku globalnym zaleca się używanie środowiska wirtualnego, dlatego w celu kontynuowania wybierz pozycję **Zainstaluj w środowisku wirtualnym** .

    ![Instalowanie kolby w środowisku wirtualnym](media/quickstart-python-07-install-into-virtual-environment.png)

1. Program Visual Studio Wyświetla okno dialogowe **Dodawanie środowiska wirtualnego** . Zaakceptuj wartość domyślną i wybierz pozycję **Utwórz**, a następnie wyrażanie zgody na wszystkie żądania podniesienia uprawnień.

    > [!Tip]
    > Po rozpoczęciu projektu zdecydowanie zaleca się utworzenie środowiska wirtualnego od razu, tak jak większość szablonów programu Visual Studio zaprasza Cię do wykonania. Środowiska wirtualne utrzymują dokładne wymagania projektu w czasie, gdy dodasz i usuniesz biblioteki. Następnie można łatwo wygenerować plik *requirements.txt* , który służy do ponownej instalacji tych zależności na innych komputerach deweloperskich (jak w przypadku korzystania z kontroli źródła) i podczas wdrażania projektu na serwerze produkcyjnym. Aby uzyskać więcej informacji o środowiskach wirtualnych i ich korzyściach, zobacz [Korzystanie z środowisk wirtualnych](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) i [Zarządzanie wymaganymi pakietami przy użyciu requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Po utworzeniu środowiska przez program Visual Studio zapoznaj się z tematem **Eksplorator rozwiązań** , aby zobaczyć, że masz plik *app.py* wraz z *requirements.txt*. Otwórz *App.py* , aby zobaczyć, że szablon dostarczył kod taki jak w [przewodniku szybki start — Utwórz aplikację internetową z kolbą](../ide/quickstart-python.md)z kilkoma dodanymi sekcjami. Cały kod przedstawiony poniżej jest tworzony przez szablon, więc nie trzeba wklejać żadnych do *App.py* siebie.

    Kod rozpoczyna się od wymaganego importu:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Poniżej znajduje się następujący wiersz, który może być przydatny podczas wdrażania aplikacji na hoście sieci Web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Następnie dostarcza funkcję Route dekoratora na prostej funkcji, która definiuje widok:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Poniższy kod uruchomienia pozwala ustawić hosta i port za pomocą zmiennych środowiskowych, a nie twardych. Taki kod umożliwia łatwe sterowanie konfiguracją na maszynach deweloperskich i produkcyjnych bez konieczności zmiany kodu:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Wybierz pozycję **Debuguj**  >  **Uruchom bez debugowania** , aby uruchomić aplikację i otworzyć przeglądarkę do programu `localhost:5555` .

**Pytanie: jakie inne szablony języka Python są oferowane przez program Visual Studio?**

**Odpowiedź**: przy zainstalowanym obciążeniu języka Python program Visual Studio oferuje różne szablony projektów, w tym te dla [platform sieci Web kolb, butelek i Django](../python/python-web-application-project-templates.md), usługi Azure Cloud Services, inne scenariusze uczenia maszynowego, a nawet szablon do tworzenia projektu na podstawie istniejącej struktury folderów zawierającej aplikację w języku Python. Dostęp do nich uzyskuje się za pomocą okna dialogowego **plik**  >  **nowego**  >  **projektu** , wybierając węzeł języka **Python** i jego węzły podrzędne.

Program Visual Studio udostępnia również różne szablony plików lub *elementów* , aby szybko utworzyć klasę języka Python, pakiet języka Python, test jednostkowy języka python, *web.config* pliki i wiele innych. Gdy masz otwarty projekt w języku Python, możesz uzyskać dostęp do szablonów elementów za pomocą polecenia **projektu**  >  **Dodaj nowy element** menu. Zobacz odwołania do [szablonów elementów](python-item-templates.md) .

Korzystanie z szablonów może zaoszczędzić dużo czasu podczas uruchamiania projektu lub tworzenia pliku, a także doskonały sposób na zapoznanie się z różnymi typami aplikacji i strukturami kodu. Tworzenie projektów i elementów z różnych szablonów może potrwać kilka minut. Zapoznaj się z ich ofertą.

**Pytanie: Czy mogę również używać szablonów Cookiecutter?**

**Odpowiedź**: tak! W rzeczywistości program Visual Studio zapewnia bezpośrednią integrację z usługą Cookiecutter, którą można uzyskać, korzystając z [przewodnika Szybki Start: Tworzenie projektu na podstawie szablonu Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: współpraca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Ręcznie Zidentyfikuj istniejący interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i starszych wersjach](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

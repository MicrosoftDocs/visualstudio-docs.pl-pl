---
title: Przewodnik Szybki Start — Tworzenie projektu języka Python przy użyciu szablonu
description: W tym przewodniku Szybki Start utworzysz projekt programu Visual Studio dla języka Python dla podstawowych aplikacji Flask za pomocą wbudowanych szablonów.
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
ms.openlocfilehash: 183067e2c155ef9a044928d875d1bb61485a1230
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043690"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Szybki start: Tworzenie projektu w języku Python na podstawie szablonu w programie Visual Studio

Po [zainstalowane obsługi języka Python w programie Visual Studio 2017](installing-python-support-in-visual-studio.md), ułatwia utworzenie nowego projektu języka Python przy użyciu różnych szablonów. W tym przewodniku Szybki Start opisano tworzenie prostej aplikacji Flask za pomocą szablonu. Projekt wynikowy jest podobny do projektu, możesz utworzyć ręcznie za pomocą [Szybki Start — tworzenie aplikacji sieci web za pomocą Flask](../ide/quickstart-python.md).

1. Uruchom program Visual Studio 2017.

1. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**, a następnie w obszarze **nowy projekt** wyszukiwania okna dialogowego "flask puste", można wybrać **pusty projekt sieci Web Flask** szablonu na liście środkowej nazwij projekt, a następnie wybierz pozycję **OK**:

    ![Tworzenie nowego projektu za pomocą szablonu pusty projekt sieci Web Flask](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio wyświetli okno dialogowe, które mówi **ten projekt wymaga zewnętrznych pakietów.** To okno dialogowe pojawia się, ponieważ szablon zawiera *requirements.txt* pliku, określając zależność Flask. Visual Studio może automatycznie zainstalować pakiety i daje możliwość ich do zainstalowania *środowiska wirtualnego*. Za pomocą środowiska wirtualnego zamiast zaleca się instalowania w środowisku globalnym, dlatego wybierz **zainstalować w środowisku wirtualnym** aby kontynuować.

    ![Instalowanie Flask w środowisku wirtualnym](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio Wyświetla **Dodawanie środowiska wirtualnego** okna dialogowego. Zaakceptuj wartości domyślne, a następnie wybierz pozycję **Utwórz**, następnie Wyraź zgodę na wszystkie żądania podniesienia uprawnień.

    > [!Tip]
    > Po rozpoczęciu projektu zdecydowanie zaleca się już teraz Utwórz środowisko wirtualne jak zapraszać większość szablonów programu Visual Studio, należy wykonać. Środowiska wirtualne Obsługa dokładnych wymaganiach projektu wraz z upływem czasu, jak dodać i usunąć biblioteki. Następnie można łatwo generować *requirements.txt* pliku, którego używasz, aby ponownie zainstalować te zależności na innych komputerach rozwoju (jako po przy użyciu kontroli źródła) i podczas wdrażania projektu na serwerze produkcyjnym. Aby uzyskać więcej informacji na temat środowisk wirtualnych i korzyści, zobacz [korzystanie ze środowisk wirtualnych](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) i [zarządzania wymagane pakiety przy użyciu pliku requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Gdy program Visual Studio utworzy tego środowiska, Szukaj w **Eksploratora rozwiązań** aby zobaczyć, że masz *app.py* plików wraz z *requirements.txt*. Otwórz *app.py* aby zobaczyć, że szablon udostępnił kodu, tak jak w [Szybki Start — tworzenie aplikacji sieci web za pomocą Flask](../ide/quickstart-python.md), kilka dodano sekcje. Cały kod poniżej jest tworzony przez szablon, więc nie trzeba wkleić dowolny do *app.py* samodzielnie.

    Odpowiednie Importy zaczyna się kod:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Następnym ekranem jest następujący wiersz, który może być przydatne podczas wdrażania aplikacji na serwerze sieci web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Skąd dekoratora trasy na prostej funkcji, który definiuje widoku:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Poniższy kod startowy pozwala na koniec Ustaw hosta i portu za pomocą zmiennych środowiskowych, zamiast kodować je. Taki kod pozwala łatwo modyfikować konfigurację na maszynach środowisk deweloperskich i produkcyjnych bez konieczności zmieniania kodu:

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

1. Wybierz **debugowania** > **Uruchom bez debugowania** do uruchamiania aplikacji i Otwórz w przeglądarce `localhost:5555`.

**Pytanie: Jakie inne szablony Python oferuje program Visual Studio?**

**Odpowiedź**: Z zainstalowanym obciążeniem Python programu Visual Studio oferuje różne szablony projektów, między innymi [struktury sieci web Flask, Bottle i Django](../python/python-web-application-project-templates.md)platformy Azure usługi w chmurze, różne usługi machine learning scenariusze, a nawet szablon, aby utworzyć projekt z istniejącą strukturę folderu zawierającego aplikację języka Python. Możesz przejść do nich za pośrednictwem **pliku** > **New** > **projektu** okno dialogowe, wybierając **Python** język węzła i jego węzłami podrzędnymi.

Visual Studio udostępnia również różnych plików lub *elementu szablony* szybko utworzyć klasę języka Python, pakiet języka Python, test jednotky Pythonu *web.config* pliki i inne. W przypadku otwarcia projektu języka Python, możesz uzyskać dostęp do szablonów elementu za pomocą **projektu** > **Dodaj nowy element** polecenia menu. Zobacz [elementu szablony](python-item-templates.md) odwołania.

Za pomocą szablonów można skrócić znaczące czas podczas uruchamiania projektu lub tworzenia pliku i są również świetnym sposobem Dowiedz się więcej o różnych typów aplikacji i kodu struktury. Warto potrwać kilka minut, aby utworzyć przy użyciu różnych szablonów projektów i elementów do zapoznania się z ich oferty.

**Pytanie: Można również używać z szablonów Cookiecutter?**

**Odpowiedź**: Tak! W rzeczywistości program Visual Studio zapewnia bezpośrednią integrację z usługą Cookiecutter, w którym można zapoznać się za pośrednictwem [Szybki Start: Tworzenie projektu z szablonów Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Ręcznie Zidentyfikuj istniejące interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

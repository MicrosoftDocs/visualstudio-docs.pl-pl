---
title: Szybki start — tworzenie projektu języka Python przy użyciu szablonu
description: W tym przewodniku Szybki start utworzysz projekt programu Visual Studio dla języka Python przy użyciu wbudowanego szablonu dla podstawowej aplikacji Flask.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62429765"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Szybki start: tworzenie projektu języka Python na podstawie szablonu w programie Visual Studio

Po [zainstalowaniu obsługi języka Python w programie Visual Studio](installing-python-support-in-visual-studio.md)można łatwo utworzyć nowy projekt języka Python przy użyciu różnych szablonów. W tym przewodniku Szybki start tworzysz prostą aplikację Flask przy użyciu szablonu. Wynikowy projekt jest podobny do projektu tworzętnego ręcznie za pomocą [przewodnika Szybki start — Tworzenie aplikacji sieci web za pomocą programu Flask](../ide/quickstart-python.md).

1. Uruchom program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**, a następnie w oknie dialogowym Nowy **projekt** wyszukaj hasło "pusta kolba", wybierz szablon Pusty projekt sieci Web **kolby** na liście środkowej, nadaj projektowi nazwę i wybierz **przycisk OK:**

    ![Tworzenie nowego projektu za pomocą szablonu Pusty projekt sieci Web Pustej Kolby](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio monituje o okno dialogowe, które mówi **Ten projekt wymaga pakietów zewnętrznych.** To okno dialogowe jest wyświetlane, ponieważ szablon zawiera plik *requirements.txt* określający zależność od flask. Program Visual Studio może automatycznie instalować pakiety i umożliwia zainstalowanie ich w *środowisku wirtualnym.* Używanie środowiska wirtualnego jest zalecane podczas instalowania w środowisku globalnym, więc wybierz **pozycję Zainstaluj w środowisku wirtualnym,** aby kontynuować.

    ![Instalowanie flask w środowisku wirtualnym](media/quickstart-python-07-install-into-virtual-environment.png)

1. Program Visual Studio wyświetla okno dialogowe **Dodawanie środowiska wirtualnego.** Zaakceptuj wartość domyślną i wybierz pozycję **Utwórz**, a następnie zgód na wszystkie żądania podniesienia uprawnień.

    > [!Tip]
    > Po rozpoczęciu projektu zaleca się utworzenie środowiska wirtualnego od razu, jak większość szablonów programu Visual Studio zaprosić do zrobienia. Środowiska wirtualne zachowują dokładne wymagania projektu w czasie podczas dodawania i usuwania bibliotek. Następnie można łatwo wygenerować plik *requirements.txt,* który służy do ponownej instalacji tych zależności na innych komputerach deweloperskich (jak podczas korzystania z kontroli źródła) i podczas wdrażania projektu na serwerze produkcyjnym. Aby uzyskać więcej informacji na temat środowisk wirtualnych i ich korzyści, zobacz [Używanie środowisk wirtualnych](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) i Zarządzanie [wymaganymi pakietami z plikem requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Po tym, jak program Visual Studio utworzy to środowisko, poszukaj w **Eksploratorze rozwiązań,** aby zobaczyć, że masz plik *app.py* wraz z *plikiem requirements.txt*. Otwórz *app.py,* aby zobaczyć, że szablon dostarczył kod taki jak w [przewodniku Szybki start — tworzenie aplikacji sieci web z flask](../ide/quickstart-python.md), z kilkoma dodanymi sekcjami. Cały kod pokazany poniżej jest tworzony przez szablon, więc nie musisz wklejać żadnych *do app.py* siebie.

    Kod rozpoczyna się od niezbędnych importów:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Dalej jest następujący wiersz, który może być przydatne podczas wdrażania aplikacji do hosta sieci web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Następnie przychodzi dekorator trasy na prostej funkcji, która definiuje widok:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Na koniec poniższy kod startowy umożliwia ustawienie hosta i portu za pomocą zmiennych środowiskowych, a nie ich kodowanie na twardo. Taki kod pozwala łatwo kontrolować konfigurację zarówno na maszynach deweloperskich, jak i produkcyjnych bez zmiany kodu:

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

1. Wybierz **debugowanie** > **start bez debugowania,** aby `localhost:5555`uruchomić aplikację i otworzyć przeglądarkę do .

**Pytanie: Jakie inne szablony języka Python oferuje program Visual Studio?**

**Odpowiedź:** Po zainstalowaniu obciążenia języka Python program Visual Studio udostępnia wiele szablonów projektów, w tym szablony dla [struktur sieci Web Flask, Bottle i Django,](../python/python-web-application-project-templates.md)usługi w chmurze platformy Azure, różne scenariusze uczenia maszynowego, a nawet szablon do tworzenia projektu z istniejącej struktury folderów zawierającej aplikację języka Python. Dostęp do nich można uzyskać za pośrednictwem okna dialogowego **Plik** > **nowego** > **projektu,** wybierając węzeł języka **Języka Python** i jego węzły podrzędne.

Visual Studio udostępnia również wiele szablonów plików lub *elementów,* aby szybko utworzyć klasę Języka Python, pakiet Pythona, test jednostkowy języka Python, pliki *web.config* i inne. Po otwarciu projektu języka Python można uzyskać dostęp do szablonów elementów za pomocą polecenia menu**Dodaj nowy element** **projektu.** >  Zobacz odwołanie do [szablonów elementów.](python-item-templates.md)

Korzystanie z szablonów może zaoszczędzić dużo czasu podczas uruchamiania projektu lub tworzenia pliku, a także jest doskonałym sposobem na poznanie różnych typów aplikacji i struktur kodu. Warto poświęcić kilka minut na tworzenie projektów i elementów z różnych szablonów, aby zapoznać się z tym, co oferują.

**Pytanie: Czy mogę również korzystać z szablonów Cookiecutter?**

**Odpowiedź**: Tak! W rzeczywistości visual studio zapewnia bezpośrednią integrację z Cookiecutter, o którym można dowiedzieć się za pomocą [przewodnika Szybki start: Utwórz projekt za pomocą szablonu Cookiecutter.](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z Pythonem w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz też

- [Ręczne identyfikowanie istniejącego interpretera języka Python](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalowanie obsługi języka Python w programie Visual Studio 2015 i wcześniejszych](installing-python-support-in-visual-studio.md)
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations)

---
title: Szablon projektów internetowych Django dla języka Python
description: Visual Studio zapewniają kompleksowego szablonu do szybkiego tworzenia aplikacji sieci web Django przy użyciu języka Python.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 136c03ef11071e5d548e36e45a6a541cffce1469
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59366383"
---
# <a name="django-web-project-template"></a>Szablon projektów internetowych Django

[Django](https://www.djangoproject.com/) jest przeznaczony do tworzenia aplikacji internetowych szybki, bezpieczny i skalowalny struktura języka Python wysokiego poziomu. Obsługa języka Python w programie Visual Studio zawiera kilka szablonów projektów konfigurowania struktury aplikacji sieci web opartych na Django. Aby użyć szablonu w programie Visual Studio, wybierz **pliku** > **New** > **projektu**, wyszukaj "Django" i wybierz z  **Pusty projekt sieci Web Django**, **projektu sieci Web Django**, i **projektu sieci Web Django sond** szablonów. Zobacz [samouczek Dowiedz się, Django](learn-django-in-visual-studio-step-01-project-and-solution.md) przewodnik wszystkich szablonów.

Program Visual Studio udostępnia pełną obsługą technologii IntelliSense dla projektów Django:

- Zmienne kontekstowe są przekazywane do szablonu:

    ![Funkcja IntelliSense dla zmiennych kontekstowych](media/template-django-intellisense.png)

- Tagowania i filtrowania dla obu elementy wbudowane i zdefiniowane przez użytkownika:

    ![Funkcja IntelliSense dla tagów i filtry](media/template-django-intellisense-filter.png)

- Kolorowanie dla osadzonych CSS i JavaScript składni:

    ![CSS, IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio udostępnia również podpowiedzi pełnej [obsługi debugowania](debugging-python-in-visual-studio.md) dla projektów Django:

![Punkty przerwania](media/template-django-debugging.png)

Jest typowy dla projektów Django, które mają być zarządzane za pomocą ich *manage.py* pliku, który jest założenie, że program Visual Studio jest zgodna. Jeśli użytkownik zaprzestanie korzystania z tego pliku jako punkt wejścia, zasadniczo przerwania pliku projektu. W takim przypadku należy [ponownie utworzyć projekt z istniejących plików](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) bez oznaczania go jako projekt Django.

## <a name="django-management-console"></a>Konsoli zarządzania Django

W konsoli zarządzania Django odbywa się za pośrednictwem różnych poleceń na **projektu** menu lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**.

- **Otwórz powłokę Django**: otwiera powłokę w kontekście swojej aplikacji, która umożliwia Ci manipulowanie swoimi modelami:

    ![Wyniki polecenia Otwórz powłokę Django](media/template-django-console-shell.png)

- **Baza danych synchronizacji Django**: wykonuje `manage.py syncdb` w **Interactive** okna:

    ![Wynik użycia polecenia Baza danych synchronizacji Django](media/template-django-console-sync-db.png)

- **Zbieraj statyczne**: wykonuje `manage.py collectstatic --noinput` do skopiowania wszystkich plików statycznych w ścieżce określonej przez `STATIC_ROOT` w swojej *settings.py*.

    ![Wynik użycia polecenia zbieranie statyczne](media/template-django-console-collect-static.png)

- **Sprawdź poprawność**: wykonuje `manage.py validate`, który zgłasza wszelkie błędy sprawdzania poprawności zainstalowanych modeli określonego przez `INSTALLED_APPS` w Twojej *settings.py*:

    ![Wynik użycia polecenia sprawdzania poprawności](media/template-django-console-validate.png)

## <a name="see-also"></a>Zobacz także

- [Poznaj samouczek Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

---
title: Szablon projektu sieciOwego Django dla Pythona
description: Visual Studio zapewnia kompleksowy szablon do szybkiego tworzenia aplikacji internetowych Django za pomocą języka Python.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784890"
---
# <a name="django-web-project-template"></a>Szablon projektów internetowych Django

[Django](https://www.djangoproject.com/) to wysokiej klasy struktura Pythona zaprojektowana z myślą o szybkim, bezpiecznym i skalowalnym tworzeniu stron internetowych. Obsługa języka Python w programie Visual Studio udostępnia kilka szablonów projektu, aby skonfigurować strukturę aplikacji sieci web opartej na Django. Aby użyć szablonu w programie Visual Studio, wybierz **pozycję Plik** > **nowego** > **projektu**, wyszukaj hasło "Django" i wybierz z **pustego projektu sieciOwego Django**, **Django Web Project**i sonduje szablony **Django Web Project.** Zapoznaj się z [samouczkiem Learn Django,](learn-django-in-visual-studio-step-01-project-and-solution.md) aby zapoznać się ze wszystkimi szablonami.

Visual Studio zapewnia pełną intellisense dla projektów Django:

- Zmienne kontekstowe przekazywane do szablonu:

    ![IntelliSense dla zmiennych kontekstowych](media/template-django-intellisense.png)

- Oznaczanie i filtrowanie zarówno dla wbudowanych, jak i zdefiniowanych przez użytkownika:

    ![IntelliSense dla tagów i filtrów](media/template-django-intellisense-filter.png)

- Kolorystyka składni dla osadzonych CSS i JavaScript:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio zapewnia również pełną [obsługę debugowania](debugging-python-in-visual-studio.md) dla projektów Django:

![Punkty przerwania](media/template-django-debugging.png)

Jest to typowe dla projektów Django, które mają być zarządzane za pośrednictwem ich *pliku manage.py,* co jest założeniem, że visual studio następuje. Jeśli przestaniesz używać tego pliku jako punktu wejścia, zasadniczo rozbijesz plik projektu. W takim przypadku musisz [odtworzyć projekt z istniejących plików](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) bez oznaczania go jako projektu Django.

## <a name="django-management-console"></a>Konsola zarządzania Django

Dostęp do konsoli zarządzania Django można uzyskać za pomocą różnych poleceń w menu **Projekt** lub po kliknięciu prawym przyciskiem myszy projektu w **Eksploratorze rozwiązań.**

- **Otwórz Powłokę Django**: otwiera powłokę w kontekście aplikacji, która umożliwia manipulowanie modelami:

    ![Wyniki polecenia Otwórz Powłokę Django](media/template-django-console-shell.png)

- **Django Sync DB** `manage.py syncdb` : wykonuje w oknie **interaktywnym:**

    ![Wynik polecenia Django Sync DB](media/template-django-console-sync-db.png)

- **Collect Static**: `manage.py collectstatic --noinput` wykonuje, aby skopiować wszystkie pliki `STATIC_ROOT` statyczne do ścieżki określonej w *settings.py*.

    ![Wynik polecenia Zbieranie ładunków statycznych](media/template-django-console-collect-static.png)

- **Sprawdź poprawność** `manage.py validate`: wykonuje , który zgłasza wszelkie błędy `INSTALLED_APPS` sprawdzania poprawności w zainstalowanych modelach określonych w *settings.py:*

    ![Wynik polecenia Sprawdzanie poprawności](media/template-django-console-validate.png)

## <a name="see-also"></a>Zobacz też

- [Dowiedz się samouczek Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

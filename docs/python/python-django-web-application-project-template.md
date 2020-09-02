---
title: Szablon projektu sieci Web Django dla języka Python
description: Program Visual Studio oferuje kompleksowy szablon służący do szybkiego tworzenia aplikacji sieci Web Django za pomocą języka Python.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62784890"
---
# <a name="django-web-project-template"></a>Szablon projektów internetowych Django

[Django](https://www.djangoproject.com/) to struktura języka Python wysokiego poziomu przeznaczona do szybkiego, bezpiecznego i skalowalnego programowania w sieci Web. Obsługa języka Python w programie Visual Studio oferuje kilka szablonów projektów służących do konfigurowania struktury aplikacji sieci Web opartej na Django. Aby użyć szablonu w programie Visual Studio, wybierz pozycję **plik**  >  **Nowy**  >  **projekt**, wyszukaj ciąg "Django", a następnie wybierz pozycję z **pustego projektu sieci Web Django**, **Django projektu**sieci Web i **sondowania Django szablonów projektu sieci Web** . Zobacz [samouczek uczenie Django](learn-django-in-visual-studio-step-01-project-and-solution.md) , aby zapoznać się z przewodnikiem dotyczącym wszystkich szablonów.

Program Visual Studio oferuje pełną funkcję IntelliSense dla projektów Django:

- Zmienne kontekstowe zostały przesłane do szablonu:

    ![Funkcja IntelliSense dla zmiennych kontekstowych](media/template-django-intellisense.png)

- Tagowanie i filtrowanie dla zarówno wbudowanych, jak i zdefiniowanych przez użytkownika:

    ![Funkcja IntelliSense dla tagów i filtrów](media/template-django-intellisense-filter.png)

- Kolorowanie składni dla osadzonych stylów CSS i JavaScript:

    ![IntelliSense CSS](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Program Visual Studio zapewnia także pełną [obsługę debugowania](debugging-python-in-visual-studio.md) dla projektów Django:

![Punkty przerwania](media/template-django-debugging.png)

Typowe dla projektów Django, które mają być zarządzane za poorednictwem ich pliku *manage.py* , założono, że program Visual Studio jest następujący. Jeśli zatrzymasz korzystanie z tego pliku jako punktu wejścia, należy zasadniczo przerwać plik projektu. W takim przypadku należy [ponownie utworzyć projekt z istniejących plików](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) bez oznaczania go jako projektu Django.

## <a name="django-management-console"></a>Konsola zarządzania Django

Konsola zarządzania Django jest dostępna za pomocą różnych poleceń w menu **projekt** lub klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**.

- **Otwórz powłokę Django**: otwiera powłokę w kontekście aplikacji, która pozwala na manipulowanie modelami:

    ![Wyniki polecenia Open Shell powłoki Django](media/template-django-console-shell.png)

- **Django synchronizacji bazy danych**: wykonuje `manage.py syncdb` się w oknie **interaktywnym** :

    ![Wynik polecenia Django Sync DB](media/template-django-console-sync-db.png)

- **Zbierz elementy statyczne**: wykonuje `manage.py collectstatic --noinput` , aby skopiować wszystkie pliki statyczne do ścieżki określonej przez `STATIC_ROOT` *Settings.py*.

    ![Wynik polecenia Collect static](media/template-django-console-collect-static.png)

- **Validate**: wykonuje `manage.py validate` , które raportuje błędy walidacji w zainstalowanych modelach określonych przez `INSTALLED_APPS` w *Settings.py*:

    ![Wynik polecenia Validate](media/template-django-console-validate.png)

## <a name="see-also"></a>Zobacz też

- [Poznaj samouczek Django](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

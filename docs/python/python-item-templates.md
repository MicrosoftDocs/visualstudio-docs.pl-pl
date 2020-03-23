---
title: Szablony elementów dla projektów języka Python
description: Lista odwołań szablonów elementów dla projektu języka Python, które są dostępne za pośrednictwem okna dialogowego Dodaj > nowy element w programie Visual Studio.
ms.date: 12/06/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c093dad1364fd5209f51c8e87e3fb99b3c1d3c4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430345"
---
# <a name="python-item-templates"></a>Szablony elementów języka Python

Szablony elementów są dostępne w projektach języka Python za pomocą polecenia menu Dodaj**nowy element** **projektu** > lub polecenia **Dodaj** > **nowy element** w menu kontekstowym w **Eksploratorze rozwiązań**.

![Okno dialogowe Dodawanie nowego elementu](media/project-item-templates.png)

Używając nazwy nadającej element, szablon zazwyczaj tworzy jeden lub więcej plików i folderów w aktualnie wybranym folderze w projekcie (kliknięcie prawym przyciskiem myszy folderu w celu wywołania menu kontekstowego powoduje automatyczne wybranie tego folderu). Dodanie elementu zawiera go w projekcie programu Visual Studio, a element pojawi się w **Eksploratorze rozwiązań**.

W poniższej tabeli pokrótce wyjaśniono efekt każdego szablonu elementu w ramach projektu języka Python:

| Szablon | Co tworzy szablon |
| --- | --- |
| **Pusty plik Pythona** | Pusty plik z rozszerzeniem *py.* |
| **Klasa Pythona** | Plik *py zawierający* pojedynczą pustą definicję klasy Języka Python. |
| **Pakiet Pythona** | Folder zawierający * \_ \_plik\_\_.py init.* |
| **Test jednostkowy Języka Python** | Plik *.py* z pojedynczym testem `unittest` jednostkowym opartym `unittest.main()` na platformie, wraz z wywołaniem uruchomienia testów w pliku. |
| **Strona HTML** | Plik *.html* z prostą strukturą `<head>` `<body>` strony składającą się z elementu i elementu. |
| **Javascript** | Pusty plik *.js.* |
| **Arkusz stylów** | Plik *css zawierający* pusty styl `body`dla . |
| **Plik tekstowy** | Pusty plik *txt.* |
| **Aplikacja Django 1.9**<br/>**Aplikacja Django 1.4** | Folder o nazwie aplikacji, który zawiera podstawowe pliki dla aplikacji Django, jak wyjaśniono w [Learn Django w Programie Visual Studio, Krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) dla Django 1.9. W przypadku Django 1.4 folder *migracji,* plik *admin.py* i plik *apps.py* nie są uwzględniane. |
| **Okno WPF IronPython** | Okno WPF składające się z dwóch plików side-by-side: pliku *xaml,* który definiuje `<Window>` z pustym `<Grid>` elementem i skojarzonego `wpf` pliku *py,* który ładuje plik XAML za pomocą biblioteki. Zazwyczaj używane w ramach projektu utworzonego przy użyciu jednego z szablonów projektu IronPython. Zobacz [Zarządzanie projektami języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates). |
| **Pliki obsługi ról sieci Web** | Folder *pojemnika* w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślny skrypt wdrażania i plik *web.config* dla ról sieci Web usługi Azure Cloud Service. Szablon zawiera również plik *readme.html,* który wyjaśnia szczegóły. |
| **Pliki obsługi ról procesu roboczego** | Folder *pojemnika* w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślny skrypt wdrażania i uruchamiania wraz z plikiem *web.config* dla ról procesu roboczego usługi Azure Cloud Service. Szablon zawiera również plik *readme.html,* który wyjaśnia szczegóły. |
| **Usługa Azure web.config (FastCGI)** | Plik *web.config* zawierający wpisy dla aplikacji używających obiektu [WSGI](https://wsgi.readthedocs.io/en/latest/) do obsługi połączeń przychodzących. Ten plik jest zazwyczaj wdrażany w katalogu głównym serwera sieci web z uruchomionymi usługami IIS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla aplikacji IIS](configure-web-apps-for-iis-windows.md). |
| **Usługa Azure web.config (httpplatformhandler)** | Plik *web.config* zawierający wpisy dla aplikacji, które nasłuchiwają na gnieździe dla połączeń przychodzących. Ten plik jest zazwyczaj wdrażany w katalogu głównym serwera sieci web z uruchomionymi usługami IIS, takich jak usługa Azure App Service. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla aplikacji IIS](configure-web-apps-for-iis-windows.md). |
| **Pliki statyczne platformy Azure web.config** | Plik *web.config* zazwyczaj dodawany do folderu *statycznego* (lub innego folderu zawierającego elementy statyczne), aby wyłączyć obsługę języka Python dla tego folderu. Ten plik konfiguracyjny działa w połączeniu z jednym z plików config FastCGI lub HttpPlatformHandler powyżej. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla aplikacji IIS](configure-web-apps-for-iis-windows.md). |
| **Zdalne debugowanie usługi Azure web.config** | Przestarzałe (był używany do zdalnego debugowania w usłudze Azure App Service dla systemu Windows, który nie jest już obsługiwany). |

## <a name="see-also"></a>Zobacz też

- [Zarządzanie projektami języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates)
- [Szablony projektów sieci Web języka Python](python-web-application-project-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

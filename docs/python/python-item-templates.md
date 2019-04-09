---
title: Szablony elementów dla projektów języka Python
description: Uzyskać listę szablonów elementów projektu języka Python, które są dostępne za pośrednictwem Dodaj > Nowy element okna dialogowego, w programie Visual Studio.
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
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366461"
---
# <a name="python-item-templates"></a>Szablony elementów języka Python

Szablony elementu są dostępne w projektach języka Python za pomocą **projektu** > **Dodaj nowy element** polecenie menu lub **Dodaj**  >  **Nowy element** polecenia menu kontekstowego w **Eksploratora rozwiązań**.

![Dodaj nowy element, okno dialogowe](media/project-item-templates.png)

Przy użyciu nazwy, podaj dla elementu, szablon zazwyczaj tworzy jeden lub więcej plików i folderów w ramach aktualnie wybranego folderu w projekcie (kliknij prawym przyciskiem myszy folder, aby wyświetlić menu kontekstowe automatycznie wybiera ten folder). Dodanie elementu zawiera w projekcie programu Visual Studio, a element pojawia się w **Eksploratora rozwiązań**.

W poniższej tabeli opisano skrótowo efekt każdego szablonu elementu w obrębie projektu języka Python:

| Szablon | Ten szablon tworzy |
| --- | --- |
| **Soubor Pythonu pusty** | Pusty plik za pomocą *PY* rozszerzenia. |
| **Klasa języka Python** | A *PY* plik zawierający pojedynczy pustą definicję klasy języka Python. |
| **Pakiet języka Python** | Folder, który zawiera  *\_ \_init\_\_PY* pliku. |
| **Test jednotky Pythonu** | A *.py* na podstawie pliku z testem pojedyncza jednostka `unittest` strukturę, wraz z wywołania `unittest.main()` do uruchamiania testów w pliku. |
| **Strona HTML** | *.Html* plik z prostą stronę strukturę złożoną z `<head>` i `<body>` elementu. |
| **JavaScript** | Pusta *js* pliku. |
| **Arkusz stylów** | A *.css* plik zawierający stylu pusty `body`. |
| **Plik tekstowy** | Pusta *.txt* pliku. |
| **Aplikacja Django 1.9**<br/>**Aplikacja Django 1.4** | Folder o nazwie aplikacji, która zawiera podstawowe pliki dla aplikacji Django, jak wyjaśniono w [Dowiedz się, Django w programie Visual Studio, krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) dla Django 1.9. Dla Django 1.4 *migracje* folderze *admin.py* pliku i *apps.py* pliku nie są uwzględniane. |
| **IronPython WPF Window** | Okno WPF, składający się z dwóch plików side-by-side: *.xaml* pliku, który definiuje `<Window>` z pustym `<Grid>` elementu, a skojarzone *PY* pliku, który ładuje, przy użyciu pliku XAML `wpf` biblioteki. Zazwyczaj używane w ramach projektu utworzonych za pomocą jednego z szablonów projektów Ironpythonu. Zobacz [Zarządzanie projektów języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates). |
| **Pliki obsługi roli sieci Web** | A *bin* folderu w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślny skrypt wdrożenia i *web.config* pliku dla ról sieci web w usłudze Azure Cloud Services. Szablon zawiera również *readme.html* pliku, który zawiera szczegółowe informacje. |
| **Pliki obsługi roli procesu roboczego** | A *bin* folderu w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślne wdrożenie, a następnie uruchom skrypt, wraz z *web.config* pliku dla ról procesów roboczych w usłudze Azure Cloud Services. Szablon zawiera również *readme.html* pliku, który zawiera szczegółowe informacje. |
| **Web.config Pro Azure (FastCGI)** | A *web.config* pliku, który zawiera wpisy dla aplikacji przy użyciu [WSGI](https://wsgi.readthedocs.io/en/latest/) obiektu do obsługi połączeń przychodzących. Ten plik zazwyczaj jest wdrażana w katalogu głównym serwera sieci web usług IIS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **Web.config Pro Azure (HttpPlatformHandler)** | A *web.config* pliku, który zawiera wpisy dla aplikacji, które nasłuchują na gniazdo dla połączeń przychodzących. Ten plik jest zwykle wdrażana do głównego serwera sieci web usług IIS, takich jak usługa Azure App Service. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **Plik web.config platformy Azure pliki statyczne** | A *web.config* zazwyczaj są dodawane do pliku *statyczne* folderu (lub inne folderu zawierającego elementy statyczne), można wyłączyć obsługi dla danego folderu języka Python. Ten plik konfiguracji działa w połączeniu z jednym z tych FastCGI lub HttpPlatformHandler konfiguracji plików. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **Web.config Pro Azure zdalnego debugowania** | Przestarzałe (został użyty do zdalnego debugowania w usłudze Azure App Service dla Windows, który nie jest już obsługiwane). |

## <a name="see-also"></a>Zobacz także

- [Zarządzanie projektów języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates)
- [Szablony projektów sieci web języka Python](python-web-application-project-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

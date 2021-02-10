---
title: Szablony elementów dla projektów języka Python
description: Lista referencyjna szablonów elementów dla projektu języka Python, które są dostępne za pomocą okna dialogowego Dodawanie > nowego elementu w programie Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 23a79d0842592ff3ad68f63c2739a2af9847aaeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945165"
---
# <a name="python-item-templates"></a>Szablony elementów języka Python

Szablony elementów są dostępne w projektach języka Python za pomocą   >  polecenia menu **Dodaj nowy element** lub polecenie **Dodaj**  >  **nowy element** w menu kontekstowym w **Eksplorator rozwiązań**.

![Okno dialogowe Dodawanie nowego elementu](media/project-item-templates.png)

Przy użyciu nazwy podanym dla elementu szablon zwykle tworzy jeden lub więcej plików i folderów w aktualnie wybranym folderze w projekcie (kliknij prawym przyciskiem myszy folder, aby wyświetlić menu kontekstowe automatycznie zaznacza ten folder). Dodanie elementu zawiera go w projekcie programu Visual Studio, a element pojawi się w **Eksplorator rozwiązań**.

W poniższej tabeli opisano efekt każdego szablonu elementu w ramach projektu języka Python:

| Template | Co tworzy szablon |
| --- | --- |
| **Pusty plik języka Python** | Pusty plik z rozszerzeniem *. PR* . |
| **Klasa języka Python** | Plik *. PR* zawierający pojedynczą pustą definicję klasy języka Python. |
| **Pakiet języka Python** | Folder zawierający plik *\_ \_ init \_ \_ . PR* . |
| **Test jednostkowy języka Python** | Plik *. PR* z pojedynczym testem jednostkowym opartym na `unittest` strukturze, wraz z wywołaniem do `unittest.main()` uruchomienia testów w pliku. |
| **Strona HTML** | Plik *. html* z prostą strukturą strony składającą się `<head>` z `<body>` elementów i. |
| **JavaScript** | Pusty plik  *. js* . |
| **Arkusz stylów** | Plik *. css* zawierający pusty styl dla `body` . |
| **Plik tekstowy** | Pusty plik *txt* . |
| **Aplikacja Django 1,9**<br/>**Aplikacja Django 1,4** | Folder o nazwie aplikacji, który zawiera podstawowe pliki dla aplikacji Django, zgodnie z opisem w temacie [Django in Visual Studio, krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) dla Django 1,9. W przypadku Django 1,4 nie są uwzględniane foldery *migracji* , plik *admin.py* i plik *Apps.py* . |
| **IronPython okno WPF** | Okno WPF składające się z dwóch plików obok siebie: plik *XAML* , który definiuje `<Window>` element z pustym `<Grid>` elementem i skojarzony z nim plik *. PR* , który ładuje plik XAML przy użyciu `wpf` biblioteki. Zwykle używane w projekcie utworzonym przy użyciu jednego z szablonów projektów IronPython. Zobacz [Zarządzanie projektami Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates). |
| **Pliki obsługi roli sieci Web** | Folder *bin* w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślny skrypt wdrażania i plik *web.config* dla ról sieci Web usług w chmurze platformy Azure. Szablon zawiera również plik *readme.html* , który objaśnia szczegóły. |
| **Pliki obsługi roli proces roboczy** | Folder *bin* w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślne wdrożenie i skrypt uruchamiania wraz z plikiem *web.config* dla ról procesów roboczych usługi w chmurze platformy Azure. Szablon zawiera również plik *readme.html* , który objaśnia szczegóły. |
| **web.config platformy Azure (FastCGI)** | Plik *web.config* zawierający wpisy dla aplikacji korzystających z obiektu [WSGI](https://wsgi.readthedocs.io/en/latest/) do obsługi połączeń przychodzących. Ten plik jest zwykle wdrażany w katalogu głównym serwera sieci Web z uruchomionymi usługami IIS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **web.config platformy Azure (HttpPlatformHandler)** | Plik *web.config* zawierający wpisy dla aplikacji, które nasłuchują w gnieździe dla połączeń przychodzących. Ten plik jest zwykle wdrażany w katalogu głównym serwera sieci Web z uruchomionymi usługami IIS, takimi jak Azure App Service. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **web.configplików statycznych platformy Azure** | Plik *web.config* zwykle dodawany do folderu *statycznego* (lub innego folderu zawierającego elementy statyczne), aby wyłączyć obsługę języka Python dla tego folderu. Ten plik konfiguracji działa w połączeniu z jednym z plików konfiguracji FastCGI lub HttpPlatformHandler powyżej. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji dla usług IIS](configure-web-apps-for-iis-windows.md). |
| **web.configzdalnego debugowania platformy Azure** | Przestarzałe (użyto do zdalnego debugowania w Azure App Service dla systemu Windows, które nie jest już obsługiwane). |

## <a name="see-also"></a>Zobacz też

- [Zarządzanie projektami języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates)
- [Szablony projektu sieci Web w języku Python](python-web-application-project-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

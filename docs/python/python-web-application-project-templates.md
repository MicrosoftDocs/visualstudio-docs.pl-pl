---
title: Szablony aplikacji sieci Web dla języka Python
description: Visual Studio udostępnia szablony dla aplikacji sieci web języka Python przy użyciu bottle, Flask i Django frameworks; obsługa obejmuje debugowanie konfiguracji i publikowanie w usłudze Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 73420f5fa6a90638f4a3dbbdf484178c5e177ce9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302757"
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji sieci Web języka Python

Python w programie Visual Studio obsługuje tworzenie projektów sieci web w strukturach Bottle, Flask i Django za pośrednictwem szablonów projektów i uruchamiania debugowania, które można skonfigurować do obsługi różnych struktur. Szablony te zawierają plik *requirements.txt* do deklarowania niezbędnych zależności. Podczas tworzenia projektu z jednego z tych szablonów program Visual Studio monituje o zainstalowanie tych pakietów (zobacz [Instalowanie wymagań projektu](#install-project-requirements) w dalszej części tego artykułu).

Można również użyć ogólnego szablonu **projektu sieci Web** dla innych struktur, takich jak Ostrosłupa. W takim przypadku nie są instalowane żadne struktury z szablonem. Zamiast tego zainstaluj niezbędne pakiety w środowisku używanym do projektu (zobacz [okno środowiska Języka Python — karta Pakiet).](python-environments-window-tab-reference.md#packages-tab)

Aby uzyskać informacje na temat wdrażania aplikacji sieci Web języka Python na platformie Azure, zobacz [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Używanie szablonu projektu

Projekt jest tworzęny na podstawie szablonu przy użyciu **pliku** > **nowego** > **projektu**. Aby wyświetlić szablony projektów internetowych, wybierz pozycję **Python** > **Web** po lewej stronie okna dialogowego. Następnie wybierz wybrany szablon, podając nazwy projektu i rozwiązania, ustaw opcje katalogu rozwiązań i repozytorium Git, a następnie wybierz **przycisk OK**.

![Nowe okno dialogowe projektu dla aplikacji sieci Web](media/projects-new-project-dialog-web.png)

Ogólny szablon **projektu sieci Web,** o którym wspomniano wcześniej, zawiera tylko pusty projekt programu Visual Studio bez kodu i bez założeń innych niż projekt języka Python. Aby uzyskać szczegółowe informacje na temat szablonu **usługi azure cloud service,** zobacz [projekty usług w chmurze platformy Azure dla języka Python.](python-azure-cloud-service-project-template.md)

Wszystkie inne szablony są oparte na platformach sieciowych Bottle, Flask lub Django i dzielą się na trzy ogólne grupy, jak opisano w poniższych sekcjach. Aplikacje utworzone przez dowolny z tych szablonów zawierają wystarczający kod do uruchamiania i debugowania aplikacji lokalnie. Każdy z nich zapewnia również niezbędny [obiekt aplikacji WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) do użytku z produkcyjnymi serwerami sieci Web.

### <a name="blank-group"></a>Pusta grupa

Wszystkie ** \<puste struktury>** szablonów projektu sieci Web tworzą projekt z mniej lub bardziej minimalnym kodem współdzielczym i niezbędnymi zależnościami zadeklarowanym w pliku *requirements.txt.*

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web z pustą butelką** | Generuje minimalną aplikację w *app.py* ze stroną `/` główną `/hello/<name>` i stroną, która odbija `<name>` się echem przy użyciu bardzo krótkiego szablonu strony wbudowanej. |
| **Pusty projekt internetowy Django** | Generuje projekt Django z podstawową strukturą witryny Django, ale bez aplikacji Django. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, jak Django Krok 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Pusty projekt sieci Web kolby** | Generuje minimalną aplikację z jednym "Hello World!" strona `/`dla . Ta aplikacja jest podobna do wyniku następujących szczegółowych kroków w [Przewodniku Szybki start: Użyj programu Visual Studio, aby utworzyć pierwszą aplikację internetową Python](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Zobacz [też: Naucz się kolby krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupa sieci Web

Wszystkie ** \<szablony programu Framework> Web Project** tworzą początkową aplikację sieci web o identycznym projekcie, niezależnie od wybranej struktury. Aplikacja ma strony Home, About i Kontakt, wraz z paskiem nawigacyjnym i responsywnym projektem za pomocą Bootstrap. Każda aplikacja jest odpowiednio skonfigurowana do obsługi plików statycznych (CSS, JavaScript i czcionek) i używa mechanizmu szablonu strony odpowiedniego dla tej struktury.

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web butelki** | Generuje aplikację, której pliki statyczne są zawarte w folderze *statycznym* i obsługiwane za pomocą kodu w *app.py*. Routing dla poszczególnych stron jest zawarty w *routes.py,* a folder *widoków* zawiera szablony stron.|
| **Projekt internetowy Django** | Generuje projekt Django i aplikację Django z trzema stronami, obsługą uwierzytelniania i bazą danych SQLite (ale bez modeli danych). Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, jak Django Krok 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Projekt sieci Web Kolby** | Generuje aplikację, której pliki statyczne znajdują się w folderze *statycznym.* Kod w *views.py* obsługuje routingu, z szablonami stron przy użyciu aparatu Jinja zawarte w folderze *szablonów.* Plik *runserver.py* zawiera kod startowy. Zobacz [: Learn Flask Step 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Projekt sieciowy Flask/Jade** | Generuje tę samą aplikację, co w przypadku szablonu **flask Web Project,** ale przy użyciu rozszerzenia Jade dla silnika szablonów Jinja. |

### <a name="polls-group"></a>Grupa Ankiety

**Struktura \<Sondy>** szablonów projektu sieci Web tworzą początkową aplikację sieci web, za pomocą której użytkownicy mogą głosować na różne pytania ankietowe. Każda aplikacja opiera się na strukturze szablonów projektów **sieci Web** do korzystania z bazy danych do zarządzania ankietami i odpowiedziami użytkowników. Aplikacje zawierają odpowiednie modele danych i specjalną stronę aplikacji (/seed), która ładuje ankiety z pliku *samples.json.*

| Szablon | Opis |
| --- | --- |
| **Sonduje bottle Web Project** | Generuje aplikację, która może działać z bazy danych w pamięci, MongoDB lub Usługi `REPOSITORY_NAME` Azure Table Storage, który jest skonfigurowany przy użyciu zmiennej środowiskowej. Modele danych i kod magazynu danych znajdują się w folderze *modeli,* a plik *settings.py* zawiera kod, aby określić, który magazyn danych jest używany. |
| **Sonduje projekt internetowy Django** | Generuje projekt Django i aplikację Django z trzema stronami i bazą danych SQLite. Zawiera dostosowania interfejsu administracyjnego Django, aby umożliwić uwierzytelnionemu administratorowi tworzenie ankiet i zarządzanie nimi. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, jak Django Step 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Sonduje projekt sieci Web Flask** | Generuje aplikację, która może działać z bazy danych w pamięci, MongoDB lub Usługi `REPOSITORY_NAME` Azure Table Storage, który jest skonfigurowany przy użyciu zmiennej środowiskowej. Modele danych i kod magazynu danych znajdują się w folderze *modeli,* a plik *settings.py* zawiera kod, aby określić, który magazyn danych jest używany. Aplikacja używa aparatu Jinja dla szablonów stron. Zobacz [: Learn Flask Step 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Sondy Flask / Jade Web Project** | Generuje tę samą aplikację, co w przypadku szablonu **projektu sieci Web Sondy Flask,** ale przy użyciu rozszerzenia Jade dla silnika szablonów Jinja. |

## <a name="install-project-requirements"></a>Instalowanie wymagań dotyczących projektu

Podczas tworzenia projektu z szablonu specyficznego dla struktury, pojawi się okno dialogowe, aby ułatwić instalowanie niezbędnych pakietów przy użyciu pip. Zaleca się również używanie [środowiska wirtualnego](selecting-a-python-environment-for-a-project.md#use-virtual-environments) dla projektów sieci web, aby podczas publikowania witryny sieci Web uwzględniane były poprawne zależności:

![Okno dialogowe instaluje potrzebne pakiety dla szablonu projektu](media/template-web-requirements-txt-wizard.png)

Jeśli używasz formantu źródła, zazwyczaj pomijasz folder środowiska wirtualnego, ponieważ to środowisko można odtworzyć tylko przy użyciu *pliku requirements.txt*. Najlepszym sposobem, aby wykluczyć folder jest najpierw wybrać ja zainstalować je samodzielnie w pytaniu **pokazanym** powyżej, a następnie wyłączyć auto-commit przed utworzeniem środowiska wirtualnego. Aby uzyskać szczegółowe informacje, zobacz [Dowiedz się Django Tutorial - Kroki 1-2 i 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) i [Dowiedz się Kolby Tutorial - Kroki 1-2 i 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Podczas wdrażania w usłudze Microsoft Azure App Service wybierz wersję języka Python jako [rozszerzenie witryny](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) i ręcznie zainstaluj pakiety. Ponadto ponieważ usługa Azure App Service **nie** instaluje automatycznie pakietów z pliku *requirements.txt* po wdrożeniu z programu Visual Studio, postępuj zgodnie ze szczegółami konfiguracji w [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md).

*Usługi* w chmurze platformy Microsoft Azure obsługują plik *requirements.txt.* Zobacz [projekty usług w chmurze platformy Azure, aby](python-azure-cloud-service-project-template.md) uzyskać szczegółowe informacje.

## <a name="debugging"></a>Debugging

Po uruchomieniu projektu sieci web do debugowania program Visual Studio uruchamia lokalny serwer sieci web na losowym porcie i otwiera domyślną przeglądarkę na ten adres i port. Aby określić dodatkowe opcje, kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Właściwości**i wybierz kartę **Web Launcher:**

![Właściwości uruchamiania sieci Web dla ogólnego szablonu sieci Web](media/template-web-launcher-properties.png)

W grupie **debugowania:**

- **Ścieżki wyszukiwania,** **argumenty skryptu,** **argumenty interpretera**i **ścieżka interpretera**: te opcje są takie same jak w przypadku [zwykłego debugowania.](debugging-python-in-visual-studio.md)
- **Uruchom adres URL:** określa adres URL, który jest otwarty w przeglądarce. Domyślnie wartość `localhost`.
- **Numer portu:** port do użycia, jeśli żaden nie jest określony w adresie URL (Visual Studio wybiera jeden automatycznie domyślnie). To ustawienie umożliwia zastąpienie domyślnej wartości `SERVER_PORT` zmiennej środowiskowej, która jest używana przez szablony do konfigurowania portu nasłuchiwał lokalnego serwera debugowania.

Właściwości grup **Polecenia uruchamiania serwera** i polecenia serwera **debugowania** (te ostatnie znajdują się poniżej tego, co jest pokazane na obrazie) określają sposób uruchamiania serwera sieci web. Ponieważ wiele struktur wymaga użycia skryptu poza bieżącym projektem, skrypt można skonfigurować w tym miejscu, a nazwa modułu startowego może być przekazywana jako parametr.

- **Polecenie**: może być skryptem Pythona ( `python.exe -m module_name` `python.exe -c "code"`*\*plik py),* nazwą modułu (jak w), lub pojedynczym wierszem kodu (jak w . ). Wartość w z listy rozwijanej wskazuje, który z tych typów jest przeznaczony.
- **Argumenty:** te argumenty są przekazywane w wierszu polecenia po poleceniu.
- **Środowisko:** oddzielona nowymi liniami \<lista>\<NAZWA = PARY> VALUE określające zmienne środowiskowe. Zmienne te są ustawiane po wszystkich właściwościach, które mogą modyfikować środowisko, takich jak numer portu i ścieżki wyszukiwania, a więc mogą zastąpić te wartości.

Dowolną właściwość projektu lub zmienną środowiskową można określić za `$(StartupFile) --port $(SERVER_PORT)`pomocą składni MSBuild, na przykład: .
`$(StartupFile)`jest względną ścieżką do `{StartupModule}` pliku startowego i jest importowaną nazwą pliku startowego. `$(SERVER_HOST)`i `$(SERVER_PORT)` są normalne zmienne środowiskowe, które są ustawiane przez **launch URL** i **numer portu** właściwości, automatycznie lub przez **Środowisko** właściwości.

> [!Note]
> Wartości w **polecenia uruchom serwer** są używane z poleceniem Uruchom**serwer** **debugowania** > lub **ctrl**+**F5**; wartości w grupie **Polecenia serwera debugowania** są używane z poleceniem **Debuguj** > **start serwera debugowania** lub **F5**.

### <a name="sample-bottle-configuration"></a>Konfiguracja butelki próbki

**Szablon Bottle Web Project** zawiera kod standardowy, który wykonuje niezbędną konfigurację. Zaimportowana aplikacja do butelek może nie zawierać tego kodu, jednak w `bottle` takim przypadku następujące ustawienia uruchamiają aplikację przy użyciu zainstalowanego modułu:

- **Uruchom grupę poleceń serwera:**
  - **Polecenie** `bottle` : (moduł)
  - **Argumenty**:`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Grupa **poleceń serwera debugowania:**
  - **Polecenie** `bottle` : (moduł)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Ta `--reload` opcja nie jest zalecane podczas korzystania z programu Visual Studio do debugowania.

### <a name="sample-pyramid-configuration"></a>Przykładowa konfiguracja piramidy

Aplikacje Pyramid są obecnie `pcreate` najlepiej tworzone za pomocą narzędzia wiersza polecenia. Po utworzeniu aplikacji można ją zaimportować za pomocą szablonu [**Z istniejącego kodu Języka Python.**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) Następnie wybierz dostosowanie **ogólnego projektu sieci Web,** aby skonfigurować opcje. Te ustawienia zakładają, że program `..\env`Pyramid jest instalowany w środowisku wirtualnym w pliku .

- Grupa **debugowania:**
  - **Port serwera:** 6543 (lub cokolwiek jest skonfigurowane w plikach *.ini)*

- **Uruchom grupę poleceń serwera:**
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty:`Production.ini`

- Grupa **poleceń serwera debugowania:**
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty:`Development.ini`

> [!Tip]
> Prawdopodobnie trzeba skonfigurować właściwość **katalogu roboczego** projektu, ponieważ aplikacje Pyramid są zazwyczaj jeden folder poniżej katalogu głównego projektu.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia innej struktury, które chcesz udostępnić, lub jeśli chcesz poprosić o ustawienia innej struktury, otwórz [problem w GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Konwertowanie projektu na usługę Azure Cloud Service

Polecenie **Konwertuj na usługę w chmurze platformy Microsoft Azure** (obrazek poniżej) dodaje do rozwiązania projekt usługi w chmurze. Ten projekt zawiera ustawienia wdrażania i konfigurację maszyn wirtualnych i usług, które mają być używane. Użyj polecenia **Publikuj** w projekcie w chmurze, aby wdrożyć je w usługach w chmurze; Polecenie **Publikuj** w projekcie języka Python nadal jest wdrażane w witrynach sieci Web. Aby uzyskać więcej informacji, zobacz [Projekty usług w chmurze platformy Azure](python-azure-cloud-service-project-template.md).

![Konwersja na polecenie projektu usługi w chmurze platformy Microsoft Azure](media/template-web-convert-menu.png)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do szablonów elementów języka Python](python-item-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

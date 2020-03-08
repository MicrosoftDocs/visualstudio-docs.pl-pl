---
title: Szablony aplikacji sieci Web dla języka Python
description: Program Visual Studio udostępnia szablony dla aplikacji sieci web języka Python za pomocą platformy Bottle, Flask i Django Obsługa obejmuje konfiguracje debugowania i publikowania w usłudze Azure App Service.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409985"
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji sieci web języka Python

Język Python w programie Visual Studio obsługuje tworzenie projektów sieci web platformy Bottle, Flask i Django przy użyciu szablonów projektu i uruchamianie debugowania, które mogą być skonfigurowane do obsługi różnych platform. Te szablony zawierają plik *Requirements. txt* , aby zadeklarować wymagane zależności. Podczas tworzenia projektu z jednego z tych szablonów program Visual Studio wyświetli komunikat z prośbą o zainstalowanie tych pakietów (zobacz temat [Instalowanie wymagań projektu](#install-project-requirements) w dalszej części tego artykułu).

Szablon ogólnego **projektu sieci Web** można również użyć dla innych struktur, takich jak ostrosłupowy. W tym przypadku nie struktur są instalowane przy użyciu szablonu. Zamiast tego Zainstaluj wymagane pakiety w środowisku używanym dla projektu (zobacz [okno środowiska języka Python — karta pakiet](python-environments-window-tab-reference.md#packages-tab)).

Aby uzyskać informacje na temat wdrażania aplikacji sieci Web w języku Python na platformie Azure, zobacz [Publikowanie w Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Należy użyć szablonu projektu

Projekt można utworzyć na podstawie szablonu przy użyciu **pliku** > **nowym** > **projekcie**. Aby wyświetlić szablony dla projektów sieci Web, wybierz pozycję **Python** > **sieci Web** po lewej stronie okna dialogowego. Następnie wybierz wybrany szablon, podając nazwy projektu i rozwiązania, ustaw opcje dla katalogu rozwiązania i repozytorium git, a następnie wybierz **przycisk OK**.

![Okno dialogowe Nowy projekt dla aplikacji sieci web](media/projects-new-project-dialog-web.png)

Ogólny szablon **projektu sieci Web** , wspomniany wcześniej, zawiera tylko pusty projekt programu Visual Studio bez kodu i nie ma założeń innych niż projekt języka Python. Aby uzyskać szczegółowe informacje na temat szablonu **usługi w chmurze platformy Azure** , zobacz [projekty usług w chmurze platformy Azure dla języka Python](python-azure-cloud-service-project-template.md).

Wszystkie inne szablony zależą od struktury sieci web Bottle, Flask i Django i można podzielić na trzy główne grupy, zgodnie z opisem w poniższych sekcjach. Aplikacje utworzone przez dowolnego z tych szablonów zawierają kod wystarczający do uruchamiania i debugowania aplikacji w środowisku lokalnym. Każdy z nich udostępnia również wymagany [obiekt aplikacji WSGI](https://www.python.org/dev/peps/pep-3333/) (Python.org) do użytku z serwerami produkcyjnymi sieci Web.

### <a name="blank-group"></a>Pusta grupa

Wszystkie **puste szablony projektu sieci Web w programie \<framework >** tworzą projekt z bardziej lub mniej minimalnym kodem i niezbędnymi zależnościami zadeklarowanymi w pliku *Requirements. txt* .

| Szablon | Opis |
| --- | --- |
| **Pusty projekt sieci Web** | Generuje minimalną aplikację w *App.py* ze stroną główną dla `/` i stronę `/hello/<name>`, która wyświetla `<name>` przy użyciu bardzo krótkiego szablonu strony wbudowanej. |
| **Pusty projekt sieci Web Django** | Generuje projekt Django przy użyciu struktury lokacji Django core, ale nie ma aplikacji Django. Aby uzyskać więcej informacji, zobacz [Szablony Django](python-django-web-application-project-template.md) i [Naucz Django krok 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Pusty projekt sieci Web** | Generuje minimalną aplikację za pomocą pojedynczego "Hello World!" Strona `/`. Ta aplikacja jest podobna do wyniku wykonania szczegółowych czynności z [przewodnika Szybki Start: Użyj programu Visual Studio, aby utworzyć pierwszą aplikację sieci Web w języku Python](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Zobacz też [więcej informacji o kolbie krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupa aplikacji sieci Web

Wszystkie szablony **projektu sieci Web platformy\<Framework >** tworzą Starter aplikacji sieci Web o identycznym projekcie niezależnie od wybranej struktury. Aplikacja ma w domu, stron o i skontaktuj się z pomocą, wraz z paska nawigacji i elastyczne środowisko za pomocą narzędzia Bootstrap. Każda aplikacja jest odpowiednio skonfigurowany do obsługi plików statycznych (CSS, JavaScript i czcionki) i używa mechanizmu szablon strony właściwe dla platformy.

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web butelek** | Generuje aplikację, której pliki statyczne są zawarte w folderze *statycznym* i obsługiwane przez kod w *App.py*. Routing dla poszczególnych stron jest zawarty w *Routes.py*, a folder *widoki* zawiera szablony stron.|
| **Projekt sieci Web Django** | Generuje projekt Django i aplikacji Django przy użyciu trzech stron, obsługę uwierzytelniania i bazy danych SQLite (ale nie modeli danych). Aby uzyskać więcej informacji, zobacz [Szablony Django](python-django-web-application-project-template.md) i [Naucz Django Step 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Przednie projektu sieci Web** | Generuje aplikację, której pliki statyczne są zawarte w folderze *statycznym* . Kod w *views.py* obsługuje routing z szablonami stron za pomocą aparatu jinja znajdującego się w folderze *templates* . Plik *runserver.py* zawiera kod uruchomienia. Zobacz [więcej informacji o kolbie krok 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Jade/projekt sieci Web** | Generuje tę samą aplikację jak dla szablonu **projektu sieci Web** , ale przy użyciu rozszerzenia Jade dla aparatu jinja tworzenia szablonów. |

### <a name="polls-group"></a>Grupa sond

Szablony **projektu sieci Web w programie sondy \<framework >** tworzą startową aplikację sieci Web, za pomocą której użytkownicy mogą głosować na różnych pytaniach dotyczących sondowania. Każda aplikacja tworzy na podstawie struktury szablonów projektu **sieci Web** , aby użyć bazy danych do zarządzania sondami i odpowiedziami użytkowników. Aplikacje obejmują odpowiednie modele danych i specjalną stronę aplikacji (/Seed), która ładuje sondy z pliku *Samples. JSON* .

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web w butelkach sond** | Generuje aplikację, która może być uruchamiana względem bazy danych w pamięci, MongoDB lub Table Storage platformy Azure, która jest konfigurowana przy użyciu zmiennej środowiskowej `REPOSITORY_NAME`. Modele danych i kod magazynu danych znajdują się w folderze *modele* , a plik *Settings.py* zawiera kod umożliwiający określenie, który magazyn danych jest używany. |
| **Projekt sieci Web Django sondowań** | Generuje projekt Django i aplikacja Django z trzy strony i bazy danych SQLite. Zawiera dostosowania interfejsu administracyjnego Django, aby umożliwić administratorowi tworzenie i zarządzanie nimi sond uwierzytelnionego. Aby uzyskać więcej informacji, zobacz [Szablony Django](python-django-web-application-project-template.md) i [Naucz Django krok 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Projekt sieci Web w kolbie sondowań** | Generuje aplikację, która może być uruchamiana względem bazy danych w pamięci, MongoDB lub Table Storage platformy Azure, która jest konfigurowana przy użyciu zmiennej środowiskowej `REPOSITORY_NAME`. Modele danych i kod magazynu danych znajdują się w folderze *modele* , a plik *Settings.py* zawiera kod umożliwiający określenie, który magazyn danych jest używany. Aplikacja używa aparatu Jinja dla szablonów stron. Zobacz [więcej informacji o kolbie krok 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Sonda/projekt sieci Web Jade** | Generuje taką samą aplikację jak w przypadku szablonu **projektu sieci Web kolby sondy** , ale przy użyciu rozszerzenia Jade dla aparatu jinja tworzenia szablonów. |

## <a name="install-project-requirements"></a>Zainstaluj wymagania projektu

Podczas tworzenia projektu z szablonu określonej platformy, aby zainstalować wymagane pakiety przy użyciu narzędzia pip pojawi się okno dialogowe. Zalecamy również użycie [środowiska wirtualnego](selecting-a-python-environment-for-a-project.md#use-virtual-environments) dla projektów sieci Web, aby podczas publikowania witryny sieci Web uwzględnić odpowiednie zależności:

![Okno dialogowe, które instaluje wymagane pakiety dla szablonu projektu](media/template-web-requirements-txt-wizard.png)

Jeśli używasz kontroli źródła, zazwyczaj pominięto folder środowiska wirtualnego, ponieważ to środowisko można odtworzyć tylko przy użyciu programu *Requirements. txt*. Najlepszym sposobem wykluczenia folderu jest wybranie opcji **I zainstalowanie ich samodzielnie** w pokazanym powyżej monicie, a następnie wyłączenie automatycznego zatwierdzania przed utworzeniem środowiska wirtualnego. Aby uzyskać szczegółowe informacje, zobacz [nauka samouczka Django — kroki 1-2 i 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) oraz [samouczki dotyczące kolb — kroki 1-2 i 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Podczas wdrażania programu w celu Microsoft Azure App Service wybierz wersję środowiska Python jako [rozszerzenie witryny](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) i ręcznie zainstaluj pakiety. Ponadto, ponieważ program Azure App Service **nie instaluje automatycznie pakietów** z pliku *Requirements. txt* w przypadku wdrożenia z programu Visual Studio, postępuj zgodnie ze szczegółowymi informacjami o konfiguracji w witrynie [aka.MS/PythonOnAppService](managing-python-on-azure-app-service.md).

Microsoft Azure Cloud Services *obsługuje* plik *Requirements. txt* . Aby uzyskać szczegółowe informacje, zobacz [projekty usługi w chmurze platformy Azure](python-azure-cloud-service-project-template.md) .

## <a name="debugging"></a>Debugowanie

Po rozpoczęciu debugowania projektu sieci web programu Visual Studio uruchamia lokalny serwer internetowy na losowy port i otwiera domyślna przeglądarka, w tym adres i port. Aby określić dodatkowe opcje, kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Właściwości**, a następnie wybierz kartę **Uruchamianie sieci Web** :

![Właściwości uruchamiającego sieci Web dla szablonu sieci web ogólnego](media/template-web-launcher-properties.png)

W grupie **debugowania** :

- **Ścieżki wyszukiwania**, **argumenty skryptu**, **argumenty interpretera**i **ścieżka interpretera**: te opcje są takie same jak w przypadku [normalnego debugowania](debugging-python-in-visual-studio.md).
- **Adres URL uruchamiania**: określa adres URL, który jest otwarty w przeglądarce. Domyślna wartość `localhost`.
- **Numer portu**: port, który ma być używany, jeśli żaden z nich nie jest określony w adresie URL (Domyślnie program Visual Studio wybierze opcję automatycznie). To ustawienie umożliwia przesłonięcie domyślnej wartości zmiennej środowiskowej `SERVER_PORT`, która jest używana przez szablony w celu skonfigurowania portu, na którym nasłuchuje lokalny serwer debugowania.

Właściwości w grupach poleceń **Uruchom serwer** i **Debuguj serwer** (te ostatnie są poniżej informacji przedstawionych na obrazie) określają sposób uruchamiania serwera sieci Web. Ponieważ wiele struktur wymaga użycia skryptu poza bieżący projekt, w tym miejscu można skonfigurować skrypt i nazwa modułu uruchamiania może być przekazywany jako parametr.

- **Polecenie**: może to być skrypt w języku Python (plik *\*. PR* ), Nazwa modułu (jak w, `python.exe -m module_name`) lub jeden wiersz kodu (jak w, `python.exe -c "code"`). Wartość w polu listy rozwijanej wskazuje, który z tych typów jest przeznaczony.
- **Argumenty**: te argumenty są przekazane w wierszu polecenia po poleceniu.
- **Środowisko**: rozdzielana znakami wielowierszowa lista \<nazw > =\<wartość > par określająca zmienne środowiskowe. Te zmienne są ustawiane po wszystkich właściwości, które mogą być modyfikowane w środowisku, na przykład portu ścieżki numer i wyszukiwania, a więc może spowodować zastąpienie tych wartości.

Dowolna właściwość projektu lub zmienna środowiskowa może być określona za pomocą składni MSBuild, na przykład: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` jest ścieżką względną do pliku startowego, a `{StartupModule}` to nieportowa nazwa pliku startowego. `$(SERVER_HOST)` i `$(SERVER_PORT)` są normalnymi zmiennymi środowiskowymi, które są ustawiane przez właściwości **Uruchom adres URL** i **numer portu** , automatycznie lub przez właściwość **Environment** .

> [!Note]
> Wartości w **poleceniu uruchamiania serwera** są używane z poleceniem **Debug** > **Start Server** lub **Ctrl**+**F5**; wartości w grupie **poleceń serwera debugowania** są używane z poleceniem **Debuguj** > **Uruchom serwer debugowania** lub **F5**.

### <a name="sample-bottle-configuration"></a>Przykładowa konfiguracja Bottle

Szablon **projektu sieci Web butelek** zawiera kod standardowy, który jest niezbędną konfiguracją. Zaimportowana aplikacja butelkowa nie może zawierać tego kodu, jednak w takim przypadku następujące ustawienia uruchamiają aplikację przy użyciu zainstalowanego modułu `bottle`:

- **Uruchom grupę poleceń serwera** :
  - **Polecenie**: `bottle` (moduł)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Grupa **poleceń serwera debugowania** :
  - **Polecenie**: `bottle` (moduł)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Opcja `--reload` nie jest zalecana w przypadku debugowania za pomocą programu Visual Studio.

### <a name="sample-pyramid-configuration"></a>Przykładowa konfiguracja ostrosłupowy

Aplikacje ostrosłupowe są obecnie najlepiej utworzone przy użyciu narzędzia wiersza polecenia `pcreate`. Po utworzeniu aplikacji można ją zaimportować przy użyciu [**istniejącego szablonu kodu języka Python**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) . Po wykonaniu tej czynności wybierz **Ogólne dostosowanie projektu sieci Web** , aby skonfigurować opcje. W tych ustawieniach przyjęto założenie, że ostrosłup jest instalowany w środowisku wirtualnym w `..\env`.

- Grupa **debugowania** :
  - **Port serwera**: 6543 (lub niezależnie od tego, czy jest skonfigurowany w plikach *. ini* )

- **Uruchom grupę poleceń serwera** :
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Production.ini`

- Grupa **poleceń serwera debugowania** :
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Development.ini`

> [!Tip]
> Prawdopodobnie trzeba będzie skonfigurować właściwość **katalogu roboczego** projektu, ponieważ aplikacje ostrosłupowe są zazwyczaj jednym folderem poniżej katalogu głównego projektu.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia dla innej struktury, którą chcesz udostępnić, lub jeśli chcesz zażądać ustawień dla innej platformy, Otwórz [problem w usłudze GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Konwertuj projekt na usługi w chmurze Azure

Polecenie **Konwertuj do Microsoft Azure projektu usługi w chmurze** (obraz poniżej) umożliwia dodanie projektu usługi w chmurze do rozwiązania. Ten projekt zawiera ustawienia wdrażania i konfiguracji dla maszyn wirtualnych i usług, które ma być używany. Użyj polecenia **Publikuj** w projekcie w chmurze, aby wdrożyć w Cloud Services; polecenie **Publikuj** w projekcie w języku Python jest nadal wdrażane w witrynach sieci Web. Aby uzyskać więcej informacji, zobacz [projekty usług w chmurze platformy Azure](python-azure-cloud-service-project-template.md).

![Konwertuj na projekt usługi chmury Microsoft Azure — polecenie](media/template-web-convert-menu.png)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja szablonów elementów języka Python](python-item-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

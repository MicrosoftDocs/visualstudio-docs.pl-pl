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
ms.openlocfilehash: 952c4d9ab82275ff7b1550a3704e89b93c6260a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954834"
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji sieci web języka Python

Język Python w programie Visual Studio obsługuje tworzenie projektów sieci web platformy Bottle, Flask i Django przy użyciu szablonów projektu i uruchamianie debugowania, które mogą być skonfigurowane do obsługi różnych platform. Te szablony obejmują *requirements.txt* pliku do zadeklarowania zależnościami. Podczas tworzenia projektu z jednej z tych szablonów, programu Visual Studio wyświetli monit o zainstalowanie tych pakietów (zobacz [Zainstaluj wymagania projektu](#install-project-requirements) w dalszej części tego artykułu).

Możesz również użyć ogólnego **projektu sieci Web** szablonu dla innych platform, takich jak ostrosłupa. W tym przypadku nie struktur są instalowane przy użyciu szablonu. Zamiast tego Zainstaluj wymagane pakiety do środowiska używasz projektu (zobacz [okna środowiska Python - karcie pakietu](python-environments-window-tab-reference.md#packages-tab)).

Aby uzyskać informacje na temat wdrażania aplikacji sieci web w języku Python na platformie Azure, zobacz [Publikuj w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Należy użyć szablonu projektu

Tworzenie projektu z szablonu za pomocą **pliku** > **New** > **projektu**. Aby wyświetlić szablony dla projektów sieci web, wybierz **Python** > **Web** po lewej stronie okna dialogowego. Następnie wybierz szablon wybranego, podanie nazwy projektu i rozwiązania, ustaw opcje katalogu rozwiązania i repozytorium Git i wybierz **OK**.

![Okno dialogowe Nowy projekt dla aplikacji sieci web](media/projects-new-project-dialog-web.png)

Ogólny **projektu sieci Web** szablon, wspomniano wcześniej, zawiera tylko pusty projekt programu Visual Studio z żadnego kodu i żadnych założeń niż trwa projektu języka Python. Aby uzyskać szczegółowe informacje na temat **usługa w chmurze** szablonu, zobacz [projektów usług w chmurze platformy Azure dla języka Python](python-azure-cloud-service-project-template.md).

Wszystkie inne szablony zależą od struktury sieci web Bottle, Flask i Django i można podzielić na trzy główne grupy, zgodnie z opisem w poniższych sekcjach. Aplikacje utworzone przez dowolnego z tych szablonów zawierają kod wystarczający do uruchamiania i debugowania aplikacji w środowisku lokalnym. Każdy z nich są także niezbędne [obiekt aplikacji WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) do użytku z serwerów sieci web w środowisku produkcyjnym.

### <a name="blank-group"></a>Pusta grupa

Wszystkie **puste \<framework > Projekt sieci Web** szablony tworzenia projektu z większej lub mniejszej ilości kodu w minimalnym stopniu deklaratywnie i zależnościami zadeklarowane w *requirements.txt* pliku.

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web Bottle puste** | Generuje minimalną aplikację w *app.py* ze stroną główną dla `/` i `/hello/<name>` strona, która zwraca `<name>` przy użyciu szablonu stronę wbudowanych bardzo krótki. |
| **Projekt puste Django sieci Web** | Generuje projekt Django przy użyciu struktury lokacji Django core, ale nie ma aplikacji Django. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, Django, krok 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Projekt sieci Web Flask puste** | Generuje minimalną aplikację za pomocą pojedynczego "Hello World!" stronie `/`. Ta aplikacja jest podobne do wyniku następującego szczegółowy opis kroków [Szybki Start: Tworzenie pierwszej aplikacji sieci web języka Python przy użyciu programu Visual Studio](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Zobacz też [Dowiedz się, Flask kroku 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupa aplikacji sieci Web

Wszystkie  **\<Framework > Projekt sieci Web** szablony utworzyć początkową aplikację sieci web za pomocą identycznych projektu, niezależnie od tego, w ramach wybranej. Aplikacja ma w domu, stron o i skontaktuj się z pomocą, wraz z paska nawigacji i elastyczne środowisko za pomocą narzędzia Bootstrap. Każda aplikacja jest odpowiednio skonfigurowany do obsługi plików statycznych (CSS, JavaScript i czcionki) i używa mechanizmu szablon strony właściwe dla platformy.

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web Bottle** | Generuje aplikację, w których pliki statyczne są zawarte w *statyczne* folder i obsłużony przez kod w *app.py*. Routing dla poszczególnych stron znajduje się w *routes.py*i *widoków* folder zawiera szablony stron.|
| **Projekt sieci Web Django** | Generuje projekt Django i aplikacji Django przy użyciu trzech stron, obsługę uwierzytelniania i bazy danych SQLite (ale nie modeli danych). Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, Django, krok 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Projekt sieci Web Flask** | Generuje aplikację, w których pliki statyczne są zawarte w *statyczne* folderu. Możesz pisać kod w *views.py* obsługuje routing za pomocą szablonów stron przy użyciu aparatu Jinja zawarte w *szablony* folderu. *Runserver.py* plik zawiera kod startowy. Zobacz [Dowiedz się, Flask kroku 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Projekt sieci Web Flask/Jade** | Generuje przy użyciu tej samej aplikacji jako **projektu sieci Web Flask** szablon, ale przy użyciu rozszerzenia Jade dla Jinja aparatu tworzenia szablonów. |

### <a name="polls-group"></a>Grupa sond

**Sond \<framework > Projekt sieci Web** szablony utworzyć początkową aplikację sieci web za pomocą którego użytkownicy mogą głosować na pytania dotyczące różnych sondowania. Każda aplikacja opiera się na strukturze **Web** szablony, aby zarządzać, sond i odpowiedzi użytkownika przy użyciu bazy danych projektu. Aplikacje obejmują modeli właściwych danych i aplikacji specjalne strony (/ umieszczenia), ładuje ankiety z *samples.json* pliku.

| Szablon | Opis |
| --- | --- |
| **Projekt sieci Web Bottle sond** | Generuje aplikację, która może działać względem bazy danych w pamięci, bazy danych MongoDB lub Azure Table Storage, która została skonfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej. Modele danych i kod magazynu danych, które są zawarte w *modeli* folder, a *settings.py* plik zawiera kod, aby ustalić, który magazyn danych jest używany. |
| **Projekt sieci Web Django sond** | Generuje projekt Django i aplikacja Django z trzy strony i bazy danych SQLite. Zawiera dostosowania interfejsu administracyjnego Django, aby umożliwić administratorowi tworzenie i zarządzanie nimi sond uwierzytelnionego. Aby uzyskać więcej informacji, zobacz [szablony Django](python-django-web-application-project-template.md) i [Dowiedz się, Django kroku 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Projekt sieci Web Flask sond** | Generuje aplikację, która może działać względem bazy danych w pamięci, bazy danych MongoDB lub Azure Table Storage, która została skonfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej. Modele danych i kod magazynu danych, które są zawarte w *modeli* folder, a *settings.py* plik zawiera kod, aby ustalić, który magazyn danych jest używany. Aplikacja używa aparatu Jinja dla szablonów stron. Zobacz [Dowiedz się, Flask w kroku 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Projekt sieci Web Flask/Jade sond** | Generuje przy użyciu tej samej aplikacji jako **projektu sieci Web Flask sond** szablon, ale przy użyciu rozszerzenia Jade dla Jinja aparatu tworzenia szablonów. |

## <a name="install-project-requirements"></a>Zainstaluj wymagania projektu

Podczas tworzenia projektu z szablonu określonej platformy, aby zainstalować wymagane pakiety przy użyciu narzędzia pip pojawi się okno dialogowe. Zalecamy również przy użyciu [środowiska wirtualnego](selecting-a-python-environment-for-a-project.md#use-virtual-environments) dla projektów sieci web, tak aby prawidłowymi zależnościami są uwzględniane podczas publikowania witryny sieci web:

![Okno dialogowe, które instaluje wymagane pakiety dla szablonu projektu](media/template-web-requirements-txt-wizard.png)

Jeśli używasz kontroli źródła, zwykle pominięto folderu środowisko wirtualne zgodnie z tym środowisku można odtworzyć za pomocą tylko *requirements.txt*. Najlepszym sposobem, aby wykluczyć folder jest najpierw wybierz **I zainstaluje je samodzielnie** w wierszu powyżej, następnie wyłącz automatyczne zatwierdzenie przed utworzeniem środowiska wirtualnego. Aby uzyskać więcej informacji, zobacz [Dowiedz się, samouczek Django — kroki 1 – 2 i 1 – 3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) i [Dowiedz się, samouczek Flask — kroki 1 – 2 i 1 – 3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

W przypadku wdrażania w usłudze Microsoft Azure App Service, wybierz wersję języka Python jako [rozszerzenie witryny](https://aka.ms/PythonOnAppService) i ręcznie zainstalować pakiety. Ponadto ponieważ usługi Azure App Service jest **nie** automatycznie zainstalować pakiety z *requirements.txt* podczas wdrażania w programie Visual Studio, wykonaj szczegóły konfiguracji [aka.ms/ PythonOnAppService](https://aka.ms/PythonOnAppService).

Microsoft Azure Cloud Services *jest* obsługuje *requirements.txt* pliku. Zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md) Aby uzyskać szczegółowe informacje.

## <a name="debugging"></a>Debugowanie

Po rozpoczęciu debugowania projektu sieci web programu Visual Studio uruchamia lokalny serwer internetowy na losowy port i otwiera domyślna przeglądarka, w tym adres i port. Aby określić dodatkowe opcje, kliknij prawym przyciskiem myszy projekt, wybierz **właściwości**i wybierz **uruchamiania Web** karty:

![Właściwości uruchamiającego sieci Web dla szablonu sieci web ogólnego](media/template-web-launcher-properties.png)

W **debugowania** grupy:

- **Ścieżki wyszukiwania**, **argumenty skryptu**, **argumenty Interpreter**, i **cesta k Interpretu**: te opcje są takie same jak w przypadku [normalnego debugowanie](debugging-python-in-visual-studio.md).
- **Adres URL do uruchomienia**: Określa adres URL, który jest otwierany w przeglądarce. Jego wartość domyślna to `localhost`.
- **Numer portu**: port do użycia, jeśli nie jest określona w adresie URL (Visual Studio: wybiera jeden automatycznie domyślnie). To ustawienie pozwala zastąpić wartość domyślną `SERVER_PORT` zmiennej środowiskowej, która jest używana przez Szablony do skonfigurowania portu nasłuchuje serwer debugowania lokalnego.

Właściwości w **polecenia Uruchom serwer** i **polecenia Debug serwera** grup (nie jest poniżej przedstawiono na ilustracji) określić, jak serwer sieci web jest uruchamiana. Ponieważ wiele struktur wymaga użycia skryptu poza bieżący projekt, w tym miejscu można skonfigurować skrypt i nazwa modułu uruchamiania może być przekazywany jako parametr.

- **Polecenie**: mogą być skryptami języka Python (*\*PY* pliku), nazwa modułu (na przykład `python.exe -m module_name`), lub jednego wiersza kodu (na przykład `python.exe -c "code"`). Wartość w polu listy rozwijanej wskazuje, który z tych typów jest przeznaczony.
- **Argumenty**: te argumenty są przekazywane w wierszu polecenia następujące polecenie.
- **Środowisko**: listę rozdzielonych znakami nowego wiersza \<NAME > =\<wartość > pary Określanie zmiennych środowiskowych. Te zmienne są ustawiane po wszystkich właściwości, które mogą być modyfikowane w środowisku, na przykład portu ścieżki numer i wyszukiwania, a więc może spowodować zastąpienie tych wartości.

Jakakolwiek zmienna środowisku lub właściwości projektu można określić przy użyciu składni programu MSBuild, na przykład: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` to ścieżka względna do pliku uruchamiania i `{StartupModule}` jest możliwy do zaimportowania nazwę pliku uruchamiania. `$(SERVER_HOST)` i `$(SERVER_PORT)` są zmienne środowiskowe normalne, które są ustawiane przez **adres URL do uruchomienia** i **numer portu** właściwości, automatycznie lub przez **środowiska** właściwości.

> [!Note]
> Wartości w **polecenia Uruchom serwer** są używane wraz z **debugowania** > **uruchamianie serwera** polecenia lub **Ctrl** + **F5**; wartości w **polecenia Debug serwera** grupy są używane wraz z **debugowania** > **uruchamianie serwera debugowania** polecenie lub **F5**.

### <a name="sample-bottle-configuration"></a>Przykładowa konfiguracja Bottle

**Projektu sieci Web Bottle** szablon zawiera schematyczny kod, który wykonuje niezbędną konfigurację. Aplikację bottle importowanych nie może zawierać ten kod, jednak w takim przypadku następujące ustawienia uruchamiania aplikacji przy użyciu zainstalowanych `bottle` modułu:

- **Uruchom polecenie serwera** grupy:
  - **Polecenie**: `bottle` (moduł)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Debugowanie polecenia serwera** grupy:
  - **Polecenie**: `bottle` (moduł)
  - **argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload` Opcja nie jest zalecana w przypadku korzystania z programu Visual Studio do debugowania.

### <a name="sample-pyramid-configuration"></a>Przykładowa konfiguracja ostrosłupowy

Ostrosłupowy aplikacji są obecnie najlepiej tworzone przy użyciu `pcreate` narzędzie wiersza polecenia. Po utworzeniu aplikacji można go było zaimportować przy użyciu [ **za pomocą języka Python istniejącego kodu** ](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) szablonu. Po wykonaniu tej czynności wybierz **ogólny projekt sieci Web** dostosowywaniem, aby skonfigurować opcje. Te ustawienia przyjęto założenie, że ostrosłupowy jest zainstalowany w środowisku wirtualnym przy `..\env`.

- **Debugowanie** grupy:
  - **Port serwera**: 6543 (lub niezależnie od skonfigurowanego w *.ini* plików)

- **Uruchom polecenie serwera** grupy:
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Production.ini`

- **Debugowanie polecenia serwera** grupy:
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Development.ini`

> [!Tip]
> Prawdopodobnie należy skonfigurować **katalog roboczy** właściwości projektu, ponieważ aplikacje ostrosłupowy są zazwyczaj jednego folderu poniżej katalogu głównego projektu.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia dla innej platformy, który chcesz udostępnić, lub jeśli chcesz zażądać ustawienia dla innej platformy, otwórz [problemu w usłudze GitHub](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Konwertuj projekt na usługi w chmurze Azure

**Konwertuj na projekt usługi w chmurze Microsoft Azure** polecenie (obraz poniżej) dodaje projekt usługi w chmurze do rozwiązania. Ten projekt zawiera ustawienia wdrażania i konfiguracji dla maszyn wirtualnych i usług, które ma być używany. Użyj **Publikuj** polecenia na projekt w chmurze do wdrożenia usług w chmurze; **Publikuj** polecenie projektu w języku Python nadal wdraża do witryn sieci Web. Aby uzyskać więcej informacji, zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md).

![Konwertuj na projekt usługi chmury Microsoft Azure — polecenie](media/template-web-convert-menu.png)

## <a name="see-also"></a>Zobacz także

- [Szablony elementów języka Python — dokumentacja](python-item-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)

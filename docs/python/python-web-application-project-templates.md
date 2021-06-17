---
title: Szablony aplikacji internetowych dla języka Python
description: Visual Studio szablony dla aplikacji internetowych w języku Python przy użyciu platform Bottle, Flask i Django; Obsługa obejmuje konfiguracje debugowania i publikowanie w Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6553017034dc46cfd1c035564a83dde89d77d057
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254852"
---
# <a name="python-web-application-project-templates"></a>Szablony projektów aplikacji internetowej w języku Python

Język Python w Visual Studio obsługuje tworzenie projektów internetowych w platformach Bottle, Flask i Django za pomocą szablonów projektów i uruchamiania debugowania, które można skonfigurować do obsługi różnych platform. Te szablony zawierają *plikrequirements.txt* do deklarowania niezbędnych zależności. Podczas tworzenia projektu na podstawie jednego z tych szablonów program Visual Studio monit o zainstalowanie tych pakietów (zobacz Wymagania dotyczące instalacji [projektu](#install-project-requirements) w dalszej części tego artykułu).

Można również użyć ogólnego szablonu **projektu sieci Web** dla innych platform, takich jak Ostrosłupowy. W takim przypadku z szablonem nie są instalowane żadne struktury. Zamiast tego zainstaluj niezbędne pakiety w środowisku, które jest wymagane dla projektu (zobacz okno środowiska [Python — karta Pakiet](python-environments-window-tab-reference.md#packages-tab)).

Aby uzyskać informacje na temat wdrażania aplikacji internetowej w języku Python na platformie Azure, zobacz [Publikowanie w Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Korzystanie z szablonu projektu

Projekt można utworzyć na podstawie szablonu przy użyciu funkcji **File** New Project  >    >  **(Nowy projekt pliku).** Aby wyświetlić szablony dla projektów internetowych, wybierz pozycję **Python**  >  **Web** po lewej stronie okna dialogowego. Następnie wybierz szablon, podając nazwy projektu i rozwiązania, ustaw opcje dla katalogu rozwiązania i repozytorium Git i wybierz przycisk **OK.**

![Okno dialogowe Nowego projektu dla aplikacji internetowych](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

Wspomniano  wcześniej, że ogólny szablon projektu internetowego zawiera tylko pusty projekt Visual Studio bez kodu i bez założeń innych niż projekt w języku Python. Aby uzyskać szczegółowe informacje na **temat szablonu usługi Azure Cloud Service,** zobacz Azure cloud service projects for Python (Projekty usługi w chmurze platformy Azure dla języka [Python).](python-azure-cloud-service-project-template.md)

::: moniker-end

::: moniker range=">=vs-2019"

Wspomniano  wcześniej, że ogólny szablon projektu internetowego zawiera tylko pusty projekt Visual Studio bez kodu i bez założeń innych niż projekt w języku Python.

::: moniker-end

Wszystkie pozostałe szablony są oparte na platformach internetowych Bottle, Flask lub Django i można je ująć w trzy ogólne grupy, zgodnie z opisem w poniższych sekcjach. Aplikacje utworzone za pomocą dowolnego z tych szablonów zawierają wystarczający kod, aby uruchomić i debugować aplikację lokalnie. Każdy z nich udostępnia również niezbędny obiekt aplikacji [WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) do użytku z produkcyjnymi serwerami internetowymi.

### <a name="blank-group"></a>Pusta grupa

Wszystkie **szablony \<framework> pustego projektu sieci** Web tworzą projekt z bardziej lub mniej minimalnym kodem wzorcowym i niezbędnymi zależnościami *zadeklarowane wrequirements.txt* pliku.

| Template | Opis |
| --- | --- |
| **Pusty projekt internetowy Bottle** | Generuje minimalną aplikację w *app.py* z stroną główną dla i stroną, która jest powtarzana przy użyciu bardzo `/` `/hello/<name>` `<name>` krótkiego szablonu strony wbudowanej. |
| **Pusty projekt internetowy Django** | Generuje projekt Django z podstawową strukturą witryny Django, ale bez aplikacji Django. Aby uzyskać więcej informacji, zobacz [Django templates (Szablony Django)](python-django-web-application-project-template.md) i [Learn Django Step 1 (Poznaj django , krok 1).](learn-django-in-visual-studio-step-01-project-and-solution.md) |
| **Pusty projekt internetowy Flask** | Generuje minimalną aplikację z pojedynczym "Hello world!" strona dla `/` . Ta aplikacja jest podobna do wyniku następującego szczegółowego działania opisanego w przewodniku Szybki start: tworzenie pierwszej aplikacji internetowej w języku Python przy użyciu Visual Studio w [języku Python.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) Zobacz też [learn flask step 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Grupa sieci Web

Wszystkie **\<Framework> szablony projektów internetowych** tworzą startową aplikację internetową o identycznym projekcie niezależnie od wybranej struktury. Aplikacja zawiera strony Strona główna, Informacje i Kontakt, a także pasek nav i dynamiczny projekt korzystający z narzędzia Bootstrap. Każda aplikacja jest odpowiednio skonfigurowana do obsługi plików statycznych (CSS, JavaScript i czcionek) i używa mechanizmu szablonu strony odpowiedniego dla struktury.

| Template | Opis |
| --- | --- |
| **Projekt internetowy Bottle** | Generuje aplikację, której pliki statyczne znajdują się w *folderze static* i są obsługiwane za pośrednictwem kodu w *app.py*. Routing dla poszczególnych stron jest zawarty w *routes.py*, a folder *views* zawiera szablony stron.|
| **Projekt internetowy Django** | Generuje projekt Django i aplikację Django z trzema stronami, obsługą uwierzytelniania i bazą danych SQLite (ale bez modeli danych). Aby uzyskać więcej informacji, zobacz [Django templates (Szablony Django)](python-django-web-application-project-template.md) i [Learn Django Step 4 (Poznaj django , krok 4).](learn-django-in-visual-studio-step-04-full-django-project-template.md) |
| **Projekt internetowy flask** | Generuje aplikację, której pliki statyczne znajdują się w *folderze static.* Kod w *views.py* obsługuje routing, przy użyciu szablonów stron korzystających z aparatu Jinja zawartego w *folderze templates.* Plik *runserver.py* zawiera kod startowy. Zobacz [Learn Flask Step 4 (Poznaj flask, krok 4).](learn-flask-visual-studio-step-04-full-flask-project-template.md) |
| **Projekt internetowy Flask/Jade** | Generuje tę samą aplikację co szablon **projektu internetowego Flask,** ale przy użyciu rozszerzenia Jade dla aparatu szablonów Jinja. |

::: moniker range="vs-2017"
### <a name="polls-group"></a>Grupa sondowania

Szablony **projektów internetowych \<framework> usługi Polls** tworzą startową aplikację internetową, za pomocą której użytkownicy mogą głosować na różne pytania ankiety. Każda aplikacja bazuje na  strukturze szablonów projektów internetowych, aby używać bazy danych do zarządzania sondami i odpowiedziami użytkowników. Aplikacje obejmują odpowiednie modele danych i specjalną stronę aplikacji (/inicjuje), która ładuje sondy zsamples.js *pliku.*

| Template | Opis |
| --- | --- |
| **Projekt internetowy Polls Bottle** | Generuje aplikację, która może być uruchamiana względem bazy danych w pamięci, bazy danych MongoDB lub usługi Azure Table Storage, która jest konfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej . Modele danych i kod magazynu danych znajdują się w folderze *models,* a plik *settings.py* zawiera kod w celu określenia, który magazyn danych jest używany. |
| **Projekt internetowy Django sonduje** | Generuje projekt Django i aplikację Django z trzema stronami i bazą danych SQLite. Zawiera dostosowania interfejsu administracyjnego Django umożliwiające uwierzytelnioneowi administratorowi tworzenie sond i zarządzanie nimi. Aby uzyskać więcej informacji, zobacz [Django templates (Szablony Django)](python-django-web-application-project-template.md) i [Learn Django Step 6 (Poznaj django , krok 6).](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md) |
| **Projekt internetowy flask sondowania** | Generuje aplikację, która może być uruchamiana względem bazy danych w pamięci, bazy danych MongoDB lub usługi Azure Table Storage, która jest konfigurowana przy użyciu `REPOSITORY_NAME` zmiennej środowiskowej . Modele danych i kod magazynu danych znajdują się w folderze *models,* a plik *settings.py* zawiera kod w celu określenia, który magazyn danych jest używany. Aplikacja używa aparatu Jinja do tworzenia szablonów stron. Zobacz [Learn Flask Step 5 (Poznaj flask, krok 5).](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md) |
| **Polls Flask/Jade Web Project** | Generuje tę samą aplikację co szablon projektu internetowego **polls Flask,** ale przy użyciu rozszerzenia Jade dla aparatu szablonów Jinja. |
::: moniker-end

## <a name="install-project-requirements"></a>Wymagania dotyczące instalacji projektu

Podczas tworzenia projektu na podstawie szablonu specyficznego dla struktury jest wyświetlane okno dialogowe, które pomaga zainstalować niezbędne pakiety przy użyciu narzędzia pip. Zalecamy również użycie środowiska [wirtualnego dla](selecting-a-python-environment-for-a-project.md#use-virtual-environments) projektów internetowych, aby podczas publikowania witryny internetowej uwzględniać poprawne zależności:

![Okno dialogowe instalowania wymaganych pakietów dla szablonu projektu](media/template-web-requirements-txt-wizard.png)

Jeśli używasz kontroli źródła, zwykle pomijasz folder środowiska wirtualnego, ponieważ to środowisko można odtworzyć przy użyciu tylkorequirements.txt *.* Najlepszym sposobem wykluczenia folderu jest najpierw wybranie opcji **Zainstaluję** je samodzielnie w powyższym wierszu polecenia, a następnie wyłączenie automatycznego zatwierdzania przed utworzeniem środowiska wirtualnego. Aby uzyskać szczegółowe informacje, zobacz Learn [Django Tutorial - Steps 1-2 and 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) (Samouczek dotyczący uczenia się na platformie Django — kroki 1–2 i 1–3) oraz [Learn Flask Tutorial - Steps 1-2 and 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)(Samouczek dotyczący języka Learn Flask — kroki 1–2 i 1–3).

Podczas wdrażania w Microsoft Azure App Service wybierz wersję języka [](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) Python jako rozszerzenie witryny i ręcznie zainstaluj pakiety. Ponadto ponieważ program Azure App Service  automatycznie instalować pakietów z pliku *requirements.txt* po wdrożeniu z programu Visual Studio, postępuj zgodnie ze szczegółami konfiguracji w aka.ms/PythonOnAppService [.](managing-python-on-azure-app-service.md)

::: moniker range="<=vs-2017"

Microsoft Azure Cloud Services *obsługuje* plik *requirements.txt* plików. Aby uzyskać szczegółowe informacje, zobacz [Projekty usług w chmurze](python-azure-cloud-service-project-template.md) platformy Azure.

::: moniker-end

## <a name="debugging"></a>Debugowanie

Gdy projekt internetowy jest uruchamiany na potrzeby debugowania, program Visual Studio lokalny serwer internetowy na losowym porcie i otwiera w domyślnej przeglądarce ten adres i port. Aby określić dodatkowe opcje, kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Właściwości** i wybierz **kartę Web Launcher:**

![Właściwości uruchamiania sieci Web dla ogólnego szablonu internetowego](media/template-web-launcher-properties.png)

W grupie **Debugowanie:**

- **Ścieżki wyszukiwania,** **argumenty skryptu,** **argumenty interpretera** i ścieżka **interpretera:** te opcje są takie same jak w przypadku [normalnego debugowania](debugging-python-in-visual-studio.md).
- **Adres URL uruchamiania:** określa adres URL otwarty w przeglądarce. Wartość domyślna to `localhost` .
- **Numer portu:** port do użycia, jeśli w adresie URL nie zostanie określony żaden Visual Studio domyślnie wybierany automatycznie. To ustawienie umożliwia zastąpienie domyślnej wartości zmiennej środowiskowej, która jest używana przez szablony do konfigurowania portu, na którym nasłuchuje lokalny `SERVER_PORT` serwer debugowania.

Właściwości w grupach **Polecenia** serwera uruchamiania i Polecenia debugowania serwera (te drugie znajdują się poniżej tego, co pokazano na obrazie) określają sposób uruchamiania serwera internetowego.  Ze względu na to, że wiele platform wymaga użycia skryptu poza bieżącym projektem, w tym miejscu można skonfigurować skrypt, a nazwa modułu startowego może zostać przekazana jako parametr.

- **Polecenie**: może być skryptem języka Python *\* (plik PY),* nazwą modułu (na przykład w pliku ) lub pojedynczym wierszem `python.exe -m module_name` kodu (jak w systemie `python.exe -c "code"` ). Wartość na liście rozwijanej wskazuje, który z tych typów jest przeznaczony.
- **Argumenty**: te argumenty są przekazywane w wierszu polecenia po poleceniu .
- **Środowisko:** lista par rozdzielonych nowymi linią \<NAME> = \<VALUE> określająca zmienne środowiskowe. Te zmienne są ustawiane po wszystkich właściwościach, które mogą modyfikować środowisko, takich jak numer portu i ścieżki wyszukiwania, a więc mogą zastąpić te wartości.

Dowolną właściwość projektu lub zmienną środowiskową można określić za pomocą składni programu MSBuild, na przykład: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` jest ścieżką względną do pliku startowego i `{StartupModule}` jest importowalna nazwa pliku startowego. `$(SERVER_HOST)` i `$(SERVER_PORT)` są normalnymi zmiennymi środowisk, które są ustawiane przez właściwości **Adres URL** uruchamiania i **Numer** portu, automatycznie lub przez **właściwość** Environment.

> [!Note]
> Wartości w **Uruchom serwer polecenia** są używane z debugowania serwera startowego polecenia lub   >   **Ctrl** F5; wartości w grupie poleceń serwera debugowania są używane z +  **debugowania** start   >  **debugowania serwera** polecenia lub **F5**.

### <a name="sample-bottle-configuration"></a>Konfiguracja przykładowej aplikacji Bottle

Szablon **Bottle Web Project zawiera** kod, który zawiera kod, który robi niezbędną konfigurację. Zaimportowana aplikacja Bottle może nie zawierać tego kodu, jednak w takim przypadku następujące ustawienia uruchamiają aplikację przy użyciu zainstalowanego `bottle` modułu:

- **Uruchom grupę poleceń** serwera:
  - **Polecenie**: `bottle` (moduł)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Grupa poleceń serwera debugowania:**
  - **Polecenie**: `bottle` (moduł)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Ta `--reload` opcja nie jest zalecana w przypadku używania Visual Studio debugowania.

### <a name="sample-pyramid-configuration"></a>Przykładowa konfiguracja ostrosłupa

Aplikacje Ostrosłupowe najlepiej obecnie tworzyć przy użyciu `pcreate` narzędzia wiersza polecenia. Po utworzeniu aplikacji można ją zaimportować przy użyciu szablonu kodu [**Z istniejącego języka Python.**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) Następnie wybierz dostosowanie Ogólny **projekt internetowy,** aby skonfigurować opcje. Te ustawienia zakładają, że ostrosłupowy serwer jest zainstalowany w środowisku wirtualnym w programie `..\env` .

- **Grupa debugowania:**
  - **Port serwera:** 6543 (lub cokolwiek jest skonfigurowane w *.ini* plików)

- **Uruchom grupę poleceń** serwera:
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Production.ini`

- **Grupa poleceń serwera debugowania:**
  - Polecenie: `..\env\scripts\pserve-script.py` (skrypt)
  - Argumenty: `Development.ini`

> [!Tip]
> Prawdopodobnie musisz skonfigurować właściwość **Katalog roboczy** projektu, ponieważ aplikacje Ostrosłupowe zazwyczaj znajdują się w folderze poniżej katalogu głównego projektu.

### <a name="other-configurations"></a>Inne konfiguracje

Jeśli masz ustawienia dla innej struktury, które chcesz udostępnić, lub jeśli chcesz zażądać ustawień dla innej struktury, otwórz [problem w usłudze GitHub.](https://github.com/Microsoft/PTVS/issues)

::: moniker range="<=vs-2017"

## <a name="convert-a-project-to-azure-cloud-service"></a>Konwertowanie projektu na usługę Azure Cloud Service

Polecenie **Konwertuj na Microsoft Azure projektu usługi w chmurze** (obraz poniżej) dodaje projekt usługi w chmurze do rozwiązania. Ten projekt zawiera ustawienia wdrażania i konfigurację maszyn wirtualnych i usług, które mają być używane. Użyj polecenia **Publish (Publikuj)** w projekcie w chmurze, aby wdrożyć program Cloud Services; Polecenie **Publish** (Publikuj) w projekcie języka Python nadal jest wdrażane w witrynach internetowych. Aby uzyskać więcej informacji, zobacz [Projekty usługi w chmurze platformy Azure.](python-azure-cloud-service-project-template.md)

![Polecenie Konwertuj na Microsoft Azure projektu usługi w chmurze](media/template-web-convert-menu.png)

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Informacje o szablonach elementów języka Python](python-item-templates.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
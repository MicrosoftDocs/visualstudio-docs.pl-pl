---
title: Szablon projektu usługi w chmurze platformy Azure dla języka Python
description: Visual Studio udostępnia szablony dla usług w chmurze platformy Azure napisanych w języku Python, w tym wdrażania ról, zależności i rozwiązywania problemów.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 4d205ee2bbc0a6e9c44c34f3b0487abb4f22283e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72983663"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty usług w chmurze platformy Azure dla języka Python

Program Visual Studio udostępnia szablony ułatwiające rozpoczęcie tworzenia usług Azure Cloud Services przy użyciu języka Python.

[Usługa w chmurze](/azure/cloud-services/) składa się z dowolnej liczby *ról procesu roboczego* i *ról sieci web,* z których każda wykonuje koncepcyjnie oddzielne zadanie, ale może być replikowana oddzielnie na maszynach wirtualnych, zgodnie z potrzebami do skalowania. Role sieci Web zapewniają hosting dla aplikacji sieci web front-end. Jeśli chodzi o język Python, do napisania takiej aplikacji (obsługiwanej przez szablon [projektu sieci Web)](python-web-application-project-templates.md)można użyć dowolnej struktury sieci Web obsługującej usługę WSGI. Role procesu roboczego są przeznaczone dla długotrwałych procesów, które nie wchodzą w bezpośrednią interakcję z użytkownikami. Zazwyczaj korzystają z pakietów w pakiecie "azure", który [`pip install azure`](https://pypi.org/project/azure)jest instalowany z .

Ten artykuł zawiera szczegółowe informacje na temat szablonu projektu i innej pomocy technicznej w programie Visual Studio 2017 i nowszych (wcześniejsze wersje są podobne, ale z pewnymi różnicami). Aby uzyskać więcej informacji na temat pracy z platformą Azure z języka Python, odwiedź [Centrum deweloperów języka Azure Python](/azure/python/).

## <a name="create-a-project"></a>Tworzenie projektu

1. Zainstaluj [zestaw SDK platformy Azure .NET dla programu Visual Studio,](https://visualstudio.microsoft.com/vs/azure-tools/)który jest wymagany do korzystania z szablonu usługi w chmurze.
1. W programie Visual Studio wybierz **pozycję Plik** > **nowego** > **projektu**, a następnie wyszukaj hasło "Azure Python" i wybierz z listy usługę Azure **Cloud Service:**

    ![Szablon projektu chmury azure dla języka Python](media/template-azure-cloud-project.png)

1. Wybierz jedną lub więcej ról do uwzględnienia. Projekty w chmurze mogą łączyć role napisane w różnych językach, dzięki czemu można łatwo napisać każdą część aplikacji w najbardziej odpowiednim języku. Aby dodać nowe role do projektu po zakończeniu tego okna dialogowego, kliknij prawym przyciskiem myszy **pozycję Role** w **Eksploratorze rozwiązań** i wybierz jeden z elementów w obszarze **Dodaj**.

    ![Dodawanie ról w szablonie projektu usługi Azure Cloud Project](media/template-azure-cloud-service-project-wizard.png)

1. Podczas tworzenia poszczególnych projektów ról może zostać wyświetlony monit o zainstalowanie dodatkowych pakietów języka Python, takich jak struktury Django, Bottle lub Flask, jeśli wybrano rolę, która używa jednej z nich.

1. Po dodaniu nowej roli do projektu pojawią się instrukcje konfiguracji. Zmiany konfiguracji są zwykle niepotrzebne, ale mogą być przydatne do przyszłego dostosowywania projektów. Należy zauważyć, że podczas dodawania wielu ról w tym samym czasie, tylko instrukcje dla ostatniej roli pozostają otwarte. Można jednak znaleźć instrukcje i wskazówki dotyczące rozwiązywania problemów dla innych ról w odpowiednich plikach *readme.mht,* znajdujących się w katalogu głównym roli lub w folderze *bin.*

1. Folder *pojemnika* projektu zawiera również jeden lub dwa skrypty programu PowerShell, które są używane do konfigurowania zdalnej maszyny wirtualnej, w tym instalowanie języka Python, dowolny plik [*requirements.txt*](#dependencies) w projekcie i konfigurowanie usług IIS w razie potrzeby. Można edytować te pliki zgodnie z potrzebami wdrożenia, choć większość typowych opcji można zarządzać w inny sposób (zobacz [Konfigurowanie wdrożenia roli](#configure-role-deployment) poniżej). Nie sugerujemy usunięcia tych plików, ponieważ zamiast tego używany jest starszy skrypt konfiguracyjny, jeśli pliki nie są dostępne.

    ![Pliki obsługi ról procesu roboczego](media/template-azure-cloud-service-worker-role-support-files.png)

    Aby dodać te skrypty konfiguracji do nowego projektu, kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Dodaj** > **nowy element**i wybierz opcję Pliki obsługi ról sieci **Web** lub Pliki obsługi ról procesu **roboczego**.

## <a name="configure-role-deployment"></a>Konfigurowanie wdrażania ról

Skrypty programu PowerShell w folderze *bin* projektu roli kontrolują wdrażanie tej roli i mogą być edytowane w celu dostosowania konfiguracji:

- *ConfigureCloudService.ps1* jest używany do ról sieci web i procesu roboczego, zazwyczaj do instalowania i konfigurowania zależności i ustawiania wersji języka Python.
- *LaunchWorker.ps1* jest używany tylko dla ról procesu roboczego i służy do zmiany zachowania uruchamiania, dodawania argumentów wiersza polecenia lub dodawania zmiennych środowiskowych.

Oba pliki zawierają instrukcje dostosowywania. Można również zainstalować własną wersję języka Python, dodając kolejne zadanie do pliku *ServiceDefinition.csdef* projektu usługi głównej chmury, ustawiając zmienną na `PYTHON` zainstalowaną ścieżkę *python.exe* (lub równoważną). Gdy `PYTHON` jest ustawiona, Python nie jest zainstalowany z NuGet.

Dodatkową konfigurację można wykonać w następujący sposób:

1. Zainstaluj pakiety, aktualizując `pip` plik *requirements.txt* w katalogu głównym projektu. Skrypt *ConfigureCloudService.ps1* instaluje ten plik podczas wdrażania.
1. Ustaw zmienne środowiskowe, modyfikując plik *web.config* (role sieci web) lub sekcję `Runtime` pliku *ServiceDefinition.csdef* (role procesu roboczego).
1. Określ skrypt i argumenty, które mają być używane dla `Runtime/EntryPoint` roli procesu roboczego, modyfikując wiersz polecenia w sekcji pliku *ServiceDefinitions.csdef.*
1. Ustaw główny skrypt obsługi dla roli sieci web za pośrednictwem pliku *web.config.*

## <a name="test-role-deployment"></a>Wdrażanie roli testowej

Podczas pisania ról można przetestować projekt chmury lokalnie przy użyciu emulatora usługi w chmurze. Emulator jest dołączony do narzędzi zestawu Azure SDK i jest ograniczoną wersją środowiska używanego podczas publikowania usługi w chmurze na platformie Azure.

Aby uruchomić emulator, najpierw upewnij się, że projekt w chmurze jest projektem startowym w rozwiązaniu, klikając prawym przyciskiem myszy i wybierając **polecenie Ustaw jako projekt startowy.** Następnie wybierz **debugowanie** > **start debugowania** **(F5**) lub **debugowanie** > **start bez debugowania** (**Ctrl**+**F5**).

Należy zauważyć, że ze względu na ograniczenia w emulatorze nie jest możliwe debugowanie kodu języka Python. W związku z tym zaleca się debugowanie ról, uruchamiając je niezależnie, a następnie użyć emulatora do testowania integracji przed opublikowaniem.

## <a name="deploy-a-role"></a>Wdrażanie roli

Aby otworzyć **Kreatora publikowania,** wybierz projekt roli w **Eksploratorze rozwiązań** i wybierz polecenie **Buduj** > **publikuj** z menu głównego lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

Proces publikowania obejmuje dwie fazy. Najpierw visual studio tworzy pojedynczy pakiet zawierający wszystkie role dla usługi w chmurze. Ten pakiet jest tym, co jest wdrażane na platformie Azure, która inicjuje jedną lub więcej maszyn wirtualnych dla każdej roli i wdraża źródło.

Podczas aktywacji każdej maszyny wirtualnej wykonuje skrypt *ConfigureCloudService.ps1* i instaluje wszystkie zależności. Ten skrypt domyślnie instaluje najnowszą wersję języka Python z [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) i wszystkie pakiety określone w pliku *requirements.txt.*

Na koniec role procesu roboczego wykonują *launchworker.ps1*, który rozpoczyna uruchamianie skryptu Pythona; role sieci web inicjują usługi IIS i rozpoczynają obsługę żądań sieci Web.

## <a name="dependencies"></a>Zależności

W przypadku usług w chmurze skrypt *ConfigureCloudService.ps1* służy `pip` do instalowania zestawu zależności języka Python. Zależności powinny być określone w pliku o nazwie *requirements.txt* (można dostosowywać, modyfikując *ConfigureCloudService.ps1*). Plik jest wykonywany `pip install -r requirements.txt` w ramach inicjowania.

Należy zauważyć, że wystąpienia usługi w chmurze nie zawierają kompilatorów Języka C, więc wszystkie biblioteki z rozszerzeniami C muszą zawierać wstępnie skompilowane pliki binarne.

pip i jego zależności, a także pakiety w *requirements.txt*, są pobierane automatycznie i mogą być liczone jako wymagalne wykorzystanie przepustowości. Aby uzyskać szczegółowe informacje na temat zarządzania plikami *requirements.txt,* zobacz [Zarządzanie wymaganymi pakietami.](managing-required-packages-with-requirements-txt.md)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli rola sieci web lub pracownika nie działa poprawnie po wdrożeniu, sprawdź następujące kwestie:

- Projekt języka Python zawiera folder *bin\\ * z (co najmniej):

  - *Konfigurowanie usługiCloudService.ps1*
  - *LaunchWorker.ps1* (dla ról procesu roboczego)
  - *ps.cmd*

- Projekt języka Python zawiera plik *requirements.txt* zawierający listę wszystkich zależności (lub na przemian kolekcję plików kół).
- Włącz pulpit zdalny w usłudze w chmurze i zbadaj pliki dziennika.
- Dzienniki *configureCloudService.ps1* i *LaunchWorker.ps1* są przechowywane w *języku\%C:\Resources\Directory RoleId. Folder DiagnosticStore\LogFiles* na komputerze zdalnym.
- Role sieci Web mogą zapisywać dodatkowe dzienniki do ścieżki skonfigurowanej `WSGI_LOG` w *web.config*, a mianowicie ścieżkę w appSetting. Większość regularnych iis lub fastcgi rejestrowania również działa.
- Obecnie plik *LaunchWorker.ps1.log* jest jedynym sposobem wyświetlania danych wyjściowych lub błędów wyświetlanych przez rolę pracownika języka Python.

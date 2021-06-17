---
title: Szablon projektu usługi w chmurze platformy Azure dla języka Python
description: Visual Studio udostępnia szablony dla usług w chmurze platformy Azure napisanych w języku Python, w tym wdrażanie ról, zależności i rozwiązywanie problemów.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 2de0f255da54d5bd8abf865f6534041d88bbbca3
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254839"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty usług w chmurze platformy Azure dla języka Python

Visual Studio szablony, które ułatwiają rozpoczynanie tworzenia aplikacji Azure Cloud Services języka Python.

Usługa [w chmurze](/azure/cloud-services/) składa  się z dowolnej liczby ról procesu roboczego i ról sieci *Web,* z których każda wykonuje koncepcyjnie oddzielne zadanie, ale może być oddzielnie replikowana między maszynami wirtualnymi w razie potrzeby skalowania. Role sieci Web zapewniają hosting dla aplikacji internetowych frontony. Jeśli chodzi o język Python, do napisania takiej aplikacji (obsługiwanej przez szablon projektu internetowego) można użyć dowolnej struktury [internetowej](python-web-application-project-templates.md)obsługującej usługę WSGI. Role procesu roboczego są przeznaczone dla długotrwałych procesów, które nie wchodzą w bezpośrednią interakcję z użytkownikami. Zazwyczaj używają pakietów w ramach pakietu "azure", który jest instalowany z pakietem [`pip install azure`](https://pypi.org/project/azure) .

Ten artykuł zawiera szczegółowe informacje o szablonie projektu i innej pomocy technicznej w wersji Visual Studio 2017 i nowszych (wcześniejsze wersje są podobne, ale z pewnymi różnicami). Aby uzyskać więcej informacji na temat pracy z platformą Azure z języka Python, odwiedź Centrum [deweloperów języka Python platformy Azure.](/azure/python/)

## <a name="create-a-project"></a>Tworzenie projektu

1. Zainstaluj zestaw [Azure .NET SDK dla Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), który jest wymagany do korzystania z szablonu usługi w chmurze.
1. W Visual Studio wybierz pozycję **File** New Project (Nowy projekt pliku), a następnie wyszukaj pozycję  >    >  "Azure Python" i wybierz pozycję Azure **Cloud Service** z listy:

    ![Szablon projektu w chmurze platformy Azure dla języka Python](media/template-azure-cloud-project.png)

1. Wybierz co najmniej jedną rolę do do dołączyć. Projekty w chmurze mogą łączyć role napisane w różnych językach, dzięki czemu można łatwo pisać poszczególne części aplikacji w najbardziej odpowiednim języku. Aby dodać nowe role do projektu po ukończeniu  tego okna dialogowego, kliknij prawym przyciskiem myszy pozycję **Role** w Eksplorator rozwiązań i wybierz jeden z elementów w obszarze **Dodaj**.

    ![Dodawanie ról w szablonie projektu w chmurze platformy Azure](media/template-azure-cloud-service-project-wizard.png)

1. Podczas tworzenia poszczególnych projektów ról może zostać wyświetlony monit o zainstalowanie dodatkowych pakietów języka Python, takich jak struktury Django, Bottle lub Flask, jeśli wybrano rolę, która używa jednego z tych pakietów.

1. Po dodaniu nowej roli do projektu zostaną wyświetlone instrukcje konfiguracji. Zmiany konfiguracji są zwykle niepotrzebne, ale mogą być przydatne do przyszłego dostosowywania projektów. Pamiętaj, że podczas dodawania wielu ról w tym samym czasie otwarte są tylko instrukcje dotyczące ostatniej roli. Można jednak znaleźć instrukcje i wskazówki dotyczące rozwiązywania problemów dla innych ról w odpowiednich plikach *readme.mht* znajdujących się w katalogu głównym roli lub w *folderze bin.*

1. Folder bin  projektu zawiera również jeden lub dwa skrypty programu PowerShell, które są używane do konfigurowania zdalnej maszyny wirtualnej, w tym instalowania języka Python, dowolnego plikurequirements.txtw projekcie i konfigurowania usług IIS w [*razie*](#dependencies) potrzeby. Możesz edytować te pliki zgodnie z potrzebami wdrożenia, chociaż najbardziej typowe opcje można zarządzać w inny sposób (zobacz [Konfigurowanie wdrożenia roli](#configure-role-deployment) poniżej). Nie zalecamy usuwania tych plików, ponieważ zamiast tego jest używany starszy skrypt konfiguracji, jeśli pliki nie są dostępne.

    ![Pliki obsługi roli procesu roboczego](media/template-azure-cloud-service-worker-role-support-files.png)

    Aby dodać te skrypty konfiguracji do nowego projektu, kliknij projekt prawym przyciskiem myszy, wybierz polecenie Dodaj nowy element i wybierz pozycję Pliki obsługi roli sieci Web lub Pliki obsługi roli  >   **procesu roboczego.** 

## <a name="configure-role-deployment"></a>Konfigurowanie wdrożenia roli

Skrypty programu PowerShell w folderze *bin* projektu roli kontrolują wdrożenie tej roli i mogą być edytowane w celu dostosowania konfiguracji:

- *ConfigureCloudService.ps1* jest używana dla ról Sieć Web i Proces roboczy, zazwyczaj do instalowania i konfigurowania zależności oraz do konfigurowania wersji języka Python.
- *LaunchWorker.ps1* jest używana tylko dla ról procesu roboczego i służy do zmiany zachowania podczas uruchamiania, dodawania argumentów wiersza polecenia lub dodawania zmiennych środowiskowych.

Oba pliki zawierają instrukcje dostosowywania. Możesz również zainstalować własną wersję języka Python, dodając kolejne zadanie do pliku *ServiceDefinition.csdef* głównego projektu usługi w chmurze, ustawiając dla zmiennej zainstalowaną ścieżkępython.exe`PYTHON` (lub równoważną).  Gdy `PYTHON` ustawienie jest ustawione, język Python nie jest instalowany z pakietu NuGet.

Dodatkową konfigurację można wykonać w następujący sposób:

1. Instaluj pakiety przy `pip` *użyciurequirements.txt* pliku w katalogu głównym projektu. Skrypt *ConfigureCloudService.ps1* instaluje ten plik podczas wdrażania.
1. Ustaw zmienne środowiskowe, modyfikując *plikweb.config* (role sieci Web) lub sekcję pliku `Runtime` *ServiceDefinition.csdef* (role procesu roboczego).
1. Określ skrypt i argumenty do użycia dla roli procesu roboczego, modyfikując wiersz polecenia w sekcji pliku `Runtime/EntryPoint` *ServiceDefinitions.csdef.*
1. Ustaw główny skrypt obsługi dla roli sieci Web za pomocą *web.config* pliku.

## <a name="test-role-deployment"></a>Testowanie wdrożenia roli

Podczas pisania ról możesz przetestować projekt w chmurze lokalnie przy użyciu emulatora usługi w chmurze. Emulator jest dołączony do usługi Azure SDK Tools i jest ograniczoną wersją środowiska używanego podczas opublikowania usługi w chmurze na platformie Azure.

Aby uruchomić emulator, najpierw upewnij się, że projekt w chmurze jest projektem startowym w rozwiązaniu, klikając prawym przyciskiem myszy i wybierając polecenie **Ustaw jako projekt startowy.** Następnie wybierz pozycję  >  **Debuguj rozpocznij debugowanie** **(F5)** lub **Rozpocznij**  >  **debugowanie bez debugowania** **(Ctrl** + **F5).**

Należy pamiętać, że z powodu ograniczeń emulatora nie można debugować kodu w języku Python. W związku z tym zalecamy debugowanie ról przez ich niezależne uruchamianie, a następnie używanie emulatora do testowania integracji przed opublikowaniem.

## <a name="deploy-a-role"></a>Wdrażanie roli

Aby otworzyć kreatora **publikowania,** wybierz projekt roli w programie **Eksplorator rozwiązań** wybierz polecenie Build Publish (Kompilacja opublikuj) z menu głównego lub kliknij projekt prawym przyciskiem myszy i wybierz  >   polecenie **Publish (Publikuj).**

Proces publikowania obejmuje dwie fazy. Najpierw Visual Studio jeden pakiet zawierający wszystkie role dla usługi w chmurze. Ten pakiet jest wdrażany na platformie Azure, który inicjuje co najmniej jedną maszynę wirtualną dla każdej roli i wdraża źródło.

W momencie aktywowania każdej maszyny wirtualnej wykonuje skrypt *ConfigureCloudService.ps1* i instaluje wszelkie zależności. Ten skrypt domyślnie instaluje najnowszą wersję języka Python z pakietu [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) i wszystkie pakiety określone w *requirements.txt* pliku.

Na koniec role procesu roboczego *wykonująLaunchWorker.ps1*, co uruchamia skrypt języka Python; role sieci Web inicjują usługi IIS i rozpoczynają obsługę żądań internetowych.

## <a name="dependencies"></a>Zależności

Na Cloud Services skrypt *ConfigureCloudService.ps1* używa polecenia do `pip` zainstalowania zestawu zależności języka Python. Zależności należy określić w pliku o nazwie *requirements.txt* (dostosowywalny przez zmodyfikowanie *ConfigureCloudService.ps1*). Plik jest wykonywany za pomocą `pip install -r requirements.txt` pliku w ramach inicjowania.

Należy pamiętać, że wystąpienia usługi w chmurze nie zawierają kompilatorów języka C, dlatego wszystkie biblioteki z rozszerzeniami języka C muszą dostarczać wstępnie skompilowane pliki binarne.

Program pip i jego zależności, a także pakiety w programie *requirements.txt*, są pobierane automatycznie i mogą być liczone jako obciążenie użycia przepustowości. Zobacz [Zarządzanie wymaganymi pakietami,](managing-required-packages-with-requirements-txt.md) aby uzyskać szczegółowe informacje na *temat zarządzaniarequirements.txt* plików.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli twoja rola Sieć Web lub Proces roboczy nie działa prawidłowo po wdrożeniu, sprawdź następujące kwestie:

- Projekt języka Python zawiera folder *bin \\* z (co najmniej):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (dla ról procesu roboczego)
  - *ps.cmd*

- Projekt języka Python zawiera *requirements.txt* listę wszystkich zależności (lub alternatywnie kolekcję plików wheel).
- Włącz Pulpit zdalny w usłudze w chmurze i zbadaj pliki dziennika.
- Dzienniki dla *ConfigureCloudService.ps1* *iLaunchWorker.ps1* są przechowywane w *folderze C:\Resources\Directory \% RoleId%. Folder DiagnosticStore\LogFiles* na komputerze zdalnym.
- Role sieci Web mogą zapisywać dodatkowe dzienniki w ścieżce skonfigurowanejweb.config *,* czyli ścieżce w `WSGI_LOG` pliku appSetting. Działa również większość zwykłego rejestrowania usług IIS lub FastCGI.
- Obecnie plik *LaunchWorker.ps1.log* jest jedynym sposobem wyświetlania danych wyjściowych lub błędów wyświetlanych przez rolę procesu roboczego języka Python.

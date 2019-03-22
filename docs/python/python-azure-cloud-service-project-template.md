---
title: Szablon projektu usługi w chmurze platformy Azure dla języka Python
description: Program Visual Studio udostępnia szablony dla usług Azure cloud services, napisany w języku Python, w tym wdrażanie ról w zależności i rozwiązywania problemów.
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 77da3ee8af0b14171e8cc525c2e6d95c6a38a205
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355714"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty usługi w chmurze platformy Azure dla języka Python

Program Visual Studio zawiera szablony ułatwiające wprowadzenie do tworzenia usług Azure Cloud Services przy użyciu języka Python.

A [usługi w chmurze](https://docs.microsoft.com/azure/cloud-services/) składa się z dowolną liczbą *ról procesów roboczych* i *role sieci web*, z których każdy wykonuje koncepcyjnie osobne zadania, ale można osobno być replikowane między maszyny wirtualne w razie potrzeby skalowania. Role sieć Web udostępniają hosting dla aplikacji frontonu sieci web. W przypadku danego języka Python, wszystkie struktury sieci web, który obsługuje WSGI może być użyty do zapisu takiej aplikacji (obsługiwana przez [szablon projektów internetowych](python-web-application-project-templates.md)). Role procesów roboczych są przeznaczone dla długotrwałe procesy, które nie bezpośrednią interakcję z użytkownikami. Zazwyczaj należy używać pakietów w pakiecie "azure", który został zainstalowany przy użyciu [ `pip install azure` ](https://pypi.org/project/azure).

Ten artykuł zawiera szczegółowe informacje o szablonu projektu oraz innych pomocy technicznej w programie Visual Studio 2017 i nowsze (wcześniejszych wersji są podobne, ale w edytorze). Aby uzyskać więcej informacji dotyczących pracy z platformą Azure za pomocą języka Python, odwiedź stronę [Centrum deweloperów języka Python Azure](https://docs.microsoft.com/python/azure/?view=azure-python/?view=azure-python).

## <a name="create-a-project"></a>Tworzenie projektu

1. Zainstaluj [Azure .NET SDK dla programu Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), co jest wymagane do przy użyciu szablonu usługi w chmurze.
1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**, a następnie wyszukaj "Python platformy Azure" i wybierz **w chmurze platformy Azure Usługa** z listy:

    ![Szablonu projektu w chmurze platformy Azure dla języka Python](media/template-azure-cloud-project.png)

1. Wybierz co najmniej jedną rolę, aby uwzględnić. Projekty w chmurze mogą łączyć role napisane w różnych językach, dzięki czemu można łatwo napisać poszczególnych części aplikacji w najbardziej odpowiedni język. Aby dodać nowe role do projektu po zakończeniu to okno dialogowe, kliknij prawym przyciskiem myszy **role** w **Eksploratora rozwiązań** i wybierz jeden z elementów w obszarze **Dodaj**.

    ![Dodawanie ról w szablonie projektu w chmurze platformy Azure](media/template-azure-cloud-service-project-wizard.png)

1. Podczas tworzenia projektów poszczególnych ról monit może zainstalować dodatkowe pakiety Python, takie jak struktury Django, Bottle lub Flask w przypadku wybrania roli, która korzysta z jednego z nich.

1. Po dodaniu nowej roli do projektu, są wyświetlane instrukcje konfiguracji. Zmiany konfiguracji są zazwyczaj zbędna, ale mogą być przydatne do dostosowywania przyszłych projektów. Należy pamiętać, że podczas dodawania wielu ról w tym samym czasie, pozostają otwarte, tylko instrukcje dotyczące ostatniej roli. Jednakże, można znaleźć instrukcje i wskazówki dotyczące rozwiązywania problemów dla innych ról na odpowiednich *readme.mht* plików znajdujących się w domenie głównej roli lub w *bin* folderu.

1. Projekt *bin* folder zawiera także jednego lub dwóch skryptów programu PowerShell, które są używane do konfigurowania zdalnego maszyny wirtualnej, łącznie z zainstalowaniem języka Python, wszelkie [ *requirements.txt* ](#dependencies) plik w projekcie i konfigurowania usług IIS, jeśli to konieczne. Możesz edytować te pliki do wdrożenia, jednak najbardziej typowe opcje mogą być zarządzane w inny sposób (zobacz [skonfigurować wdrażanie ról w usługach](#configure-role-deployment) poniżej). Nie zaleca się usunięcie tych plików skryptu konfiguracyjnego starszej wersji jest używany zamiast tego, jeśli pliki nie są dostępne.

    ![Pliki obsługi roli procesu roboczego](media/template-azure-cloud-service-worker-role-support-files.png)

    Aby dodać te skrypty konfiguracji do nowego projektu, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj** > **nowy element**i wybierz opcję **pliki obsługi roli sieci Web** lub **Pliki obsługi roli procesu roboczego**.

## <a name="configure-role-deployment"></a>Konfigurowanie wdrożenia roli

Skrypty programu PowerShell w projekcie roli *bin* folderu kontrolować wdrażanie tej roli i może być edytowana, aby dostosować konfigurację:

- *ConfigureCloudService.ps1* służy do ról sieć web i proces roboczy, zazwyczaj można zainstalować i skonfigurować zależności i ustaw wersję języka Python.
- *Skryptu LaunchWorker.ps1* jest używany tylko w przypadku ról procesów roboczych i jest używany, aby zmienić zachowanie podczas uruchamiania, Dodaj argumenty wiersza polecenia lub dodać zmienne środowiskowe.

Oba te pliki zawierają instrukcje dotyczące dostosowywania. Można także zainstalować własną wersję języka Python, dodając inne zadanie do głównego projektu usługi w chmurze firmy *ServiceDefinition.csdef* pliku, ustawianie `PYTHON` zmienną i jej zainstalowanych *python.exe*(lub równoważnego) ścieżki. Gdy `PYTHON` jest ustawiona, język Python nie jest instalowany z pakietów NuGet.

Dodatkowa konfiguracja może się odbywać w następujący sposób:

1. Instalowanie pakietów przy użyciu `pip` , aktualizując *requirements.txt* pliku w katalogu głównym projektu. *ConfigureCloudService.ps1* skrypt instaluje ten plik na wdrożenie.
1. Ustawianie zmiennych środowiskowych, modyfikując swoje *web.config* pliku (role sieci web) lub `Runtime` części Twojej *ServiceDefinition.csdef* pliku (role proces roboczy).
1. Określ skrypt i argumenty do użycia dla roli procesu roboczego, modyfikując wiersza polecenia w pliku `Runtime/EntryPoint` części Twojej *ServiceDefinitions.csdef* pliku.
1. Ustaw skrypt głównego programu obsługi dla roli sieci web, za pośrednictwem *web.config* pliku.

## <a name="test-role-deployment"></a>Testowanie wdrażania roli

Podczas zapisywania roli, należy przetestować projekt w chmurze lokalnie przy użyciu emulatora usługi chmury. Emulator jest dołączony do platformy Azure SDK Tools i jest ograniczona wersja środowiska używane po opublikowaniu usługi w chmurze na platformie Azure.

Aby uruchomić emulator, najpierw upewnij się, projekt w chmurze jest projektem startowym w rozwiązaniu, kliknij prawym przyciskiem myszy i wybierając **Ustaw jako projekt startowy**. Następnie wybierz pozycję **debugowania** > **Rozpocznij debugowanie** (**F5**) lub **debugowania** > **uruchomić bez Debugowanie** (**Ctrl**+**F5**).

Należy pamiętać, że ze względu na ograniczenia w emulatorze nie jest możliwe debugowanie kodu w języku Python. Dlatego zalecamy debugować role, uruchamiając je niezależnie, a następnie użyć emulatora usługi integracji, testowania, przed opublikowaniem.

## <a name="deploy-a-role"></a>Wdrażania roli

Aby otworzyć **Publikuj** kreatora, wybierz rolę, projekt w **Eksploratora rozwiązań** i wybierz **kompilacji** > **Publikuj** z menu głównego, lub kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Publikuj**.

Proces publikowania obejmuje dwa etapy. Po pierwsze Visual Studio tworzy pojedynczy pakiet zawierający wszystkie role dla usługi w chmurze. Ten pakiet jest o tym, co jest wdrożona na platformie Azure, inicjuje co najmniej jednej maszyny wirtualnej dla każdej roli, która wdraża źródła.

Ponieważ każda maszyna wirtualna aktywuje, wykonuje *ConfigureCloudService.ps1* skryptu i instaluje wszystkie zależności. Ten skrypt domyślnie instaluje najnowszą wersję języka Python z [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) i wszelkich pakietów, które określono w *requirements.txt* pliku.

Na koniec ról procesów roboczych wykonania *skryptu LaunchWorker.ps1*, co spowoduje włączenie uruchamiania skryptu w języku Python; web zainicjować role usług IIS i rozpocząć obsługę żądań sieci web.

## <a name="dependencies"></a>Zależności

Dla usług Cloud Services *ConfigureCloudService.ps1* skrypt `pip` zainstalować zestaw zależności języka Python. Zależności powinny być określone w pliku o nazwie *requirements.txt* (można dostosować, modyfikując *ConfigureCloudService.ps1*). Plik jest wykonywane przy użyciu `pip install -r requirements.txt` częścią inicjowania.

Należy zauważyć, że wystąpienia usługi w chmurze nie zawierają Kompilatory języka C, dlatego wszystkie biblioteki za pomocą rozszerzenia języka C, należy podać wstępnie skompilowane pliki binarne.

narzędzia PIP i jego zależności, a także pakietów w *requirements.txt*, są pobierane automatycznie i może być liczone jako płatny przepustowości. Zobacz [zarządzania wymagane pakiety](managing-required-packages-with-requirements-txt.md) Aby uzyskać szczegółowe informacje na temat zarządzania *requirements.txt* plików.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli po wdrożeniu Twojej roli sieci web lub proces roboczy nie działają prawidłowo, sprawdź następujące informacje:

- Obejmuje projektu języka Python *bin\\*  folder z (co najmniej):

  - *ConfigureCloudService.ps1*
  - *Skryptu LaunchWorker.ps1* (dla ról procesów roboczych)
  - *PS.cmd*

- Obejmuje projektu języka Python *requirements.txt* plików, wyświetlanie listy wszystkich zależności (lub też Kolekcja plików kółka).
- Włączanie pulpitu zdalnego w usłudze w chmurze i sprawdź pliki dziennika.
- W dziennikach *ConfigureCloudService.ps1* i *skryptu LaunchWorker.ps1* są przechowywane w *C:\Resources\Directory\%roli o identyfikatorze %. DiagnosticStore\LogFiles* folderu na komputerze zdalnym.
- Role sieci Web może tworzyć dodatkowe dzienniki ścieżką skonfigurowane w *web.config*, to znaczy ścieżka w `WSGI_LOG` appSetting. Działa także najbardziej regularne rejestrowania usług IIS i FastCGI.
- Obecnie *LaunchWorker.ps1.log* plik jest jedynym sposobem, aby wyświetlić dane wyjściowe lub błędy wyświetlane przez rolę proces roboczy języka Python.

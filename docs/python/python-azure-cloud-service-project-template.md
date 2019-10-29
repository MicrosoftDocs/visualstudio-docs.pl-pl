---
title: Szablon projektu usługi w chmurze platformy Azure dla języka Python
description: Program Visual Studio udostępnia szablony dla usług Azure Cloud Services utworzonych w języku Python, w tym wdrażanie roli, zależności i rozwiązywanie problemów.
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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983663"
---
# <a name="azure-cloud-service-projects-for-python"></a>Projekty usług w chmurze platformy Azure dla języka Python

Program Visual Studio udostępnia szablony ułatwiające rozpoczęcie tworzenia Cloud Services platformy Azure przy użyciu języka Python.

[Usługa w chmurze](/azure/cloud-services/) składa się z dowolnej liczby *ról procesów roboczych* i *ról sieci Web*, z których każda wykonuje koncepcyjnie oddzielne zadanie, ale może być oddzielnie replikowana między maszynami wirtualnymi w razie potrzeby skalowania. Role sieci Web zapewniają hosting dla aplikacji sieci Web frontonu. W przypadku, gdy język Python jest objęty, dowolna architektura sieci Web, która obsługuje WSGI, może być używana do pisania takiej aplikacji (zgodnie z obsługą [szablonu projektu sieci Web](python-web-application-project-templates.md)). Role procesu roboczego są przeznaczone dla długotrwałych procesów, które nie współdziałają bezpośrednio z użytkownikami. Zwykle korzystają z pakietów w pakiecie "Azure", który jest instalowany z [`pip install azure`](https://pypi.org/project/azure).

Ten artykuł zawiera szczegółowe informacje o szablonie projektu i innych obsłudze programu Visual Studio 2017 i nowszych (starsze wersje są podobne, ale z pewnymi różnicami). Aby uzyskać więcej informacji na temat pracy z platformą Azure w języku Python, odwiedź [Centrum deweloperów języka Python platformy Azure](/azure/python/).

## <a name="create-a-project"></a>Tworzenie projektu

1. Zainstaluj [zestaw Azure .NET SDK dla programu Visual Studio](https://visualstudio.microsoft.com/vs/azure-tools/), który jest wymagany do użycia szablonu usługi w chmurze.
1. W programie Visual Studio wybierz pozycję **plik** > **Nowy** > **projekt**, wyszukaj ciąg "Azure Python" i wybierz z listy pozycję **Usługa w chmurze platformy Azure** :

    ![Szablon projektu w chmurze platformy Azure dla języka Python](media/template-azure-cloud-project.png)

1. Wybierz co najmniej jedną rolę do dołączenia. Projekty w chmurze mogą łączyć role pisane w różnych językach, dzięki czemu można łatwo napisać każdą część aplikacji w najbardziej odpowiednim języku. Aby dodać nowe role do projektu po zakończeniu tego okna dialogowego, kliknij prawym przyciskiem myszy pozycję **role** w **Eksplorator rozwiązań** i wybierz jeden z elementów w obszarze **Dodaj**.

    ![Dodawanie ról w szablonie projektu w chmurze platformy Azure](media/template-azure-cloud-service-project-wizard.png)

1. W miarę tworzenia projektów poszczególnych ról może zostać wyświetlony monit o zainstalowanie dodatkowych pakietów języka Python, takich jak Django, butelka lub struktury kolb, jeśli wybrano rolę, która używa jednego z nich.

1. Po dodaniu nowej roli do projektu pojawiają się instrukcje dotyczące konfiguracji. Zmiany konfiguracji są zwykle niepotrzebne, ale mogą być przydatne do przyszłego dostosowywania projektów. Należy pamiętać, że podczas dodawania wielu ról w tym samym czasie tylko instrukcje dla ostatniej roli pozostają otwarte. Można jednak znaleźć instrukcje i wskazówki dotyczące rozwiązywania problemów dla innych ról w odpowiednich plikach *README. mht* , znajdujących się w katalogu głównym roli lub w folderze *bin* .

1. Folder *bin* projektu zawiera również jeden lub dwa skrypty programu PowerShell, które służą do konfigurowania zdalnej maszyny wirtualnej, w tym Instalowanie języka Python, każdy plik [*Requirements. txt*](#dependencies) w projekcie i Konfigurowanie usług IIS w razie potrzeby. Pliki te można edytować zgodnie z potrzebami we wdrożeniu, ale większość typowych opcji można zarządzać innymi sposobami (zobacz [Konfigurowanie wdrożenia roli](#configure-role-deployment) poniżej). Nie sugerujemy usuwania tych plików, ponieważ zamiast nich jest używany starszy skrypt konfiguracji, jeśli pliki są niedostępne.

    ![Pliki obsługi roli proces roboczy](media/template-azure-cloud-service-worker-role-support-files.png)

    Aby dodać te skrypty konfiguracji do nowego projektu, kliknij prawym przyciskiem myszy projekt, wybierz polecenie **dodaj** > **nowy element**i wybierz opcję **pliki obsługi roli sieci Web** lub **pliki obsługi roli procesu roboczego**.

## <a name="configure-role-deployment"></a>Konfigurowanie wdrożenia roli

Skrypty programu PowerShell w folderze *bin* projektu roli sterują wdrożeniem tej roli i mogą być edytowane w celu dostosowania konfiguracji:

- *ConfigureCloudService. ps1* jest używany dla ról Sieć Web i proces roboczy, zazwyczaj w celu zainstalowania i skonfigurowania zależności oraz ustawienia wersji języka Python.
- *LaunchWorker. ps1* jest używany tylko dla ról procesów roboczych i służy do zmiany zachowania uruchamiania, dodawania argumentów wiersza polecenia lub dodawania zmiennych środowiskowych.

Oba pliki zawierają instrukcje dotyczące dostosowywania. Możesz również zainstalować własną wersję środowiska Python, dodając kolejne zadanie do pliku *ServiceDefinition. csdef* projektu usługi w chmurze, ustawiając zmienną `PYTHON` na jej zainstalowaną ścieżkę *Python. exe* (lub równoważną). Po ustawieniu `PYTHON` Język Python nie jest instalowany z narzędzia NuGet.

Dodatkową konfigurację można wykonać w następujący sposób:

1. Zainstaluj pakiety przy użyciu `pip`, aktualizując plik *Requirements. txt* w katalogu głównym projektu. Skrypt *ConfigureCloudService. ps1* instaluje ten plik we wdrożeniu.
1. Ustaw zmienne środowiskowe, modyfikując plik *Web. config* (role sieci Web) lub sekcję `Runtime` pliku *ServiceDefinition. csdef* (role procesów roboczych).
1. Określ skrypt i argumenty, które mają być używane przez rolę procesu roboczego, modyfikując wiersz polecenia w sekcji `Runtime/EntryPoint` pliku *ServiceDefinitions. csdef* .
1. Ustaw główny skrypt obsługi dla roli sieci Web za pomocą pliku *Web. config* .

## <a name="test-role-deployment"></a>Testowanie wdrożenia roli

Podczas pisania ról można testować projekt w chmurze lokalnie za pomocą emulatora usługi w chmurze. Emulator jest dołączony do usługi Azure SDK Tools i jest ograniczoną wersją środowiska używanego podczas publikowania usługi w chmurze na platformie Azure.

Aby uruchomić emulator, najpierw upewnij się, że projekt w chmurze jest projektem startowym w rozwiązaniu, klikając prawym przyciskiem myszy i wybierając pozycję **Ustaw jako projekt startowy**. Następnie wybierz kolejno opcje **debuguj** > **Rozpocznij debugowanie** (**F5**) lub **debuguj** > **Uruchom bez debugowania** (**Ctrl**+**F5**).

Należy zauważyć, że ze względu na ograniczenia w emulatorze nie jest możliwe debugowanie kodu w języku Python. W ten sposób zalecamy debugowanie ról przez uruchamianie ich niezależnie, a następnie użycie emulatora do testowania integracji przed opublikowaniem.

## <a name="deploy-a-role"></a>Wdróż rolę

Aby otworzyć kreatora **publikacji** , wybierz projekt roli w **Eksplorator rozwiązań** i wybierz opcję **Kompiluj** > **Opublikuj** z menu głównego lub kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Publikuj**.

Proces publikowania obejmuje dwie fazy. Po pierwsze program Visual Studio tworzy pojedynczy pakiet zawierający wszystkie role dla usługi w chmurze. Ten pakiet jest wdrożony na platformie Azure, co inicjuje co najmniej jedną maszynę wirtualną dla każdej roli i wdraża źródło.

W miarę aktywowania każdej maszyny wirtualnej jest wykonywany skrypt *ConfigureCloudService. ps1* i instalowane są wszystkie zależności. Ten skrypt domyślnie instaluje najnowszą wersję środowiska Python z narzędzia [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) i wszystkie pakiety określone w pliku *Requirements. txt* .

Na koniec role procesów roboczych wykonują *LaunchWorker. ps1*, które zaczynają uruchamiać skrypt języka Python; role sieci Web inicjują usługi IIS i zaczynają obsługiwać żądania sieci Web.

## <a name="dependencies"></a>Zależności

W przypadku Cloud Services skrypt *ConfigureCloudService. ps1* używa `pip` do instalowania zestawu zależności języka Python. Zależności należy określać w pliku o nazwie *Requirements. txt* (dostosowywalny, modyfikując *ConfigureCloudService. ps1*). Plik jest wykonywany z `pip install -r requirements.txt` w ramach inicjalizacji.

Należy pamiętać, że wystąpienia usługi w chmurze nie obejmują kompilatorów języka C, dlatego wszystkie biblioteki z rozszerzeniami języka C muszą udostępniać wstępnie skompilowane pliki binarne.

Program PIP i jego zależności, a także pakiety w programie *Requirements. txt*, są pobierane automatycznie i mogą być zliczane jako obciążenie przepustowością. Zobacz [Zarządzanie wymaganymi pakietami](managing-required-packages-with-requirements-txt.md) , aby uzyskać szczegółowe informacje na temat zarządzania plikami *Requirements. txt* .

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli rola sieci Web lub proces roboczy nie działa prawidłowo po wdrożeniu, należy sprawdzić następujące kwestie:

- Projekt w języku Python zawiera folder *\\bin* z (co najmniej):

  - *ConfigureCloudService. ps1*
  - *LaunchWorker. ps1* (dla ról procesów roboczych)
  - *PS. cmd*

- Projekt w języku Python zawiera plik *Requirements. txt* zawierający wszystkie zależności (lub alternatywnie zbiór plików kółka).
- Włącz Pulpit zdalny w usłudze w chmurze i zbadaj pliki dziennika.
- Dzienniki dla *ConfigureCloudService. ps1* i *LaunchWorker. ps1* są przechowywane w *folderze c:\resources\directory\%RoleId%. Folder DiagnosticStore\LogFiles* na komputerze zdalnym.
- Role sieci Web mogą zapisywać dodatkowe dzienniki w ścieżce skonfigurowanej w *pliku Web. config*, a mianowicie ścieżki w `WSGI_LOG` element appSetting. Najczęściej działa również rejestrowanie w usługach IIS lub FastCGI.
- Obecnie plik *LaunchWorker. ps1. log* jest jedynym sposobem wyświetlania danych wyjściowych lub błędów wyświetlanych przez rolę procesu roboczego języka Python.

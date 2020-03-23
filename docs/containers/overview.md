---
title: Narzędzia kontenerów programu Visual Studio w systemie Windows
description: Poznaj narzędzia dostępne w programie Visual Studio do pracy z platformą Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0d5859016a02de259c24c213c6cfef8cb5fce005
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916565"
---
# <a name="container-tools-in-visual-studio"></a>Narzędzia kontenerów w programie Visual Studio

Narzędzia zawarte w programie Visual Studio do tworzenia za pomocą kontenerów są łatwe w użyciu i znacznie upraszczają tworzenie, debugowanie i wdrażanie dla aplikacji konteneryzowanych. Można pracować z kontenerem dla pojedynczego projektu lub użyć aranżacji kontenera z Docker Compose, Service Fabric lub Kubernetes do pracy z wieloma usługami w kontenerach.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Pomoc techniczna platformy Docker w programie Visual Studio

Obsługa platformy Docker jest dostępna dla projektów ASP.NET, ASP.NET podstawowych oraz projektów konsoli .NET Core i .NET Framework.

Obsługa platformy Docker w programie Visual Studio uległa zmianie w wielu wersjach w odpowiedzi na potrzeby klientów. Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu, a obsługiwane opcje różnią się w zależności od typu projektu i wersji programu Visual Studio. W przypadku niektórych obsługiwanych typów projektów, jeśli chcesz tylko kontener dla pojedynczego projektu, bez użycia aranżacji, można to zrobić, dodając obsługę platformy Docker.  Następny poziom jest obsługa aranżacji kontenera, który dodaje odpowiednie pliki obsługi dla określonego koordynatora wybrać.  

Za pomocą programu Visual Studio 2017 można używać docker compose i sieci szkieletowej usług jako usługi aranżacji kontenerów.  Narzędzia Kubernetes można również użyć również po zainstalowaniu [narzędzia programu Visual Studio dla aplikacji Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).

> [!NOTE]
> Jeśli używasz wersji programu Visual Studio 2017 przed 15.8 lub używasz szablonu projektu programu .NET Framework (nie .NET Core), podczas dodawania obsługi platformy Docker, obsługa aranżacji przy użyciu docker Compose jest dodawany automatycznie. Obsługa aranżacji kontenera za pośrednictwem aplikacji Docker Compose jest dodawana automatycznie w programie Visual Studio 2017 w wersjach od 15.0 do 15.7 i dla projektów .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit platformy Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowanym **programem Web Development,** **obciążeniem narzędzi platformy Azure** i/lub **międzyplatformowym** obciążeniem programistycznym .NET Core
* [.NET Core Development Tools](https://dotnet.microsoft.com/download/dotnet-core/) do tworzenia za pomocą platformy .NET Core.
* Aby opublikować w usłudze Azure Container Registry, subskrypcję platformy Azure. [Zarejestruj się, aby uzyskać bezpłatną wersję próbną](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Pomoc techniczna platformy Docker w programie Visual Studio

Obsługa platformy Docker jest dostępna dla projektów ASP.NET, ASP.NET podstawowych oraz projektów konsoli .NET Core i .NET Framework.

Obsługa platformy Docker w programie Visual Studio uległa zmianie w wielu wersjach w odpowiedzi na potrzeby klientów. Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu, a obsługiwane opcje różnią się w zależności od typu projektu i wersji programu Visual Studio. W przypadku niektórych obsługiwanych typów projektów, jeśli chcesz tylko kontener dla pojedynczego projektu, bez użycia aranżacji, można to zrobić, dodając obsługę platformy Docker.  Następny poziom jest obsługa aranżacji kontenera, który dodaje odpowiednie pliki obsługi dla określonego koordynatora wybrać.  

Za pomocą programu Visual Studio 2019 można używać docker compose, Kubernetes i service fabric jako usługi aranżacji kontenerów.

> [!NOTE]
> Jeśli używasz pełnego szablonu projektu konsoli platformy .NET Framework, obsługiwaną opcją jest **Dodaj obsługę koordynatora kontenera** po utworzeniu projektu, z opcjami użycia sieci szkieletowej usług lub docker compose. Dodawanie pomocy technicznej podczas tworzenia projektu i **dokcker do strony obsługi** dla pojedynczego projektu bez aranżacji nie są dostępne opcje.

W programie Visual Studio 2019 w wersji 16.4 lub nowszej dostępne jest okno **Kontenery,** które umożliwia wyświetlanie uruchomionych kontenerów, przeglądanie dostępnych obrazów, wyświetlanie zmiennych środowiskowych, dzienników i mapowań portów, sprawdzanie systemu plików, dołączanie debugera lub otwieranie okna terminala w środowisku kontenera. Zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w programie Visual Studio.](view-and-diagnose-containers.md)

::: moniker-end

### <a name="adding-docker-support"></a>Dodawanie obsługi platformy Docker

Obsługę platformy Docker można włączyć podczas tworzenia projektu, wybierając **pozycję Włącz obsługę platformy Docker** podczas tworzenia nowego projektu, jak pokazano na poniższym zrzucie ekranu:

::: moniker range="vs-2017"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci Web ASP.NET Core w programie Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci Web ASP.NET Core w programie Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> W przypadku projektów programu .NET Framework (nie .NET Core) dostępne są tylko kontenery systemu Windows.

Obsługę platformy Docker można dodać do istniejącego projektu, wybierając pozycję **Dodaj** > **obsługę platformy Docker** w **Eksploratorze rozwiązań**. Polecenia **Dodaj > docker support** i Add > Container **Orchestrator Support** znajdują się w menu prawym przyciskiem myszy (lub menu kontekstowym) węzła projektu dla projektu ASP.NET Core w **Eksploratorze rozwiązań,** jak pokazano na poniższym zrzucie ekranu:

![Opcja menu Dodaj obsługę platformy Docker w programie Visual Studio](./media/overview/add-docker-support-menu.png)

Po dodaniu lub włączeniu obsługi platformy Docker program Visual Studio dodaje do projektu następujące elementy:

- plik *Dockerfile*
- plik .dockerignore
- a NuGet odwołanie do pakietu Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
Rozwiązanie wygląda następująco po dodaniu obsługi platformy Docker:

![Zrzut ekranu przedstawiający Eksploratora rozwiązań za pomocą pliku Dockerfile i .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Po włączeniu obsługi platformy Docker podczas tworzenia projektu dla projektu ASP.NET (.NET Framework, a nie .NET Core projektu), jak pokazano na poniższym zrzucie ekranu, zostanie również dodana obsługa aranżacji kontenera.

![Włączanie obsługi tworzenia docker dla projektu ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Pomoc techniczna w grze Docker Compose

Jeśli chcesz skomponować rozwiązanie z wieloma kontenerami przy użyciu aplikacji Docker Compose, dodaj obsługę aranżacji kontenerów do swoich projektów. Dzięki temu można uruchomić i debugować grupę kontenerów (całe rozwiązanie lub grupę projektów) w tym samym czasie, jeśli są one zdefiniowane w tym samym pliku *docker-compose.yml.*

Aby dodać obsługę aranżacji kontenerów przy użyciu aplikacji Docker Compose, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratorze rozwiązań**i wybierz polecenie **Dodaj > obsługę aranżacji kontenerów**. Następnie wybierz **docker Compose** do zarządzania kontenerami.

Po dodaniu obsługi aranżacji kontenera do projektu zostanie wyświetlony *plik Dockerfile* dodany do projektu (jeśli nie było go już tam) i folder **docker-compose** dodany do rozwiązania w **Eksploratorze rozwiązań,** jak pokazano poniżej:

![Pliki platformy Docker w Eksploratorze rozwiązań w programie Visual Studio](media/overview/docker-support-solution-explorer.png)

Jeśli *docker-compose.yml* już istnieje, visual studio po prostu dodaje wymagane wiersze kodu konfiguracji do niego.

Powtórz proces z innymi projektami, które chcesz kontrolować za pomocą docker compose.

## <a name="kubernetes-support"></a>Pomoc techniczna firmy Kubernetes

::: moniker range="vs-2017"
Aby dodać obsługę aplikacji Kubernetes, zainstaluj [narzędzie Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Dzięki obsłudze usługi Kubernetes można włączyć połączenie między projektem lokalnym a klastrem kubernetes uruchomionym w [usłudze Azure Kubernetes Service (AKS),](/azure/aks)a tym samym zmodyfikować i debugować usługi uruchomione w programie AKS przy użyciu programu Visual Studio.  Ta usługa jest świadczona przez [usługę Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio). Usługa Azure Dev Spaces umożliwia również konfigurowanie oddzielnych gałęzi usług Kubernetes *nazywanych przestrzeniami deweloperskimi* do celów programistycznych, dzięki czemu można skutecznie izolować usługi produkcyjne od wersji roboczych w programowaniu i zachować wyraźne modyfikacje czysto oddzielone od siebie.

Aby dodać obsługę kubernetes do projektów, wybierz **Kubernetes/Helm** podczas dodawania obsługi aranżacji kontenera. Kilka plików są dodawane do projektu, w tym *azds.yaml*, który konfiguruje usługi Azure Dev Spaces i helm wykresy, które opisują strukturę usług Kubernetes.

## <a name="service-fabric-support"></a>Obsługa sieci szkieletowej usług

Za pomocą narzędzi sieci szkieletowej usług w programie Visual Studio można tworzyć i debugować dla sieci szkieletowej usług Azure, uruchamiać i debugować lokalnie oraz wdrażać na platformie Azure.

::: moniker range="vs-2017"
Visual Studio 2017 w wersji 15.9 i nowszych z zainstalowanym obciążeniem dewelopera platformy Azure obsługuje tworzenie konteneryzowanych mikrousług przy użyciu kontenerów systemu Windows i aranżacji sieci szkieletowej usług.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 obsługuje tworzenie konteneryzowanych mikrousług przy użyciu kontenerów systemu Windows i aranżacji sieci szkieletowej usług.
::: moniker-end

Aby uzyskać szczegółowy samouczek, zobacz [Samouczek: Wdrażanie aplikacji platformy .NET w kontenerze systemu Windows w sieci szkieletowej usług Azure](/azure/service-fabric/service-fabric-host-app-in-a-container).

Aby uzyskać więcej informacji na temat sieci szkieletowej usług Azure, zobacz [Sieci szkieletowej usług](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Ciągłe dostarczanie i ciągła integracja (CI/CD)

Visual Studio łatwo integruje się z usługi Azure Pipelines w celu zautomatyzowanej i ciągłej integracji oraz dostarczania zmian w kodzie i konfiguracji usługi. Aby rozpocząć, zobacz [Tworzenie pierwszego potoku](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

W przypadku sieci szkieletowej usług zobacz [Samouczek: Wdrażanie aplikacji ASP.NET Core w sieci szkieletowej usługi Azure przy użyciu projektów devops platformy Azure.](/azure/devops-project/azure-devops-project-service-fabric)

W przypadku aplikacji Kubernetes zobacz [Wdrażanie aplikacji kontenera platformy Docker w usłudze Azure Kubernetes](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat implementacji usług i korzystania z narzędzi programu Visual Studio do pracy z kontenerami, przeczytaj następujące artykuły:

[Debugowanie aplikacji w lokalnym kontenerze platformy Docker](edit-and-refresh.md)

[Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio](hosting-web-apps-in-docker.md)

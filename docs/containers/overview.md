---
title: Narzędzia kontenera programu Visual Studio w systemie Windows
description: Poznaj narzędzia dostępne w programie Visual Studio do pracy z platformą Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 4f8c1c265f49b600880cd1278b51095fda9cfb1d
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975150"
---
# <a name="container-tools-in-visual-studio"></a>Narzędzia kontenerów w programie Visual Studio

Narzędzia dostępne w programie Visual Studio do programowania przy użyciu kontenerów są łatwe w użyciu i znacznie upraszczają kompilowanie, debugowanie i wdrażanie dla aplikacji kontenerowych. Możesz współpracować z kontenerem dla pojedynczego projektu lub używać aranżacji kontenerów z Docker Compose, Service Fabric lub Kubernetes do pracy z wieloma usługami w kontenerach.

::: moniker range="vs-2017"

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Obsługa platformy Docker w programie Visual Studio

Obsługa platformy Docker jest dostępna dla projektów ASP.NET, projektów ASP.NET Core i projektów programu .NET Core i .NET Framework.

Obsługa platformy Docker w programie Visual Studio została zmieniona na wiele wydań w odpowiedzi na potrzeby klientów. Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu, a obsługiwane opcje różnią się w zależności od typu projektu i wersji programu Visual Studio. W przypadku niektórych obsługiwanych typów projektów, jeśli chcesz tylko kontener dla pojedynczego projektu, bez korzystania z aranżacji, możesz to zrobić, dodając obsługę platformy Docker.  Następnym poziomem jest obsługa aranżacji kontenerów, która dodaje odpowiednie pliki obsługi dla wybranego koordynatora.

Program Visual Studio 2017 umożliwia używanie Docker Compose i Service Fabric jako usług aranżacji kontenerów.  W przypadku instalowania [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)można również użyć Kubernetes.

> [!NOTE]
> Jeśli używasz wersji programu Visual Studio 2017 wcześniejszej niż 15,8, lub używasz szablonu projektu .NET Framework (nie platformy .NET Core), podczas dodawania obsługi platformy Docker, obsługa aranżacji przy użyciu Docker Compose jest automatycznie dodawana. Obsługa aranżacji kontenerów za pośrednictwem Docker Compose jest automatycznie dodawana w programie Visual Studio 2017 w wersji 15,0 do 15,7 i dla projektów .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="prerequisites"></a>Wymagania wstępne

* [Pulpit Docker](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z zainstalowaną obsługą tworzenia aplikacji dla **sieci Web**, obciążeń **narzędzi platformy Azure** i/lub **oprogramowania .NET Core dla wielu platform**
* [Narzędzia programistyczne platformy .NET Core](https://dotnet.microsoft.com/download/dotnet-core/) do programowania przy użyciu platformy .NET Core.
* Do opublikowania w usłudze Azure Container Registry, subskrypcji platformy Azure. [Zarejestruj się, aby skorzystać z bezpłatnej wersji próbnej](https://azure.microsoft.com/offers/ms-azr-0044p/).

## <a name="docker-support-in-visual-studio"></a>Obsługa platformy Docker w programie Visual Studio

Obsługa platformy Docker jest dostępna dla projektów ASP.NET, projektów ASP.NET Core i projektów programu .NET Core i .NET Framework.

Obsługa platformy Docker w programie Visual Studio została zmieniona na wiele wydań w odpowiedzi na potrzeby klientów. Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu, a obsługiwane opcje różnią się w zależności od typu projektu i wersji programu Visual Studio. W przypadku niektórych obsługiwanych typów projektów, jeśli chcesz tylko kontener dla pojedynczego projektu, bez korzystania z aranżacji, możesz to zrobić, dodając obsługę platformy Docker.  Następnym poziomem jest obsługa aranżacji kontenerów, która dodaje odpowiednie pliki obsługi dla wybranego koordynatora.

Za pomocą programu Visual Studio 2019 można używać Docker Compose, Kubernetes i Service Fabric jako usług aranżacji kontenerów.

> [!NOTE]
> Jeśli używasz szablonu projektu konsoli pełnej .NET Framework, obsługiwana opcja to **Dodaj obsługę programu Orchestrator kontenera** po utworzeniu projektu, z opcjami używania Service Fabric lub Docker Compose. Dodanie obsługi podczas tworzenia projektu i **dodanie obsługi platformy Docker** dla pojedynczego projektu bez aranżacji nie jest możliwe.

W programie Visual Studio 2019 w wersji 16,4 i nowszych dostępne jest okno **kontenery** , które pozwala wyświetlać uruchomione kontenery, przeglądać dostępne obrazy, wyświetlać zmienne środowiskowe, dzienniki i mapowania portów, sprawdzać system plików, dołączać debuger lub otwierać okno terminalu w środowisku kontenera. Zobacz [Wyświetlanie i diagnozowanie kontenerów i obrazów w programie Visual Studio](view-and-diagnose-containers.md).

::: moniker-end

### <a name="adding-docker-support"></a>Dodawanie obsługi platformy Docker

Obsługę platformy Docker można włączyć podczas tworzenia projektu, wybierając opcję **Włącz obsługę platformy Docker** podczas tworzenia nowego projektu, jak pokazano na poniższym zrzucie ekranu:

::: moniker range="vs-2017"
![Włącz obsługę platformy Docker dla nowej aplikacji internetowej ASP.NET Core w programie Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Włącz obsługę platformy Docker dla nowej aplikacji internetowej ASP.NET Core w programie Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

> [!NOTE]
> W przypadku projektów .NET Framework (nie .NET Core) dostępne są tylko kontenery systemu Windows.

Obsługę platformy Docker można dodać do istniejącego projektu, wybierając pozycję **Dodaj**  >  **obsługę platformy Docker** w **Eksplorator rozwiązań**. Polecenia **dodaj > Docker support** i **Dodawanie > kontenerów pomocy technicznej programu Orchestrator** znajdują się w menu rozwijanym prawym przyciskiem myszy (lub w menu kontekstowym) węzła projektu dla projektu ASP.NET Core w **Eksplorator rozwiązań**, jak pokazano na poniższym zrzucie ekranu:

![Opcja menu Dodaj obsługę platformy Docker w programie Visual Studio](./media/overview/add-docker-support-menu.png)

Po dodaniu lub włączeniu obsługi platformy Docker program Visual Studio dodaje do projektu następujące elementy:

- plik *pliku dockerfile*
- plik. dockerignore
- odwołanie do pakietu NuGet do elementu Microsoft. VisualStudio. Azure. Containers. Tools. targets

::: moniker range=">=vs-2019"
Rozwiązanie wygląda następująco po dodaniu obsługi platformy Docker:

![Zrzut ekranu Eksploratora rozwiązań z plikiem pliku dockerfile i. dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Po włączeniu obsługi platformy Docker podczas tworzenia projektu dla projektu ASP.NET (.NET Framework, a nie projektu .NET Core), jak pokazano na poniższym zrzucie ekranu, również zostanie dodana obsługa aranżacji kontenerów.

![Włącz obsługę redagowania platformy Docker dla projektu ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Obsługa Docker Compose

Jeśli chcesz utworzyć rozwiązanie wielokontenerowe przy użyciu Docker Compose, Dodaj obsługę aranżacji kontenera do projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie lub grupę projektów) w tym samym czasie, jeśli są one zdefiniowane w tym samym pliku *Docker-Compose. yml* .

Aby dodać obsługę aranżacji kontenera przy użyciu Docker Compose, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj obsługę aranżacji kontenerów >**. Następnie wybierz **Docker Compose** , aby zarządzać kontenerami.

Po dodaniu obsługi aranżacji kontenera do projektu zobaczysz *pliku dockerfile* dodany do projektu (jeśli jeszcze go nie ma) i folderem **"Docker-Zredaguj"** dodanym do rozwiązania w **Eksplorator rozwiązań**, jak pokazano poniżej:

![Pliki platformy Docker w Eksplorator rozwiązań w programie Visual Studio](media/overview/docker-support-solution-explorer.png)

Jeśli *Docker-Compose. yml* już istnieje, Visual Studio dodaje do niego wymagane wiersze kodu konfiguracji.

Powtórz ten proces z innymi projektami, które chcesz kontrolować przy użyciu Docker Compose.

## <a name="kubernetes-support"></a>Obsługa Kubernetes

::: moniker range="vs-2017"
Aby dodać obsługę Kubernetes, zainstaluj [Visual Studio Tools for Kubernetes](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes).
::: moniker-end

Dzięki obsłudze Kubernetes można włączyć połączenie między projektem lokalnym i klastrem Kubernetes działającym w [usłudze Azure Kubernetes Service (AKS)](/azure/aks), a tym samym zmodyfikować i debugować usługi działające przy użyciu programu Visual Studio.  Ta usługa jest świadczona przez [mostek do Kubernetes](overview-bridge-to-kubernetes.md). Mostek do Kubernetes umożliwia również Konfigurowanie oddzielnych gałęzi usług Kubernetes do celów programistycznych, dzięki czemu można efektywnie izolować usługi produkcyjne od wersji roboczych w trakcie opracowywania i utrzymywać nieznacznie oddzielone od siebie zmiany.

Aby dodać obsługę Kubernetes do projektów, wybierz pozycję **Kubernetes/Helm** , gdy zostanie dodana obsługa aranżacji kontenera. Do projektu dodawane są kilka plików, w tym wykresy Helm opisujące strukturę usług Kubernetes Services. Aby rozpocząć pracę z usługą Bridge do Kubernetes, zobacz [Korzystanie z mostka do Kubernetes](bridge-to-kubernetes.md).

## <a name="service-fabric-support"></a>Obsługa Service Fabric

Dzięki narzędziom Service Fabric w programie Visual Studio można opracowywać i debugować Service Fabric na platformie Azure, uruchamiać i debugować lokalnie oraz wdrażać je na platformie Azure.

::: moniker range="vs-2017"
Program Visual Studio 2017 w wersji 15,9 lub nowszej z zainstalowanym obciążeniem programistycznym platformy Azure obsługuje tworzenie mikrousług kontenerów przy użyciu kontenerów systemu Windows i aranżacji Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Program Visual Studio 2019 obsługuje opracowywanie mikrousług kontenerów przy użyciu kontenerów systemu Windows i aranżacji Service Fabric.
::: moniker-end

Aby uzyskać szczegółowy samouczek, zobacz [Samouczek: wdrażanie aplikacji .NET w kontenerze systemu Windows na platformie Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Aby uzyskać więcej informacji na temat usługi Azure Service Fabric, zobacz [Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Ciągłe dostarczanie i ciągła integracja (CI/CD)

Program Visual Studio umożliwia łatwe i szybkie integrację z Azure Pipelines na potrzeby zautomatyzowanej i ciągłej integracji oraz dostarczania zmian w kodzie i konfiguracji usługi. Aby rozpocząć, zobacz [Tworzenie pierwszego potoku](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2&preserve-view=true).

Aby uzyskać Service Fabric, zobacz [Samouczek: wdrażanie aplikacji ASP.NET Core na platformie Azure Service Fabric przy użyciu Azure DevOps projects](/azure/devops-project/azure-devops-project-service-fabric).

Aby uzyskać Kubernetes, zobacz [wdrażanie aplikacji kontenera platformy Docker w usłudze Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&preserve-view=true).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat implementacji usług i korzystania z narzędzi Visual Studio Tools do pracy z kontenerami, przeczytaj następujące artykuły:

[Debugowanie aplikacji w lokalnym kontenerze platformy Docker](edit-and-refresh.md)

[Wdrażanie kontenera platformy ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio](hosting-web-apps-in-docker.md)

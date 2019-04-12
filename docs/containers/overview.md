---
title: Narzędzia kontenerów programu Visual Studio na Windows
description: Poznawanie narzędzi dostępnych w programie Visual Studio do pracy z platformą Docker
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 4b03ccddadf954b8430b7ad9b5a4ed765fccc3f5
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537971"
---
# <a name="container-tools-in-visual-studio"></a>Narzędzia kontenerów programu Visual Studio

Narzędzi dostępnych w programie Visual Studio do programowania z użyciem kontenery są łatwe w użyciu i znacznie upraszczają tworzenie, debugowanie i wdrażanie konteneryzowanych aplikacji. Praca z kontener dla jednego projektu lub użyć aranżacji kontenerów przy użyciu narzędzia Docker Compose, Usługa Service Fabric lub Kubernetes do pracy z wieloma usługami w kontenerach.

> [!NOTE]
> Ten artykuł dotyczy programu Visual Studio w Windows, a nie programu Visual Studio dla komputerów Mac.

> [!TIP]
> Aby dowiedzieć się więcej o instalowaniu platformy Docker for Windows, zobacz [pulpitu platformy Docker for Windows](https://docs.docker.com/docker-for-windows/).

## <a name="docker-support-in-visual-studio"></a>Obsługę platformy docker w programie Visual Studio

Obsługę platformy docker jest dostępna dla niektórych typach projektów .NET.  Jest ona dostępna dla projektów programu ASP.NET, projektów ASP.NET Core i projektach konsoli .NET Core i .NET Framework.

Obsługa platformy Docker w programie Visual Studio został zmieniony w liczbie wersjach w odpowiedzi na potrzeby klientów. Istnieją dwa poziomy obsługę platformy Docker, które można dodać do projektu i obsługiwane opcje zależne od typu projektu i wersji programu Visual Studio. W niektórych typach projektów obsługiwanych Jeśli Ty chcesz po prostu kontener dla jednego projektu, bez używania aranżacji, możesz tworzyć, dodając obsługę platformy Docker.  Następny poziom to obsługa aranżacji kontenerów, który dodaje pliki pomocnicze odpowiednie dla danego programu orchestrator, wybranych.  

::: moniker range="vs-2017"

Za pomocą programu Visual Studio 2017 można użyć narzędzia Docker Compose i Service Fabric, jako usługach aranżacji kontenerów.  Można również użyć rozwiązania Kubernetes, po zainstalowaniu [Visual Studio Tools dla platformy Kubernetes](https://aka.ms/get-vsk8stools).

> [!NOTE]
> Jeśli używasz programu Visual Studio 2017 w wersji wcześniejszej niż 15.8 lub używasz szablonu projektu .NET Framework (nie .NET Core), dodając obsługę platformy Docker, orkiestracji obsługi przy użyciu narzędzia Docker Compose jest automatycznie dodawany. Obsługa aranżacji kontenerów przy użyciu narzędzia Docker Compose jest automatycznie dodawany w programie Visual Studio 2017 w wersji 15.0 wersji 15.7 i dla projektów programu .NET Framework.

::: moniker-end

::: moniker range=">=vs-2019"

Za pomocą programu Visual Studio 2019 r można użyć narzędzia Docker Compose, Kubernetes i usługi Service Fabric, jako usługach aranżacji kontenerów.

> [!NOTE]
> Jeśli używasz pełnej szablonu Projekt konsoli .NET Framework, po dodaniu obsługi programu Docker obsługę organizowanie za pomocą narzędzia Docker Compose jest automatycznie dodawany.
::: moniker-end

**Dodaj > obsługę platformy Docker** i **Dodaj > Obsługa Orkiestratora kontenerów** polecenia znajdują się w menu kliknij prawym przyciskiem myszy (lub menu kontekstowego) węzeł projektu dla projektu platformy ASP.NET Core w  **Eksplorator rozwiązań**, jak pokazano na poniższym zrzucie ekranu:

![Dodaj opcję menu obsługę platformy Docker w programie Visual Studio](./media/overview/add-docker-support-menu.png)

### <a name="adding-docker-support-without-orchestration"></a>Dodawanie obsługi platformy Docker (bez aranżacji)

Obsługę platformy Docker można dodać do istniejącego projektu, wybierając **Dodaj** > **obsługę platformy Docker** w **Eksploratora rozwiązań**. Można również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając **włączyć obsługę platformy Docker** podczas tworzenia nowego projektu, jak pokazano na poniższym zrzucie ekranu:

::: moniker range="vs-2017"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Włącz obsługę platformy Docker dla nowej aplikacji sieci web platformy ASP.NET Core w programie Visual Studio](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

Podczas dodawania lub Włącz obsługę platformy Docker programu Visual Studio dodaje następujące do projektu:

- *pliku Dockerfile* pliku
- plik .dockerignore
- Odwołanie do pakietu NuGet, aby Microsoft.VisualStudio.Azure.Containers.Tools.Targets

::: moniker range=">=vs-2019"
Po dodaniu obsługę platformy Docker, rozwiązanie wyglądają następująco:

![Zrzut ekranu przedstawiający Eksploratora rozwiązań za pomocą pliku Dockerfile i .dockerignore](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> Gdy włączysz obsługę platformy Docker podczas tworzenia projektu dla projektu platformy ASP.NET (.NET Framework, nie w projekcie platformy .NET Core), jak pokazano na poniższym zrzucie ekranu, dodawany jest również obsługa aranżacji kontenerów.

![Włącz Docker compose obsługę projektu programu ASP.NET](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Obsługi programu docker Compose

Do tworzenia rozwiązania wielu kontenerów przy użyciu narzędzia Docker Compose, należy dodać Obsługa aranżacji kontenerów do swoich projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całego rozwiązania lub grupy projektów) w tym samym czasie, jeśli są one definiowane w tym samym *docker-compose.yml* pliku.

Aby dodać obsługę aranżacji kontenerów przy użyciu narzędzia Docker Compose, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratora rozwiązań**i wybierz polecenie **Dodaj > kontener obsługuje aranżacji**. Następnie wybierz **narzędzia Docker Compose** Zarządzanie kontenerów.

Po dodaniu obsługi aranżacji kontenerów do projektu, zobacz *pliku Dockerfile* dodane do projektu (Jeśli nie było jednym istnieje już) i **narzędzia docker compose** folderu dodawany do rozwiązania w  **Eksplorator rozwiązań**, jak pokazano poniżej:

![Pliki docker w Eksploratorze rozwiązań w programie Visual Studio](media/overview/docker-support-solution-explorer.png)

Jeśli *docker-compose.yml* już istnieje, program Visual Studio po prostu dodaje wymagane wierszy kodu konfiguracji do niego.

Powtórz te czynności z innymi projektami, które użytkownik chce sterować przy użyciu narzędzia Docker Compose.

## <a name="kubernetes-support"></a>Obsługa klastra Kubernetes

::: moniker range="vs-2017"
Aby dodać obsługę rozwiązania Kubernetes, należy zainstalować [Visual Studio Tools dla platformy Kubernetes](https://aka.ms/get-vsk8stools).
::: moniker-end

Z obsługą rozwiązania Kubernetes, możesz włączyć połączenie między lokalnym projektu i klastra Kubernetes uruchomionego [Azure Kubernetes Service (AKS)](/azure/aks)i w ten sposób modyfikować i debugować swoich usług w usłudze AKS za pomocą programu Visual Studio.  Ta usługa jest świadczona przez [miejsca do magazynowania Azure Dev](/azure/dev-spaces/quickstart-netcore-visualstudio). Usługa Azure Dev spacje również umożliwia skonfigurowanie osobnych oddziałach usługi Kubernetes o nazwie *dev miejsca do magazynowania* do celów programistycznych, więc można efektywnie izolowania usług produkcyjnych z wersji roboczych w rozwoju i zachować odrębne modyfikacje nie pozostawia żadnych śladów oddzielone od siebie nawzajem.

Aby dodać obsługę rozwiązania Kubernetes do swoich projektów, wybierz **Kubernetes i Helm** po dodaniu obsługi aranżacji kontenerów. Kilka plików są dodawane do projektu, łącznie z *azds.yaml*, który umożliwia skonfigurowanie usługi Azure Dev miejsca do magazynowania i wykresów rozwiązania Helm, które opisują strukturę usługi Kubernetes.

## <a name="service-fabric-support"></a>Obsługa usługi Service Fabric

Za pomocą narzędzi usługi Service Fabric w programie Visual Studio można tworzyć i debugowania dla usługi Azure Service Fabric, uruchamianie i debugowanie lokalnie i wdrażanie na platformie Azure.

::: moniker range="vs-2017"
Visual Studio 2017 w wersji 15.9 lub nowszym z zainstalowanym obciążeniem programowanie na platformie Azure obsługuje opracowywanie konteneryzowanych mikrousług przy użyciu Windows kontenery i aranżacji usługi Service Fabric.
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 obsługuje tworzenie konteneryzowane mikrousługi przy użyciu Windows kontenery i aranżacji usługi Service Fabric.
::: moniker-end

Aby uzyskać szczegółowy samouczek, zobacz [samouczka: Wdrażanie aplikacji .NET w kontenerze Windows w usłudze Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container).

Aby uzyskać więcej informacji na temat usługi Azure Service Fabric, zobacz [usługi Service Fabric](/azure/service-fabric).

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>Ciągłe dostarczanie i ciągłej integracji (CI/CD)

Program Visual Studio łatwo integruje potoki usługi Azure dla zautomatyzowanych i ciągłej integracji i dostarczania zmiany do kodu usługi i konfiguracji. Aby rozpocząć pracę, zobacz [Tworzenie pierwszego potoku](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2).

Dla usługi Service Fabric, zobacz [samouczka: Wdrażanie aplikacji platformy ASP.NET Core w usłudze Azure Service Fabric przy użyciu usługi Azure DevOps Projects](/azure/devops-project/azure-devops-project-service-fabric).

Dla rozwiązania Kubernetes, zobacz [wdrażanie aplikacji kontenera aparatu Docker w usłudze Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops).

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o usługach wdrażania i korzystania z narzędzi programu Visual Studio do pracy z kontenerami, przeczytaj następujące artykuły:

[Debugowanie aplikacji w lokalnym kontenerze Docker](vs-azure-tools-docker-edit-and-refresh.md)

[Wdrażanie kontenera platformy ASP.NET do rejestru kontenerów przy użyciu programu Visual Studio](vs-azure-tools-docker-hosting-web-apps-in-docker.md)

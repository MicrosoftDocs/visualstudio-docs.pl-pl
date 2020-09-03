---
title: Samouczek narzędzi Kubernetess | Microsoft Docs
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913296"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Wprowadzenie do narzędzi Visual Studio Kubernetes Tools

Narzędzia Kubernetes programu Visual Studio pomagają usprawnić opracowywanie aplikacji kontenerowych ukierunkowanych na Kubernetes. Program Visual Studio może automatycznie tworzyć pliki konfiguracji jako kod, które są konieczne do obsługi wdrażania Kubernetes, takie jak wykresy wieloetapowe dockerfile i Helm. Możesz debugować kod w klastrze usługi Azure Kubernetes Service (AKS) przy użyciu Azure Dev Spaces lub publikować bezpośrednio w klastrze AKS z poziomu programu Visual Studio.

Ten samouczek obejmuje użycie programu Visual Studio w celu dodania obsługi Kubernetes do projektu i opublikowania w AKS. Jeśli zamierzasz głównie używać [Azure dev Spaces](/azure/dev-spaces/) do debugowania i testowania projektu działającego w AKS, możesz przejść do [samouczka Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio) .

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tej nowej funkcji, potrzebne są:

::: moniker range="vs-2017"
- Najnowsza wersja programu [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z *ASP.NET i programowaniem aplikacji sieci Web* .
- [Narzędzia Kubernetes Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), dostępne jako oddzielne pobieranie.
::: moniker-end
::: moniker range="vs-2019"
- [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z *ASP.NET i programowaniem w sieci Web* .
::: moniker-end
- Program [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) został zainstalowany na stacji roboczej deweloperskiej (czyli w przypadku uruchamiania programu Visual Studio), jeśli chcesz skompilować obrazy platformy Docker, Debuguj kontenery platformy Docker działające lokalnie lub Opublikuj w AKS. (Platforma Docker *nie* jest wymagana do kompilowania i debugowania kontenerów platformy Docker w programie AKS przy użyciu Azure dev Spaces).
::: moniker range="vs-2017"
- Jeśli chcesz opublikować AKS z programu Visual Studio (*nie jest* to wymagane do debugowania w AKS przy użyciu Azure dev Spaces):

    1. [Narzędzia do publikowania AKS](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), dostępne jako oddzielne pobieranie.

    1. Klaster usługi Azure Kubernetes. Aby uzyskać więcej informacji, zobacz [Tworzenie klastra AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Upewnij się [, że Nawiąż połączenie z klastrem](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z poziomu stacji roboczej deweloperskiej.

    1. Interfejs wiersza polecenia Helm został zainstalowany na stacji roboczej deweloperskiej. Aby uzyskać więcej informacji, zobacz [Installing Helm](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md).

    1. Helm skonfigurowany dla klastra AKS przy użyciu `helm init` polecenia. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [How to configure Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Utwórz nowy projekt Kubernetes

::: moniker range="vs-2017"

Po zainstalowaniu odpowiednich narzędzi uruchom program Visual Studio i Utwórz nowy projekt. W obszarze **chmura**wybierz pozycję **aplikacja kontenera dla** typu projektu Kubernetes. Wybierz typ projektu i wybierz **OK**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

W oknie uruchamiania programu Visual Studio Wyszukaj pozycję *Kubernetes*i wybierz pozycję **aplikacja kontenera dla Kubernetes**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Podaj nazwę projektu.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Następnie możesz wybrać typ ASP.NET Core aplikacji sieci Web, która ma zostać utworzona. Wybierz pozycję **aplikacja sieci Web**. Zwykle opcja **Włącz obsługę platformy Docker** nie jest wyświetlana w tym oknie dialogowym.  Obsługa platformy Docker jest domyślnie włączona dla aplikacji kontenera dla Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający wybór aplikacji sieci Web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający wybór aplikacji sieci Web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Dodawanie obsługi Kubernetes do istniejącego projektu

Alternatywnie można dodać obsługę Kubernetes do istniejącego projektu aplikacji sieci Web ASP.NET Core. W tym celu kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **obsługę koordynatora kontenerów**.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający element menu Dodaj kontener programu Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający element menu Dodaj kontener programu Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

W oknie dialogowym wybierz pozycję **Kubernetes/Helm** i wybierz **przycisk OK**.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie kontenera programu Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Jakie dane są tworzone przez program Visual Studio

Po utworzeniu nowej **aplikacji kontenera dla projektu Kubernetes** lub dodaniu obsługi usługi Orchestrator kontenera Kubernetes do istniejącego projektu zobaczysz kilka dodatkowych plików w projekcie, które ułatwiają wdrażanie do Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający Eksplorator rozwiązań po dodaniu obsługi koordynatora kontenerów](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający Eksplorator rozwiązań po dodaniu obsługi koordynatora kontenerów](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Dodane pliki to:

- element pliku dockerfile, który umożliwia generowanie obrazu kontenera Docker obsługującego tę aplikację sieci Web. Jak widać, narzędzia programu Visual Studio wykorzystują ten pliku dockerfile podczas debugowania i wdrażania w Kubernetes. Jeśli wolisz pracować bezpośrednio z obrazem platformy Docker, możesz kliknąć prawym przyciskiem myszy pliku dockerfile i wybrać polecenie **Kompiluj obraz platformy Docker**.

   ![Zrzut ekranu przedstawiający opcję tworzenia obrazu platformy Docker](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Wykres Helm i folder *wykresów* . Te pliki YAML tworzą wykres Helm dla aplikacji, którego można użyć do wdrożenia jej w usłudze Kubernetes. Aby uzyskać więcej informacji na temat Helm, zobacz [https://www.helm.sh](https://www.helm.sh) .

- *azds. YAML*. Zawiera ustawienia Azure Dev Spaces, które zapewniają szybkie i iteracyjne środowisko debugowania w usłudze Azure Kubernetes Service. Aby uzyskać więcej informacji, zobacz [dokumentację Azure dev Spaces](/azure/dev-spaces/azure-dev-spaces).

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikowanie w usłudze Azure Kubernetes Service (AKS)

W przypadku wszystkich tych plików można użyć środowiska IDE programu Visual Studio do pisania i debugowania kodu aplikacji, tak jak zawsze. Możesz również użyć [Azure dev Spaces](/azure/dev-spaces/) , aby szybko uruchomić i debugować swój kod działający w klastrze AKS. Aby uzyskać więcej informacji, zapoznaj się z [samouczkiem Azure dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio)

Gdy Twój kod będzie działać zgodnie z oczekiwaniami, możesz publikować bezpośrednio z programu Visual Studio do klastra AKS.

Aby to zrobić, należy najpierw sprawdzić, czy zainstalowano wszystkie elementy, zgodnie z opisem w sekcji [wymagania wstępne](#prerequisites) w obszarze elementu do opublikowania w usłudze AKS, a następnie wykonać wszystkie kroki wiersza polecenia podane w łączach. Następnie skonfiguruj profil publikowania, który publikuje obraz kontenera w Azure Container Registry (ACR). Następnie AKS może ściągnąć obraz kontenera z ACR i wdrożyć go w klastrze.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy *projekt* i wybierz polecenie **Publikuj**.

   ![Zrzut ekranu przedstawiający element menu Publikuj](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Na ekranie **Publikowanie** wybierz **Container Registry** jako element docelowy publikowania i postępuj zgodnie z monitami, aby wybrać rejestr kontenerów. Jeśli nie masz jeszcze rejestru kontenerów, wybierz pozycję **Utwórz nowy Azure Container Registry** , aby utworzyć go z poziomu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Publikowanie kontenera do Azure Container Registry](hosting-web-apps-in-docker.md).

   ![Zrzut ekranu przedstawiający ekran Wybieranie elementu docelowego](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. Wróć do Eksplorator rozwiązań, kliknij prawym przyciskiem myszy *rozwiązanie* , a następnie kliknij pozycję **Publikuj na platformie Azure AKS**.

   ![Zrzut ekranu przedstawiający element menu Publikuj w usłudze Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Wybierz swoją subskrypcję i klaster AKS wraz z utworzonym profilem publikowania ACR. Następnie kliknij przycisk **OK**.

   ![Zrzut ekranu przedstawiający ekran publikowanie na AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Spowoduje to przejście do ekranu **Publikowanie na platformie Azure AKS** .

5. Wybierz łącze **Konfiguruj Helm** , aby zaktualizować wiersz polecenia służący do instalowania wykresów Helm na serwerze.

   ![Zrzut ekranu przedstawiający Konfigurowanie linku Helm](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Aktualizowanie wiersza polecenia jest przydatne, jeśli istnieją niestandardowe argumenty wiersza polecenia, które chcesz określić, takie jak inny kontekst Kubernetes lub nazwa wykresu.

   ![Zrzut ekranu przedstawiający ekran konfiguracja Helm](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Gdy wszystko będzie gotowe do wdrożenia, kliknij przycisk **Publikuj** , aby opublikować aplikację w usłudze AKS.

   ![Zrzut ekranu przedstawiający ekran publikowanie na platformie Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Gratulacje! Możesz teraz używać pełnych możliwości programu Visual Studio do tworzenia aplikacji Kubernetes.

## <a name="remove-kubernetes-support"></a>Usuń pomoc techniczną Kubernetes

1. W **Eksplorator rozwiązań**, w obszarze **właściwości**, Otwórz *launchSettings.jsna*.

1. Usuń kontener sekcji **w Kubernetes**.

1. Jeśli przełączasz się z powrotem do obszaru redagowanie platformy Docker, zaznacz ten projekt w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw jako projekt startowy**.

1. Obowiązkowe Można również usunąć inne artefakty wymienione wcześniej w artykule, takie jak folder **wykresów** i *azds. YAML*.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o programowaniu Kubernetes na platformie Azure, odczytując [dokumentację AKS](/azure/aks).

Dowiedz się więcej na temat Azure Dev Spaces, odczytując [dokumentację Azure dev Spaces](/azure/dev-spaces/)

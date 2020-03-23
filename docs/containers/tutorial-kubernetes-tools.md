---
title: Samouczek narzędzi Kubernetes | Dokumenty firmy Microsoft
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: f5868f97301eba62d16ea68cdaa0c97c8e20edd1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916952"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Wprowadzenie do narzędzi programu Visual Studio Kubernetes

Narzędzia Kubernetes programu Visual Studio ułatwiają opracowywanie konteneryzowanych aplikacji kierowanych na usługi Kubernetes. Visual Studio może automatycznie tworzyć pliki konfiguracji jako kodu potrzebne do obsługi wdrożenia kubernetes, takie jak Dockerfiles i wykresy Helm. Można debugować kod w klastrze usługi Azure Kubernetes (AKS) na żywo przy użyciu usługi Azure Dev Spaces lub publikować bezpośrednio w klastrze AKS z wewnątrz programu Visual Studio.

W tym samouczku opisano korzystanie z programu Visual Studio w celu dodania obsługi kubernetes do projektu i opublikowania w usłudze AKS. Jeśli jesteś przede wszystkim zainteresowany przy użyciu [usługi Azure Dev Spaces](/azure/dev-spaces/) do debugowania i testowania projektu uruchomionego w usłudze AKS, możesz przejść do [samouczka Azure Dev Spaces.](/azure/dev-spaces/get-started-netcore-visualstudio)

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tej nowej funkcji, musisz:

::: moniker range="vs-2017"
- Najnowsza wersja [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z *obciążeniem ASP.NET i tworzenia sieci Web.*
- [Narzędzia Kubernetes dla programu Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), dostępne jako oddzielne pobieranie.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) z *obciążeniem ASP.NET i tworzenia sieci Web.*
::: moniker-end
- [Pulpit platformy Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows) zainstalowany na deweloperskiej stacji roboczej (czyli w miejscu uruchamiania programu Visual Studio), jeśli chcesz tworzyć obrazy platformy Docker, debugować kontenery platformy Docker uruchomione lokalnie lub publikować w u usług AKS. (Platforma Docker *nie* jest wymagana do tworzenia i debugowania kontenerów platformy Docker w usłudze AKS przy użyciu usługi Azure Dev Spaces).
::: moniker range="vs-2017"
- Jeśli chcesz opublikować w usłudze AKS z programu Visual Studio *(nie* jest wymagane do debugowania w usłudze AKS przy użyciu usługi Azure Dev Spaces):

    1. [Narzędzia do publikowania AKS,](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)dostępne jako oddzielne pobieranie.

    1. Klaster usługi Kubernetes platformy Azure. Aby uzyskać więcej informacji, zobacz [Tworzenie klastra AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Pamiętaj, [aby połączyć się](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z klastrem z dewelopera stacji roboczej.

    1. Helm CLI zainstalowany na stacji roboczej rozwoju. Aby uzyskać więcej informacji, zobacz [Instalowanie helmu](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Helm skonfigurowany względem klastra AKS za pomocą `helm init` polecenia. Aby uzyskać więcej informacji na temat tego, jak to zrobić, zobacz [Jak skonfigurować Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Tworzenie nowego projektu kubernetes

::: moniker range="vs-2017"

Po zainstalowaniu odpowiednich narzędzi uruchom program Visual Studio i utwórz nowy projekt. W obszarze **Chmura**wybierz typ projektu **Aplikacji kontenera dla aplikacji Kubernetes.** Wybierz ten typ projektu i wybierz przycisk **OK**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

W oknie startowym programu Visual Studio wyszukaj aplikację *Kubernetes*i wybierz **aplikację kontenera dla aplikacji Kubernetes**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Podaj nazwę projektu.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Następnie można wybrać typ ASP.NET podstawowej aplikacji sieci web do utworzenia. Wybierz **pozycję Aplikacja sieci Web**. Opcja **Włącz obsługę platformy Docker** nie jest wyświetlana w tym oknie dialogowym.  Obsługa platformy Docker jest domyślnie włączona dla aplikacji kontenera dla aplikacji Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający wybór aplikacji sieci Web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający wybór aplikacji sieci Web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Dodawanie obsługi kubernetes do istniejącego projektu

Alternatywnie można dodać obsługę kubernetes do istniejącego projektu aplikacji sieci web ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **obsługę koordynatora kontenerów**.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający pozycję menu Dodaj koordynatora kontenera](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający pozycję menu Dodaj koordynatora kontenera](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

W oknie dialogowym wybierz pozycję **Kubernetes/Helm** i wybierz przycisk **OK**.

![Zrzut ekranu przedstawiający okno dialogowe Dodawanie programu Orchestrator kontenera](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Co program Visual Studio tworzy dla Ciebie

Po utworzeniu nowej aplikacji kontenera dla projektu **Kubernetes** lub dodaniu obsługi koordynatora kontenera Kubernetes do istniejącego projektu, w projekcie zostaną wyświetlonych dodatkowe pliki ułatwiające wdrażanie w usłudze Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający Eksploratora rozwiązań po dodaniu pomocy technicznej programu Container Orchestrator](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Zrzut ekranu przedstawiający Eksploratora rozwiązań po dodaniu pomocy technicznej programu Container Orchestrator](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Dodane pliki to:

- plik Dockerfile, który umożliwia wygenerowanie obrazu kontenera platformy Docker obsługującego tę aplikację sieci web. Jak zobaczysz, narzędzia programu Visual Studio wykorzystuje ten plik dockerfile podczas debugowania i wdrażania w urzędzie Kubernetes. Jeśli wolisz pracować bezpośrednio z obrazem platformy Docker, możesz kliknąć prawym przyciskiem myszy plik dockerfile i wybrać polecenie **Buduj obraz platformy Docker**.

   ![Zrzut ekranu przedstawiający opcję Tworzenie obrazu platformy Docker](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- wykres helm i folder *wykresów.* Te pliki yaml tworzą wykres Helm dla aplikacji, którego można użyć do wdrożenia go w usłudze Kubernetes. Aby uzyskać więcej informacji [https://www.helm.sh](https://www.helm.sh)na temat Helm, zobacz .

- *azds.yaml*. Zawiera ustawienia usługi Azure Dev Spaces, która zapewnia szybkie, iteracyjne środowisko debugowania w usłudze Azure Kubernetes. Aby uzyskać więcej informacji, zobacz [dokumentację usługi Azure Dev Spaces](/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikowanie w usłudze Azure Kubernetes (AKS)

Z wszystkich tych plików w miejscu, można użyć ide programu Visual Studio do pisania i debugowania kodu aplikacji, tak jak zawsze. Można również użyć [usługi Azure Dev Spaces,](/azure/dev-spaces/) aby szybko uruchomić i debugować kod uruchomiony na żywo w klastrze AKS. Aby uzyskać więcej informacji, zapoznaj się z [samouczkiem usługi Azure Dev Spaces](/azure/dev-spaces/get-started-netcore-visualstudio)

Po uruchomieniu kodu w odpowiedni sposób, można opublikować bezpośrednio z programu Visual Studio do klastra AKS.

Aby to zrobić, należy najpierw dokładnie sprawdzić, czy zainstalowano wszystko, zgodnie z opisem w sekcji [Wymagania wstępne](#prerequisites) w obszarze elementu do publikowania w Udosie, i uruchomić za pomocą wszystkich kroków wiersza polecenia podanych w łączach. Następnie skonfiguruj profil publikowania, który publikuje obraz kontenera w usłudze Azure Container Registry (ACR). Następnie usługa AKS może pobierać obraz kontenera z usługi ACR i wdrażać go w klastrze.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy *projekt* i wybierz polecenie **Publikuj**.

   ![Zrzut ekranu przedstawiający pozycję menu Publikowania](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. Na ekranie **Publikowanie** wybierz pozycję **Rejestr kontenerów** jako miejsce docelowe publikowania i postępuj zgodnie z monitami, aby wybrać rejestr kontenerów. Jeśli nie masz jeszcze rejestru kontenerów, wybierz pozycję **Utwórz nowy rejestr kontenerów platformy Azure,** aby utworzyć go z programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Publikowanie kontenera w rejestrze kontenerów platformy Azure](hosting-web-apps-in-docker.md).

   ![Zrzut ekranu przedstawiający wybieranie ekranu docelowego publikowania](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy *rozwiązanie* i kliknij polecenie **Publikuj w usłudze Azure AKS**.

   ![Zrzut ekranu przedstawiający pozycję menu Publikuj w usłudze Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Wybierz subskrypcję i klaster AKS wraz z utworzonym właśnie profilem publikowania usługi ACR. Następnie kliknij przycisk **OK**.

   ![Zrzut ekranu przedstawiający ekran Publikowania w U. AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Spowoduje to przejście do ekranu **Publikowania na platformie Azure AKS.**

5. Wybierz **łącze Konfiguruj helm,** aby zaktualizować wiersz polecenia używany do instalowania wykresów Helm na serwerze.

   ![Zrzut ekranu przedstawiający łącze Konfigurowanie helmu](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Aktualizowanie wiersza polecenia jest przydatne, jeśli istnieją niestandardowe argumenty wiersza polecenia, które chcesz określić, takie jak inny kontekst kubernetes lub nazwa wykresu.

   ![Zrzut ekranu przedstawiający ekran konfigurowania helmu](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Gdy będziesz gotowy do wdrożenia, kliknij przycisk **Publikuj,** aby opublikować aplikację w udręki AKS.

   ![Zrzut ekranu przedstawiający publikowanie na ekranie usługi Azure AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Gratulacje! Teraz można użyć pełnej mocy programu Visual Studio dla wszystkich tworzenia aplikacji Kubernetes.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o rozwoju firmy Kubernetes na platformie Azure, czytając [dokumentację usługi AKS.](/azure/aks)

Dowiedz się więcej o usługach Azure Dev Spaces, czytając [dokumentację usługi Azure Dev Spaces](/azure/dev-spaces/)

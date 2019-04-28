---
title: Samouczka dotyczącego narzędzia Kubernetes | Dokumentacja firmy Microsoft
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 55e18da9eb7e887ca49565725737cfb8c5aa719e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820220"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Rozpoczynanie pracy z usługą Visual Studio Tools rozwiązania Kubernetes

Visual Studio Kubernetes Tools usprawnić tworzenie konteneryzowanych aplikacji przeznaczonych dla platformy Kubernetes. Program Visual Studio może automatycznie tworzyć pliki konfiguracji jako kodu, potrzebne do obsługi platformy Kubernetes, takiego jak wdrożenie plików Dockerfile i Helm wykresów. Debugowanie kodu na żywo za pomocą usługi Azure Dev miejsca do magazynowania klastra Azure Kubernetes Service (AKS) lub opublikować bezpośrednio do klastra usługi AKS z poziomu programu Visual Studio.

W tym samouczku opisano Dodawanie Obsługa klastra Kubernetes do projektu i publikowanie w usłudze AKS za pomocą programu Visual Studio. Jeśli interesuje Cię przede wszystkim za pomocą [miejsca do magazynowania Azure Dev](https://aka.ms/get-azds) do debugowania i przetestować projekt, uruchomiony w usłudze AKS, możesz przejść do tematu [samouczek usługi Azure Dev miejsca do magazynowania](/azure/dev-spaces/get-started-netcore-visualstudio) zamiast tego.

## <a name="prerequisites"></a>Wymagania wstępne

Aby korzystać z tej nowej funkcji, należy:

::: moniker range="vs-2017"
- Najnowszą wersję [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) z *ASP.NET i tworzenie aplikacji internetowych* obciążenia.
- [Narzędzi usługi Kubernetes dla programu Visual Studio](https://aka.ms/get-vsk8stools), która jest dostępna do pobrania osobno.
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z *ASP.NET i tworzenie aplikacji internetowych* obciążenia.
::: moniker-end
- [Docker pulpitu](https://store.docker.com/editions/community/docker-ce-desktop-windows) zainstalowane na deweloperskiej stacji roboczej (oznacza to, gdzie możesz uruchomić program Visual Studio), jeśli chcesz skompilować obrazy Docker, debugowanie kontenerów platformy Docker działa lokalnie, lub opublikować w usłudze AKS. (Docker jest *nie* wymagane do kompilowania i debugowania kontenerów platformy Docker w usłudze AKS za pomocą usługi Azure Dev miejsca do magazynowania.)
::: moniker range="vs-2017"
- Jeśli chcesz opublikować w usłudze AKS za pomocą programu Visual Studio (*nie* wymagane do debugowania w usłudze AKS za pomocą usługi Azure Dev miejsca do magazynowania):

    1. [AKS narzędzia publikowania](https://aka.ms/get-vsk8spublish), która jest dostępna do pobrania osobno.

    1. Klaster Azure Kubernetes Service. Aby uzyskać więcej informacji, zobacz [tworzenia klastra usługi AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster). Pamiętaj, aby [łączenia z klastrem](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) z deweloperskiej stacji roboczej.

    1. Polecenie Helm interfejsu wiersza polecenia, zainstalowane na deweloperskiej stacji roboczej. Aby uzyskać więcej informacji, zobacz [instalowanie narzędzia Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1. Skonfigurowane dla klastra usługi AKS przy użyciu narzędzia Helm `helm init` polecenia. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [sposobu konfigurowania Helm](/azure/aks/kubernetes-helm#configure-helm).
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>Utwórz nowy projekt rozwiązania Kubernetes

::: moniker range="vs-2017"

Po utworzeniu odpowiednich narzędzi, które są zainstalowane, uruchom program Visual Studio i Utwórz nowy projekt. W obszarze **chmury**, wybierz **aplikacji kontenera dla rozwiązania Kubernetes** typ projektu. Wybierz ten typ projektu, a następnie wybierz **OK**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji platformy Kubernetes](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

W oknie uruchamiania programu Visual Studio, wyszukaj *Kubernetes*i wybierz polecenie **aplikacji kontenera dla rozwiązania Kubernetes**.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji platformy Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

Podaj nazwę projektu.

![Zrzut ekranu przedstawiający tworzenie nowego projektu aplikacji platformy Kubernetes](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

Można następnie jakiego typu platforma ASP.NET Core w aplikacji sieci web do utworzenia. Wybierz **aplikacji sieci Web**. Zwykle **włączyć obsługę platformy Docker** opcja nie jest wyświetlana w tym oknie dialogowym.  Obsługę platformy docker jest domyślnie włączone dla aplikacji kontenera dla rozwiązania Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu przedstawiający wybór aplikacji sieci web](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu przedstawiający wybór aplikacji sieci web](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>Dodawanie Obsługa klastra Kubernetes do istniejącego projektu

Alternatywnie można dodać Obsługa klastra Kubernetes do istniejącego projektu aplikacji sieci web platformy ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie **Dodaj** > **obsługi Orkiestratora kontenerów**.

::: moniker range="vs-2017"

![Zrzut ekranu z Dodaj koordynatorem kontenera elementu menu.](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Zrzut ekranu z Dodaj koordynatorem kontenera elementu menu.](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

W oknie dialogowym wybierz **Kubernetes i Helm** i wybierz polecenie **OK**.

![Zrzut ekranu z Dodaj Orkiestrator kontenerów, okno dialogowe](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Program Visual Studio utworzy dla Ciebie

Po utworzeniu nowego **aplikacji kontenera dla rozwiązania Kubernetes** projektu lub dodawania obsługi orkiestratora kontenera Kubernetes do istniejącego projektu, zobaczysz niektóre dodatkowe pliki w projekcie, które ułatwiają wdrażanie platformy Kubernetes.

::: moniker range="vs-2017"

![Zrzut ekranu Eksploratora rozwiązań po dodaniu obsługi Orkiestratora kontenerów](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![Zrzut ekranu Eksploratora rozwiązań po dodaniu obsługi Orkiestratora kontenerów](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

Dodano pliki są:

- Plik Dockerfile, który umożliwia generowanie Docker obrazów kontenera hostowania tej aplikacji sieci web. Jak można zauważyć, narzędzia programu Visual Studio korzysta z tego pliku Dockerfile podczas debugowania i wdrażania w usłudze Kubernetes. Jeśli wolisz pracować bezpośrednio z obrazu platformy Docker, możesz kliknąć prawym przyciskiem myszy w pliku Dockerfile i wybrać **tworzenia obrazu platformy Docker**.

   ![Zrzut ekranu z tworzenia obrazu platformy Docker — opcja](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Wykres Helm i *wykresy* folderu. Te pliki yaml tworzą wykresu Helm w aplikacji, w którym można wdrożyć w usłudze Kubernetes. Aby uzyskać więcej informacji na temat narzędzia Helm, zobacz [ https://www.helm.sh ](https://www.helm.sh).

- *azds.yaml*. Zawiera ustawienia dla usługi Azure Dev spacje, co zapewnia szybkie, iteracyjne środowiska debugowania w usłudze Azure Kubernetes Service. Aby uzyskać więcej informacji, zobacz [dokumentacji usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces).

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publikowanie w usłudze Azure Kubernetes Service (AKS)

Wszystkie te pliki w miejscu można użyć środowiska IDE programu Visual Studio umożliwia pisanie i debugowanie kodu aplikacji, tak samo, jak zawsze mieć. Można również użyć [miejsca do magazynowania Azure Dev](https://aka.ms/get-azds) do szybkiego uruchamiania i debugowania kodu działającej w klastrze AKS. Aby uzyskać więcej informacji, zobacz [samouczek usługi Azure Dev miejsca do magazynowania](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)

Po utworzeniu działanie kodu tak jak chcesz, możesz opublikować bezpośrednio z programu Visual Studio klastra usługi AKS.

Aby to zrobić, należy najpierw upewnić się, że zainstalowano wszystkie elementy zgodnie z opisem w [wymagania wstępne](#prerequisites) w obszarze elementu do publikowania w usłudze AKS, a następnie uruchom wszystkie kroki z wiersza polecenia podanych w łączach. Następnie skonfiguruj profil publikowania, który publikuje obraz kontenera do usługi Azure Container Registry (ACR). Następnie AKS można ściągnąć obraz kontenera z rejestru Azure container Registry i wdrożenia go w klastrze.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy użytkownika *projektu* i wybierz polecenie **Publikuj**.

   ![Zrzut ekranu opublikować element menu](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. W **Publikuj** ekranu, wybierz **Container Registry** jako publikowania docelowy, a następnie postępuj zgodnie z monitami, aby wybrać usługi container registry. Jeśli nie masz jeszcze rejestru kontenerów, wybierz opcję **Tworzenie nowej usługi Azure Container Registry** ją utworzyć za pomocą programu Visual Studio. Aby uzyskać więcej informacji, zobacz [opublikowany kontener w usłudze Azure Container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

   ![Zrzut ekranu przedstawiający wybierz ekran docelowy publikowania](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy użytkownika *rozwiązania* i kliknij przycisk **publikowanie w usłudze Azure AKS**.

   ![Zrzut ekranu z opublikować element menu platformy Azure w usłudze AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. Wybierz subskrypcję i klastra usługi AKS, wraz z rekordu ACR opublikować profil, który został utworzony. Następnie kliknij przycisk **OK**.

   ![Zrzut ekranu z publikowania do ekranu usługi AKS](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   Spowoduje to przejście do **publikowanie w usłudze Azure AKS** ekranu.

5. Wybierz **skonfigurować Helm** łącze, aby zaktualizować wiersza polecenia używane do instalowania wykresów rozwiązania Helm na serwerze.

   ![Zrzut ekranu z skonfigurować narzędzia Helm łącza](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   Aktualizowanie wiersza polecenia jest przydatne, jeśli argumenty niestandardowe wiersza polecenia, które chcesz określić, takich jak Kubernetes kontekstu lub wykresu innej.

   ![Zrzut ekranu narzędzia Helm, skonfigurować ekran](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. Gdy wszystko jest gotowe do wdrożenia, kliknij przycisk **Publikuj** przycisk, aby opublikować aplikację w usłudze AKS.

   ![Zrzut ekranu przedstawiający publikowanie do usługi Azure AKS ekranu](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

Gratulacje! Można teraz używać pełnych możliwości programu Visual Studio wszystkie tworzenia aplikacji platformy Kubernetes.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat programowania w usłudze Kubernetes na platformie Azure, czytając [dokumentację dotyczącą usługi AKS](/azure/aks).

Więcej informacji na temat usługi Azure Dev miejsca do magazynowania, czytając [dokumentacji usługi Azure Dev miejsca do magazynowania](https://aka.ms/get-azds)

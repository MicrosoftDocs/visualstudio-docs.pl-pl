---
title: Używanie Mostka na platformę Kubernetes z programem Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Dowiedz się, jak używać programu Bridge do Kubernetes z programem Visual Studio, aby połączyć komputer deweloperski z klastrem Kubernetes
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 7bbeec2baab018ea770dbee60db507399ebeb745
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860441"
---
# <a name="use-bridge-to-kubernetes"></a>Korzystanie z mostka do Kubernetes

Za pomocą mostka Kubernetes można przekierowywać ruch między klastrem Kubernetes i kodem uruchomionym na komputerze deweloperskim. Ten przewodnik zawiera również skrypt służący do wdrażania dużej przykładowej aplikacji z wieloma mikrousługami w klastrze Kubernetes.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten przewodnik korzysta z [przykładowej aplikacji do udostępniania roweru][bike-sharing-github] do zademonstrowania połączenia komputera deweloperskiego z klastrem Kubernetes. Jeśli masz już uruchomioną aplikację w klastrze Kubernetes, możesz wykonać poniższe kroki i użyć nazw własnych usług.

### <a name="prerequisites"></a>Wymagania wstępne

* Subskrypcja platformy Azure. Jeśli nie masz subskrypcji platformy Azure, możesz utworzyć [bezpłatne konto](https://azure.microsoft.com/free).
* [Zainstalowany interfejs wiersza polecenia platformy Azure][azure-cli].
* [Program Visual Studio 2019][visual-studio] w wersji 16,7 Preview 4 lub nowszej działający w systemie Windows 10 z zainstalowanym obciążeniem *programistycznym platformy Azure* .
* [Zainstalowano rozszerzenie Bridge to Kubernetes][btk-extension].

Ponadto w przypadku aplikacji konsolowych platformy .NET Zainstaluj pakiet NuGet *Microsoft. VisualStudio. Azure. Kubernetes. Tools. targets* .

## <a name="create-a-kubernetes-cluster"></a>Tworzenie klastra Kubernetes

Utwórz klaster AKS w [obsługiwanym regionie][supported-regions]. Poniższe polecenia tworzą grupę zasobów o nazwie Moja *zasobów* i klaster AKS o nazwie *MyAKS*.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>Instalowanie przykładowej aplikacji

Zainstaluj przykładową aplikację w klastrze przy użyciu dostarczonego skryptu. Ten skrypt można uruchomić przy użyciu [Azure Cloud Shell][azure-cloud-shell].

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

Przejdź do przykładowej aplikacji, w której działa klaster, otwierając swój publiczny adres URL, który jest wyświetlany w danych wyjściowych skryptu instalacji.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

W powyższym przykładzie publiczny adres URL to `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` .

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Nawiązywanie połączenia z klastrem i debugowanie usługi

Na komputerze deweloperskim Pobierz i skonfiguruj interfejs wiersza polecenia Kubernetes, aby połączyć się z klastrem Kubernetes przy użyciu polecenia [AZ AKS Get-Credentials][az-aks-get-credentials].

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

W repozytorium [przykładowej aplikacji do udostępniania roweru][bike-sharing-github] w usłudze GitHub Użyj listy rozwijanej na przycisku zielonym **kod** , a następnie wybierz **Otwórz w programie Visual Studio** , aby sklonować repozytorium lokalnie, a następnie otwórz folder w programie Visual Studio. Następnie użyj **plik**  >  **Otwórz projekt** , aby otworzyć projekt **App. csproj** w folderze *Samples/BikeSharingApp/ReservationEngine* .

W projekcie wybierz pozycję **Kubernetes** z listy rozwijanej ustawienia uruchamiania, jak pokazano poniżej.

![Wybierz mostek do Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Kliknij przycisk Start obok pozycji *mostek do Kubernetes*. W oknie dialogowym **Tworzenie profilu dla mostka do Kubernetes** :

* Wybierz subskrypcję.
* Wybierz pozycję *MyAKS* dla klastra.
* Wybierz pozycję *bikeapp* dla przestrzeni nazw.
* Wybierz pozycję *reservationengine* , aby przekierować usługę.
* Wybierz pozycję *aplikacja* dla profilu uruchamiania.
* Wybierz `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` adres URL, na który ma zostać uruchomiona przeglądarka.

![Wybierz mostek do klastra Kubernetes](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> Można przekierować tylko usługi, które mają pojedynczy pod.

Zdecyduj, czy chcesz uruchomić odizolowany, co oznacza, że zmiany nie wpłyną na inne osoby korzystające z danego klastra. Ten tryb izolacji jest realizowany przez kierowanie żądań do kopii każdej usługi, której to dotyczy, ale przez kierowanie całego ruchu. Dokładniejsze wyjaśnienie tego, jak to zrobić, można znaleźć na drodze [działania programu Bridge do Kubernetes][btk-overview-routing].

Kliknij przycisk **Zapisz i Rozpocznij debugowanie**.

Cały ruch w klastrze Kubernetes jest przekierowywany dla usługi *reservationengine* do wersji aplikacji działającej na komputerze deweloperskim. Mostek do Kubernetes kieruje również cały ruch wychodzący z aplikacji z powrotem do klastra Kubernetes.

> [!NOTE]
> Zostanie wyświetlony monit o zezwolenie programowi *endpointmanager* na uruchomienie podniesienia uprawnień i zmodyfikowanie pliku Hosts.

Komputer deweloperski jest połączony, gdy zostanie wyświetlony pasek stanu połączony z `reservationengine` usługą.

![Komputer deweloperski jest podłączony](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Przy kolejnych uruchomieniach nie zostanie wyświetlony monit z oknem dialogowym **Tworzenie profilu dla mostka do Kubernetes** . Te ustawienia są aktualizowane w **debugowaniu** we właściwościach projektu.

Po nawiązaniu połączenia z komputerem deweloperskim ruch zaczyna się przekierować do komputera deweloperskiego w przypadku zastępowanej usługi.

## <a name="set-a-break-point"></a>Ustaw punkt przerwania

Otwórz [BikesHelper.cs][bikeshelper-cs-breakpoint] i kliknij gdziekolwiek w wierszu 26, aby umieścić w nim kursor. Ustaw punkt przerwania, naciskając klawisz *F9* lub wybierając pozycję **Debuguj**  >  **przełączenie punktu przerwania**.

Przejdź do przykładowej aplikacji, otwierając publiczny adres URL. Wybierz pozycję **Aurelia Briggs (Customer)** jako użytkownik, a następnie wybierz rower do wynajęcia. Wybierz pozycję **Wynajem roweru**. Wróć do programu Visual Studio i obserwuj wiersz 26. Ustawiony punkt przerwania został wstrzymany usługi w wierszu 26. Aby wznowić działanie usługi, naciśnij klawisz **F5** lub kliknij pozycję **Debuguj**  >  **Kontynuuj**. Wróć do przeglądarki i sprawdź, czy na stronie zostały wydzierżawione rowery.

Usuń punkt przerwania, umieszczając kursor w wierszu 26 w `BikesHelper.cs` i naciskając klawisz **F9**.

> [!NOTE]
> Domyślnie Zatrzymywanie zadania debugowania powoduje także odłączenie komputera deweloperskiego od klastra Kubernetes. Możesz zmienić to zachowanie, zmieniając opcję **Rozłącz po debugowaniu** na `false` w sekcji **narzędzia debugowania Kubernetes** opcji debugowanie. Po zaktualizowaniu tego ustawienia komputer programistyczny pozostanie połączony, gdy zatrzymasz i zaczniesz debugowanie. Aby odłączyć komputer deweloperski od klastra, kliknij przycisk **Rozłącz** na pasku narzędzi.

## <a name="additional-configuration"></a>Dodatkowa konfiguracja

Mostek do Kubernetes może obsługiwać ruch routingu i replikować zmienne środowiskowe bez żadnej dodatkowej konfiguracji. Jeśli musisz pobrać wszystkie pliki, które są zainstalowane do kontenera w klastrze Kubernetes, na przykład plik ConfigMap, możesz utworzyć, `KubernetesLocalProcessConfig.yaml` Aby pobrać te pliki na komputer deweloperski. Aby uzyskać więcej informacji, zobacz [Używanie KubernetesLocalProcessConfig. YAML w celu uzyskania dodatkowej konfiguracji programu dla mostka do Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Korzystanie z funkcji rejestrowania i diagnostyki

Dzienniki diagnostyczne znajdują się w `Bridge to Kubernetes` katalogu *tymczasowym* komputera deweloperskiego. 

## <a name="remove-the-sample-application-from-your-cluster"></a>Usuwanie przykładowej aplikacji z klastra

Użyj dostarczonego skryptu, aby usunąć przykładową aplikację z klastra.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak działa mostek Kubernetes.

> [!div class="nextstepaction"]
> [Jak działa Mostek na platformę Kubernetes](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
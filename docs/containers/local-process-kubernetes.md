---
title: Używanie procesu lokalnego w usłudze Kubernetes z programem Visual Studio (wersja zapoznawcza)
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Dowiedz się, jak używać procesu lokalnego z programem Kubernetes z programem Visual Studio, aby połączyć komputer deweloperski z klastrem Kubernetes
keywords: Proces lokalny z Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
ms.openlocfilehash: b057670f60554a066356ad34525f0276d8dc826c
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454324"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Korzystanie z procesu lokalnego z Kubernetes (wersja zapoznawcza)

Proces lokalny z programem Kubernetes umożliwia uruchamianie i debugowanie kodu na komputerze deweloperskim, przy jednoczesnym połączeniu z klastrem Kubernetes z pozostałą częścią aplikacji lub usług. Na przykład jeśli masz dużą architekturę mikrousług z wieloma zależnymi usługami i bazami danych, replikowanie tych zależności na komputerze deweloperskim może być trudne. Ponadto Kompilowanie i wdrażanie kodu w klastrze Kubernetes dla każdej zmiany kodu podczas programowania w pętli wewnętrznej może być powolne, czasochłonne i trudne do użycia z debugerem.

Proces lokalny z Kubernetes pozwala uniknąć konieczności kompilowania i wdrażania kodu w klastrze przez utworzenie połączenia bezpośrednio między komputerem deweloperskim i klastrem. Połączenie komputera deweloperskiego z klastrem podczas debugowania umożliwia szybkie testowanie i opracowywanie usługi w kontekście pełnej aplikacji bez konieczności tworzenia żadnej konfiguracji platformy Docker lub Kubernetes.

Proces lokalny z Kubernetes przekierowuje ruch między podłączonym klastrem Kubernetes i komputerem deweloperskim. To przekierowywanie ruchu umożliwia kod na komputerze deweloperskim i usługach uruchomionych w klastrze Kubernetes, aby komunikować się tak, jakby znajdowały się w tym samym klastrze Kubernetes. Proces lokalny z usługą Kubernetes umożliwia także replikować zmienne środowiskowe i zainstalowane woluminy dostępne dla zasobników w klastrze Kubernetes na komputerze deweloperskim. Zapewnianie dostępu do zmiennych środowiskowych i zainstalowanych woluminów na komputerze deweloperskim pozwala szybko korzystać z kodu bez konieczności ręcznego replikowania tych zależności.

W tym przewodniku dowiesz się, jak używać procesu lokalnego z usługą Kubernetes, aby przekierowywać ruch między klastrem Kubernetes i kodem uruchomionym na komputerze deweloperskim. Ten przewodnik zawiera również skrypt służący do wdrażania dużej przykładowej aplikacji z wieloma mikrousługami w klastrze Kubernetes.

> [!IMPORTANT]
> Ta funkcja jest obecnie w wersji zapoznawczej. Wersje zapoznawcze są udostępniane pod warunkiem udzielenia zgody na [dodatkowe warunki użytkowania][preview-terms]. Niektóre cechy funkcji mogą ulec zmianie, zanim stanie się ona ogólnie dostępna.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Ten przewodnik korzysta z [przykładowej aplikacji do udostępniania roweru][bike-sharing-github] do zademonstrowania połączenia komputera deweloperskiego z klastrem Kubernetes. Jeśli masz już uruchomioną aplikację w klastrze Kubernetes, możesz wykonać poniższe kroki i użyć nazw własnych usług.

### <a name="prerequisites"></a>Wymagania wstępne

* Subskrypcja platformy Azure. Jeśli nie masz subskrypcji platformy Azure, możesz utworzyć [bezpłatne konto](https://azure.microsoft.com/free).
* [Zainstalowany interfejs wiersza polecenia platformy Azure][azure-cli].
* [Program Visual Studio 2019][visual-studio] w wersji 16,7 Preview 4 lub nowszej działający w systemie Windows 10 z zainstalowanym obciążeniem *programistycznym platformy Azure* .
* [Zainstalowano proces lokalny dla rozszerzenia Kubernetes][lpk-extension].

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

Przejdź do przykładowej aplikacji, w której działa klaster, otwierając swój publiczny adres URL, który jest wyświetlany w danych wyjściowych skryptu instalacji.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

Otwórz aplikację *mindaro/Samples/BikeSharingApp/ReservationEngine/App. csproj* z [przykładowej aplikacji do udostępniania roweru][bike-sharing-github] w programie Visual Studio.

W projekcie wybierz pozycję *proces lokalny z Kubernetes* na liście rozwijanej ustawienia uruchamiania, jak pokazano poniżej.

![Wybieranie procesu lokalnego z Kubernetes](media/local-process-kubernetes/choose-local-process.png)

Kliknij przycisk Start obok pozycji *proces lokalny z Kubernetes*. W oknie dialogowym *proces lokalny z Kubernetes* :

* Wybierz subskrypcję.
* Wybierz pozycję *MyAKS* dla klastra.
* Wybierz pozycję *dev* dla obszaru nazw.
* Wybierz pozycję *reservationengine* , aby przekierować usługę.
* Wybierz pozycję *aplikacja* dla profilu uruchamiania.
* Wybierz `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` adres URL, na który ma zostać uruchomiona przeglądarka.

![Wybieranie procesu lokalnego z klastrem Kubernetes](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> Można przekierować tylko usługi, które mają pojedynczy pod.

Kliknij przycisk *Zapisz i Rozpocznij debugowanie*.

Cały ruch w klastrze Kubernetes jest przekierowywany dla usługi *reservationengine* do wersji aplikacji działającej na komputerze deweloperskim. Proces lokalny z usługą Kubernetes kieruje również cały ruch wychodzący z aplikacji z powrotem do klastra Kubernetes.

> [!NOTE]
> Zostanie wyświetlony monit o zezwolenie *KubernetesDNSManager* na uruchomienie podniesienia uprawnień i zmodyfikowanie pliku Hosts.

Komputer deweloperski jest połączony, gdy zostanie wyświetlony pasek stanu połączony z usługą *reservationengine* .

![Komputer deweloperski jest podłączony](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> W przypadku uruchomienia subesquent nie zostanie wyświetlony monit z *procesem lokalnym przy użyciu* okna dialogowego Kubernetes. Te ustawienia są aktualizowane w okienku *debugowanie* we właściwościach projektu.

Po nawiązaniu połączenia z komputerem deweloperskim ruch zaczyna się przekierować do komputera deweloperskiego w przypadku zastępowanej usługi.

## <a name="set-a-break-point"></a>Ustaw punkt przerwania

Otwórz [BikesHelper.cs][bikeshelper-cs-breakpoint] i kliknij gdziekolwiek w wierszu 26, aby umieścić w nim kursor. Ustaw punkt przerwania, naciskając klawisz *F9* lub klikając polecenie *Debuguj* , a następnie *Przełącz punkt przerwania*.

Przejdź do przykładowej aplikacji, otwierając publiczny adres URL. Wybierz pozycję *Aurelia Briggs (Customer)* jako użytkownik, a następnie wybierz rower do wynajęcia. Kliknij pozycję *Wynajem roweru*. Wróć do programu Visual Studio i obserwuj wiersz 26. Ustawiony punkt przerwania został wstrzymany usługi w wierszu 26. Aby wznowić działanie usługi, naciśnij klawisz *F5* lub kliknij pozycję *Debuguj* i *Kontynuuj*. Wróć do przeglądarki i sprawdź, czy na stronie zostały wydzierżawione rowery.

Usuń punkt przerwania, umieszczając kursor w wierszu 26 w `BikesHelper.cs` i naciskając klawisz *F9*.

> [!NOTE]
> Domyślnie Zatrzymywanie zadania debugowania powoduje także odłączenie komputera deweloperskiego od klastra Kubernetes. Możesz zmienić to zachowanie, zmieniając opcję *Rozłącz po debugowaniu* na *false* w sekcji *narzędzia debugowania Kubernetes* opcji debugowanie. Po zaktualizowaniu tego ustawienia komputer programistyczny pozostanie połączony, gdy zatrzymasz i zaczniesz debugowanie. Aby odłączyć komputer deweloperski od klastra, kliknij przycisk *Rozłącz* na pasku narzędzi.
>
> Jeśli program Visual Studio nagle kończy połączenie z klastrem lub kończy działanie, przekierowanie usługi może nie zostać przywrócone do oryginalnego stanu przed połączeniem z procesem lokalnym za pomocą usługi Kubernetes. Aby rozwiązać ten problem, zobacz [Przewodnik rozwiązywania problemów][troubleshooting].

## <a name="using-logging-and-diagnostics"></a>Korzystanie z funkcji rejestrowania i diagnostyki

Dzienniki diagnostyczne znajdują się w `Azure Dev Spaces` katalogu [ *tymczasowym* komputera deweloperskiego][azds-tmp-dir].

## <a name="remove-the-sample-application-from-your-cluster"></a>Usuwanie przykładowej aplikacji z klastra

Użyj dostarczonego skryptu, aby usunąć przykładową aplikację z klastra.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak działa Kubernetes procesów lokalnych.

> [!div class="nextstepaction"]
> [Jak działa proces lokalny z usługą Kubernetes](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
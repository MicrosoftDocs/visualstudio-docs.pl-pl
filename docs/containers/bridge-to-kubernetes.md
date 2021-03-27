---
title: Używanie Mostka na platformę Kubernetes z programem Visual Studio
titleSuffix: ''
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: quickstart
description: Dowiedz się, jak używać programu Bridge do Kubernetes z programem Visual Studio, aby połączyć komputer deweloperski z klastrem Kubernetes
keywords: Bridge to Kubernetes, Azure Dev Spaces, dev Spaces, Docker, Kubernetes, Azure, Containers
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: fdcf31d062fe2be72709979f0892e6a7f535024a
ms.sourcegitcommit: 2049ec99f1439ec91d002853226934b067b1ee70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2021
ms.locfileid: "105635049"
---
# <a name="use-bridge-to-kubernetes"></a>Korzystanie z mostka do Kubernetes

Za pomocą mostka Kubernetes można przekierowywać ruch między klastrem Kubernetes i kodem uruchomionym na komputerze deweloperskim. Ten przewodnik zawiera również skrypt służący do wdrażania dużej przykładowej aplikacji z wieloma mikrousługami w klastrze Kubernetes.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Ten przewodnik zawiera [przykładową aplikację do wykonania aplikacji][todo-app-github] do zademonstrowania połączenia komputera deweloperskiego z klastrem Kubernetes. Jeśli masz już uruchomioną aplikację w klastrze Kubernetes, możesz wykonać poniższe kroki i użyć nazw własnych usług.

Ten przykład ilustruje sposób, w jaki mostek Kubernetes może służyć do tworzenia mikrousług dla prostej aplikacji do wykonania w dowolnym klastrze Kubernetes. Ten przykład przy użyciu programu Visual Studio został dostosowany z kodu dostarczonego przez [TodoMVC](http://todomvc.com). Te kroki powinny współpracować z dowolnym klastrem Kubernetes.

Przykład aplikacji do zrobienia składa się z frontonu i zaplecza, który zapewnia magazyn trwały. Ten rozszerzony przykład dodaje składnik statystyki i dzieli aplikację na kilka mikrousług, w tym:

- Fronton wywołuje interfejs API bazy danych w celu utrwalenia i zaktualizowania elementów do wykonania.
- Usługa API Database korzysta z bazy danych Mongo, aby zachować elementy do wykonania.
- Fronton zapisuje zdarzenia dodawania, kończenia i usuwania do kolejki RabbitMQ;
- Pracownik przetwarzający dane statystyczne odbiera zdarzenia z kolejki RabbitMQ i aktualizuje pamięć podręczną Redis;
- Interfejs API statystyk udostępnia buforowane statystyki dla frontonu do wyświetlenia.

W ogóle ta rozszerzona aplikacja do zrobienia składa się z sześciu powiązanych składników.

### <a name="prerequisites"></a>Wymagania wstępne

- klaster Kubernetes
- [Program Visual Studio 2019][visual-studio] w wersji 16,7 Preview 4 lub nowszej działający w systemie Windows 10.
- [Zainstalowano rozszerzenie Bridge to Kubernetes][btk-extension].

## <a name="check-the-cluster"></a>Sprawdź klaster

Otwórz wiersz polecenia i sprawdź, czy polecenia kubectl jest zainstalowany i na ścieżce, klaster, który ma być używany, jest dostępny i gotowy, a następnie ustaw kontekst dla tego klastra.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

gdzie {Context-Name} jest nazwą kontekstu klastra, którego chcesz użyć dla przykładu do wykonania aplikacji.

## <a name="deploy-the-application"></a>Wdrażanie aplikacji

Sklonuj [repozytorium mindaro](https://github.com/Microsoft/mindaro) i Otwórz okno poleceń z bieżącym folderem roboczym do *przykładów/do zrobienia — aplikacji*.

Utwórz przestrzeń nazw dla przykładu.

```cmd
kubectl create namespace todo-app
```

Następnie Zastosuj manifest wdrożenia:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Jest to proste wdrożenie, które uwidacznia fronton przy użyciu usługi typu `LoadBalancer` . Poczekaj, aż wszystkie zasobniki będą działać i że zewnętrzny adres IP `frontend` usługi stanie się dostępny.

Jeśli testujesz się za pomocą MiniKube, musisz użyć, `minikube tunnel` Aby rozwiązać zewnętrzny adres IP. Jeśli używasz usługi AKS lub innego dostawcy Kubernetes opartego na chmurze, zewnętrzny adres IP jest przypisywany automatycznie. Użyj poniższego polecenia, aby monitorować `frontend` usługę, aby czekać, aż zostanie uruchomiona:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Przejdź do aplikacji przy użyciu zewnętrznego adresu IP i portu lokalnego (pierwszy numer w kolumnie PORT (S).

```
http://{external-ip}:{local-port}
```

Przetestuj uruchomioną aplikację w przeglądarce. Po dodaniu, zakończeniu i usunięciu elementów do wykonania należy zauważyć, że strona statystyki jest aktualizowana o oczekiwanych metrykach.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Nawiązywanie połączenia z klastrem i debugowanie usługi

Otwórz *samples\todo-app\database-api\database-API.csproj* w programie Visual Studio. W projekcie wybierz pozycję **Kubernetes** z listy rozwijanej ustawienia uruchamiania, jak pokazano poniżej.

![Wybierz mostek do Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Kliknij przycisk Start obok pozycji *mostek do Kubernetes*. W oknie dialogowym **Tworzenie profilu dla mostka do Kubernetes** :

- Wybierz nazwę klastra.
- Wybierz pozycję do *zrobienia — aplikacja* dla przestrzeni nazw.
- Wybierz opcję *Database-API* dla usługi do przekierowania.
- Wybierz ten sam adres URL, który został wcześniej użyty do uruchomienia przeglądarki, http://{External-IP}: {Local-Port}

![Wybierz mostek do klastra Kubernetes](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Zdecyduj, czy chcesz uruchomić odizolowany, co oznacza, że zmiany nie wpłyną na inne osoby korzystające z danego klastra. Ten tryb izolacji jest realizowany przez kierowanie żądań do kopii każdej usługi, której to dotyczy, ale przez kierowanie całego ruchu. Dokładniejsze wyjaśnienie tego, jak to zrobić, można znaleźć na drodze [działania programu Bridge do Kubernetes][btk-overview-routing].

Kliknij przycisk **OK**. Cały ruch w klastrze Kubernetes jest przekierowywany dla usługi *API Database* do wersji aplikacji działającej na komputerze deweloperskim. Mostek do Kubernetes kieruje również cały ruch wychodzący z aplikacji z powrotem do klastra Kubernetes.

> [!NOTE]
> Zostanie wyświetlony monit o zezwolenie programowi *endpointmanager* na uruchomienie podniesienia uprawnień i zmodyfikowanie pliku Hosts.

Komputer deweloperski jest połączony, gdy zostanie wyświetlony pasek stanu połączony z `database-api` usługą.

![Komputer deweloperski jest podłączony](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Przy kolejnych uruchomieniach nie zostanie wyświetlony monit z oknem dialogowym **Tworzenie profilu dla mostka do Kubernetes** . Te ustawienia są aktualizowane w **debugowaniu** we właściwościach projektu.

Po nawiązaniu połączenia z komputerem deweloperskim ruch zaczyna się przekierować do komputera deweloperskiego w przypadku zastępowanej usługi.

> [!NOTE]
> Aby później edytować profil debugowania, na przykład w celu przetestowania z inną usługą Kubernetes wybierz polecenie **Debuguj**  >  **właściwości debugowania**, a następnie kliknij przycisk **Zmień** .

## <a name="set-a-break-point"></a>Ustaw punkt przerwania

Otwórz MongoHelper. cs i kliknij w dowolnym miejscu w wierszu 68 w metodzie ontask, aby umieścić w niej kursor. Ustaw punkt przerwania, naciskając klawisz *F9* lub wybierając pozycję **Debuguj**  >  **przełączenie punktu przerwania**.

Przejdź do przykładowej aplikacji, otwierając publiczny adres URL (zewnętrzny adres IP dla usługi frontonu). Aby wznowić działanie usługi, naciśnij klawisz **F5** lub kliknij pozycję **Debuguj**  >  **Kontynuuj**.

Usuń punkt przerwania, umieszczając kursor w wierszu z punktem przerwania i naciskając klawisz **F9**.

> [!NOTE]
> Domyślnie Zatrzymywanie zadania debugowania powoduje także odłączenie komputera deweloperskiego od klastra Kubernetes. Możesz zmienić to zachowanie, zmieniając opcję **Rozłącz po debugowaniu** na `false` w sekcji **narzędzia debugowania Kubernetes** w   >  oknie dialogowym **Opcje** narzędzi. Po zaktualizowaniu tego ustawienia komputer programistyczny pozostanie połączony, gdy zatrzymasz i zaczniesz debugowanie. Aby odłączyć komputer deweloperski od klastra, kliknij przycisk **Rozłącz** na pasku narzędzi.
>
>![Zrzut ekranu przedstawiający opcje debugowania Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Dodatkowa konfiguracja

Mostek do Kubernetes może obsługiwać ruch routingu i replikować zmienne środowiskowe bez żadnej dodatkowej konfiguracji. Jeśli musisz pobrać wszystkie pliki, które są zainstalowane do kontenera w klastrze Kubernetes, na przykład plik ConfigMap, możesz utworzyć, `KubernetesLocalProcessConfig.yaml` Aby pobrać te pliki na komputer deweloperski. Aby uzyskać więcej informacji, zobacz [Używanie KubernetesLocalProcessConfig. YAML w celu uzyskania dodatkowej konfiguracji programu dla mostka do Kubernetes][kubernetesLocalProcessConfig-yaml].

## <a name="using-logging-and-diagnostics"></a>Korzystanie z funkcji rejestrowania i diagnostyki

Dzienniki diagnostyczne znajdują się w `Bridge to Kubernetes` katalogu *tymczasowym* komputera deweloperskiego.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, jak działa mostek Kubernetes.

> [!div class="nextstepaction"]
> [Jak działa Mostek na platformę Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
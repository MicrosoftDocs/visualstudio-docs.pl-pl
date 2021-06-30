---
title: 'Samouczek: łączenie maszyn programistów z Bridge to Kubernetes'
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: Połącz komputer deweloperska z klastrem Kubernetes za pomocą Bridge to Kubernetes z Visual Studio.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, kontenery
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046121"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>Samouczek: używanie Bridge to Kubernetes do łączenia klastrów i komputerów programistów

W tym samouczku dowiesz się, jak za pomocą usługi Bridge to Kubernetes przekierowywać ruch między klastrem Kubernetes i kodem uruchomionym na komputerze dewelopera. 

Ten przewodnik zawiera również skrypt do wdrażania dużej przykładowej aplikacji z wieloma mikrousługami w klastrze Kubernetes.

Dowiedz się więcej Bridge to Kubernetes artykule How Bridge to Kubernetes works (Jak [Bridge to Kubernetes działa).](overview-bridge-to-kubernetes.md)

## <a name="prerequisites"></a>Wymagania wstępne

- Klaster Kubernetes
- [Visual Studio 2019][visual-studio] 16.7 (wersja zapoznawcza 4) lub nowsza uruchomiona na Windows 10.
- [Bridge to Kubernetes zainstalowane rozszerzenie][btk-extension]

## <a name="about-the-data"></a>Informacje o danych

W tym samouczku Bridge to Kubernetes tworzenie wersji mikrousług prostej przykładowej aplikacji TODO w dowolnym klastrze Kubernetes. Ta [przykładowa aplikacja TODO][todo-app-github]korzystająca z Visual Studio została dostosowana z kodu dostarczonego przez [todoMVC.](http://todomvc.com) 

 Te kroki powinny działać z dowolnym klastrem Kubernetes. Dlatego jeśli masz już własną aplikację uruchamianą w klastrze Kubernetes, nadal możesz wykonać poniższe kroki i użyć nazw własnych usług.

Przykład aplikacji TODO składa się z frontonu i zaplecza, które zapewnia magazyn trwały. Ten rozszerzony przykład dodaje składnik statystyk i dzieli aplikację na wiele mikrousług, a w szczególności:

- Frontend wywołuje interfejs database-api w celu utrwalania i aktualizowania elementów TODO;
- Usługa database-api opiera się na bazie danych Mongo w celu utrwalania elementów TODO;
- Frontend zapisuje zdarzenia w kolejce RabbitMQ, a następnie je kończy i usuwa.
- Proces roboczy statystyk odbiera zdarzenia z kolejki RabbitMQ i aktualizuje pamięć podręczną Redis Cache.
- Interfejs API statystyk uwidacznia buforowane statystyki dla frontonu do pokazania.

W ogóle ta rozszerzona aplikacja TODO składa się z sześciu wzajemnie powiązanych składników.


## <a name="check-the-cluster"></a>Sprawdzanie klastra

Otwórz wiersz polecenia i sprawdź, czy klaster jest zainstalowany, a w ścieżce klaster, którego chcesz użyć, jest dostępny i gotowy, a następnie ustaw kontekst `kubectl` na ten klaster.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

gdzie {nazwa-kontekstu} to nazwa kontekstu dla klastra, którego chcesz użyć dla przykładu todo-app.

## <a name="deploy-the-application"></a>Wdrażanie aplikacji

[Sklonuj repo mindaro](https://github.com/Microsoft/mindaro) i otwórz okno polecenia z bieżącym folderem pracy do *folderu samples/todo-app.*

Utwórz przestrzeń nazw dla przykładu.

```cmd
kubectl create namespace todo-app
```

Następnie zastosuj manifest wdrożenia:

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

Jest to proste wdrożenie, które uwidacznia fronton przy użyciu usługi typu `LoadBalancer` . Poczekaj, aż wszystkie zasobniki będą uruchomione, a zewnętrzny adres IP `frontend` usługi stanie się dostępny.

W przypadku testowania za pomocą rozwiązania MiniKube należy użyć metody w celu `minikube tunnel` rozpoznania zewnętrznego adresu IP. Jeśli używasz usługi AKS lub innego dostawcy Kubernetes opartego na chmurze, zewnętrzny adres IP jest przypisywany automatycznie. Użyj następującego polecenia, aby monitorować usługę w celu oczekiwania na `frontend` jej uruchomienie:

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

Przejdź do aplikacji przy użyciu zewnętrznego adresu IP i portu lokalnego (pierwszy numer w kolumnie PORT(S).

```
http://{external-ip}:{local-port}
```

Przetestuj uruchamianą aplikację w przeglądarce. Podczas dodawania, ukończenia i usuwania elementów todo zwróć uwagę, że strona statystyk jest aktualizowana o oczekiwane metryki.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>Nawiązywanie połączenia z klastrem i debugowanie usługi

Otwórz *folder samples\todo-app\database-api\database-api.csproj* w Visual Studio. W projekcie wybierz pozycję **Bridge to Kubernetes** z listy rozwijanej ustawień uruchamiania, jak pokazano poniżej.

![Wybierz Bridge to Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

Kliknij przycisk Start obok *przycisku Bridge to Kubernetes*. W **oknie dialogowym Tworzenie profilu Bridge to Kubernetes** aplikacji:

- Wybierz nazwę klastra.
- Wybierz *pozycję todo-app* dla przestrzeni nazw.
- Wybierz *pozycję database-api,* aby przekierowywać usługę.
- Wybierz ten sam adres URL, który był wcześniej używany do uruchamiania przeglądarki, http://{external-ip}:{local-port}

![Wybieranie Bridge to Kubernetes klastra](media/bridge-to-kubernetes/configure-bridge-debugging.png)

Wybierz, czy chcesz uruchamiać odizolowane klastry, co oznacza, że zmiany nie będą mieć wpływu na inne osoby używające klastra. Ten tryb izolacji jest osiągany przez kierowanie żądań do kopii każdej objętej usługi, ale kierowanie całego pozostałego ruchu normalnie. Więcej informacji na temat tego, jak to zrobić, można znaleźć na stronie How Bridge to Kubernetes Works (Jak [działa Bridge to Kubernetes).][btk-overview-routing]

Kliknij przycisk **OK**. Cały ruch w klastrze Kubernetes jest przekierowywany dla usługi *database-api* do wersji aplikacji uruchomionej na komputerze dewelopera. Bridge to Kubernetes również kieruje cały ruch wychodzący z aplikacji z powrotem do klastra Kubernetes.

> [!NOTE]
> Zostanie wyświetlony monit o umożliwienie programowi *EndpointManager* uruchamiania z podwyższonym poziomem uprawnień i modyfikowania pliku hosts.

Komputer dewelopera jest połączony, gdy na pasku stanu jest widać, że masz połączenie z `database-api` usługą.

![Połączony komputer dewelopera](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> Podczas kolejnych uruchomień nie będzie wyświetlany monit o utworzenie profilu dla **Bridge to Kubernetes** uruchomieniowego. Te ustawienia są aktualizowane we **właściwościach projektu Debug** (Debugowanie).

Po podłączeniu komputera dewelopera ruch rozpoczyna przekierowywanie do komputera dewelopera dla wymienianej usługi.

> [!NOTE]
> Aby później edytować profil debugowania, na przykład jeśli chcesz przetestować z inną usługą Kubernetes, wybierz pozycję  >  **Debuguj** właściwości debugowania i kliknij **przycisk** Zmień.

## <a name="set-a-break-point"></a>Ustawianie punktu przerwania

Otwórz pozycję MongoHelper.cs i kliknij gdzieś w wierszu 68 metody CreateTask, aby umieścić tam kursor. Ustaw punkt przerwania, naciskając klawisz *F9* lub wybierając **pozycję**  >  **Debuguj przełącz punkt przerwania.**

Przejdź do przykładowej aplikacji, otwierając publiczny adres URL (zewnętrzny adres IP dla usługi frontendu). Aby wznowić działanie usługi, naciśnij **klawisz F5** lub kliknij pozycję **Kontynuuj**  >  **debugowanie.**

Usuń punkt przerwania, umieszczając kursor w wierszu z punktem przerwania i naciskając **klawisz F9**.

> [!NOTE]
> Domyślnie zatrzymanie zadania debugowania odłącza również komputer dewelopera od klastra Kubernetes. To zachowanie można zmienić, zmieniając pole **Rozłącz** po debugowaniu na w sekcji Narzędzia debugowania `false` **Kubernetes** okna **dialogowego**  >  **Opcje** narzędzi. Po zaktualizowaniu tego ustawienia komputer dewelopera pozostanie połączony po zatrzymaniu i rozpoczęciu debugowania. Aby odłączyć komputer dewelopera od klastra, kliknij przycisk **Rozłącz** na pasku narzędzi.
>
>![Zrzut ekranu przedstawiający opcje debugowania rozwiązania Kubernetes](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>Dodatkowa konfiguracja

Bridge to Kubernetes może obsługiwać ruch routingu i replikowanie zmiennych środowiskowych bez żadnej dodatkowej konfiguracji. Jeśli musisz pobrać pliki zainstalowane w kontenerze w klastrze Kubernetes, takie jak plik ConfigMap, możesz utworzyć plik , aby pobrać te pliki na `KubernetesLocalProcessConfig.yaml` komputer dewelopera. Aby uzyskać więcej informacji, zobacz [Using KubernetesLocalProcessConfig.yaml (Używanie pliku KubernetesLocalProcessConfig.yaml),][kubernetesLocalProcessConfig-yaml]aby uzyskać dodatkową konfigurację za pomocą pliku Bridge to Kubernetes .

## <a name="using-logging-and-diagnostics"></a>Korzystanie z rejestrowania i diagnostyki

Dzienniki diagnostyczne można znaleźć w katalogu w katalogu `Bridge to Kubernetes` *TEMP* komputera dewelopera.

## <a name="next-steps"></a>Następne kroki

Dowiedz się, Bridge to Kubernetes działa.

> [!div class="nextstepaction"]
> [Jak działa Mostek na platformę Kubernetes](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation

---
title: Jak działa Mostek na platformę Kubernetes
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Opis procesów używania Bridge to Kubernetes do łączenia komputera dewelopera z klastrem Kubernetes
keywords: Bridge to Kubernetes, Docker, Kubernetes, Azure, kontenery
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: 838589e0dd81232de25b88989d621a07fb22f972
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043058"
---
# <a name="how-bridge-to-kubernetes-works"></a>Jak działa Mostek na platformę Kubernetes

Bridge to Kubernetes umożliwia uruchamianie i debugowanie kodu na komputerze dewelopera przy zachowaniu połączenia z klastrem Kubernetes z resztą aplikacji lub usług. Jeśli na przykład masz dużą architekturę mikrousług z wieloma współzależnościami usług i baz danych, replikowanie tych zależności na komputerze deweloperskim może być trudne. Ponadto tworzenie i wdrażanie kodu w klastrze Kubernetes dla każdej zmiany kodu podczas tworzenia pętli wewnętrznej może być powolne, czasochłonne i trudne do użycia z debugerem.

Bridge to Kubernetes uniknąć konieczności kompilowania i wdrażania kodu w klastrze przez utworzenie połączenia bezpośrednio między komputerem dewelopera a klastrem. Połączenie komputera dewelopera z klastrem podczas debugowania umożliwia szybkie testowanie i opracowywanie usługi w kontekście pełnej aplikacji bez konieczności tworzenia konfiguracji platformy Docker lub Kubernetes.

Bridge to Kubernetes przekierowuje ruch między połączonym klastrem Kubernetes i komputerem dewelopera. To przekierowanie ruchu umożliwia kodowi na komputerze dewelopera i usługach uruchomionych w klastrze Kubernetes komunikowanie się tak, jakby były w tym samym klastrze Kubernetes. Bridge to Kubernetes umożliwia również replikowanie zmiennych środowiskowych i zainstalowanych woluminów dostępnych dla zasobników w klastrze Kubernetes na komputerze deweloperskim. Zapewnienie dostępu do zmiennych środowiskowych i woluminów zainstalowanych na komputerze dewelopera umożliwia szybką pracę nad kodem bez konieczności ręcznego replikowania tych zależności.

> [!WARNING]
> Bridge to Kubernetes jest przeznaczona tylko do użytku w scenariuszach testowania i testowania. Nie jest ona przeznaczona ani obsługiwana do użytku z klastrami produkcyjnymi lub usługami aktywnymi w aktywnym użyciu.

Informacje na temat obecnie obsługiwanych funkcji i przyszłego planu rozwoju Bridge to Kubernetes można znaleźć na stronie [Bridge to Kubernetes mapy.](https://github.com/microsoft/mindaro/projects/1)

## <a name="using-bridge-to-kubernetes"></a>Korzystanie z Bridge to Kubernetes

Aby korzystać z usługi Bridge to Kubernetes w programie Visual Studio, musisz mieć program [Visual Studio 2019][visual-studio] w wersji 16.7 (wersja zapoznawcza 4 lub nowsza) uruchomiony w programie Windows 10 z zainstalowanym obciążeniem *ASP.NET* i tworzeniem aplikacji internetowych oraz zainstalowanym rozszerzeniem [Bridge to Kubernetes.][btk-extension] W przypadku nawiązania połączenia z klastrem Kubernetes przy użyciu usługi Bridge to Kubernetes można przekierować cały ruch do i z istniejącego zasobnika w klastrze na komputer deweloperski.

> [!NOTE]
> Podczas Bridge to Kubernetes jest wyświetlany monit o nazwę usługi w celu przekierowania do komputera dewelopera. Ta opcja jest wygodnym sposobem identyfikowania zasobnika do przekierowywania. Całe przekierowanie między klastrem Kubernetes i komputerem deweloperskim jest dla zasobnika.

Po Bridge to Kubernetes nawiązania połączenia z klastrem:

* Monituje o skonfigurowanie usługi do zastąpienia w klastrze, portu na komputerze dewelopera do użycia dla kodu oraz zadania uruchamiania kodu w ramach akcji razowej.
* Zastępuje kontener w zasobniku w klastrze kontenerem agenta zdalnego, który przekierowuje ruch do komputera deweloperskiego.
* Uruchamia [port kubectl na][kubectl-port-forward] komputerze dewelopera w celu przekazywania ruchu z komputera dewelopera do zdalnego agenta uruchomionego w klastrze.
* Zbiera informacje o środowisku z klastra przy użyciu agenta zdalnego. Te informacje o środowisku obejmują zmienne środowiskowe, widoczne usługi, instalacji woluminów i instalacji tajnych.
* Konfiguruje środowisko w programie Visual Studio aby usługa na komputerze dewelopera była w stanie uzyskać dostęp do tych samych zmiennych, tak jakby była uruchomiona w klastrze.
* Aktualizuje plik hosts w celu mapowania usług w klastrze na lokalne adresy IP na komputerze dewelopera. Te wpisy pliku hostów umożliwiają kodowi uruchomionego na komputerze dewelopera tworzenie żądań do innych usług uruchomionych w klastrze. Aby zaktualizować plik hosts, Bridge to Kubernetes poprosi o dostęp administratora na komputerze dewelopera podczas nawiązywania połączenia z klastrem.
* Rozpoczyna uruchamianie i debugowanie kodu na komputerze dewelopera. W razie potrzeby Bridge to Kubernetes porty na komputerze dewelopera przez zatrzymanie usług lub procesów, które obecnie z nich korzystają.

Po nawiązaniu połączenia z klastrem można natywnie uruchamiać i debugować kod na komputerze bez konteneryzacji, a kod może bezpośrednio wchodzić w interakcje z resztą klastra. Każdy ruch sieciowy odbierany przez agenta zdalnego jest przekierowywany do portu lokalnego określonego podczas połączenia, dzięki czemu kod natywnie uruchomiony może akceptować i przetwarzać ten ruch. Zmienne środowiskowe, woluminy i wpisy tajne z klastra są udostępniane kodowi uruchomionemu na komputerze dewelopera. Ponadto ze względu na wpisy pliku hostów i przekazywanie portów dodane do komputera dewelopera przez program Bridge to Kubernetes kod może wysyłać ruch sieciowy do usług uruchomionych w klastrze przy użyciu nazw usług z klastra, a ruch jest przesyłany dalej do usług uruchomionych w klastrze. Ruch jest przekierowywany między komputerem dewelopera a klastrem przez cały czas połączenia.

Ponadto program Bridge to Kubernetes sposób replikowania zmiennych środowiskowych i zainstalowanych plików dostępnych dla zasobników w klastrze na komputerze deweloperskim za pośrednictwem `KubernetesLocalProcessConfig.yaml` pliku . Ten plik umożliwia również tworzenie nowych zmiennych środowiskowych i instalacji woluminów.

> [!NOTE]
> Przez czas trwania połączenia z klastrem (plus dodatkowe 15 minut) program Bridge to Kubernetes proces o nazwie *EndpointManager* z uprawnieniami administratora na komputerze lokalnym.

> [!NOTE]
> Możesz debugować równolegle, z wieloma usługami, ale musisz uruchomić tyle wystąpień usługi Visual Studio ile usług chcesz debugować. Upewnij się, że usługi nasłuchują na różnych portach lokalnie, a następnie skonfiguruj je i debuguj oddzielnie. Izolacja nie jest obsługiwana w tym scenariuszu.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Dodatkowa konfiguracja przy użyciu pliku KubernetesLocalProcessConfig.yaml

Plik `KubernetesLocalProcessConfig.yaml` umożliwia replikowanie zmiennych środowiskowych i zainstalowanych plików dostępnych dla zasobników w klastrze. W przypadku używania pliku Visual Studio do tworzenia aplikacji Bridge to Kubernetes plik KubernetesLocalConfig.yaml musi znajdować się w tym samym katalogu co plik projektu dla przekierowywanych usług. Aby uzyskać więcej informacji na temat dodatkowych opcji konfiguracji, zobacz [Konfigurowanie Bridge to Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Korzystanie z możliwości routingu do tworzenia aplikacji w izolacji

Domyślnie program Bridge to Kubernetes przekierowuje cały ruch usługi do komputera dewelopera. Możesz również użyć możliwości routingu, aby przekierowywać tylko żądania do usługi pochodzące z poddomeny na komputer dewelopera. Te możliwości routingu umożliwiają korzystanie z Bridge to Kubernetes w izolacji i uniknięcie zakłócania innego ruchu w klastrze.

Następująca animacja przedstawia dwóch deweloperów pracujących w tym samym klastrze w izolacji:

![Animowany obraz GIF ilustrujący izolację](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Po włączeniu pracy w izolacji program Bridge to Kubernetes oprócz nawiązywania połączenia z klastrem Kubernetes:

* Sprawdza, czy klaster Kubernetes nie ma włączonych Azure Dev Spaces.
* Replikuje wybraną usługę w klastrze w  tej samej przestrzeni nazw i dodaje etykietę routing.visualstudio.io/route-from=SERVICE_NAME i *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* adnotacji.
* Konfiguruje i uruchamia menedżera routingu w tej samej przestrzeni nazw w klastrze Kubernetes. Menedżer routingu używa selektora  etykiet do wyszukiwania etykiety routing.visualstudio.io/route-from=SERVICE_NAME i *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* podczas konfigurowania routingu w przestrzeni nazw.

Jeśli Bridge to Kubernetes, że Azure Dev Spaces w klastrze Kubernetes, zostanie wyświetlony monit o wyłączenie usługi Azure Dev Spaces przed użyciem Bridge to Kubernetes.

Podczas uruchamiania menedżera routingu są następujące czynności:

* Duplikuje wszystkie ruchy przychodzących (w tym ruch przychodzący usługi równoważenia obciążenia) znalezione w przestrzeni *nazw przy użyciu GENERATED_NAME* dla poddomeny.
* Tworzy zasobnik envoy dla każdej usługi skojarzonej ze  zduplikowanymi ruchami przychodzącymi GENERATED_NAME poddomeny.
* Tworzy dodatkowy zasobnik envoy dla usługi, nad która pracujesz w izolacji. Dzięki temu żądania z poddomeną mogą być kierowane do komputera dewelopera.
* Konfiguruje reguły routingu dla każdego zasobnika envoy w celu obsługi routingu dla usług z poddomeną.

Na poniższym diagramie przedstawiono klaster Kubernetes przed Bridge to Kubernetes się z klastrem:

![Diagram przedstawiający klaster bez Bridge to Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Na poniższym diagramie przedstawiono ten sam klaster z włączoną Bridge to Kubernetes w trybie izolacji. W tym miejscu możesz zobaczyć zduplikowaną usługę i zasobniki envoy, które obsługują routing w izolacji.

![Diagram klastra z włączonymi Bridge to Kubernetes klastra](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Gdy w klastrze zostanie *odebrane GENERATED_NAME* z poddomeną usługi , do żądania zostanie dodany nagłówek *kubernetes-route-as=GENERATED_NAME.* Zasobniki envoy obsługują routing tego żądania do odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, nad która jest pracowana w izolacji, to żądanie jest przekierowywany do komputera dewelopera przez agenta zdalnego.

Gdy żądanie bez *GENERATED_NAME* podrzędnej zostanie odebrane w klastrze, do żądania nie zostanie dodany żaden nagłówek. Zasobniki envoy obsługują routing tego żądania do odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, która jest zastępowana, to żądanie jest zamiast tego kierowane do oryginalnej usługi, a nie do agenta zdalnego.

> [!IMPORTANT]
> Każda usługa w klastrze musi przesyłać dalej nagłówek *kubernetes-route-as=GENERATED_NAME* podczas tworzenia dodatkowych żądań. Na przykład gdy *usługa A* odbiera żądanie, następnie wykonuje żądanie do *usługi serviceB* przed zwróceniem odpowiedzi. W tym przykładzie *usługa SERVICEA* musi przesyłać dalej nagłówek *kubernetes-route-as=GENERATED_NAME* w żądaniu do *usługi serviceB.* Niektóre języki, takie [jak ASP.NET][asp-net-header], mogą mieć metody do obsługi propagacji nagłówka.

Po rozłączeniu z klastrem program Bridge to Kubernetes wszystkie zasobniki envoy i zduplikowaną usługę.

> [!NOTE]
> Wdrożenie i usługa menedżera routingu pozostaną uruchomione w przestrzeni nazw. Aby usunąć wdrożenie i usługę, uruchom następujące polecenia dla przestrzeni nazw.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostyka i rejestrowanie

W przypadku Bridge to Kubernetes z klastrem dzienniki diagnostyczne z klastra są rejestrowane w katalogu *TEMP* komputera dewelopera w *Bridge to Kubernetes* klastra.

## <a name="rbac-authorization"></a>Autoryzacja RBAC

Na platformie Kubernetes są Access Control (RBAC) do zarządzania uprawnieniami użytkowników i grup. Aby uzyskać więcej informacji, zobacz dokumentację [usługi Kubernetes.](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) Aby ustawić uprawnienia dla klastra z włączoną obsługą RBAC, należy utworzyć plik YAML i zastosować go do klastra za pomocą `kubectl` narzędzia . 

Aby ustawić uprawnienia w klastrze, utwórz lub zmodyfikuj plik YAML, taki jak *permissions.yml,* w następujący sposób, używając własnej przestrzeni nazw dla tematów (użytkowników i grup), które `<namespace>` wymagają dostępu.

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

Zastosuj uprawnienia za pomocą polecenia :

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Ograniczenia

Bridge to Kubernetes ma następujące ograniczenia:

* Zasobnik może mieć uruchomiony tylko jeden kontener, aby Bridge to Kubernetes pomyślnie nawiązać połączenie.
* Obecnie Bridge to Kubernetes muszą być kontenerami systemu Linux. Kontenery systemu Windows nie są obsługiwane.
* Bridge to Kubernetes wymaga podwyższonego poziomu uprawnień do uruchamiania na komputerze dewelopera w celu edytowania pliku hosts.
* Bridge to Kubernetes nie można używać w klastrach z włączoną Azure Dev Spaces klastra.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Bridge to Kubernetes klastrów z włączonymi Azure Dev Spaces klastrami

Nie można używać funkcji Bridge to Kubernetes klastrze z włączonymi Azure Dev Spaces klastra. Jeśli chcesz używać funkcji Bridge to Kubernetes klastrze z włączoną Azure Dev Spaces, musisz wyłączyć Azure Dev Spaces przed nawiązaniem połączenia z klastrem.

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć nawiązywanie połączenia Bridge to Kubernetes lokalnym komputerem dewelopera z klastrem za pomocą usługi Bridge to Kubernetes [.](bridge-to-kubernetes.md)

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md

---
title: Jak działa Mostek na platformę Kubernetes
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: Zawiera opis procesów korzystania z usługi Bridge do Kubernetes w celu połączenia komputera deweloperskiego z klastrem Kubernetes
keywords: Mostek do Kubernetes, Docker, Kubernetes, Azure, kontenerów
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: d1a92433a90e6e6b7f71d0c7db6ced3a52c33315
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440613"
---
# <a name="how-bridge-to-kubernetes-works"></a>Jak działa Mostek na platformę Kubernetes

Usługa Bridge do Kubernetes umożliwia uruchamianie i debugowanie kodu na komputerze deweloperskim, przy jednoczesnym połączeniu z klastrem Kubernetes z pozostałą częścią aplikacji lub usług. Na przykład jeśli masz dużą architekturę mikrousług z wieloma zależnymi usługami i bazami danych, replikowanie tych zależności na komputerze deweloperskim może być trudne. Ponadto Kompilowanie i wdrażanie kodu w klastrze Kubernetes dla każdej zmiany kodu podczas programowania w pętli wewnętrznej może być powolne, czasochłonne i trudne do użycia z debugerem.

Mostek do Kubernetes pozwala uniknąć konieczności kompilowania i wdrażania kodu w klastrze przez utworzenie połączenia bezpośrednio między komputerem deweloperskim i klastrem. Połączenie komputera deweloperskiego z klastrem podczas debugowania umożliwia szybkie testowanie i opracowywanie usługi w kontekście pełnej aplikacji bez konieczności tworzenia żadnej konfiguracji platformy Docker lub Kubernetes.

Mostek do Kubernetes przekierowuje ruch między podłączonym klastrem Kubernetes i komputerem deweloperskim. To przekierowywanie ruchu umożliwia kod na komputerze deweloperskim i usługach uruchomionych w klastrze Kubernetes, aby komunikować się tak, jakby znajdowały się w tym samym klastrze Kubernetes. Mostek do Kubernetes umożliwia również replikowanie zmiennych środowiskowych i zainstalowanych woluminów dostępnych dla zasobników w klastrze Kubernetes na komputerze deweloperskim. Zapewnianie dostępu do zmiennych środowiskowych i zainstalowanych woluminów na komputerze deweloperskim pozwala szybko korzystać z kodu bez konieczności ręcznego replikowania tych zależności.

> [!WARNING]
> Mostek do Kubernetes jest przeznaczony do użycia tylko w scenariuszach deweloperskich i testowych. Nie jest ona przeznaczona do użycia ani nie jest obsługiwana w przypadku klastrów produkcyjnych lub usług na żywo w aktywnym użytkowaniu.

## <a name="using-bridge-to-kubernetes"></a>Korzystanie z mostka do Kubernetes

Aby można było używać programu Bridge do Kubernetes w programie Visual Studio, wymagany jest [program Visual studio 2019][visual-studio] w wersji 16,7 Preview 4 lub nowszy w systemie Windows 10 z zainstalowanym obciążeniem programu *ASP.NET i sieci Web* oraz zainstalowaną usługą [Bridge to Kubernetes Extension][btk-extension] . W przypadku używania programu Bridge do Kubernetes do nawiązywania połączenia z klastrem Kubernetes można przekierować cały ruch do i z istniejącego obszaru w klastrze do komputera deweloperskiego.

> [!NOTE]
> W przypadku korzystania z programu Bridge do Kubernetes zostanie wyświetlony monit o podanie nazwy usługi, która ma zostać przekierowana na komputer deweloperski. Ta opcja jest wygodnym sposobem identyfikacji pod kątem przekierowania. Wszystkie przekierowania między klastrem Kubernetes a komputerem deweloperskim dotyczą usługi pod.

Gdy mostek do Kubernetes nawiązuje połączenie z klastrem,:

* Zostanie wyświetlony komunikat z prośbą o skonfigurowanie usługi do zamiany na klaster, port na komputerze deweloperskim, który będzie używany w kodzie, oraz zadanie uruchamiania dla kodu jako akcję jednorazową.
* Zastępuje kontener w obszarze na klastrze z kontenerem zdalnego agenta, który przekierowuje ruch do komputera deweloperskiego.
* Uruchamia funkcję [polecenia kubectl port-forward][kubectl-port-forward] na komputerze deweloperskim, aby przekazywać ruch z komputera deweloperskiego do zdalnego agenta działającego w klastrze.
* Zbiera informacje o środowisku z klastra przy użyciu zdalnego agenta. Informacje o środowisku obejmują zmienne środowiskowe, widoczne usługi, instalacje woluminów i instalacje tajne.
* Konfiguruje środowisko w programie Visual Studio, aby usługa na komputerze deweloperskim mogła uzyskiwać dostęp do tych samych zmiennych, tak jakby były one uruchomione w klastrze.
* Aktualizuje plik hosts w celu mapowania usług w klastrze na lokalne adresy IP na komputerze deweloperskim. Te wpisy plików hostów umożliwiają uruchamianie kodu na komputerze deweloperskim w celu wykonywania żądań do innych usług uruchomionych w klastrze. Aby zaktualizować plik hosts, mostek do Kubernetes będzie pytał o dostęp administratora na komputerze deweloperskim podczas nawiązywania połączenia z klastrem.
* Uruchamia uruchamianie i debugowanie kodu na komputerze deweloperskim. W razie potrzeby program Bridge do Kubernetes będzie zwalniać wymagane porty na komputerze deweloperskim przez zatrzymywanie usług lub procesów, które aktualnie korzystają z tych portów.

Po nawiązaniu połączenia z klastrem można uruchomić i debugować kod natywnie na komputerze bez kontenerach, a kod może bezpośrednio współdziałać z resztą klastra. Każdy ruch sieciowy odbierany przez agenta zdalnego jest przekierowywany do portu lokalnego określonego podczas połączenia, dzięki czemu kod natywnie uruchomiony może zaakceptować i przetworzyć ten ruch. Zmienne środowiskowe, woluminy i wpisy tajne z klastra są udostępniane w kodzie uruchomionym na komputerze deweloperskim. Ponadto ze względu na to, że w przypadku wpisów w pliku Hosts i przekazywania portów dodano do komputera dewelopera przez mostek do Kubernetes, kod może wysyłać ruch sieciowy do usług uruchomionych w klastrze przy użyciu nazw usług z klastra, a ruch jest przesyłany do usług uruchomionych w klastrze. Ruch jest kierowany między komputerem deweloperskim i klastrem przez cały czas, gdy masz połączenie.

Ponadto program Bridge do Kubernetes umożliwia replikowanie zmiennych środowiskowych i zainstalowanych plików dostępnych dla zasobników w klastrze na komputerze deweloperskim przy użyciu `KubernetesLocalProcessConfig.yaml` pliku. Możesz również użyć tego pliku, aby utworzyć nowe zmienne środowiskowe i instalacje woluminów.

> [!NOTE]
> W przypadku czasu trwania połączenia z klastrem (plus dodatkowego 15 minut) mostek do Kubernetes uruchamia proces o nazwie *endpointmanager* z uprawnieniami administratora na komputerze lokalnym.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>Dodatkowa konfiguracja z KubernetesLocalProcessConfig. YAML

`KubernetesLocalProcessConfig.yaml`Plik umożliwia replikowanie zmiennych środowiskowych i zainstalowanych plików dostępnych dla Twojego zasobnika w klastrze. Aby uzyskać więcej informacji na temat dodatkowych opcji konfiguracji, zobacz [Konfigurowanie mostka do Kubernetes][using-config-yaml].

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>Korzystanie z funkcji routingu do programowania w izolacji

Domyślnie program Bridge do Kubernetes przekierowuje cały ruch dla usługi do komputera deweloperskiego. Istnieje również możliwość użycia funkcji routingu do przekierowywania tylko żądań do usługi pochodzącej z poddomeny do komputera deweloperskiego. Dzięki tym funkcjom routingu można używać programu Bridge do Kubernetes w celu rozbudowy izolacji i uniknięcia zakłócania innego ruchu w klastrze.

Poniższe animacje przedstawiają dwóch deweloperów pracujących nad tym samym klastrem w izolacji:

![Animowanie izolowania obrazu GIF](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

Po włączeniu pracy w izolacji program Bridge do Kubernetes wykonuje następujące czynności oprócz nawiązywania połączenia z klastrem Kubernetes:

* Sprawdza, czy klaster Kubernetes nie ma włączonej Azure Dev Spaces.
* Replikuje wybraną usługę w klastrze w tej samej przestrzeni nazw i dodaje etykietę *Routing.VisualStudio.IO/Route-from=service_name* i *Routing.VisualStudio.IO/Route-on-header=Kubernetes-Route-as: GENERATED_NAME* adnotację.
* Konfiguruje i uruchamia Menedżera routingu w tej samej przestrzeni nazw klastra Kubernetes. Menedżer routingu używa selektora etykiet do wyszukiwania etykiet *Routing.VisualStudio.IO/Route-from=service_name* i  *Routing.VisualStudio.IO/Route-on-header=Kubernetes-Route-as: GENERATED_NAME* adnotacji podczas konfigurowania routingu w przestrzeni nazw.

Jeśli program Bridge do Kubernetes wykryje, że Azure Dev Spaces jest włączona w klastrze Kubernetes, zostanie wyświetlony monit o wyłączenie Azure Dev Spaces, zanim będzie można użyć programu Bridge do Kubernetes.

Podczas uruchamiania Menedżer routingu wykonuje następujące czynności:
* Duplikuje wszystkie ingresses Znalezione w przestrzeni nazw za pomocą *GENERATED_NAME* dla domeny podrzędnej.
* Tworzy wysłannika pod dla każdej usługi skojarzonej z powielonym ingresses z poddomeną *GENERATED_NAME* .
* Tworzy dodatkowy wysłannika pod względem usługi, w której pracujesz w izolacji. Pozwala to na kierowanie żądań z poddomeną do komputera deweloperskiego.
* Konfiguruje reguły routingu dla każdego wysłannika pod względem obsługi routingu dla usług z poddomeną.

Na poniższym diagramie przedstawiono klaster Kubernetes przed nawiązaniem połączenia z klastrem Kubernetes przez mostek:

![Diagram klastra bez mostka do Kubernetes](media/bridge-to-kubernetes/kubr-cluster.svg)

Na poniższym diagramie przedstawiono ten sam klaster z mostkiem, który Kubernetes włączony w trybie izolacji. Tutaj można zobaczyć duplikat usługi i wysłannika, które obsługują Routing w izolacji.

![Diagram klastra z włączonym mostkiem do Kubernetes](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

Gdy w klastrze zostanie odebrane żądanie z poddomeną *GENERATED_NAME* , do żądania zostanie dodany nagłówek *Kubernetes-Route-as = GENERATED_NAME* . Wysłannika, które obsługują Routing, który żąda odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, która jest przetwarzana w izolacji, żądanie jest przekierowywane do komputera deweloperskiego przez agenta zdalnego.

Gdy w klastrze zostanie odebrane żądanie bez poddomeny *GENERATED_NAME* , nagłówek nie zostanie dodany do żądania. Wysłannika, które obsługują Routing, który żąda odpowiedniej usługi w klastrze. Jeśli żądanie jest kierowane do usługi, która jest zastępowana, to żądanie jest wysyłane do oryginalnej usługi zamiast agenta zdalnego.

> [!IMPORTANT]
> Każda usługa w klastrze musi przesłać dalej nagłówek *Kubernetes-Route-as = GENERATED_NAME* podczas wykonywania dodatkowych żądań. Na przykład gdy *Usługa Service* w odbierze żądanie, wysyła żądanie *serviceB* przed zwróceniem odpowiedzi. W tym przykładzie *Usługa Service* . musi przesłać dalej nagłówek *Kubernetes-Route-as = GENERATED_NAME* w żądaniu do *serviceB*. Niektóre języki, takie jak [ASP.NET][asp-net-header], mogą mieć metody obsługi propagacji nagłówka.

Po rozłączeniu z klastrem Domyślnie program Bridge do usługi Kubernetes usunie wszystkie wysłannikay i powieloną usługę.

> [!NOTE]
> Wdrożenie i usługa Menedżera routingu pozostaną uruchomione w Twojej przestrzeni nazw. Aby usunąć wdrożenie i usługę, uruchom następujące polecenia dla swojej przestrzeni nazw.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>Diagnostyka i rejestrowanie

W przypadku łączenia się z klastrem za pomocą mostka Kubernetes dzienniki diagnostyczne z klastra są rejestrowane w katalogu *tymczasowym* komputera deweloperskiego w *Bridge do folderu Kubernetes* .

## <a name="rbac-authorization"></a>Autoryzacja RBAC

Kubernetes zawiera Access Control oparte na rolach (RBAC) do zarządzania uprawnieniami dla użytkowników i grup. Aby uzyskać więcej informacji, zobacz [dokumentację Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) , aby ustawić uprawnienia dla klastra z WŁĄCZONĄ funkcją RBAC, tworząc plik YAML i używając `kubectl` go do zastosowania do klastra. 

Aby ustawić uprawnienia do klastra, Utwórz lub zmodyfikuj plik YAML, taki jak *uprawnienia. yml* jak poniżej, korzystając z własnej przestrzeni nazw dla `<namespace>` i tematów (użytkowników i grup), które wymagają dostępu.

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

Zastosuj uprawnienia za pomocą polecenia:

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>Ograniczenia

Mostek do Kubernetes ma następujące ograniczenia:

* Aby można było połączyć się z tą usługą, usługa musi być objęta usługą. Nie można nawiązać połączenia z usługą z wieloma zasobnikami, takimi jak usługa z replikami.
* Może istnieć tylko jeden kontener uruchomiony w tym pod, aby most Kubernetes pomyślnie nawiązać połączenie. Mostek do Kubernetes nie może nawiązać połączenia z usługami za pomocą zasobników z dodatkowymi kontenerami, takimi jak kontenery przyczepek z systemem.
* Obecnie mostek do Kubernetesy są kontenerami systemu Linux. Kontenery systemu Windows nie są obsługiwane.
* Nie można używać izolacji z protokołem HTTPS.
* Mostek do Kubernetes wymaga podniesionych uprawnień do uruchomienia na komputerze deweloperskim, aby można było edytować plik Hosts.
* Nie można używać mostu do Kubernetes w przypadku klastrów z włączonym Azure Dev Spaces.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Mostek do Kubernetes i klastrów z włączonym Azure Dev Spaces

Nie można użyć mostka do Kubernetes w klastrze z włączonym Azure Dev Spaces. Jeśli chcesz użyć programu Bridge do Kubernetes w klastrze z włączonym Azure Dev Spaces, musisz wyłączyć Azure Dev Spaces przed nawiązaniem połączenia z klastrem.

## <a name="next-steps"></a>Następne kroki

Aby rozpocząć korzystanie z usługi Bridge do Kubernetes w celu nawiązania połączenia z lokalnym komputerem deweloperskim z klastrem, zobacz [Korzystanie z mostka do Kubernetes](bridge-to-kubernetes.md).

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md